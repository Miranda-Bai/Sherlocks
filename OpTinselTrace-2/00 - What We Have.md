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