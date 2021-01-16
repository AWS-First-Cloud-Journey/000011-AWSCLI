+++
title = "Examples with AWS CLI"
date = 2020
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

This section describes how to use the AWS CLI to work on creating infrastructure on AWS.

**Contents:**
- [1. Working with a VPC](#1-working-with-a-vpc)
- [2. Working with subnets in VPC](#2-working-with-subnets-in-vpc)
- [3. Working with Internet Gateway & NAT Gateway](#3-working-with-internet-gateway--nat-gateway)
- [4. Working with Routing Table](#4-working-with-routing-table)
- [5. Working with Transit Gateway](#5-working-with-transit-gateway)
- [6. Implement Cloud Trail](#6-implement-cloud-trail)
- [7. Working with S3 Gateway VPC Endpoint](#7-working-with-s3-gateway-vpc-endpoint)

#### 1. Working with a VPC

```bash
export VPC_CIDR=<CidrBlock>
export VPC_ID=$(aws ec2 create-vpc --cidr-block $VPC_CIDR --query 'Vpc.VpcId' --output text)

aws ec2 create-tags --resources $VPC_ID --tags Key=Name,Value=DEV-VPC-$VPC_CIDR
```

#### 2. Working with subnets in VPC

```bash
# NAT Internet subnet  
export VPC_ID=<VpcId>
export REGION=<Region>
export AZ1=<AvailabilityZone1>
export AZ2=<AvailabilityZone2>
export NAT_SUBNET_CIDR=<CidrBlock>
export SUBNET_ID_INTERNET=$(aws ec2 create-subnet --vpc-id $VPC_ID --cidr-block $NAT_SUBNET_CIDR --availability-zone $AZ1 --query 'Subnet.SubnetId' --output text)

aws ec2 create-tags --resources $SUBNET_ID_INTERNET --tags Key=Name,Value=DEV-InternetSubnet-$NAT_SUBNET_CIDR --output text

# Web subnet  
export WEB_SUBNET_CIDR1=<CidrBlock>
export WEB_SUBNET_CIDR2=<CidrBlock>
export SUBNET_ID_WEB1=$(aws ec2 create-subnet --vpc-id $VPC_ID --cidr-block $WEB_SUBNET_CIDR1 --availability-zone $AZ1 --query 'Subnet.SubnetId' --output text)

aws ec2 create-tags --resources $SUBNET_ID_WEB1 --tags Key=Name,Value=Web-PublicSubnet-$AZ1-$WEB_SUBNET_CIDR1 --output text

export SUBNET_ID_WEB2=$(aws ec2 create-subnet --vpc-id $VPC_ID --cidr-block $WEB_SUBNET_CIDR2 --availability-zone $AZ2 --query 'Subnet.SubnetId' --output text)

aws ec2 create-tags --resources $SUBNET_ID_WEB2 --tags Key=Name,Value=DEV-Web-PublicSubnet-$AZ2-$WEB_SUBNET_CIDR2 --output text

# Application subnet  
export APP_SUBNET_CIDR1=<CidrBlock>
export APP_SUBNET_CIDR2=<CidrBlock>
export SUBNET_ID_APP1=$(aws ec2 create-subnet --vpc-id $VPC_ID --cidr-block $APP_SUBNET_CIDR1 --availability-zone $AZ1 --query 'Subnet.SubnetId' --output text)

aws ec2 create-tags --resources $SUBNET_ID_APP1 --tags Key=Name,Value=DEV-APP-PrivateSubnet-$AZ1-$APP_SUBNET_CIDR1 --output text

export SUBNET_ID_APP2=$(aws ec2 create-subnet --vpc-id $VPC_ID --cidr-block $APP_SUBNET_CIDR2 --availability-zone $AZ2 --query 'Subnet.SubnetId' --output text)

aws ec2 create-tags --resources $SUBNET_ID_APP2 --tags Key=Name,Value=DEV-APP-PrivateSubnet-$AZ2-$APP_SUBNET_CIDR2 --output text

# Database subnet
export DB_SUBNET_CIDR1=<CidrBlock>
export DB_SUBNET_CIDR2=<CidrBlock>
export SUBNET_ID_DB1=$(aws ec2 create-subnet --vpc-id $VPC_ID --cidr-block $DB_SUBNET_CIDR1 --availability-zone $AZ1 --query 'Subnet.SubnetId' --output text)

aws ec2 create-tags --resources $SUBNET_ID_DB1 --tags Key=Name,Value=DEV-DB-PrivateSubnet-$AZ1-$DB_SUBNET_CIDR1 --output text

export SUBNET_ID_DB2=$(aws ec2 create-subnet --vpc-id $VPC_ID --cidr-block $DB_SUBNET_CIDR2 --availability-zone $AZ2 --query 'Subnet.SubnetId' --output text)

aws ec2 create-tags --resources $SUBNET_ID_DB2 --tags Key=Name,Value=DEV-DB-PrivateSubnet-$AZ2-$DB_SUBNET_CIDR2 --output text
```

#### 3. Working with Internet Gateway & NAT Gateway

```bash
# Create Internet Gateway
export VPC_ID=<VpcId>
export SUBNET_ID_INTERNET=<SubnetId>
export IGW_ID=$(aws ec2 create-internet-gateway --query 'InternetGateway.InternetGatewayId' --output text)

aws ec2 create-tags --resources $IGW_ID --tags Key=Name,Value=DEV-InternetGateway

# Attach Internet Gateway to VPC
aws ec2 attach-internet-gateway --internet-gateway-id $IGW_ID --vpc-id $VPC_ID --output text

# Create Elastic IP address
export ALLOC_ID=$(aws ec2 allocate-address --domain vpc --query 'AllocationId' --output text)

aws ec2 create-tags --resources $ALLOC_ID --tags Key=Name,Value=DEV-Elastic-IP

# Create NAT Gateway
export NATGW_ID=$(aws ec2 create-nat-gateway --allocation-id $ALLOC_ID --subnet-id $SUBNET_ID_INTERNET --query 'NatGateway.NatGatewayId' --output text)

aws ec2 create-tags --resources $NATGW_ID --tags Key=Name,Value=DEV-NAT-GW
```

#### 4. Working with Routing Table

```bash
#Create custom routable
export VPC_ID=<VpcId>
export NATGW_ID=<NatGatewayId>
export SUBNET_ID_INTERNET=<SubnetId>
export RTB_ID=$(aws ec2 create-route-table --vpc-id $VPC_ID --query 'RouteTable.RouteTableId' --output text)

aws ec2 create-tags --resources $RTB_ID --tags Key=Name,Value=DEV-RouteTable-Internet

#Add route entry that direct traffic to internet through NAT Gateway
aws ec2 create-route --route-table-id $RTB_ID --destination-cidr-block 0.0.0.0/0 --nat-gateway-id $NATGW_ID --output text 

#Associate the custom routable to the subnet that required internet connection
aws ec2 associate-route-table --route-table-id $RTB_ID --subnet-id $SUBNET_ID_INTERNET --output text 
```

#### 5. Working with Transit Gateway

```bash
# List Transit Gateway in system
aws ec2 describe-transit-gateways --output text

# Create Transit Gateway attachment ( Require to list at least 1 subnet per availability zone )
export TGW_ID=<TransitGatewayId>
export VPC_ID=<VpcId>
export SUBNET_ID_WEB1=<SubnetId>
export SUBNET_ID_WEB2=<SubnetId>

export TGW_ATTACHMENT=$(aws ec2 create-transit-gateway-vpc-attachment --transit-gateway-id $TGW_ID --vpc-id $VPC_ID --subnet-ids $SUBNET_ID_WEB1 $SUBNET_ID_WEB2 --query 'TransitGatewayVpcAttachment.TransitGatewayAttachmentId' --output text)

aws ec2 create-tags --resources $TGW_ATTACHMENT --tags Key=Name,Value=DEV-Transitgateway-attachment
```

#### 6. Implement Cloud Trail

```bash
#Create bucket to store log
export TRAIL_NAME=<TrailName>
export S3_BUCKET=<S3BucketName>
export S3_PREFIX=<ObjectPrefix>
export ACCOUNT_ID=$(aws sts get-caller-identity --query 'Account' --output text)

aws s3 mb s3://$S3_BUCKET

#Create bucket policy json
cat <<'EOT'>> $S3_BUCKET-bucket-policy.json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AWSCloudTrailAclCheck20150319",
            "Effect": "Allow",
            "Principal": {"Service": "cloudtrail.amazonaws.com"},
            "Action": "s3:GetBucketAcl",
            "Resource": "arn:aws:s3:::$S3_BUCKET"
        },
        {
            "Sid": "AWSCloudTrailWrite20150319",
            "Effect": "Allow",
            "Principal": {"Service": "cloudtrail.amazonaws.com"},
            "Action": "s3:PutObject",
            "Resource": "arn:aws:s3:::$S3_BUCKET/$S3_PREFIX/AWSLogs/$ACCOUNT_ID/*",
            "Condition": {"StringEquals": {"s3:x-amz-acl": "bucket-owner-full-control"}}
        }
    ]
}
EOT

#Assign S3 bucket policy

aws s3api put-bucket-policy --bucket=$S3_BUCKET --policy=file://$(pwd)/$S3_BUCKET-bucket-policy.json

#Create and start trail

aws cloudtrail create-trail --region=$REGION --name=$TRAIL_NAME --s3-bucket-name=$S3_BUCKET --s3-key-prefix=$S3_PREFIX

aws cloudtrail start-logging --region=$REGION --name=$TRAIL_NAME
```

#### 7. Working with S3 Gateway VPC Endpoint

```bash
#Create VPC Endpoint
export REGION=<Region>
export VPC_ID=<VpcId>
export ROUTE_TABLE_ID=<RouteTableId>
export S3_BUCKET=<S3BucketName>
export VPC_ENDPOINT_ID=$(aws ec2 create-vpc-endpoint --region=$REGION --vpc-id $VPC_ID --service-name com.amazonaws.$REGION.s3 --route-table-ids $ROUTE_TABLE_ID --query 'VpcEndpoint.VpcEndpointId' --output text)

#Update Bucket Policy to allow access from the VPC Endpoint

cat <<'EOT'>> $S3_BUCKET-bucket-policy.json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Access-to-specific-VPCE-only",
            "Principal": "*",
            "Action": "s3:*",
            "Effect": "Allow",
            "Resource": ["arn:aws:s3:::$S3_BUCKET/*"],
            "Condition": {
                "StringEquals": {
                    "aws:sourceVpce": "$VPC_ENDPOINT_ID"
                }
            }
        }
   ]
}
EOT

aws s3api put-bucket-policy --bucket=$S3_BUCKET --policy=file://$(pwd)/$S3_BUCKET-bucket-policy.json
```

{{%attachments style="orange" title="Scripts for References" pattern=".*(sh|txt)"/%}}