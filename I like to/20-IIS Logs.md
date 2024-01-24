Log range: 2023-07-12 10:08:39 - 2023-07-12 11:24:47 
/home/kali/HTB/sherlocks/ILikeTo/Triage/uploads/auto/C%3A/inetpub/logs/LogFiles/W3SVC2

## Server IP's
```
└─$ grep -v '\#' u_ex230712.log | awk '{print $3}' | sort | uniq -c
     34 ::1
    303 10.10.0.25
      6 127.0.0.1
```
## Client IP's
```
└─$ grep -v '\#' u_ex230712.log | awk '{print $9}' | sort | uniq -c
	34 ::1
     29 10.255.254.2
    274 10.255.254.3
      6 127.0.0.1

```
## User Agents

^868d43

```
└─$ grep -v '\#' u_ex230712.log | awk '{print $10}' | sort | uniq -c
     16 -
      2 AnyConnect+Darwin_i386+3.1.05160
     34 CWinInetHTTPClient
     51 Mozilla/5.0+(compatible;+Nmap+Scripting+Engine;+https://nmap.org/book/nse.html)
     29 Mozilla/5.0+(Macintosh;+Intel+Mac+OS+X+10_15_7)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/114.0.0.0+Safari/537.36
     64 Mozilla/5.0+(X11;+Linux+x86_64;+rv:102.0)+Gecko/20100101+Firefox/102.0
    147 Ruby
```

```
└─$ grep nmap u_ex230712.log
2023-07-12 10:11:15 10.10.0.25 OPTIONS / - 80 - 10.255.254.3 Mozilla/5.0+(compatible;+Nmap+Scripting+Engine;+https://nmap.org/book/nse.html) - 200 0 0 101
```
 ![[Pasted image 20240124155236.png]]
 10.255.254.3 is the attacker's IP address.

## Uploaded aspx files
```
└─$ grep -v '\#' u_ex230712.log | awk '{print $5}' | sort | uniq -c | grep aspx | sort
      2 /move.aspx
     34 /machine2.aspx
      5 /human.aspx
     64 /guestaccess.aspx
      6 /machine.aspx
```

```
└─$ grep -v '\#' u_ex230712.log | awk '{print $9" "$5}' | sort | uniq -c | grep aspx | sort
      2 10.255.254.3 /move.aspx
     34 ::1 /machine2.aspx
      5 10.255.254.3 /human.aspx
      6 127.0.0.1 /machine.aspx
     64 10.255.254.3 /guestaccess.aspx
```
::1 is localhost, machine2.aspx can only be accessed by localhost.

```
└─$ grep -v '\#' u_ex230712.log | awk '{print $9" "$5}' | sort | uniq -c | grep aspx | sort | grep 254.3
      2 10.255.254.3 /move.aspx
      5 10.255.254.3 /human.aspx
     64 10.255.254.3 /guestaccess.aspx

```
## Files accessed by the attacker
```
└─$ grep move.aspx u_ex230712.log                                                                       
2023-07-12 11:24:43 10.10.0.25 GET /move.aspx - 443 - 10.255.254.3 Mozilla/5.0+(X11;+Linux+x86_64;+rv:102.0)+Gecko/20100101+Firefox/102.0 - 200 0 0 1179
2023-07-12 11:24:47 10.10.0.25 POST /move.aspx - 443 - 10.255.254.3 Mozilla/5.0+(X11;+Linux+x86_64;+rv:102.0)+Gecko/20100101+Firefox/102.0 https://moveit.htb/move.aspx 200 0 0 159
```
## Analyze MoveIt exploit
[moveit_cve_2023_34362.rb](https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/windows/http/moveit_cve_2023_34362.rb)

## Uploaded files
```
└─$ grep upload u_ex230712.log   
2023-07-12 10:24:57 10.10.0.25 POST /api/v1/folders/966794435/files uploadType=resumable 443 - 10.255.254.3 Ruby - 200 0 0 303
2023-07-12 10:25:02 10.10.0.25 PUT /api/v1/folders/966794435/files uploadType=resumable&fileId=974134622 443 - 10.255.254.3 Ruby - 500 0 0 581
2023-07-12 10:47:06 10.10.0.25 POST /api/v1/folders/966794435/files uploadType=resumable 443 - 10.255.254.3 Ruby - 200 0 0 141
2023-07-12 10:47:08 10.10.0.25 PUT /api/v1/folders/966794435/files uploadType=resumable&fileId=974134892 443 - 10.255.254.3 Ruby - 500 0 0 156
2023-07-12 11:01:00 10.10.0.25 POST /api/v1/folders/966794435/files uploadType=resumable 443 - 10.255.254.3 Ruby - 200 0 0 101
2023-07-12 11:01:02 10.10.0.25 PUT /api/v1/folders/966794435/files uploadType=resumable&fileId=974274452 443 - 10.255.254.3 Ruby - 500 0 0 140
2023-07-12 11:01:51 10.10.0.25 POST /api/v1/folders/966794435/files uploadType=resumable 443 - 10.255.254.3 Ruby - 200 0 0 131
2023-07-12 11:01:54 10.10.0.25 PUT /api/v1/folders/966794435/files uploadType=resumable&fileId=974155582 443 - 10.255.254.3 Ruby - 500 0 0 135
2023-07-12 11:04:37 10.10.0.25 POST /api/v1/folders/966794435/files uploadType=resumable 443 - 10.255.254.3 Ruby - 200 0 0 384
2023-07-12 11:04:41 10.10.0.25 PUT /api/v1/folders/966794435/files uploadType=resumable&fileId=974355270 443 - 10.255.254.3 Ruby - 500 0 0 433
2023-07-12 11:06:37 10.10.0.25 POST /api/v1/folders/966794435/files uploadType=resumable 443 - 10.255.254.3 Ruby - 200 0 0 128
2023-07-12 11:06:40 10.10.0.25 PUT /api/v1/folders/966794435/files uploadType=resumable&fileId=974331243 443 - 10.255.254.3 Ruby - 500 0 0 137
2023-07-12 11:07:25 10.10.0.25 POST /api/v1/folders/966794435/files uploadType=resumable 443 - 10.255.254.3 Ruby - 200 0 0 144
2023-07-12 11:07:28 10.10.0.25 PUT /api/v1/folders/966794435/files uploadType=resumable&fileId=974387947 443 - 10.255.254.3 Ruby - 500 0 0 87
2023-07-12 11:08:32 10.10.0.25 POST /api/v1/folders/966794435/files uploadType=resumable 443 - 10.255.254.3 Ruby - 200 0 0 144
2023-07-12 11:08:35 10.10.0.25 PUT /api/v1/folders/966794435/files uploadType=resumable&fileId=974247918 443 - 10.255.254.3 Ruby - 500 0 0 103
```