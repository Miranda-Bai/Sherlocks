- Mysql dump of moveit

`find . -type f -ls > files.out`
`less -S files.out`
`grep log$ files.out | less -S`
`grep config files.out | less -S`


- Logs
	- MoveIt
	- IIS logs
	- Windows Event logs
	- Powershell logs

- VMEM file (no VMSS)
- Registry hives (dump creds)
- MFT (MFT explorer, it will take hours to analyze it. Use [MFTECmd](https://github.com/EricZimmerman/MFTECmd))
- 