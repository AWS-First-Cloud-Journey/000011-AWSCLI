---
title: "AWS CLI với VPC"
date: "2024-09-27"
weight: 8
chapter: false
pre: "<b> 8. </b>"
---

#### AWS CLI với VPC

<!-- TOC được tạo tự động với Markdown All in One -->
<!-- Ctrl + Shift + P -> Create Table of Contents -->
<!-- TOC -->
- [AWS CLI với VPC](#aws-cli-với-vpc)
- [Tạo VPC](#tạo-vpc)
- [Tạo các thành phần VPC](#tạo-các-thành-phần-vpc)
<!-- /TOC -->

#### Tạo VPC

Bạn có thể sử dụng AWS CLI để tạo một Virtual Private Cloud (VPC) với các câu lệnh đơn giản.

```bash
aws ec2 create-vpc --cidr-block 10.0.0.0/16 --query Vpc.VpcId --output text
```

{{% notice note %}} Đây là Note: CIDR block `10.0.0.0/16` tạo VPC với địa chỉ IP từ 10.0.0.0 đến 10.0.255.255. {{% /notice %}}

#### Tạo các thành phần VPC

Tiếp theo, bạn cần tạo các thành phần khác của VPC như subnets, internet gateway, và route tables. 



