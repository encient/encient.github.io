## Password Spraying Windows Event ID
Password spraying activity will create multiple failed logon attempts from different user accounts from the same source IP address within a short period of time. Therefore, we can search for `Event ID 4625 - Failed Logon` for potential password spraying attempts.

### Splunk Query
```bash
index=main source="WinEventLog:Security" EventCode=4625
| bin span=15m _time
| stats values(user) as Users, dc(user) as dc_user by src, Source_Network_Address, dest, EventCode, Failure_Reason
```
