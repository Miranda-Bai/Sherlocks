```bash 
$ python3 vol.py --help | grep windows
    windows.bigpools.BigPools
    windows.cachedump.Cachedump
    windows.callbacks.Callbacks
    windows.cmdline.CmdLine
    windows.crashinfo.Crashinfo
    windows.devicetree.DeviceTree
                        a particular windows memory image.
    windows.dlllist.DllList
                        Lists the loaded modules in a particular windows
    windows.driverirp.DriverIrp
                        List IRPs for drivers in a particular windows memory
    windows.drivermodule.DriverModule
    windows.driverscan.DriverScan
                        Scans for drivers present in a particular windows
    windows.dumpfiles.DumpFiles
    windows.envars.Envars
    windows.filescan.FileScan
                        Scans for file objects present in a particular windows
    windows.getservicesids.GetServiceSIDs
    windows.getsids.GetSIDs
    windows.handles.Handles
    windows.hashdump.Hashdump
    windows.iat.IAT     Extract Import Address Table to list API (functions)
    windows.info.Info   Show OS & kernel details of the memory sample being
    windows.joblinks.JobLinks
    windows.ldrmodules.LdrModules
                        Lists the loaded modules in a particular windows
    windows.lsadump.Lsadump
    windows.malfind.Malfind
    windows.mbrscan.MBRScan
    windows.memmap.Memmap
    windows.mftscan.ADS
    windows.mftscan.MFTScan
                        windows memory image.
    windows.modscan.ModScan
                        Scans for modules present in a particular windows
    windows.modules.Modules
    windows.mutantscan.MutantScan
                        Scans for mutexes present in a particular windows
    windows.netscan.NetScan
                        windows memory image.
    windows.netstat.NetStat
                        particular windows memory image.
    windows.poolscanner.PoolScanner
    windows.privileges.Privs
    windows.pslist.PsList
                        Lists the processes present in a particular windows
    windows.psscan.PsScan
                        Scans for processes present in a particular windows
    windows.pstree.PsTree
    windows.registry.certificates.Certificates
    windows.registry.hivelist.HiveList
    windows.registry.hivescan.HiveScan
                        windows memory image.
    windows.registry.printkey.PrintKey
    windows.registry.userassist.UserAssist
    windows.sessions.Sessions
    windows.skeleton_key_check.Skeleton_Key_Check
    windows.ssdt.SSDT   Lists the system call table.
    windows.statistics.Statistics
    windows.strings.Strings
    windows.svcscan.SvcScan
                        Scans for windows services.
    windows.symlinkscan.SymlinkScan
                        Scans for links present in a particular windows memory
    windows.truecrypt.Passphrase
    windows.vadinfo.VadInfo
    windows.vadwalk.VadWalk
    windows.vadyarascan.VadYaraScan
    windows.verinfo.VerInfo
    windows.virtmap.VirtMap
```

```bash
$ python3 vol.py --help
Volatility 3 Framework 2.6.0
usage: volatility [-h] [-c CONFIG] [--parallelism [{processes,threads,off}]] [-e EXTEND] [-p PLUGIN_DIRS]
                  [-s SYMBOL_DIRS] [-v] [-l LOG] [-o OUTPUT_DIR] [-q] [-r RENDERER] [-f FILE] [--write-config]
                  [--save-config SAVE_CONFIG] [--clear-cache] [--cache-path CACHE_PATH] [--offline]
                  [--single-location SINGLE_LOCATION] [--stackers [STACKERS ...]]
                  [--single-swap-locations [SINGLE_SWAP_LOCATIONS ...]]
                  plugin ...

An open-source memory forensics framework

options:
  -h, --help            Show this help message and exit, for specific plugin options use 'volatility <pluginname>
                        --help'
  -c CONFIG, --config CONFIG
                        Load the configuration from a json file
  --parallelism [{processes,threads,off}]
                        Enables parallelism (defaults to off if no argument given)
  -e EXTEND, --extend EXTEND
                        Extend the configuration with a new (or changed) setting
  -p PLUGIN_DIRS, --plugin-dirs PLUGIN_DIRS
                        Semi-colon separated list of paths to find plugins
  -s SYMBOL_DIRS, --symbol-dirs SYMBOL_DIRS
                        Semi-colon separated list of paths to find symbols
  -v, --verbosity       Increase output verbosity
  -l LOG, --log LOG     Log output to a file as well as the console
  -o OUTPUT_DIR, --output-dir OUTPUT_DIR
                        Directory in which to output any generated files
  -q, --quiet           Remove progress feedback
  -r RENDERER, --renderer RENDERER
                        Determines how to render the output (quick, none, csv, pretty, json, jsonl)
  -f FILE, --file FILE  Shorthand for --single-location=file:// if single-location is not defined
  --write-config        Write configuration JSON file out to config.json
  --save-config SAVE_CONFIG
                        Save configuration JSON file to a file
  --clear-cache         Clears out all short-term cached items
  --cache-path CACHE_PATH
                        Change the default path (/home/mirandsec/.cache/volatility3) used to store the cache
  --offline             Do not search online for additional JSON files
  --single-location SINGLE_LOCATION
                        Specifies a base location on which to stack
  --stackers [STACKERS ...]
                        List of stackers
  --single-swap-locations [SINGLE_SWAP_LOCATIONS ...]
                        Specifies a list of swap layer URIs for use with single-location

Plugins:
  For plugin specific options, run 'volatility <plugin> --help'

  plugin
    banners.Banners     Attempts to identify potential linux banners in an image
    configwriter.ConfigWriter
                        Runs the automagics and both prints and outputs configuration in the output directory.
    frameworkinfo.FrameworkInfo
                        Plugin to list the various modular components of Volatility
    isfinfo.IsfInfo     Determines information about the currently available ISF files, or a specific one
    layerwriter.LayerWriter
                        Runs the automagics and writes out the primary layer produced by the stacker.
    linux.bash.Bash     Recovers bash command history from memory.
    linux.capabilities.Capabilities
                        Lists process capabilities
    linux.check_afinfo.Check_afinfo
                        Verifies the operation function pointers of network protocols.
    linux.check_creds.Check_creds
                        Checks if any processes are sharing credential structures
    linux.check_idt.Check_idt
                        Checks if the IDT has been altered
    linux.check_modules.Check_modules
                        Compares module list to sysfs info, if available
    linux.check_syscall.Check_syscall
                        Check system call table for hooks.
    linux.elfs.Elfs     Lists all memory mapped ELF files for all processes.
    linux.envars.Envars
                        Lists processes with their environment variables
    linux.iomem.IOMem   Generates an output similar to /proc/iomem on a running system.
    linux.keyboard_notifiers.Keyboard_notifiers
                        Parses the keyboard notifier call chain
    linux.kmsg.Kmsg     Kernel log buffer reader
    linux.lsmod.Lsmod   Lists loaded kernel modules.
    linux.lsof.Lsof     Lists all memory maps for all processes.
    linux.malfind.Malfind
                        Lists process memory ranges that potentially contain injected code.
    linux.mountinfo.MountInfo
                        Lists mount points on processes mount namespaces
    linux.proc.Maps     Lists all memory maps for all processes.
    linux.psaux.PsAux   Lists processes with their command line arguments
    linux.pslist.PsList
                        Lists the processes present in a particular linux memory image.
    linux.psscan.PsScan
                        Scans for processes present in a particular linux image.
    linux.pstree.PsTree
                        Plugin for listing processes in a tree based on their parent process ID.
    linux.sockstat.Sockstat
                        Lists all network connections for all processes.
    linux.tty_check.tty_check
                        Checks tty devices for hooks
    mac.bash.Bash       Recovers bash command history from memory.
    mac.check_syscall.Check_syscall
                        Check system call table for hooks.
    mac.check_sysctl.Check_sysctl
                        Check sysctl handlers for hooks.
    mac.check_trap_table.Check_trap_table
                        Check mach trap table for hooks.
    mac.ifconfig.Ifconfig
                        Lists network interface information for all devices
    mac.kauth_listeners.Kauth_listeners
                        Lists kauth listeners and their status
    mac.kauth_scopes.Kauth_scopes
                        Lists kauth scopes and their status
    mac.kevents.Kevents
                        Lists event handlers registered by processes
    mac.list_files.List_Files
                        Lists all open file descriptors for all processes.
    mac.lsmod.Lsmod     Lists loaded kernel modules.
    mac.lsof.Lsof       Lists all open file descriptors for all processes.
    mac.malfind.Malfind
                        Lists process memory ranges that potentially contain injected code.
    mac.mount.Mount     A module containing a collection of plugins that produce data typically found in Mac's mount
                        command
    mac.netstat.Netstat
                        Lists all network connections for all processes.
    mac.proc_maps.Maps  Lists process memory ranges that potentially contain injected code.
    mac.psaux.Psaux     Recovers program command line arguments.
    mac.pslist.PsList   Lists the processes present in a particular mac memory image.
    mac.pstree.PsTree   Plugin for listing processes in a tree based on their parent process ID.
    mac.socket_filters.Socket_filters
                        Enumerates kernel socket filters.
    mac.timers.Timers   Check for malicious kernel timers.
    mac.trustedbsd.Trustedbsd
                        Checks for malicious trustedbsd modules
    mac.vfsevents.VFSevents
                        Lists processes that are filtering file system events
    timeliner.Timeliner
                        Runs all relevant plugins that provide time related information and orders the results by
                        time.
    windows.bigpools.BigPools
                        List big page pools.
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
    windows.info.Info   Show OS & kernel details of the memory sample being analyzed.
    windows.joblinks.JobLinks
                        Print process job link information
    windows.ldrmodules.LdrModules
                        Lists the loaded modules in a particular windows memory image.
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
    windows.ssdt.SSDT   Lists the system call table.
    windows.statistics.Statistics
                        Lists statistics about the memory space.
    windows.strings.Strings
                        Reads output from the strings command and indicates which process(es) each string belongs to.
    windows.symlinkscan.SymlinkScan
                        Scans for links present in a particular windows memory image.
    windows.truecrypt.Passphrase
                        TrueCrypt Cached Passphrase Finder
    windows.vadinfo.VadInfo
                        Lists process memory ranges.
    windows.vadwalk.VadWalk
                        Walk the VAD tree.
    windows.virtmap.VirtMap
                        Lists virtual mapped sections.
```