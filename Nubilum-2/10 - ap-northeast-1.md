## ap-northeast-1/02/
```json
$ jq '.Records' 949622803460_CloudTrail_ap-northeast-1_20231102T0000Z
_iTnGWoyZFq1tF9fb.json
[
  {
    "eventVersion": "1.08",
    "userIdentity": {
      "type": "AWSService",
      "invokedBy": "resource-explorer-2.amazonaws.com"
    },
    "eventTime": "2023-11-01T23:59:45Z",
    "eventSource": "sts.amazonaws.com",
    "eventName": "AssumeRole",
    "awsRegion": "ap-northeast-1",
    "sourceIPAddress": "resource-explorer-2.amazonaws.com",
    "userAgent": "resource-explorer-2.amazonaws.com",
    "requestParameters": {
      "roleArn": "arn:aws:iam::949622803460:role/aws-service-role/resource-explorer-2.amazonaws.com/AWSServiceRoleForResourceExplorer",
      "roleSessionName": "resource-explorer-2",
      "durationSeconds": 3600
    },
    "responseElements": {
      "credentials": {
        "accessKeyId": "ASIA52GPOBQCMK47T5PB",
        "sessionToken": "IQoJb3JpZ2luX2VjEOj//////////wEaDmFwLW5vcnRoZWFzdC0xIkcwRQIhAIw2NtveAzzXBAOib/F5lm/R/XM+uSFZepZb7KRfOA0yAiBMKZmHYPEPRWeAlHrPhgcsAnwo/Pr4lGlaHo5FGgTy6CrwAgghEAAaDDk0OTYyMjgwMzQ2MCIMItyWqLdOuaOd4B2hKs0CxYr1+jBIUf/mLjsd9Gr3F42z4RoezNHHcq4PIZE3i/7jzj/yS9/GLDeZPdxpBhTnJGkHPgrDYmUC0yZafog09vWFcgMt0rb2xtQxhegu6HtvK5efPgVB3egZ+VjQWcXt4LCPlKiJNZ6IAoXQ6FIj9lK1i9JZXbUl94apm3ao1UFG3m3fVesMK7axRYwvxJirsT3XOnfZfr4yTH5+uEqLH9j0uoFz3CrInDEqXrw/IHxCl9Iqf3V/qf3G+AY3iXn6pkqwLNMlq++YOpztizeZQXF4wRA9Y2jwoOadosOrCAl1Gkg+J2kAY8GLTOMoROLyw/5CXYP42oBD+9a8dmQOdFpFRXLfUn/Wqfn9aAhI5J/8A3mHVwMCmBcfhaHengioBLoNy2iMVV+2nUMsxijqlFX51oTk4kEGi7KfN9GoquBWA145S2pc0lM1nfivMPHMi6oGOr8B69Id9Nr7NzylluKq77jAFz8EYojAzxWAgnSiYf+m2Cg2/DWF8t+4qR51muATG9kNAtil0o5VT8NWN3kH3ZtoebjE3fyaa0Uwh/CocKt6i2HNI4tAEnsDCh7+kZAbJeZ21lxuXIBD3HRN6ac+C+sJywSVrbIkathOyusNIOlosy3z9nrh+Q4HSN3x+f06fRQunh2GJe5t1W+QMUptgE9X3MRdlwmUtsSVgqexfsV7A5Gos+ScbF5+V/TtEHZkSl8=",
        "expiration": "Nov 2, 2023, 12:59:45 AM"
      },
      "assumedRoleUser": {
        "assumedRoleId": "AROA52GPOBQCC7XDYTFFH:resource-explorer-2",
        "arn": "arn:aws:sts::949622803460:assumed-role/AWSServiceRoleForResourceExplorer/resource-explorer-2"
      }
    },
    "requestID": "fb837910-2c85-4829-b623-9bf9c7759943",
    "eventID": "f42a24ed-0ffe-39e8-ac24-3a516ba6143d",
    "readOnly": true,
    "resources": [
      {
        "accountId": "949622803460",
        "type": "AWS::IAM::Role",
        "ARN": "arn:aws:iam::949622803460:role/aws-service-role/resource-explorer-2.amazonaws.com/AWSServiceRoleForResourceExplorer"
      }
    ],
    "eventType": "AwsApiCall",
    "managementEvent": true,
    "recipientAccountId": "949622803460",
    "sharedEventID": "1cfac190-0868-4dff-83ca-02a6833f680a",
    "eventCategory": "Management"
  },
  {
    "eventVersion": "1.08",
    "userIdentity": {
      "type": "AssumedRole",
      "principalId": "AROA52GPOBQCC7XDYTFFH:resource-explorer-2",
      "arn": "arn:aws:sts::949622803460:assumed-role/AWSServiceRoleForResourceExplorer/resource-explorer-2",
      "accountId": "949622803460",
      "accessKeyId": "ASIA52GPOBQCMK47T5PB",
      "sessionContext": {
        "sessionIssuer": {
          "type": "Role",
          "principalId": "AROA52GPOBQCC7XDYTFFH",
          "arn": "arn:aws:iam::949622803460:role/aws-service-role/resource-explorer-2.amazonaws.com/AWSServiceRoleForResourceExplorer",
          "accountId": "949622803460",
          "userName": "AWSServiceRoleForResourceExplorer"
        },
        "webIdFederationData": {},
        "attributes": {
          "creationDate": "2023-11-01T23:59:45Z",
          "mfaAuthenticated": "false"
        }
      },
      "invokedBy": "resource-explorer-2.amazonaws.com"
    },
    "eventTime": "2023-11-01T23:59:45Z",
    "eventSource": "elasticloadbalancing.amazonaws.com",
    "eventName": "DescribeLoadBalancers",
    "awsRegion": "ap-northeast-1",
    "sourceIPAddress": "resource-explorer-2.amazonaws.com",
    "userAgent": "resource-explorer-2.amazonaws.com",
    "requestParameters": null,
    "responseElements": null,
    "requestID": "afe14b4e-25ed-48a5-b089-31f58056302b",
    "eventID": "02035bee-6728-4128-90ac-fdac0ee6f77e",
    "readOnly": true,
    "eventType": "AwsApiCall",
    "apiVersion": "2015-12-01",
    "managementEvent": true,
    "recipientAccountId": "949622803460",
    "eventCategory": "Management"
  }
]
```

```bash
$ jq '.Records | .[] | .userAgent' -r * | uniq -c
 76 resource-explorer-2.amazonaws.com
```
## ap-northeast-1/03/
```bash
$ jq '.Records | .[] | .userAgent' -r * | uniq -c
20 resource-explorer-2.amazonaws.com
```