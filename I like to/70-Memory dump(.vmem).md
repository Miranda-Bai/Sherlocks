```bash
$ strings I-like-to-27a787c5.vmem > analysis/strings.vmem
$ grep moveitsvc strings.vmem
```
![[Pasted image 20240125223811.png]]
5trongP4ssw0rd
## net user command to change user's password
```bash
$ grep moveitsvc strings.vmem | sort | uniq -c
net user "moveitsvc" 5trongP4ssw0rd
```

^1753a6

## The title header of the webshell (move.aspx)
```bash
$ grep -B20 -A20 move.aspx strings.vmem | less -S
:/title
<title>awen asp.net webshell</title>
```

^1a6201

![[Pasted image 20240125224438.png]]