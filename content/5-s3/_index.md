---
title: "AWS CLI with Amazon S3"
date: "`r Sys.Date()`"
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

#### **Introduction**
In this guide, we will walk through how to use the AWS CLI to perform basic operations with Amazon S3, such as creating a bucket, listing objects, and deleting both objects and the bucket.

#### **Step 1: Create an S3 Bucket**
To create an S3 bucket using the AWS CLI, execute the following command. Make sure to replace `aws-cli-2000` with your desired bucket name.

```bash
aws s3 mb s3://aws-cli-2000
```

![AWS CLI](/images/3-s3/0001.png?featherlight=false&width=90pc)

{{% notice info %}}
Make sure your bucket name is unique and complies with AWS naming conventions.
{{% /notice %}}

#### **Step 2: List All S3 Buckets**
After creating the bucket, use the following command to list all the available S3 buckets:

```bash
aws s3 ls
```

![AWS CLI](/images/3-s3/0002.png?featherlight=false&width=90pc)

#### **Step 3: List Objects in a Specific Bucket**
To view the contents of a specific S3 bucket, use the following command:

```bash
aws s3 ls s3://bucket-name
```

Replace `bucket-name` with the name of the bucket you want to inspect.

![AWS CLI](/images/3-s3/0004.png?featherlight=false&width=90pc)

#### **Step 4: Delete an Object from the Bucket**
To remove an object from the S3 bucket, run the following command:

```bash
aws s3 rm s3://bucket-name/object
```

Replace `bucket-name` with your bucket name and `object` with the specific object you want to delete.

![AWS CLI](/images/3-s3/0005.png?featherlight=false&width=90pc)

{{% notice warning %}}
Deleting an object is permanent and cannot be undone.
{{% /notice %}}

#### **Step 5: Delete the S3 Bucket**
Finally, once all objects are removed, you can delete the bucket itself with the command:

```bash
aws s3 rb s3://bucket-name
```

![AWS CLI](/images/3-s3/0006.png?featherlight=false&width=90pc)

{{% notice tip %}}
Ensure the bucket is empty before attempting to delete it. Use `--force` to delete non-empty buckets, but exercise caution.
{{% /notice %}}

#### **Conclusion**
By following these steps, you’ve learned how to create, list, and delete S3 buckets and objects using the AWS CLI. These fundamental commands will help you manage your S3 resources efficiently.


