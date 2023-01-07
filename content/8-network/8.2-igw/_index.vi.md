---
title : "AWS CLI với Internet Gateway"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 8.2 </b> "
---

#### AWS CLI với Internet Gateway

1. Thực hiện tạo **Internet Gateway**

```
aws ec2 create-internet-gateway --query InternetGateway.InternetGatewayId --output text
```

![AWS CLI](/images/igw/0001.png?featherlight=false&width=90pc)

2. Chúng ta sẽ xác nhận lại đã tạo thành công **Internet Gateway** và sử dụng **Internet gateway ID** để thực hiện các bước tiếp theo.

![AWS CLI](/images/igw/0002.png?featherlight=false&width=90pc)

3. Sau đó, chúng ta sẽ kiểm tra **VPC** để sử dụng **VPC ID** cho bước tiếp theo.

![AWS CLI](/images/igw/0003.png?featherlight=false&width=90pc)

4. Sau khi kiểm tra Internet Gateway và VPC, chúng ta thực hiện **attach internet gateway**

```
aws ec2 attach-internet-gateway --vpc-id **VPC-ID** --internet-gateway-id **IGW ID**
```

![AWS CLI](/images/igw/0004.png?featherlight=false&width=90pc)

5. Tương tự, tạo các tài nguyên mạng như **Route Table**

```
aws ec2 create-route-table --vpc-id **VPC-ID** --query RouteTable.RouteTableId --output text
```

- Sau đó, định tuyến **Route table**

```
aws ec2 create-route --route-table-id **RTB ID** --destination-cidr-block 0.0.0.0/0 --gateway-id **IGW ID**
```
- Kiểm tra **Route table**

```
aws ec2 describe-route-tables --route-table-id **RTB-ID**
```

- Thực hiện **associate route table**

```
aws ec2 associate-route-table  --subnet-id **Subnet ID** --route-table-id **RTB ID**
```