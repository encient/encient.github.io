# Detecting Pass-the-Ticket
## Attack Steps
1. Attacker gains admin access
2. Use tools like `Mimikatz` or `Rubeus` to extract valid TGT or TGS from compromised system
3. Attacker submits the extracted ticket for current logon session

## Detection
When Pass-the-Ticket is executed, the Kerberos Authentication process will be partial.

For example, an attacker imports a TGT ticket into a logon session and requests a TGS ticket for a remote service. From the Domain Controller perspective, the imported TGT was never requested before from the attacker’s system, so there won't be an associated Event ID 4768.

### Splunk Query
```bash
index=main source="WinEventLog:Security" user!=*$ EventCode IN (4768,4769,4770) 
| rex field=user "(?<username>[^@]+)"
| rex field=src_ip "(\:\:ffff\:)?(?<src_ip_4>[0-9\.]+)"
| transaction username, src_ip_4 maxspan=10h keepevicted=true startswith=(EventCode=4768)
| where closed_txn=0
| search NOT user="*$@*"
| table _time, ComputerName, username, src_ip_4, service_name, category
```