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

Bạn có thể sử dụng AWS CLI để tạo một Virtual Private Cloud (VPC) với các câu lệnh đơn giản. Dưới đây là hướng dẫn từng bước:

```bash
aws ec2 create-vpc --cidr-block 10.0.0.0/16
```

{{% notice note %}} Đây là Note: CIDR block `10.0.0.0/16` tạo VPC với địa chỉ IP từ 10.0.0.0 đến 10.0.255.255. {{% /notice %}}

#### Tạo các thành phần VPC

Tiếp theo, bạn cần tạo các thành phần khác của VPC như subnets, internet gateway, và route tables. Ví dụ:

```bash
# Tạo subnet
aws ec2 create-subnet --vpc-id vpc-12345678 --cidr-block 10.0.1.0/24

# Tạo internet gateway
aws ec2 create-internet-gateway

# Gắn internet gateway vào VPC
aws ec2 attach-internet-gateway --vpc-id vpc-12345678 --internet-gateway-id igw-12345678
```

{{% notice tip %}} Đảm bảo rằng bạn đã tạo route table và thêm các route tới internet gateway. {{% /notice %}}

