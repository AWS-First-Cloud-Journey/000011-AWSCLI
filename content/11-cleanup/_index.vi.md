---
title : "Dọn dẹp tài nguyên"
date :  "`r Sys.Date()`" 
weight : 11
chapter : false
pre : " <b> 11. </b> "
---

#### Dọn dẹp tài nguyên

1. Thực hiện xóa **Security group**. 

```
aws ec2 delete-security-group --group-id **SG ID**
```

![AWS CLI](/images/ec2-net/00012.png?featherlight=false&width=90pc)

2. Thực hiện xóa **Subnet**

```
aws ec2 delete-subnet --subnet-id **Subnet ID**
```

![AWS CLI](/images/ec2-net/00013.png?featherlight=false&width=90pc)

3. Thực hiện xóa **Route table**

```
aws ec2 delete-route-table --route-table-id **RTB ID**
```

![AWS CLI](/images/ec2-net/00014.png?featherlight=false&width=90pc)

4. Thực hiện detach **Internet Gateway**

```
aws ec2 detach-internet-gateway --internet-gateway-id **IGW ID** --vpc-id **VPC ID**
```

![AWS CLI](/images/ec2-net/00015.png?featherlight=false&width=90pc)

5. Thực hiện xóa **Internet gateway**

```
aws ec2 delete-internet-gateway --internet-gateway-id **IGW**
```

![AWS CLI](/images/ec2-net/00016.png?featherlight=false&width=90pc)

6. Thực hiện xóa **VPC**

```
aws ec2 delete-vpc --vpc-id **VPC ID**
```

![AWS CLI](/images/ec2-net/00017.png?featherlight=false&width=90pc)