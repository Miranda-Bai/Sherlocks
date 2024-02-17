```bash
$ find . -type f -ls > files.out
$ du -sh files.out
524K    files.out
```
## Dump all json files into one file
```bash
$ find . -type f -name "*.json" -exec cat {} \; > all.json
$ du -sh all.json
33M     all.json
```

```json
$ jq '.Records | .[]' all.json | head -100
```

## Find UserAgents
```bash
$ jq '.Records | .[] | .userAgent' all.json > useragents.out
$ du -sh useragents.out
1.3M    useragents.out
```
## S3 bucket
```json
$ jq '.Records | .[] | .resources | .[] | select(.type == "AWS::S3::Bucket")' all.json | head -100
```

```bash
$ jq '.Records | .[] | select(.eventName=="GetBucketLocation")' all.json
```
## Source IP Address
```bash
$ jq '.Records | .[] | .sourceIPAddress' all.json > sourceIPAddress.out
# delete quote char in the file
$ sed -i 's/"//g' sourceIPAddress.out
# delete space in the file 
```
## GetObject Events
```bash
$ jq '.Records | .[] | select(.eventName=="GetObject")' all.json | jq -s 'sort_by(.eventTime)'
> GetObjectEvents.out

```
```bash
$ jq '.Records[] | select(.eventName=="GetObject") | [.eventTime, .sourceIPAddress, .userIdentity.arn, .eventName] | @tsv' all.json | sort | less
```
![[Pasted image 20240217185826.png]]
2023-11-29 08:24:07
2023-11-29 08:24:16

### Why the threat actor's IP address in 191.101.31.57?
```bash
$ jq '.Records[] | [.sourceIPAddress, .userAgent] | @tsv' all.json | grep python | uniq -c
  1321 "86.5.206.121\t[Boto3/1.29.7 md/Botocore#1.32.7 ua/2.0 os/linux#6.2.0-37-generic md/arch#x86_64 lang/python#3.10.12 md/pyimpl#CPython cfg/retry-mode#legacy Botocore/1.32.7]"
     43 "191.101.31.57\t[python-requests/2.25.1]"
```
![[Pasted image 20240217190417.png]]

```bash
/mnt/d/HTB/Sherlocks/optinseltrace1/elfidence_collection/TriageData/C/Users/Elfin/Appdata/Roaming/top-secret
$ strings santa_deliveries
```
![[Pasted image 20240217191726.png]]https://papa-noel.s3.eu-west-3.amazonaws.com/santa-list.csv
christmas_log.txt

Check the link: https://papa-noel.s3.eu-west-3.amazonaws.com/

Download claus.py
https://papa-noel.s3.eu-west-3.amazonaws.com/NPoleScripts/claus.py
![[Pasted image 20240217192250.png]]Download git commit message
https://papa-noel.s3.eu-west-3.amazonaws.com/NPoleScripts/.git/COMMIT_EDITMSG
![[Pasted image 20240217192523.png]]

```bash
$ jq '.Records[] | [.sourceIPAddress, .userIdentity.userName] | @tsv' all.json | sort -u
"109.205.185.126\t"
"138.199.59.46\t"
"191.101.31.26\t"
"191.101.31.57\t"
"191.101.31.57\telfadmin"
"195.181.170.226\t"
"3.236.115.9\t"
"3.236.226.247\t"
"45.133.193.41\telfadmin"
"45.148.104.164\t"
"86.5.206.121\t"
"86.5.206.121\telfadmin"
"86.5.206.121\tterraform-gumdrop"
"X.X.X.X\telfin"
"X.X.X.X\tsnowball"
"access-analyzer.amazonaws.com\t"
"cloudtrail.amazonaws.com\t"
"dynamodb.application-autoscaling.amazonaws.com\t"
"resource-explorer-2.amazonaws.com\t"
```
191.101.31.57 (TA) has logged as elfadmin, so elfadmin got compromised.
45.133.193.41, 191.101.31.57