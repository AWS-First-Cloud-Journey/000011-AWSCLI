---
title : "AWS CLI with Internet Gateway"
date : 2025-10-02
weight : 2
chapter : false
pre : " <b> 8.2 </b> "
---

#### AWS CLI with Internet Gateway


#### Introduction
This guide provides step-by-step instructions for creating and managing an Internet Gateway using AWS CLI.

{{% notice tip %}}
This guide assumes you have AWS CLI configured on your system with appropriate IAM permissions.
{{% /notice %}}

#### Steps to Create and Attach an Internet Gateway

#### 1. Create **Internet Gateway**

To create an Internet Gateway, use the following command:

```bash
aws ec2 create-internet-gateway --query InternetGateway.InternetGatewayId --output text
```

![AWS CLI](/images/igw/0001.png?featherlight=false&width=90pc)

#### 2. Confirm Internet Gateway Creation

Once the Internet Gateway is created, confirm the successful creation and retrieve the **Internet Gateway ID** for the next steps.

![AWS CLI](/images/igw/0002.png?featherlight=false&width=90pc)

#### 3. Check the VPC

Next, check your **VPC** and retrieve the **VPC ID** to use in subsequent commands:

![AWS CLI](/images/igw/0003.png?featherlight=false&width=90pc)

#### 4. Attach Internet Gateway to VPC

Attach the Internet Gateway to your VPC by using the following command:

```bash
aws ec2 attach-internet-gateway --vpc-id <VPC-ID> --internet-gateway-id <IGW-ID>
```

![AWS CLI](/images/igw/0004.png?featherlight=false&width=90pc)

#### 5. Create and Manage Network Resources

Create a **Route Table** for the VPC:

```bash
aws ec2 create-route-table --vpc-id <VPC-ID> --query RouteTable.RouteTableId --output text
```

After creating the route table, create a route for the Internet Gateway:

```bash
aws ec2 create-route --route-table-id <RTB-ID> --destination-cidr-block 0.0.0.0/0 --gateway-id <IGW-ID>
```

Check the route table:

```bash
aws ec2 describe-route-tables --route-table-id <RTB-ID>
```

Finally, associate the route table with a **Subnet**:

```bash
aws ec2 associate-route-table --subnet-id <Subnet-ID> --route-table-id <RTB-ID>
```

#### Notes
{{% notice info %}}
Make sure to replace placeholders like `<VPC-ID>`, `<IGW-ID>`, `<RTB-ID>`, and `<Subnet-ID>` with actual values from your AWS environment.
{{% /notice %}}

#### Conclusion

By following the steps in this guide, you can successfully create and manage an Internet Gateway in AWS. The Internet Gateway allows your VPC to communicate with the Internet, enabling inbound and outbound traffic for your resources.

