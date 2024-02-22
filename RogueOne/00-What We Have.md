A memory dump file
[Volatility 3 documentation](https://volatility3.readthedocs.io/en/latest/)
[Volatility 3 downlaod](https://www.volatilityfoundation.org/3)

```bash
$ python3 vol.py -f ../../Sherlocks/20230810.mem windows.info
Variable        Value

Kernel Base     0xf80178400000
DTB     0x16a000
Symbols file:///mnt/d/HTB/Tools/volatility3/volatility3/symbols/windows/ntkrnlmp.pdb/3789767E34B7A48A3FC80CE12DE18E65-1.json.xz
Is64Bit True
IsPAE   False
layer_name      0 WindowsIntel32e
memory_layer    1 FileLayer
KdVersionBlock  0xf8017900f398
Major/Minor     15.19041
MachineType     34404
KeNumberProcessors      8
SystemTime      2023-08-10 11:32:00
NtSystemRoot    C:\WINDOWS
NtProductType   NtProductWinNt
NtMajorVersion  10
NtMinorVersion  0
PE MajorOperatingSystemVersion  10
PE MinorOperatingSystemVersion  0
PE Machine      34404
PE TimeDateStamp        Mon Nov 24 23:45:00 2070
```

```bash
$ python3 vol.py -f ../../Sherlocks/20230810.mem windows.netscan.NetScan
```
![[Pasted image 20240222184203.png]]
172.17.79.131   64254   **13.127.155.166  8888**    ESTABLISHED     6812    svchost.exe     2023-08-10 11:30:03.000000 ^f3d79e

```bash
$ python3 vol.py -f ../../Sherlocks/20230810.mem windows.pslist.PsList | grep 6812
```

^61c0e4

![[Pasted image 20240222184722.png]]

```bash
$ python3 vol.py -f ../../Sherlocks/20230810.mem windows.dumpfiles.DumpFiles --pid 6812
```
![[Pasted image 20240222190228.png]]The first svchost.exe command shows dump file unsuccessfully, but we still get ImageSectionObject.
```bash
$ md5sum file.0x9e8b91ec0140.0x9e8b957f24c0.ImageSectionObject.svchost.exe.img
5bd547c6f5bfc4858fe62c8867acfbb5  file.0x9e8b91ec0140.0x9e8b957f24c0.ImageSectionObject.svchost.exe.img
```

^72b00e

```bash
$ python3 vol.py -f ~/HTB/sherlocks/20230810.mem windows.pslist.PsList
```
![[Pasted image 20240223114125.png]]![[Pasted image 20240223114158.png]]
0x9e8b87762080 ^a6465f

Upload file.0x9e8b91ec0140.0x9e8b957f24c0.ImageSectionObject.svchost.exe.img to [VirusTotal](https://www.virustotal.com/gui/home/search)
![[Pasted image 20240223114625.png]]
![[Pasted image 20240223114734.png]]
First submitted on 10/08/2023 11:58:10 ^0aea0d