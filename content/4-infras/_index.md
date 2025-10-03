---
title: "View resource via CLI"
date: 2025-10-02
weight: 4
chapter: false
pre: " <b> 4. </b> "
---

#### View resource via CLI

#### Table of Contents
<!-- TOC created using Markdown All in One -->
<!-- Ctrl + Shift + P -> Create Table of Contents -->
<!-- TOC -->

- [View resource via CLI](#view-resource-via-cli)
- [Table of Contents](#table-of-contents)
- [View EC2 instances](#view-ec2-instances)
- [Check S3 buckets](#check-s3-buckets)
- [CLI Auto Prompt](#cli-auto-prompt)
- [EC2 tabular description](#ec2-tabular-description)

#### View EC2 instances

We can check the profile's EC2 instances using the following command:

```bash
aws ec2 describe-instances --profile devops
```

![AWS CLI](/images/2-ec2/0001.png?featherlight=false&width=90pc)

{{% notice tip %}} 
You can specify the region by adding `--region <region-name>`.
{{% /notice %}}

#### Check S3 buckets

To check the number of S3 buckets in your profile:

```bash
aws s3 ls --profile devops
```

![AWS CLI](/images/2-ec2/0002.png?featherlight=false&width=90pc)

{{% notice info %}} 
This command lists all S3 buckets associated with the selected AWS profile.
{{% /notice %}}

#### CLI Auto Prompt

The AWS CLI Auto Prompt helps you interactively create AWS CLI commands:

```bash
aws --cli-auto-prompt
```

![AWS CLI](/images/2-ec2/0003.png?featherlight=false&width=90pc)

#### EC2 tabular description

To view EC2 instance details in tabular format for a specific region:

```bash
aws ec2 describe-instances --output table --region ap-southeast-1
```

![AWS CLI](/images/2-ec2/0004.png?featherlight=false&width=90pc)

