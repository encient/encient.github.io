# Detecting Unconstrained Delegation/Constrained Delegation Attacks
## Unconstraned Delegation
### Attack Steps
1. Attacker identifies system with Unconstrained Delegation enabled
2. Attacker gain access to the system
3. Attacker extracts TCT from memory using Mimikatz

### Detection
- Event ID 4104 - PowerShell script block logging
- LDAP request logging
- The main goal of an Unconstrained Delegation attack is to retrieve and reuse TGT tickets, so Pass-the-Ticket detection can be used as well

```bash
index=main source="WinEventLog:Microsoft-Windows-PowerShell/Operational" EventCode=4104 Message="*TrustedForDelegation*" OR Message="*userAccountControl:1.2.840.113556.1.4.803:=524288*" 
| table _time, ComputerName, EventCode, Message
```

## Contrained Delegation
### Attack Steps
1. Attacker identifies systems with Constrained Delegation enabled and determine which resources they are allowed to delegate
2. Attacker gains access to the TGT of the principal (user/computer)
    1. can be extracted from memory (Rubeus dump)
    2. can also be requested with the principal’s hash
3. Attacker uses S4U technique to impersonate a high-privileged account to the targeted service (requesting a TGS ticket)
4. Attacker injects the requested ticket and accesses targeted services as the impersonated user

### Detection
- Event ID 4104 - PowerShell script block logging
- LDAP request logging
- Unusual process network connection to TCP/UDP port `88` (Kerberos)

```bash
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" 
| eventstats values(process) as process by process_id
| where EventCode=3 AND dest_port=88
| table _time, Computer, dest_ip, dest_port, Image, process
```