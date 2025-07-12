icon:material/memory

This is a cheatsheet mainly for analyzing Windows memory using Volatility 2 and Volatility 3.

??? info "List of All Plugins Available"
    === "Volatility 2"
        ```
        atoms           Print session and window station atom tables
        atomscan        Pool scanner for atom tables
        bigpools        Dump the big page pools using BigPagePoolScanner
        bioskbd         Reads the keyboard buffer from Real Mode memory
        callbacks       Print system-wide notification routines
        clipboard       Extract the contents of the windows clipboard
        cmdline         Display process command-line arguments
        cmdscan         Extract command history by scanning for _COMMAND_HISTORY
        connections     Print list of open connections [Windows XP and 2003 Only]
        connscan        Pool scanner for tcp connections
        consoles        Extract command history by scanning for _CONSOLE_INFORMATION
        crashinfo       Dump crash-dump information
        deskscan        Poolscaner for tagDESKTOP (desktops)
        devicetree      Show device tree
        dlldump         Dump DLLs from a process address space
        dlllist         Print list of loaded dlls for each process
        driverirp       Driver IRP hook detection
        drivermodule    Associate driver objects to kernel modules
        driverscan      Pool scanner for driver objects
        dumpcerts       Dump RSA private and public SSL keys
        dumpfiles       Extract memory mapped and cached files
        editbox         Displays information about Edit controls. (Listbox experimental.)
        eventhooks      Print details on windows event hooks
        filescan        Pool scanner for file objects
        gahti           Dump the USER handle type information
        gditimers       Print installed GDI timers and callbacks
        gdt             Display Global Descriptor Table
        handles         Print list of open handles for each process
        hibinfo         Dump hibernation file information
        hivedump        Prints out a hive
        hivelist        Print list of registry hives.
        hivescan        Pool scanner for registry hives
        hpakextract     Extract physical memory from an HPAK file
        hpakinfo        Info on an HPAK file
        idt             Display Interrupt Descriptor Table
        iehistory       Reconstruct Internet Explorer cache / history
        imagecopy       Copies a physical address space out as a raw DD image
        imageinfo       Identify information for the image
        impscan         Scan for calls to imported functions
        joblinks        Print process job link information
        kdbgscan        Search for and dump potential KDBG values
        kpcrscan        Search for and dump potential KPCR values
        ldrmodules      Detect unlinked DLLs
        machoinfo       Dump Mach-O file format information
        malfind         Find hidden and injected code
        mbrparser       Scans for and parses potential Master Boot Records (MBRs)
        memdump         Dump the addressable memory for a process
        memmap          Print the memory map
        messagehooks    List desktop and thread window message hooks
        mftparser       Scans for and parses potential MFT entries
        moddump         Dump a kernel driver to an executable file sample
        modscan         Pool scanner for kernel modules
        modules         Print list of loaded modules
        multiscan       Scan for various objects at once
        mutantscan      Pool scanner for mutex objects
        notepad         List currently displayed notepad text
        objtypescan     Scan for Windows object type objects
        patcher         Patches memory based on page scans
        poolpeek        Configurable pool scanner plugin
        printkey        Print a registry key, and its subkeys and values
        privs           Display process privileges
        procdump        Dump a process to an executable file sample
        pslist          Print all running processes by following the EPROCESS lists
        psscan          Pool scanner for process objects
        pstree          Print process list as a tree
        psxview         Find hidden processes with various process listings
        qemuinfo        Dump Qemu information
        raw2dmp         Converts a physical memory sample to a windbg crash dump
        screenshot      Save a pseudo-screenshot based on GDI windows
        sessions        List details on _MM_SESSION_SPACE (user logon sessions)
        sockets         Print list of open sockets
        sockscan        Pool scanner for tcp socket objects
        strings         Match physical offsets to virtual addresses (may take a while, VERY verbose)
        symlinkscan     Pool scanner for symlink objects
        thrdscan        Pool scanner for thread objects
        timers          Print kernel timers and associated module DPCs
        unloadedmodules Print list of unloaded modules
        userhandles     Dump the USER handle tables
        vaddump         Dumps out the vad sections to a file
        vadinfo         Dump the VAD info
        vadtree         Walk the VAD tree and display in tree format
        vadwalk         Walk the VAD tree
        vboxinfo        Dump virtualbox information
        verinfo         Prints out the version information from PE images
        vmwareinfo      Dump VMware VMSS/VMSN information
        volshell        Shell in the memory image
        windows         Print Desktop Windows (verbose details)
        wintree         Print Z-Order Desktop Windows Tree
        wndscan         Pool scanner for window stations
        yarascan        Scan process or kernel memory with Yara signatures
        ```

    === "Volatility 3"
        ```
        timeliner.Timeliner
                            Runs all relevant plugins that provide time related information and orders the results by time.
        windows.bigpools.BigPools
                            List big page pools.
        windows.cachedump.Cachedump
                            Dumps lsa secrets from memory
        windows.callbacks.Callbacks
                            Lists kernel callbacks and notification routines.
        windows.cmdline.CmdLine
                            Lists process command line arguments.
        windows.crashinfo.Crashinfo
                            Lists the information from a Windows crash dump.
        windows.devicetree.DeviceTree
                            Listing tree based on drivers and attached devices in a particular windows memory image.
        windows.dlllist.DllList
                            Lists the loaded modules in a particular windows memory image.
        windows.driverirp.DriverIrp
                            List IRPs for drivers in a particular windows memory image.
        windows.drivermodule.DriverModule
                            Determines if any loaded drivers were hidden by a rootkit
        windows.driverscan.DriverScan
                            Scans for drivers present in a particular windows memory image.
        windows.dumpfiles.DumpFiles
                            Dumps cached file contents from Windows memory samples.
        windows.envars.Envars
                            Display process environment variables
        windows.filescan.FileScan
                            Scans for file objects present in a particular windows memory image.
        windows.getservicesids.GetServiceSIDs
                            Lists process token sids.
        windows.getsids.GetSIDs
                            Print the SIDs owning each process
        windows.handles.Handles
                            Lists process open handles.
        windows.hashdump.Hashdump
                            Dumps user hashes from memory
        windows.info.Info   Show OS & kernel details of the memory sample being analyzed.
        windows.joblinks.JobLinks
                            Print process job link information
        windows.ldrmodules.LdrModules
                            Lists the loaded modules in a particular windows memory image.
        windows.lsadump.Lsadump
                            Dumps lsa secrets from memory
        windows.malfind.Malfind
                            Lists process memory ranges that potentially contain injected code.
        windows.mbrscan.MBRScan
                            Scans for and parses potential Master Boot Records (MBRs)
        windows.memmap.Memmap
                            Prints the memory map
        windows.modscan.ModScan
                            Scans for modules present in a particular windows memory image.
        windows.modules.Modules
                            Lists the loaded kernel modules.
        windows.mutantscan.MutantScan
                            Scans for mutexes present in a particular windows memory image.
        windows.netscan.NetScan
                            Scans for network objects present in a particular windows memory image.
        windows.netstat.NetStat
                            Traverses network tracking structures present in a particular windows memory image.
        windows.poolscanner.PoolScanner
                            A generic pool scanner plugin.
        windows.privileges.Privs
                            Lists process token privileges
        windows.pslist.PsList
                            Lists the processes present in a particular windows memory image.
        windows.psscan.PsScan
                            Scans for processes present in a particular windows memory image.
        windows.pstree.PsTree
                            Plugin for listing processes in a tree based on their parent process ID.
        windows.registry.certificates.Certificates
                            Lists the certificates in the registry's Certificate Store.
        windows.registry.hivelist.HiveList
                            Lists the registry hives present in a particular memory image.
        windows.registry.hivescan.HiveScan
                            Scans for registry hives present in a particular windows memory image.
        windows.registry.printkey.PrintKey
                            Lists the registry keys under a hive or specific key value.
        windows.registry.userassist.UserAssist
                            Print userassist registry keys and information.
        windows.sessions.Sessions
                            lists Processes with Session information extracted from Environmental Variables
        windows.skeleton_key_check.Skeleton_Key_Check
                            Looks for signs of Skeleton Key malware
        windows.ssdt.SSDT   Lists the system call table.
        windows.statistics.Statistics
                            Lists statistics about the memory space.
        windows.strings.Strings
                            Reads output from the strings command and indicates which process(es) each string belongs to.
        windows.symlinkscan.SymlinkScan
                            Scans for links present in a particular windows memory image.
        windows.vadinfo.VadInfo
                            Lists process memory ranges.
        windows.vadwalk.VadWalk
                            Walk the VAD tree.
        windows.verinfo.VerInfo
                            Lists version information from PE files.
        windows.virtmap.VirtMap
                            Lists virtual mapped sections.
        ```


## System Information
---
### Identify image information / profile
=== "Volatility 2"
    ``` 
    vol.py -f /path/to/image imageinfo
    ```

=== "Volatility 3"
    ``` 
    vol.py -f /path/to/image windows.info
    ```

## Process Information
---
### List running processes
=== "Volatility 2"
    ``` 
    vol.py -f /path/to/image --profile=<profile> pstree
    vol.py -f /path/to/image --profile=<profile> pslist
    vol.py -f /path/to/image --profile=<profile> psscan
    ```

=== "Volatility 3"
    ``` 
    vol.py -f /path/to/image windows.pstree
    vol.py -f /path/to/image windows.pslist
    vol.py -f /path/to/image windows.psscan
    ```

### Identify file handles
This reveals the resources and objects a process is interacting with
=== "Volatility 2"
    ```
    vol.py -f /path/to/image --profile=<profile> handles -p <pid> --object-type=Key
    vol.py -f /path/to/image --profile=<profile> handles -p <pid> --object-type=File
    vol.py -f /path/to/image --profile=<profile> handles -p <pid> --object-type=Process
    ```

=== "Volatility 3"
    ```
    vol.py -f /path/to/image windows.handles --pid <pid>
    ```

### Identify loaded DLLs
=== "Volatility 2"
    ``` 
    vol.py -f /path/to/image --profile=<profile> dlllist -p <pid>
    ```

=== "Volatility 3"
    ``` 
    vol.py -f /path/to/image windows.dlllist --pid <pid>
    ```

## Network Information
---
### Identify network artifacts
=== "Volatility 2"
    ``` 
    vol.py -f /path/to/image --profile=<profile> netstat
    vol.py -f /path/to/image --profile=<profile> netscan
    ```

=== "Volatility 3"
    ``` 
    vol.py -f /path/to/image windows.netstat
    vol.py -f /path/to/image windows.netscan
    ```

## File Information
---
### List files
=== "Volatility 2"
    ``` 
    vol.py -f /path/to/image --profile=<profile> filescan
    ```

=== "Volatility 3"
    ``` 
    vol.py -f /path/to/image windows.filescan
    ```

### Extract files
=== "Volatility 2"
    ``` 
    vol.py -f /path/to/image --profile=<profile> dumpfiles ‑‑dump-dir="/path/to/output/dir"
    vol.py -f /path/to/image --profile=<profile> dumpfiles ‑‑dump-dir="/path/to/output/dir" -Q <offset>
    vol.py -f /path/to/image --profile=<profile> dumpfiles ‑‑dump-dir="/path/to/output/dir" -p <pid>
    ```

=== "Volatility 3"
    ``` 
    vol.py -f /path/to/image -o /path/to/output/dir windows.dumpfiles
    vol.py -f /path/to/image -o /path/to/output/dir windows.dumpfiles ‑‑virtaddr <offset>
    vol.py -f /path/to/image -o /path/to/output/dir windows.dumpfiles ‑‑physaddr <offset>
    ```

## Registry Information
---
### List registry hives
=== "Volatility 2"
    ``` 
    vol.py -f /path/to/image --profile=<profile> hivescan
    vol.py -f /path/to/image --profile=<profile> hivelist
    ```

=== "Volatility 3"
    ``` 
    vol.py -f /path/to/image windows.hivescan
    vol.py -f /path/to/image windows.hivelist
    ```

### List registry key values
=== "Volatility 2"
    ``` 
    vol.py -f /path/to/image --profile=<profile> printkey
    vol.py -f /path/to/image --profile=<profile> printkey -K "<key-path>"
                                                               # e.g. Software\Microsoft\Windows\CurrentVersion
    ```

=== "Volatility 3"
    ``` 
    vol.py -f /path/to/image windows.registry.printkey
    vol.py -f /path/to/image windows.registry.printkey --key "<key-path>"
                                                               # e.g. Software\Microsoft\Windows\CurrentVersion
    ```

## User Activity
---
### List executed commands
=== "Volatility 2"
    ``` 
    vol.py -f /path/to/image --profile=<profile> cmdline
    vol.py -f /path/to/image --profile=<profile> cmdscan
    vol.py -f /path/to/image --profile=<profile> consoles
    ```

=== "Volatility 3"
    ``` 
    vol.py -f /path/to/image windows.cmdline
    ```

### List clipboard contents
=== "Volatility 2"
    ``` 
    vol.py -f /path/to/image --profile=<profile> clipboard
    ```

=== "Volatility 3"
    ``` 
    N/A
    ```

## Miscellaneous
---
### Identify injected code
=== "Volatility 2"
    ``` 
    vol.py -f /path/to/image --profile=<profile> malfind
    ```

=== "Volatility 3"
    ``` 
    vol.py -f /path/to/image windows.malfind
    ```

### List environment variables
=== "Volatility 2"
    ``` 
    vol.py -f /path/to/image --profile=<profile> envars
    ```

=== "Volatility 3"
    ``` 
    vol.py -f /path/to/image windows.envars
    ```

### Dump password hashes
=== "Volatility 2"
    ``` 
    vol.py -f /path/to/image --profile=<profile> hashdump
    ```

=== "Volatility 3"
    ``` 
    vol.py -f /path/to/image windows.hashdump
    ```

### Dump LSA secrets
=== "Volatility 2"
    ``` 
    vol.py -f /path/to/image --profile=<profile> lsadump
    ```

=== "Volatility 3"
    ``` 
    vol.py -f /path/to/image windows.lsadump
    ```

## Strings
---
### Find IPv4 addresses
```
strings /path/to/image | grep -E "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b"
```

### Find email addresses
```
strings /path/to/image | grep -oE "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}\b"
```

### Find CMD or PowerShell artifacts
```
strings /path/to/image | grep -E "(cmd|powershell|bash)[^\s]+"
```

