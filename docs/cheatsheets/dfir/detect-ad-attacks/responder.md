# Detecting Responder-like Attacks
## Search by Sysmon Event ID 22
We can use `Sysmon Event ID 22` to track the DNS queries associated with non-existent or mistyped file shares to detect possible Responder-like attacks.

### Splunk Query
```bash
index=main EventCode=22 
| table _time, Computer, user, Image, QueryName, QueryResults
```

## Search by Windows Event ID 4648
We can also use `Windows Security Event ID 4648 (A logon was attempted using explicit credentials.)` to detect explicit logons to rogue file shares which attackers might use to gather legitimate user credentials.

### Splunk Query
```bash
index=main EventCode IN (4648) 
| table _time, EventCode, source, name, user, Target_Server_Name, Message
| sort 0 _time
```