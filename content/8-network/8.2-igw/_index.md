---
title : "AWS CLI with Internet Gateway"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 8.2 </b> "
---

#### AWS CLI with Internet Gateway

1. Create **Internet Gateway**

```
aws ec2 create-internet-gateway --query InternetGateway.InternetGatewayId --output text
```

![AWS CLI](/images/igw/0001.png?featherlight=false&width=90pc)

2. We will confirm the successful creation of **Internet Gateway** and use **Internet gateway ID** to perform the following steps.

![AWS CLI](/images/igw/0002.png?featherlight=false&width=90pc)

3. Then, we will check **VPC** to use **VPC ID** for the next step.

![AWS CLI](/images/igw/0003.png?featherlight=false&width=90pc)

4. After checking Internet Gateway and VPC, we execute **attach internet gateway**

```
aws ec2 attach-internet-gateway --vpc-id **VPC-ID** --internet-gateway-id **IGW ID**
```

![AWS CLI](/images/igw/0004.png?featherlight=false&width=90pc)

5. Similarly, create network resources like **Route Table**

```
aws ec2 create-route-table --vpc-id **VPC-ID** --query RouteTable.RouteTableId --output text
```

- Then route **Route table**

```
aws ec2 create-route --route-table-id **RTB ID** --destination-cidr-block 0.0.0.0/0 --gateway-id **IGW ID**
```
- Check **Route table**

```
aws ec2 describe-route-tables --route-table-id **RTB-ID**
```

- Implement **associate route table**

```
aws ec2 associate-route-table --subnet-id **Subnet ID** --route-table-id **RTB ID**
```