```
D:\HTB\Tools\cmder
λ ..\MFTECmd.exe -f "D:\HTB\Sherlocks\ILikeTo\Triage\uploads\ntfs\%5C%5C.%5CC%3A\$MFT" --json D:\HTB\Sherlocks\ILikeTo\analysis\ --csv D:\HTB\Sherlocks\ILikeTo\analysis
MFTECmd version 1.2.2.1
```
![[Pasted image 20240124190845.png]]
## move.aspx uploaded date

^e5c469

```json
└─$ grep move.aspx 20240124060931_MFTECmd_\$MFT_Output.json | head -1 | jq .
{
  "EntryNumber": 1293,                                                                                              
  "SequenceNumber": 31,                                                                                             
  "ParentEntryNumber": 274233,                                                                                      
  "ParentSequenceNumber": 9,                                                                                        
  "InUse": true,                                                                                                    
  "ParentPath": ".\\MOVEitTransfer\\wwwroot",                                                                       
  "FileName": "move.aspx",                                                                                          
  "Extension": ".aspx",                                                                                             
  "IsDirectory": false,                                                                                             
  "HasAds": false,                                                                                                  
  "IsAds": false,                                                                                                   
  "FileSize": 1400,                                                                                                 
  "Created0x10": "2023-07-12T11:24:30.4297594+00:00",                                                               
  "LastModified0x10": "2023-07-12T11:24:30.4610703+00:00",                                                          
  "LastModified0x30": "2023-07-12T11:24:30.4297594+00:00",                                                          
  "LastRecordChange0x10": "2023-07-12T11:24:30.4610703+00:00",                                                      
  "LastRecordChange0x30": "2023-07-12T11:24:30.4297594+00:00",                                                      
  "LastAccess0x10": "2023-07-12T11:24:30.4610703+00:00",                                                            
  "LastAccess0x30": "2023-07-12T11:24:30.4297594+00:00",                                                            
  "UpdateSequenceNumber": 1808772160,                                                                               
  "LogfileSequenceNumber": 609836657,                                                                               
  "SecurityId": 1248,                                                                                               
  "SiFlags": 32,                                                                                                    
  "ReferenceCount": 1,                                                                                              
  "NameType": 1,                                                                                                    
  "Timestomped": false,                                                                                             
  "uSecZeros": false,                                                                                               
  "Copied": false,                                                                                                  
  "FnAttributeId": 2,                                                                                               
  "OtherAttributeId": 4                                                                                             
}              
```
## moveit.asp web shell doesn't work
```json
└─$ grep moveit.asp 20240124060931_MFTECmd_\$MFT_Output.json | jq .
{
  "EntryNumber": 100896,                                                                                            
  "SequenceNumber": 6,                                                                                              
  "ParentEntryNumber": 274233,                                                                                      
  "ParentSequenceNumber": 9,                                                                                        
  "InUse": true,                                                                                                    
  "ParentPath": ".\\MOVEitTransfer\\wwwroot",                                                                       
  "FileName": "moveit.asp",                                                                                         
  "Extension": ".asp",                                                                                              
  "IsDirectory": false,                                                                                             
  "HasAds": false,                                                                                                  
  "IsAds": false,                                                                                                   
  "FileSize": 1362,                                                                                                 
  "Created0x10": "2023-07-12T11:19:37.3316397+00:00",                                                               
  "LastModified0x10": "2023-07-12T11:17:12.7120642+00:00",                                                          
  "LastModified0x30": "2023-07-12T11:19:37.3316397+00:00",                                                          
  "LastRecordChange0x10": "2023-07-12T11:17:12.7120642+00:00",                                                      
  "LastRecordChange0x30": "2023-07-12T11:19:37.3316397+00:00",                                                      
  "LastAccess0x10": "2023-07-12T11:19:37.3316397+00:00",                                                            
  "UpdateSequenceNumber": 1808725272,                                                                               
  "LogfileSequenceNumber": 609575211,                                                                               
  "SecurityId": 1936,                                                                                               
  "SiFlags": 32,                                                                                                    
  "ReferenceCount": 1,                                                                                              
  "NameType": 3,                                                                                                    
  "Timestomped": false,                                                                                             
  "uSecZeros": false,                                                                                               
  "Copied": true,                                                                                                   
  "FnAttributeId": 2,                                                                                               
  "OtherAttributeId": 3                                                                                             
}                                                                                                                   
{
  "EntryNumber": 273729,                                                                                            
  "SequenceNumber": 50,                                                                                             
  "ParentEntryNumber": 265340,                                                                                      
  "ParentSequenceNumber": 5,                                                                                        
  "InUse": true,                                                                                                    
  "ParentPath": ".\\inetpub\\wwwroot",                                                                              
  "FileName": "moveit.asp",                                                                                         
  "Extension": ".asp",                                                                                              
  "IsDirectory": false,                                                                                             
  "HasAds": false,                                                                                                  
  "IsAds": false,                                                                                                   
  "FileSize": 1362,                                                                                                 
  "Created0x10": "2023-07-12T11:17:12.6808372+00:00",                                                               
  "LastModified0x10": "2023-07-12T11:17:12.7120642+00:00",                                                          
  "LastModified0x30": "2023-07-12T11:17:12.6808372+00:00",                                                          
  "LastRecordChange0x10": "2023-07-12T11:17:12.7120642+00:00",                                                      
  "LastRecordChange0x30": "2023-07-12T11:17:12.6808372+00:00",                                                      
  "LastAccess0x10": "2023-07-12T11:17:12.7120642+00:00",                                                            
  "LastAccess0x30": "2023-07-12T11:17:12.6808372+00:00",                                                            
  "UpdateSequenceNumber": 1808710920,                                                                               
  "LogfileSequenceNumber": 609432138,                                                                               
  "SecurityId": 1935,                                                                                               
  "SiFlags": 32,                                                                                                    
  "ReferenceCount": 1,                                                                                              
  "NameType": 3,                                                                                                    
  "Timestomped": false,                                                                                             
  "uSecZeros": false,                                                                                               
  "Copied": false,                                                                                                  
  "FnAttributeId": 2,                                                                                               
  "OtherAttributeId": 3                                                                                             
}             
```