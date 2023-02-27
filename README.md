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
4. In CloudFront, create a new distruibution and assign the S3 bucket. Allow redirect from HTTP to HTTPS.

#### Setting domain name:
1. After registering your domain name, go to AWS certificates manager and assign your domain for SSL request.
2. If your domain is registered by Route53, then simply you can record CNAME key and value in your DNS settings in route53. for GoDaddy, in DNS settings, add new record and insert the CNAME values. It will take time until the SSL request get certified.
3. If you want to use Route53 DNS Host, then create a new Hosted Zone in Route53, and assign your example.com.
4. Now copy the NS DNS route traffic and replace your GoDaddy route traffic in the GoDaddy DNS settings.
5. Apply step 2
6. In CloudFront distribution, edit the `Alternate domain names` and add the same URL domain URL you regsitered in the SSL certificate and choosethe SSL certificate you created. The changes will take time to make the change, so have patience.

