```bash
$ cat ./C/Users/Simon.stark/AppData/Roaming/Notepad++/session.xml
<?xml version="1.0" encoding="UTF-8" ?>
<NotepadPlus>
    <Session activeView="0">
        <mainView activeIndex="1">
            <File firstVisibleLine="21" xOffset="0" scrollWidth="848" startPos="1697" endPos="1697" selMode="0" offset="0" wrapCount="1" lang="Java" encoding="-1" userReadOnly="no" filename="C:\Users\Simon.stark\Desktop\LootAndPurge.java" backupFilePath="C:\Users\Simon.stark\AppData\Roaming\Notepad++\backup\LootAndPurge.java@2023-07-24_145332" originalFileLastModifTimestamp="-1354503710" originalFileLastModifTimestampHigh="31047188" tabColourId="-1" mapFirstVisibleDisplayLine="-1" mapFirstVisibleDocLine="-1" mapLastVisibleDocLine="-1" mapNbLine="-1" mapHigherPos="-1" mapWidth="-1" mapHeight="-1" mapKByteInDoc="512" mapWrapIndentMode="-1" mapIsWrap="no" />
            <File firstVisibleLine="0" xOffset="0" scrollWidth="1072" startPos="672" endPos="672" selMode="0" offset="0" wrapCount="1" lang="None (Normal Text)" encoding="-1" userReadOnly="no" filename="C:\Users\Simon.stark\Desktop\YOU HAVE BEEN HACKED.txt" backupFilePath="C:\Users\Simon.stark\AppData\Roaming\Notepad++\backup\YOU HAVE BEEN HACKED.txt@2023-07-24_150548" originalFileLastModifTimestamp="1536217129" originalFileLastModifTimestampHigh="31047190" tabColourId="-1" mapFirstVisibleDisplayLine="-1" mapFirstVisibleDocLine="-1" mapLastVisibleDocLine="-1" mapNbLine="-1" mapHigherPos="-1" mapWidth="-1" mapHeight="-1" mapKByteInDoc="512" mapWrapIndentMode="-1" mapIsWrap="no" />
        </mainView>
        <subView activeIndex="0" />
    </Session>
</NotepadPlus>
```
C:\Users\Simon.stark\Desktop\LootAndPurge.java

[Need Explanation of a few Session.xml Parameters & Values](https://community.notepad-plus-plus.org/topic/22662/need-explanation-of-a-few-session-xml-parameters-values)

low=2940463585
`4294967296*high + low`

`low=4294967296+1354503710=5649471007`
`4294967296*31047188+5649471007=133346662742234656`

```bash
* originalFileLastModifTimestamp="-386892058" 
* originalFileLastModifTimestampHigh="30736076"
```
```sql
( 2^32 - (-386892058) ) * 30736076 + (-386892058) = 18-digit LDAP/FILETIME timestamp
```

```bash
(2^32 + 1354503710) * 31047188 - 1354503710
5649471006 * 31047188=175400188423831136
175400188423831136 - 1354503710 = 175400187069327424
```

```sql
high = 30736076 (from originalFileLastModifTimestampHigh)
low = -386892058 = -X (so X = 386892058) (from originalFileLastModifTimestamp)
2^32 = 4294967296 (yes, exponentiation)
full value = high * 2^32 + (2^32 - X) = 30736076 * 4294967296  + (4294967296 - 386892058)
```

`high * 2^32 + (2^32 - X) = 31047188 * 2^32  + (2^32 - 1354503710)=133346660033227232`
![[Pasted image 20240129172840.png]]
[LDAP to human date](https://www.epochconverter.com/ldap)
![[Pasted image 20240129172906.png]]
2023-07-24 09:53:23 ^65729e

`high * 2^32 + (2^32 - X) = 31047190 * 2^32  + (2^32 - 1536217129)=133346668441448400`