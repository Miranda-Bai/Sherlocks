```bash
$ jq '.Records | .[] | "\(.userAgent) \(.sourceIPAddress)"' cloudtrail_logs.json | uniq -c | less

$ jq '.Records | .[]' cloudtrail_logs.json | jq -s 'sort_by(.eventTime)' > sortedbytime.json
```