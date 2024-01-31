```bash
$ cat files.out | uniq -c
 ./949622803460/CloudTrail/ap-northeast-1/
 ./949622803460/CloudTrail/ap-south-1/
 ./949622803460/CloudTrail/ap-southeast-1/
 ./949622803460/CloudTrail/ap-southeast-2/
 ./949622803460/CloudTrail/ca-central-1/
 ./949622803460/CloudTrail/eu-central-1/
 ./949622803460/CloudTrail/eu-north-1/
 ./949622803460/CloudTrail/me-south-1/
./949622803460/CloudTrail/sa-east-1/
./949622803460/CloudTrail/us-east-1/
./949622803460/CloudTrail/us-east-2/
./949622803460/CloudTrail/us-west-1/
./949622803460/CloudTrail/us-west-2/
```
## dump all json files into one file
```bash
$ find . -type f -exec cat {} \; > all.json
OR
$ find . -type f -name "*.json" -exec cat {} \; > all.json
$ du -sh all.json
40M     all.json
```
## find userAgent
```bash
$ jq '.Records | .[] | .userAgent' all.json | uniq -c > useragents.txt

```
## Find sourceIPAddress
```bash
$ jq '.Records | .[] | "\(.sourceIPAddress) \(.userAgent)"' all.json > sourceIPAddresses.out

$ cat sourceIPAddresses.out | uniq -c
$ cat sourceIPAddresses.out | uniq -c | grep kali
```
![[Pasted image 20240130172803.png]]
54.242.59.197
## Filter the activities done by TA (54.242.59.197)
```bash
$ jq '.Records | .[] | select(.sourceIPAddress=="54.242.59.197")' all.json | jq -s 'sort_by(.eventTime)' > activities.json

$ jq '.[] | select(.eventName == "GetObject")' activities.json | jq -s 'sort_by(.eventTime)' | less
```
The first record:
2023-11-02T14:52:03Z,prod-EC2-readonly_accessKeys.csv,anonymous
## Count access keys
```bash
$ jq '.[] | select(.eventName == "GetObject")' activities.json > getobjects.json
$ jq '.resources | .[] | .ARN' getobjects.json > filesARN.out
$ cat filesARN.out | awk -F ':' '{print $6}' | grep accessKeys
```
![[Pasted image 20240131101825.png]]
Access Keys files count 7

"userName": "dev-policy-specialist" has powerful can "eventName": "CopyObject"
```json
{
  "instancesSet": {},
  "filterSet": {
    "items": [
      {
        "name": "instance-state-name",
        "valueSet": {
          "items": [
            {
              "value": "running"
            }
          ]
        }
      }
    ]
  }
}
```
instance-state-name:running
## error messages
```bash
$ jq '.[] | .errorMessage' activities.json > errorMessages.out
$ cat errorMessages.out | tr -d "null" | grep "\S" | wc -l
42
```

![[Pasted image 20240131105443.png]]PutUserPolicy
```json
"requestParameters": {
    "userName": "dev-policy-specialist",
    "policyName": "sbhyy79zky",
    "policyDocument": "{\"Version\": \"2012-10-17\",\"Statement\": [{\"Effect\": \"Allow\",\"Action\": \"*\",\"Resource\": \"*\"}]}"
  },
```
sbhyy79zky,[{"Effect": "Allow","Action": "*","Resource": "*"}]

```json
 "eventVersion": "1.08",
  "userIdentity": {
    "type": "IAMUser",
    "principalId": "AIDA52GPOBQCG3LZF5EYW",
    "arn": "arn:aws:iam::949622803460:user/dev-policy-specialist",
    "accountId": "949622803460",
    "accessKeyId": "AKIA52GPOBQCMBGZADBX",
    "userName": "dev-policy-specialist"
  },
  "eventTime": "2023-11-02T15:26:53Z",
  "eventSource": "iam.amazonaws.com",
  "eventName": "CreateAccessKey",
  "awsRegion": "us-east-1",
  "sourceIPAddress": "54.242.59.197",
  "userAgent": "aws-cli/2.12.0 Python/3.11.4 Linux/6.3.0-kali1-cloud-amd64 source/x86_64.kali.2023 prompt/off command/iam.create-access-key",
  "requestParameters": {
    "userName": "forela-admin"
  },
  "responseElements": {
    "accessKey": {
      "accessKeyId": "AKIA52GPOBQCAB3EEAXZ",
      "status": "Active",
      "userName": "forela-admin",
      "createDate": "Nov 2, 2023 3:26:53 PM"
    }
  },
```

```bash
$ jq '.[] | select(.userIdentity.userName == "dev-policy-specialist")' activities.json > dev-policy-specialist.json
 "eventTime": "2023-11-02T15:26:02Z",
  "eventSource": "s3.amazonaws.com",
  "eventName": "CopyObject",
  "awsRegion": "us-east-1",
  "sourceIPAddress": "54.242.59.197",
  "userAgent": "[aws-cli/2.12.0 Python/3.11.4 Linux/6.3.0-kali1-cloud-amd64 source/x86_64.kali.2023 prompt/off command/s3.cp]",
  "requestParameters": {
    "bucketName": "forela-fileshare",
    "x-amz-server-side-encryption-aws-kms-key-id": "arn:aws:kms:us-east-1:263954014653:key/mrk-85e24f85d964469cba9e4589335dd0f4",
    "Host": "forela-fileshare.s3.us-east-1.amazonaws.com",
    "x-amz-server-side-encryption": "aws:kms",
    "x-amz-copy-source": "forela-fileshare/billing_data/Billing_Statement_2023_08.xlsx",
    "key": "billing_data/Billing_Statement_2023_08.xlsx"
  },
```
arn:aws:kms:us-east-1:263954014653:key/mrk-85e24f85d964469cba9e4589335dd0f4
```json
"eventTime": "2023-11-02T15:26:22Z",
  "eventSource": "s3.amazonaws.com",
  "eventName": "PutObject",
  "awsRegion": "us-east-1",
  "sourceIPAddress": "54.242.59.197",
  "userAgent": "[aws-cli/2.12.0 Python/3.11.4 Linux/6.3.0-kali1-cloud-amd64 source/x86_64.kali.2023 prompt/off command/s3.cp]",
  "requestParameters": {
    "bucketName": "forela-fileshare",
    "Host": "forela-fileshare.s3.us-east-1.amazonaws.com",
    "key": "README2DECRYPT.txt"
  },
```
README2DECRYPT.txt

AWS S3 Bucket actions