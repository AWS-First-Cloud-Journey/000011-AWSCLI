---
title : "Clean up resources"
date : "`r Sys.Date()`"
weight : 11
chapter : false
pre : " <b> 11. </b> "
---

#### Clean up resources

1. Delete **Security group**.

```
aws ec2 delete-security-group --group-id **SG ID**
```

![AWS CLI](/images/ec2-net/00012.png?featherlight=false&width=90pc)

2. Delete **Subnet**

```
aws ec2 delete-subnet --subnet-id **Subnet ID**
```

![AWS CLI](/images/ec2-net/00013.png?featherlight=false&width=90pc)

3. Delete **Route table**

```
aws ec2 delete-route-table --route-table-id **RTB ID**
```

![AWS CLI](/images/ec2-net/00014.png?featherlight=false&width=90pc)

4. Detach **Internet Gateway**

```
aws ec2 detach-internet-gateway --internet-gateway-id **IGW ID** --vpc-id **VPC ID**
```

![AWS CLI](/images/ec2-net/00015.png?featherlight=false&width=90pc)

5. Delete **Internet gateway**

```
aws ec2 delete-internet-gateway --internet-gateway-id **IGW**
```

![AWS CLI](/images/ec2-net/00016.png?featherlight=false&width=90pc)

6. Perform a **VPC** deletion

```
aws ec2 delete-vpc --vpc-id **VPC ID**
```

![AWS CLI](/images/ec2-net/00017.png?featherlight=false&width=90pc)