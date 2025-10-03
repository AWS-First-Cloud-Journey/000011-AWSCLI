---
title: "Dọn dẹp tài nguyên"
date: "2024-09-27"
weight: 11
chapter: false
pre: "<b> 11. </b>"
---

#### Dọn dẹp tài nguyên
<!-- TOC created with Markdown All in One -->
- [Dọn dẹp tài nguyên](#dọn-dẹp-tài-nguyên)
- [1. Xóa **Security Group**](#1-xóa-security-group)
- [2. Xóa **Subnet**](#2-xóa-subnet)
- [3. Xóa **Route Table**](#3-xóa-route-table)
- [4. Detach **Internet Gateway**](#4-detach-internet-gateway)
- [5. Xóa **Internet Gateway**](#5-xóa-internet-gateway)
- [6. Xóa **VPC**](#6-xóa-vpc)

<!-- /TOC -->

#### 1. Xóa **Security Group**

{{% notice warning %}} Đảm bảo bạn đã xác nhận xóa mọi kết nối liên quan đến Security Group trước khi thực hiện lệnh xóa. {{% /notice %}}

```bash
aws ec2 delete-security-group --group-id <SG ID>
```

![AWS CLI](/images/ec2-net/00012.png?featherlight=false&width=90pc)

#### 2. Xóa **Subnet**

```bash
aws ec2 delete-subnet --subnet-id <Subnet ID>
```

![AWS CLI](/images/ec2-net/00013.png?featherlight=false&width=90pc)

#### 3. Xóa **Route Table**

```bash
aws ec2 delete-route-table --route-table-id <RTB ID>
```

![AWS CLI](/images/ec2-net/00014.png?featherlight=false&width=90pc)

#### 4. Detach **Internet Gateway**

```bash
aws ec2 detach-internet-gateway --internet-gateway-id <IGW ID> --vpc-id <VPC ID>
```

![AWS CLI](/images/ec2-net/00015.png?featherlight=false&width=90pc)

#### 5. Xóa **Internet Gateway**

```bash
aws ec2 delete-internet-gateway --internet-gateway-id <IGW ID>
```

![AWS CLI](/images/ec2-net/00016.png?featherlight=false&width=90pc)

#### 6. Xóa **VPC**

```bash
aws ec2 delete-vpc --vpc-id <VPC ID>
```

![AWS CLI](/images/ec2-net/00017.png?featherlight=false&width=90pc)

#### 7. Xóa **aws-cli-instance**
     
        aws ec2 terminate-instances --instance-ids <aws-cli-instance ID>

#### 8. Xóa Access Key của **aws-cli-user** và **devops**

        aws iam delete-access-key --user-name aws-cli-user --access-key-id *aws-cli-user-Access key*

        aws iam delete-access-key --user-name devops --access-key-id *devops-Access key*


        