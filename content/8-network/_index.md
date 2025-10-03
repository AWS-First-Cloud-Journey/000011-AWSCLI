---
title: "AWS CLI with VPC"
date: 2025-10-02
weight: 8
chapter: false
pre: " <b> 8. </b> "
---

#### AWS CLI with VPC

- [AWS CLI with VPC](#aws-cli-with-vpc)
- [**Create VPC**](#create-vpc)
- [**Create VPC Components**](#create-vpc-components)
- [**Tables**](#tables)

---

#### **Create VPC**

To create a Virtual Private Cloud (VPC) using AWS CLI, follow these steps:

{{% notice note %}} This section covers basic VPC creation using AWS CLI. {{% /notice %}}

1. Open your terminal and configure AWS CLI with your credentials:

   ```bash
   aws configure
   ```

2. Create a VPC with a CIDR block:

   ```bash
   aws ec2 create-vpc --cidr-block 10.0.0.0/16
   ```

{{% notice tip %}} Ensure you use a unique CIDR block that doesn't overlap with other networks. {{% /notice %}}

#### **Create VPC Components**

After creating the VPC, you can add components like subnets, route tables, and internet gateways.

1. **Create a Subnet**:

   ```bash
   aws ec2 create-subnet --vpc-id <vpc-id> --cidr-block 10.0.1.0/24
   ```

2. **Create an Internet Gateway**:

   ```bash
   aws ec2 create-internet-gateway
   ```

   Attach the internet gateway to your VPC:

   ```bash
   aws ec2 attach-internet-gateway --vpc-id <vpc-id> --internet-gateway-id <igw-id>
   ```

{{% notice warning %}} Ensure you modify the route table to allow internet traffic for public subnets. {{% /notice %}}

---

#### **Tables**

| Component        | Description                            |
|------------------|----------------------------------------|
| VPC              | Virtual Private Cloud, defines the network space. |
| Subnet           | Divides the VPC into smaller networks. |
| Internet Gateway | Enables internet access for public subnets. |

