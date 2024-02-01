```bash
$ find . -type f -ls > ./analysis/files.out
$ du -sh ./analysis/files.out
2.9M    ./analysis/files.out
```
## forela-storage
```bash
./forela-storage/backups/ec2.py
./forela-storage/backups/forela-cytopia-ansible.tar
./forela-storage/backups/forela-static-site-version1.tar
./forela-storage/backups/forela-static-site-version2.tar
./forela-storage/backups/forela-static-site-version3.tar
./forela-storage/backups/jenkins-forela-automation.tar
./forela-storage/backups/test.txt
```
## CloudTrail logs
```bash
# dump all CloudTrail logs into one file
$ find ./CloudTrail -type f -exec cat {} \; > ./analysis/cloudtrail_logs.json
$ find ./CloudTrail -type f -exec cat {} \; > ./analysis/cloudtrail_logs.json
$ du -sh ./analysis/cloudtrail_logs.json
66M     ./analysis/cloudtrail_logs.json
```
## catscale_out_ip-172-31-24-20-20230130-1628

## poshc2_unusual_directories

## interview.txt
86.5.206.X
the S3 bucket directories in /forela-storage/