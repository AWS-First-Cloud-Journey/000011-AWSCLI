---
title : "AWS CLI with VPC"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 8.1 </b> "
---

#### AWS CLI with VPC

1. Create VPC with **CLI**

```
aws ec2 create-vpc --cidr-block 10.0.0.0/16 --query Vpc.VpcId --output text
```


![AWS CLI](/images/vpc/0002.png?featherlight=false&width=90pc)

2. Next, we will create a subnet based on **VPC ID**.


```
aws ec2 create-subnet --vpc-id **VPC-ID** --cidr-block 10.0.1.0/24
```


![AWS CLI](/images/vpc/0003.png?featherlight=false&width=90pc)

3. Similarly, we create a second subnet.


![AWS CLI](/images/vpc/0004.png?featherlight=false&width=90pc)

