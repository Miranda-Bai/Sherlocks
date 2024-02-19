T1: What is the MD5 sum of the binary the Threat Actor found the S3 bucket location in?
Most commonly, md5sum is used **to verify that a file has not changed as a result of a faulty file transfer, a disk error or non-malicious modification**. Every file in the GDC contains an md5sum to ensure file integrity.
The same data always has the same MD5 hash, so if you transfer a file and it has a different MD5 hash at the destination than at the source, then the file was corrupted.
```bash
/optinseltrace1/elfidence_collection/TriageData/C/users/Elfin/Appdata/Roaming/top-secret$ md5sum santa_deliveries
62d5c1f1f9020c98f97d8085b9456b05  santa_deliveries
```
The result relies on "optinseltrace1".
62d5c1f1f9020c98f97d8085b9456b05

T2: What time did the Threat Actor begin their automated retrieval of the contents of our exposed S3 bucket?
2023-11-29 08:24:07[[OpTinselTrace-2/00 - What We Have#^387e61|00 - What We Have]]

T3: What time did the Threat Actor complete their automated retrieval of the contents of our exposed S3 bucket?
2023-11-29 08:24:16[[OpTinselTrace-2/00 - What We Have#^387e61|00 - What We Have]]

T4: Based on the Threat Actor's user agent - what scripting language did the TA likely utilise to retrieve the files?
python

T5: Which file did the Threat Actor locate some hard coded credentials within?
claus.py [[OpTinselTrace-2/00 - What We Have#^5ea14c]]

T6: Please detail all confirmed malicious IP addresses. (Ascending Order)
45.133.193.41, 191.101.31.57 [[OpTinselTrace-2/00 - What We Have#^9a5ea4|00 - What We Have]]

T7: We are extremely concerned the TA managed to compromise our private S3 bucket, which contains an important VPN file. Please confirm the name of this VPN file and the time it was retrieved by the TA.
bytesparkle.ovpn, 2023-11-29 10:16:53 [[OpTinselTrace-2/00 - What We Have#^fc8b78]]

T8: Please confirm the username of the compromised AWS account?
elfadmin [[OpTinselTrace-2/00 - What We Have#^9a5ea4|00 - What We Have]]

T9: Based on the analysis completed Santa Claus has asked for some advice. What is the ARN of the S3 Bucket that requires locking down?
arn:aws:s3:::papa-noel [[OpTinselTrace-2/00 - What We Have#^5f8df2|00 - What We Have]]