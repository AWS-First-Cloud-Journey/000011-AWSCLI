---
title: "Kiểm tra tài nguyên qua CLI"
date: "2024-09-27"
weight: 4
chapter: false
pre: "<b>4.</b>"
---

#### Kiểm tra tài nguyên qua CLI

#### Table of Contents
<!-- TOC created automatically using Markdown All in One -->
<!-- TOC -->

- [Kiểm tra tài nguyên qua CLI](#kiểm-tra-tài-nguyên-qua-cli)
- [Table of Contents](#table-of-contents)
- [Kiểm tra tài nguyên của profile qua AWS CLI](#kiểm-tra-tài-nguyên-của-profile-qua-aws-cli)
- [Kiểm tra số lượng S3 bucket của profile](#kiểm-tra-số-lượng-s3-bucket-của-profile)
- [Sử dụng CLI Auto Prompt](#sử-dụng-cli-auto-prompt)
- [Xem mô tả chi tiết EC2 dưới dạng bảng](#xem-mô-tả-chi-tiết-ec2-dưới-dạng-bảng)

<!-- /TOC -->

#### Kiểm tra tài nguyên của profile qua AWS CLI

Để kiểm tra các instance EC2 của profile, chúng ta sử dụng lệnh sau:

```bash
aws ec2 describe-instances --profile devops
```

![Kiểm tra tài nguyên EC2 qua CLI](/images/2-ec2/0001.png?featherlight=false&width=90pc)

{{% notice note %}} 
Đảm bảo rằng bạn đã cấu hình đúng profile AWS trước khi chạy lệnh này.
{{% /notice %}}

#### Kiểm tra số lượng S3 bucket của profile

Để liệt kê các bucket S3 của profile, sử dụng lệnh:

```bash
aws s3 ls --profile devops
```

![Liệt kê S3 bucket qua CLI](/images/2-ec2/0002.png?featherlight=false&width=90pc)

#### Sử dụng CLI Auto Prompt

Auto Prompt của AWS CLI giúp gợi ý các tham số và lệnh, rất tiện dụng khi không nhớ chính xác cú pháp:

```bash
aws --cli-auto-prompt
```

![CLI Auto Prompt](/images/2-ec2/0003.png?featherlight=false&width=90pc)

#### Xem mô tả chi tiết EC2 dưới dạng bảng

Để xem thông tin các EC2 instance dưới dạng bảng (table), có thể sử dụng lệnh:

```bash
aws ec2 describe-instances --output table --region ap-southeast-1
```

![Mô tả EC2 dưới dạng bảng](/images/2-ec2/0004.png?featherlight=false&width=90pc)

