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