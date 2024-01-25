```bash
$ find . | grep evtx | grep -i defender
./auto/C%3A/Windows/System32/winevt/Logs/Microsoft-Windows-Windows Defender%254Operational.evtx
./auto/C%3A/Windows/System32/winevt/Logs/Microsoft-Windows-Windows Defender%254WHC.evtx

$ DEFDIR='/home/kali/HTB/sherlocks/ILikeTo/Triage/uploads/auto/C%3A/Windows/System32/winevt/Logs/Microsoft-Windows-Windows Defender%254Operational.evtx'
$ chainsaw hunt -s /opt/chainsaw/sigma -r /opt/chainsaw/rules -m /opt/chainsaw/mappings/sigma-event-logs-all.yml $DEFDIR -o defender.chainsaw 

$ chainsaw dump $DEFDIR --json -o defender.json
```
