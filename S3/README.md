# S3

#### [aws_cdk.aws_s3.Bucket](https://docs.aws.amazon.com/cdk/api/latest/docs/@aws-cdk_aws-s3.Bucket.html)

```
s3.Bucket(self,"BuildArtifactBucket",
        bucket_name='<BUCKET_NAME>',
        versioned=True,
        block_public_access=s3.BlockPublicAccess(block_public_acls=True, block_public_policy=True, ignore_public_acls=True),
        encryption=s3.BucketEncryption.S3_MANAGED,
        removal_policy=core.RemovalPolicy.DESTROY)

```

#### [aws_cdk.aws_s3.BucketEncryption]()

```
encryption = s3.BucketEncryption.S3_MANAGED
```

#### [aws_cdk.core.RemovalPolicy]()

Determines what to do when the resource is removed from the app.

```
core.RemovalPolicy.DESTROY
```

#### aws_cdk.aws_s3.BlockPublicAccess

```
block_public_access=s3.BlockPublicAccess(block_public_acls=True, block_public_policy=True, ignore_public_acls=True),
```

#### aws_cdk.s3.CorsRule

```
cors=[s3.CorsRule(allowed_methods=[
            s3.HttpMethods.DELETE,
            s3.HttpMethods.POST,
            s3.HttpMethods.PUT,
            s3.HttpMethods.GET,
            s3.HttpMethods.HEAD],
            allowed_origins=["*"],
            max_age=3000)]
        )]
```

#### Update bucket policy of an existing bucket

```
bucket_policy = {
    "Statement": [
        {
            "Sid": "AllowSSLRequestsOnly",
            "Action": "s3:*",
            "Effect": "Deny",
            "Resource": [
                "arn:aws:s3:::grafana-metrics-test-bucket-kaise",
                "arn:aws:s3:::grafana-metrics-test-bucket-kaise/*"
            ],
            "Condition": {
                "Bool": {
                    "aws:SecureTransport": "false"
                }
            },
            "Principal": "*"
        }
    ]
 }

add_policy = s3.CfnBucketPolicy(self, "add_policy_to_bucket",
        #                                bucket="grafana-metrics-test-bucket-kaise", policy_document=bucket_policy)
```
