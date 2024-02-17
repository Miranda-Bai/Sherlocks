T1: What is the name of the email client that Elfin is using?
![[Pasted image 20240201193440.png]]eM Client
T2: What is the email the threat is using?`/home/kali/Desktop/optinseltrace1/elfidence_collection/TriageData/C/users/Elfin/Appdata/Roaming/eM Client/32969170-c98d-4a48-b444-526374e467e4/23848ff4-bf57-4577-bdb7-06e8a178560d/conversations.dat`
`/home/kali/Desktop/optinseltrace1/elfidence_collection/TriageData/C/users/Elfin/Appdata/Roaming/eM Client/32969170-c98d-4a48-b444-526374e467e4/23848ff4-bf57-4577-bdb7-06e8a178560d/mail_fti.dat`
![[Pasted image 20240202115139.png]]
definitelynotthegrinch@gmail.com
T3: When does the threat actor reach out to Elfin?
`Date 27/11/2023 17:27:26`
`2023-11-27 17:27:26`
T4: What is the name of Elfins boss?
![[Pasted image 20240202120225.png]]
`elfuttin bigelf`
T5: What is the title of the email in which Elfin first mentions his access to Santas special files?
Install eM Client; copy the 'eM Client' folder to `C:\Users\miran\AppData\Roaming`; then open the eM Client.
![[Pasted image 20240202191747.png]]
![[Pasted image 20240202193251.png]]
View Mail Header
Re: work

T6: The threat actor changes their name, what is the new name + the date of the first email Elfin receives with it?
![[Pasted image 20240202195035.png]]
It was 'Grinch Grincher' and then, changed to 'Wendy Elflower' but still same email address.
![[Pasted image 20240202195510.png]]
View Mail Source
`Wendy Elflower, 2023-11-28 10:00:21`

T7: What is the name of the bar that Elfin offers to meet the threat actor at?
![[Pasted image 20240202195646.png]]
SnowGlobe

T8: When does Elfin offer to send the secret files to the actor?
![[Pasted image 20240202200435.png]]
![[Pasted image 20240202200505.png]]
View Mail Header
2023-11-28 16:56:13

T9: What is the search string for the first suspicious google search from Elfin? (Format: string)
`D:\HTB\Sherlocks\optinseltrace1\elfidence_collection\TriageData\C\users\Elfin\Appdata\Local\Google\Chrome\User Data\Default\History`
![[Pasted image 20240202203608.png]]
how to get around work security

Another way is import the whole Google Chrome folder to the VM, and open Chrome to see the search history easily.

T10: What is the name of the author who wrote the article from the CIA field manual?
![[Pasted image 20240202204020.png]]
`https://www.corporate-rebels.com/blog/cia-field-manual`
![[Pasted image 20240202204039.png]]
Joost Minnaar

T11: What is the name of Santas secret file that Elfin sent to the actor?
![[Pasted image 20240202200830.png]]
santa_deliveries.zip

```bash
$ file santa_deliveries
santa_deliveries: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=cca09f1ef95bb11b258f9ce6c44a8084769012c3, for GNU/Linux 3.2.0, not stripped

$ strings santa_deliveries

```
![[Pasted image 20240217181543.png]]

T12: According to the filesystem, what is the exact CreationTime of the secret file on Elfins host?
2023-11-28 17:01:29[[20 - $MFT#^dc84ae]]

T13: What is the full directory name that Elfin stored the file in?
`C:\users\Elfin\Appdata\Roaming\top-secret`

T14: Which country is Elfin trying to flee to after he exfiltrates the file?
`D:\HTB\Sherlocks\optinseltrace1\elfidence_collection\TriageData\C\users\Elfin\Appdata\Local\Google\Chrome\User Data\Default\History`
In the search history of Google, I saw "flight to canada" and "flight to greece", I tried both Canada and Greece. It turns out the answer is Greece.
Greece

T15: What is the email address of the apology letter the user (elfin) wrote out but didn’t send?
![[Pasted image 20240202201124.png]]
In the Drafts box, there is an email sent to santa.
Santa.claus@gmail.com

T16: The head elf PixelPeppermint has requested any passwords of Elfins to assist in the investigation down the line. What’s the windows password of Elfin’s host?
Santaknowskungfu[[10 - Credentials#^1c15a4]]