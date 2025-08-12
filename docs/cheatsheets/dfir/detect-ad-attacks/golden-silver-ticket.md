# Detecting Golden Tickets and Silver Tickets
## Golden Ticket
### Attack Steps
1. Attacker extract NTLM hash of KRBTGT account using DCSync attack
    1. or can use NTDS.dit and LSASS process dumps on Domain Controller
2. Forge a fake user acc with KRBTGT hash and assign it to Domain Admin
3. The attacker injects the forged TGT in the same manner as a Pass-the-Ticket attack

### Detection
Detecting Golden Ticket attacks can be challenging, as the TGT can be forged offline by an attacker, leaving virtually no traces of `Mimikatz` execution. One option is to monitor common methods of extracting the `KRBTGT` hash:

- `DCSync attack`
- `NTDS.dit file access`
- `LSASS memory read on the domain controller (Sysmon Event ID 10)`

From another standpoint, a Golden Ticket is just another ticket for Pass-the-Ticket detection.

```bash
index=main source="WinEventLog:Security" user!=*$ EventCode IN (4768,4769,4770) 
| rex field=user "(?<username>[^@]+)"
| rex field=src_ip "(\:\:ffff\:)?(?<src_ip_4>[0-9\.]+)"
| transaction username, src_ip_4 maxspan=10h keepevicted=true startswith=(EventCode=4768)
| where closed_txn=0
| search NOT user="*$@*"
| table _time, ComputerName, username, src_ip_4, service_name, category
```

## Silver Ticket
### Attack Steps
1. The attacker extracts the NTLM hash of the targeted service account (or the computer account for `CIFS` access) using tools like `Mimikatz` or other credential dumping techniques.
2. Generate a Silver Ticket: Using the extracted NTLM hash, the attacker employs tools like `Mimikatz` to create a forged TGS ticket for the specified service.
3. The attacker injects the forged TGT in the same manner as a Pass-the-Ticket attack.

### Detecting Silter Tickets Through User Correlation
- Event ID 4720 - Identify newly created users (cuz attacker created fake user acc)
    - Then can compare the list with logged-in users

Create a list of users with Event ID 4720
```bash
index=main latest=1690448444 EventCode=4720
| stats min(_time) as _time, values(EventCode) as EventCode by user
| outputlookup users.csv
```

Compare list above with logged-in users
```bash
index=main latest=1690545656 EventCode=4624
| stats min(_time) as firstTime, values(ComputerName) as ComputerName, values(EventCode) as EventCode by user
| eval last24h = 1690451977
| where firstTime > last24h
```| eval last24h=relative_time(now(),"-24h@h")```
| convert ctime(firstTime)
| convert ctime(last24h)
| lookup users.csv user as user OUTPUT EventCode as Events
| where isnull(Events)
```

### Detecting Silter Tickets by Targeting Special Privileges Assigned To New Logon
- Event ID 4672 - Detect anomalously assigned privileges

```bash
index=main latest=1690545656 EventCode=4672
| stats min(_time) as firstTime, values(ComputerName) as ComputerName by Account_Name
| eval last24h = 1690451977 
```| eval last24h=relative_time(now(),"-24h@h") ```
| where firstTime > last24h 
| table firstTime, ComputerName, Account_Name 
| convert ctime(firstTime)
```