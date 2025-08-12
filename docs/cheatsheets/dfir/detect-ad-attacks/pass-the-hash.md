# Detecting Pass-the-Hash
## Attack Steps
1. Use Mimikatz to extract NTLM hash of currently logged user on the compromised system (local admin priv required)
2. Use Mimikatz with the hash and authenticate as the targeted user
3. Move laterally within the network to gain access to systems and resources

## Detection - Look for Event ID 4624 with Logon Type 9
### Splunk Query
```bash
index=main source="WinEventLog:Security" EventCode=4624 Logon_Type=9 Logon_Process=seclogo
| table _time, ComputerName, EventCode, user, Network_Account_Domain, Network_Account_Name, Logon_Type, Logon_Process
```

## Detection - Look for LSASS memory access
### Splunk Query
```bash
index=main (source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=10 TargetImage="C:\\Windows\\system32\\lsass.exe" SourceImage!="C:\\ProgramData\\Microsoft\\Windows Defender\\platform\\*\\MsMpEng.exe") OR (source="WinEventLog:Security" EventCode=4624 Logon_Type=9 Logon_Process=seclogo)
| sort _time, RecordNumber
| transaction host maxspan=1m endswith=(EventCode=4624) startswith=(EventCode=10)
| stats count by _time, Computer, SourceImage, SourceProcessId, Network_Account_Domain, Network_Account_Name, Logon_Type, Logon_Process
| fields - count
```