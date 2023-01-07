---
title : "AWS CLI with Amazon S3"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

#### Use the AWS CLI to initialize an S3 resource.

1. Implement using **CLI** to interact with S3. For example, create **S3** bucket.

```
aws s3 mb s3://aws-cli-2000
```

![AWS CLI](/images/3-s3/0001.png?featherlight=false&width=10pc)

2. Checklist **s3 bucket**

```
aws s3 ls
```

![AWS CLI](/images/3-s3/0002.png?featherlight=false&width=10pc)

3. Check the object in the s3 bucket.

```
aws s3 ls s3://bucket-name
```

![AWS CLI](/images/3-s3/0004.png?featherlight=false&width=10pc)

4. Then, we will delete the object

```
aws s3 rm s3://bucket-name/object
```

![AWS CLI](/images/3-s3/0005.png?featherlight=false&width=10pc)

5. Then, we delete the bucket.

```
aws s3 rb s3://bucket-name
```

![AWS CLI](/images/3-s3/0006.png?featherlight=false&width=10pc)

