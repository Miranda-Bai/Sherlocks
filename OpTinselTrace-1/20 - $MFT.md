C:\$LogFile (NTFS Volume Log)
MFT (Managed _file_ transfer)

```powershell
PS D:\HTB\Tools> .\MFTECmd.exe -f 'D:\HTB\Sherlocks\optinseltrace1\elfidence_collection\TriageData\C\$MFT' --json D:\HTB\Sherlocks\optinseltrace1\analysis
$ du -sh '20240202075504_MFTECmd_$MFT_Output.json'
339M    20240202075504_MFTECmd_$MFT_Output.json
$ grep deliveries '20240202075504_MFTECmd_$MFT_Output.json'
```
![[Pasted image 20240202210005.png]]
2023-11-28 17:01:29 ^dc84ae
