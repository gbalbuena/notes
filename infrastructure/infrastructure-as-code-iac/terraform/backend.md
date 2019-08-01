# Backend

Backend Policy Template

```javascript
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "0",
            "Effect": "Allow",
            "Action": [
                "s3:PutObject",
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::{bucket}/{objectsPrefix}*"
            ]
        },
        {
            "Sid": "1",
            "Effect": "Allow",
            "Action": [
                "dynamodb:PutItem",
                "dynamodb:DeleteItem",
                "dynamodb:GetItem"
            ],
            "Resource": [
                "arn:aws:dynamodb:{region}:{accountId}:table/{tableName}"
            ]
        },
        {
            "Sid": "2",
            "Effect": "Allow",
            "Action": "s3:ListBucket",
            "Resource": "arn:aws:s3:::{bucket}"
        }
    ]
}
```

