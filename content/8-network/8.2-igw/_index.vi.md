---
title : "AWS CLI với Internet Gateway"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 8.2 </b> "
---

#### AWS CLI với Internet Gateway

#### Mục lục

<!-- TOC created with Markdown All in One -->

- [AWS CLI với Internet Gateway](#aws-cli-với-internet-gateway)
- [Mục lục](#mục-lục)
- [1. Thực hiện tạo Internet Gateway](#1-thực-hiện-tạo-internet-gateway)
- [2. Xác nhận Internet Gateway](#2-xác-nhận-internet-gateway)
- [3. Kiểm tra VPC](#3-kiểm-tra-vpc)
- [4. Attach Internet Gateway](#4-attach-internet-gateway)
- [5. Tạo Route Table](#5-tạo-route-table)
- [6. Định tuyến Route Table](#6-định-tuyến-route-table)
- [7. Kiểm tra Route Table](#7-kiểm-tra-route-table)
- [8. Associate Route Table](#8-associate-route-table)

<!-- /TOC -->

#### 1. Thực hiện tạo Internet Gateway

```bash
aws ec2 create-internet-gateway --query InternetGateway.InternetGatewayId --output text
```

![AWS CLI](/images/igw/0001.png?featherlight=false&width=90pc)

{{% notice note %}} Đây là bước khởi tạo Internet Gateway. {{% /notice %}}

#### 2. Xác nhận Internet Gateway

Chúng ta sẽ xác nhận lại đã tạo thành công **Internet Gateway** và sử dụng **Internet Gateway ID** để thực hiện các bước tiếp theo.

![AWS CLI](/images/igw/0002.png?featherlight=false&width=90pc)

{{% notice info %}} Xác nhận Internet Gateway là bước quan trọng trước khi thực hiện các bước tiếp theo. {{% /notice %}}

#### 3. Kiểm tra VPC

Chúng ta sẽ kiểm tra **VPC** để sử dụng **VPC ID** cho bước tiếp theo.

![AWS CLI](/images/igw/0003.png?featherlight=false&width=90pc)

#### 4. Attach Internet Gateway

Sau khi kiểm tra Internet Gateway và VPC, chúng ta thực hiện **attach internet gateway** bằng cách:

```bash
aws ec2 attach-internet-gateway --vpc-id <VPC-ID> --internet-gateway-id <IGW-ID>
```

![AWS CLI](/images/igw/0004.png?featherlight=false&width=90pc)

{{% notice tip %}} Chúng ta cần sử dụng đúng VPC ID và Internet Gateway ID để attach thành công. {{% /notice %}}

#### 5. Tạo Route Table

Tương tự, chúng ta tạo **Route Table** cho VPC của mình:

```bash
aws ec2 create-route-table --vpc-id <VPC-ID> --query RouteTable.RouteTableId --output text
```

#### 6. Định tuyến Route Table

Sau đó, chúng ta định tuyến cho **Route Table** để kết nối ra Internet:

```bash
aws ec2 create-route --route-table-id <RTB-ID> --destination-cidr-block 0.0.0.0/0 --gateway-id <IGW-ID>
```

#### 7. Kiểm tra Route Table

Sau khi tạo route, chúng ta kiểm tra lại cấu hình của **Route Table**:

```bash
aws ec2 describe-route-tables --route-table-id <RTB-ID>
```

#### 8. Associate Route Table

Cuối cùng, thực hiện **associate route table** với một **subnet** cụ thể:

```bash
aws ec2 associate-route-table --subnet-id <Subnet-ID> --route-table-id <RTB-ID>
```

