---
title : "AWS CLI với VPC"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 8.1 </b> "
---

#### AWS CLI với VPC

1. Thực hiện tạo VPC bằng **CLI**

```
aws ec2 create-vpc --cidr-block 10.0.0.0/16 --query Vpc.VpcId --output text
```


![AWS CLI](/images/vpc/0002.png?featherlight=false&width=90pc)

2. Tiếp theo chúng ta sẽ tạo subnet dựa theo **VPC ID** đã tạo.


```
aws ec2 create-subnet --vpc-id **VPC-ID** --cidr-block 10.0.1.0/24
```


![AWS CLI](/images/vpc/0003.png?featherlight=false&width=90pc)

3. Tương tự chúng ta tạo một subnet thứ 2.


![AWS CLI](/images/vpc/0004.png?featherlight=false&width=90pc)
