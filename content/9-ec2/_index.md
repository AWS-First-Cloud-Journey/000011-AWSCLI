---
title : "Creating EC2 Using AWS CLI"
date : "`r Sys.Date()`"
weight : 9
chapter : false
pre : " <b> 9. </b> "
---

#### Create EC2 using AWS CLI

1. From the network infrastructure created with **CLI**, we will create **EC2**. First, create **AWS Key pair**

```
aws ec2 create-key-pair --key-name MyKeyPair --query "KeyMaterial" --output text > MyKeyPair.pem
```

![AWS CLI](/images/ec2-net/0001.png?featherlight=false&width=90pc)

2. Check on the interface; we confirm that we have successfully created **Key pair**

![AWS CLI](/images/ec2-net/0002.png?featherlight=false&width=90pc)

3. Use the command to decentralize:

```
chmod 400 MyKeyPair.pem
```

![AWS CLI](/images/ec2-net/0003.png?featherlight=false&width=90pc)

4. Create **Security group** for **EC2**

```
aws ec2 create-security-group --group-name SSHAccess --description "Security group for SSH access" --vpc-id **VPC ID**
```

![AWS CLI](/images/ec2-net/0004.png?featherlight=false&width=90pc)

5. Then, we check the created **Security group**.

![AWS CLI](/images/ec2-net/0005.png?featherlight=false&width=90pc)

6. Make permission to SSH:

```
aws ec2 authorize-security-group-ingress --group-id **SG ID** --protocol tcp --port 22 --cidr 0.0.0.0/0
```

![AWS CLI](/images/ec2-net/0006.png?featherlight=false&width=90pc)

7. Preparation is complete. Let's start **EC2**

```
aws ec2 run-instances --image-id **AMI** --count 1 --instance-type t2.micro --key-name MyKeyPair --security-group-ids **SG ID** --subnet- id **Subnet ID**
```

![AWS CLI](/images/ec2-net/0007.png?featherlight=false&width=90pc)

8. Wait about 2 minutes, see the status of **EC2 instance**

```
aws ec2 describe-instances --instance-id **Instance ID** --query "Reservations[*].Instances[*].{State:State.Name,Address:PublicIpAddress}"
```

![AWS CLI](/images/ec2-net/0008.png?featherlight=false&width=90pc)

9. When the instance is in **running** state. We make the connection

```
ssh -i "MyKeyPair.pem" ec2-user@IP Public
```

![AWS CLI](/images/ec2-net/0009.png?featherlight=false&width=90pc)

10. Once used, we execute **terminate** with the command:

```
aws ec2 terminate-instance --instances-ids **Instance ID**
```

![AWS CLI](/images/ec2-net/00010.png?featherlight=false&width=90pc)

11. After about 2-3 minutes later. We check the status of **instance**

![AWS CLI](/images/ec2-net/00011.png?featherlight=false&width=90pc)