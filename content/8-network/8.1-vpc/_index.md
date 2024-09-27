---

title : "AWS CLI with VPC"  
date : "`r Sys.Date()`"  
weight : 1  
chapter : false  
pre : " <b> 8.1 </b> "  

---

#### AWS CLI with VPC

1. **Create a VPC using CLI**

```bash
aws ec2 create-vpc --cidr-block 10.0.0.0/16 --query Vpc.VpcId --output text
```

![AWS CLI](/images/vpc/0002.png?featherlight=false&width=90pc)

2. **Create a subnet based on VPC ID**

```bash
aws ec2 create-subnet --vpc-id **VPC-ID** --cidr-block 10.0.1.0/24
```

![AWS CLI](/images/vpc/0003.png?featherlight=false&width=90pc)

3. **Create a second subnet**

```bash
aws ec2 create-subnet --vpc-id **VPC-ID** --cidr-block 10.0.2.0/24
```

![AWS CLI](/images/vpc/0004.png?featherlight=false&width=90pc)

#### **Notes:**

- Ensure the correct **VPC ID** is provided when creating subnets.
  
{{% notice tip %}} 
Use `aws ec2 describe-vpcs` to list all VPCs and find the correct **VPC ID**.  
{{% /notice %}}

