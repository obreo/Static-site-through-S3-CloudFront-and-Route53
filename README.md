# Static-site-through-S3-CloudFront-and-Route53
## Designing Static Site with S3 and linking it to CloudFront distribution with route53 DNS (registered by GoDaddy)
![Architecture](/architecture.png)

### Instructions:
1. Create an S3 Bucket, Allow public access and enable access from bucket policy.
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "",
            "Effect": "Allow",
            "Principal": {
                "AWS": "*"
            },
            "Action": [
                "s3:ListBucket",
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::BUCKET/*",
                "arn:aws:s3:::BUCKET"
            ]
        }
    ]
}
```
2. From properties, enable static site and add index.html, and error.html for Index and error documents. 
Note: the names should be labeled as mentioned above because this is how S3 calls the objects.
3. Upload your static site and make your Index.html and error.html document in the root directory.

