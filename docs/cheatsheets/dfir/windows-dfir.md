This cheatsheet provides a quick reference for DFIR analysis. It is not intended to be a comprehensive checklist, as the scope and depth of an investigation will vary depending on the context of the incident.

!!! info 

    This cheatsheet is mainly focusing on ransomware cases, but same methodology could be used in other cases as well.

## Narrowing Down the Timeline
- Windows Event Logs
    - **Event ID 1116 - Microsoft Defender malware detection**
        - Log: `Microsoft-Windows-Windows Defender/Operational`
        - Search for Defender alerts (if there's any) regarding the execution of ransomware binary or ransom note. Note that it does not necessarily represent the exact execution time.
- MFT
    - Ransom note creation: Search for the first ransom note creation time
    - File encryption: Search for the first file encryption time 

## Lateral Movement
### Incoming connection
- Windows Event Logs
    - **Event ID 4624 - Successful logon**
        - Log: `Security.evtx`
        - Relevant logon types include:
            - `Type 3 - Network`: Commonly associated with SMB, remote services, WinRM, and other network-based access.
            - `Type 10 - RemoteInteractive`: Commonly associated with a new RDP session.
            - `Type 7 - Unlock`: May appear when a user reconnects to or unlocks an existing session.
    - **Event ID 1149 - Successful RDP authentication**
        - Log: `Microsoft-Windows-TerminalServices-RemoteConnectionManager/Operational`
        - Indicates that a user successfully passed the RDP authentication stage on the destination system.
        - NOTE: This event does not always prove that a complete RDP session was established. It only confirms successful authentication. In order to prove successful connection, correlate with:
            - Event ID 4624, Logon Type 10
            - Terminal Services Event ID 21 for session logon
            - Event ID 25 for session reconnection
            - Event IDs 23 and 24 for logoff or disconnection 
- UsnJournal
    - `PSEXEC-[Source Hostname]-[8 Characters].key`

!!! tip

    If the log was cleared by the threat actor, review the last logoff time of the compromised/suspected compromised user to correlate with the incident.

- User Access Log
    - Location: `%SYSTEMROOT%\System32\LogFiles\SUM`
    - Filter the parsed UAL output for "File Server" under `Role Description` or `Role Name`.
    - Correlate the outcome with the compromised user, IP address, and the incident timeframe.

### Outgoing connection
- Windows Event Logs
    - Event ID 1024
        - Log: `Microsoft-Windows-TerminalServices-RDPClient/Operational`
    - Event ID 1102
        - Log: `Microsoft-Windows-TerminalServices-RDPClient/Operational`

### Additional Outbound Evidence
Correlate outbound RDP events with other source-system artifacts, including:

- RDP connection history in the user registry (`Terminal Server Client` registry key) 
- Prefetch for `mstsc.exe`

## Persistence
- Registry
    - **System Services**
        - Hive: `SYSTEM`
        - Path: `HKLM\SYSTEM\CurrentControlSet\Services`
    - **Scheduled TaskCache**
        - Hive: `SOFTWARE`
        - Path: `HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Schedule\TaskCache`
    - **Machine-Wide Run Keys**
        - Hive: `SOFTWARE`
        - Path: `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run`
                `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce`
    - **User Run Keys**
        - Hive: User's `NTUSER.DAT`
        - Path: `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Run`
                `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\RunOnce`
- Windows Event Log
    - **Event ID 7045 - Service/application installation**
        - Log: `System.evtx`
- MFT
    - Startup folders
        - User-Specific: `%APPDATA%\Microsoft\Windows\Start Menu\Programs\Startup`
        - All Users: `C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup`

## Exfiltration
*There are several activities that can indicate possible data exfiltration activities, such as data staging, significant amount of data browsing, execution of data transfering tools, etc.*

- Browser History
    - Accessing of file transfer websites, cloud storage services, attacker-controlled infrastructure, etc.
- PowerShell Command
    - Location: `%APPDATA%\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt`
        - Execution of commands for data exfiltration such as uploading files over HTTP, FTP, SMB, or cloud APIs.
        - Execution of commands for archiving files.
- Execution of Suspicous Tools
    - UserAssist
    - SRUM
    - Amcache
    - Shimcache
    - Windows Event Logs
- MFT
    - Evidence of data staging - Look for files created during the incident period (e.g. zip, 7z, rar, csv)