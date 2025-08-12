# Detecting Overpass-the-Hash/Pass-the-Key
## Attack Steps
1. Use Mimikatz to extract NTLM hash of current logged on user in compromised system (local admin priv required)
2. Use Rubeus to craft AS-REQ request for a specific user to request a TGT ticket (does not require elevated priv)
3. Analogous to the Pass-the-Ticket technique, the attacker submits the requested ticket for the current logon session

## Detection
Attack using `Mimikatz` leaves the same artifacts as Pass-the-Hash attack, hence it can be detected using the same strategies.
However, attack using `Rubeus` is different. Unless the requested TGT is used on another host, Pass-the-Ticket detection mechanisms may not be effective, as Rubeus sends an AS-REQ request directly to the Domain Controller (DC), generating Event ID 4768 (Kerberos TGT Request). However, communication with the DC (TCP/UDP port 88) from an unusual process can serve as an indicator of a potential Overpass-the-Hash attack.

### Splunk Query
```bash
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" (EventCode=3 dest_port=88 Image!=*lsass.exe) OR EventCode=1
| eventstats values(process) as process by process_id
| where EventCode=3
| stats count by _time, Computer, dest_ip, dest_port, Image, process
| fields - count
```