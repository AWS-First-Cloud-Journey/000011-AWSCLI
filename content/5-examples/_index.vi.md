+++
title = "Các Ví Dụ với AWS CLI"
date = 2020
weight = 5
chapter = false
pre = "<b>5. </b>"
+++
  
This section describes how to use the AWS CLI to work on creating infrastructure on AWS.

**Nội dung:**
- [1. Tạo một VPC](#1-tạo-một-vpc)
- [2. Tạo các Subnet trong VPC](#2-tạo-các-subnet-trong-vpc)
- [3. Tạo Internet Gateway và NAT Gateway](#3-tạo-internet-gateway-và-nat-gateway)
- [4. Tạo Routing Table](#4-tạo-routing-table)
- [5.Làm việc với Transit Gateway](#5làm-việc-với-transit-gateway)
- [6. Thiết lập Cloud Trail](#6-thiết-lập-cloud-trail)
- [7. Tạo S3 Gateway VPC Endpoint](#7-tạo-s3-gateway-vpc-endpoint)

#### 1. Tạo một VPC

```bash
aws ec2 create-vpc --cidr-block 10.0.0.0/16 --output text

export VPC_ID=<VpcId>
aws ec2 create-tags --resources $VPC_ID --tags Key=Name,Value=DEV-VPC-10.0.0.0/16
```

#### 2. Tạo các Subnet trong VPC

```bash
# NAT Internet subnet  
aws ec2 create-subnet --vpc-id $VPC_ID --cidr-block 10.0.1.0/24 --availability-zone ap-southeast-1a --output text 

export SUBNET_ID_INTERNET=<SubnetId>

aws ec2 create-tags --resources $SUBNET_ID_INTERNET --tags Key=Name,Value=DEV-InternetSubnet-1a-10.0.1.0/24 --output text

# Web subnet  
aws ec2 create-subnet --vpc-id $VPC_ID --cidr-block 10.0.10.0/24 --availability-zone ap-southeast-1a --output text

export SUBNET_ID_WEB1=<SubnetId>

aws ec2 create-tags --resources $SUBNET_ID_WEB1 --tags Key=Name,Value=DEV-WebPublicSubnet-1a-10.0.10.0/24 --output text

aws ec2 create-subnet --vpc-id $VPC_ID --cidr-block 10.0.1111.0/24 --availability-zone ap-southeast-1b --output text

export SUBNET_ID_WEB2=<SubnetId>

aws ec2 create-tags --resources $SUBNET_ID_WEB2 --tags Key=Name,Value=DEV-WebPublicSubnet-1b-10.0.1111.0/24 --output text

# Application subnet  
aws ec2 create-subnet --vpc-id $VPC_ID --cidr-block 10.0.20.0/24 --availability-zone ap-southeast-1a --output text

export SUBNET_ID_APP1=<SubnetId>

aws ec2 create-tags --resources $SUBNET_ID_APP1 --tags Key=Name,Value=DEV-APP-PrivateSubnet-1a-10.0.20.0/24 --output text


aws ec2 create-subnet --vpc-id $VPC_ID --cidr-block 10.0.21.0/24 --availability-zone ap-southeast-1b --output text

export SUBNET_ID_APP2=<SubnetId>

aws ec2 create-tags --resources $SUBNET_ID_APP2 --tags Key=Name,Value=DEV-APP-PrivateSubnet-1b-10.0.21.0/24 --output text

# Database subnet
aws ec2 create-subnet --vpc-id $VPC_ID --cidr-block 10.0.30.0/24 --availability-zone ap-southeast-1a --output text

export SUBNET_ID_DB1=<SubnetId>

aws ec2 create-tags --resources $SUBNET_ID_DB1 --tags Key=Name,Value=DEV-DB-PrivateSubnet-1a-10.0.30.0/24 

aws ec2 create-subnet --vpc-id $VPC_ID --cidr-block 10.0.31.0/24 --availability-zone ap-southeast-1b --output text

export SUBNET_ID_DB2=<SubnetId>

aws ec2 create-tags --resources $SUBNET_ID_DB2 --tags Key=Name,Value=DEV-DBPrivateSubnet-1b-10.0.31.0/24 --output text
```

#### 3. Tạo Internet Gateway và NAT Gateway

```bash
# Create Internet Gateway
aws ec2 create-internet-gateway --output text

export IGW_ID=<InternetGatewayId>

aws ec2 create-tags --resources $IGW_ID --tags Key=Name,Value=DEV-InternetGateway

# Attach Internet Gateway to VPC
aws ec2 attach-internet-gateway --internet-gateway-id $IGW_ID --vpc-id $VPC_ID --output text

# Create Elastic IP address
aws ec2 allocate-address --domain vpc --output text

export ALLOC_ID=<AllocationId>

aws ec2 create-tags --resources $ALLOC_ID --tags Key=Name,Value=DEV-Elastic-IP

# Create NAT Gateway
aws ec2 create-nat-gateway --allocation-id $ALLOC_ID --subnet-id $SUBNET_ID_INTERNET

export NATGW_ID=<NatGatewayId>

aws ec2 create-tags --resources $NATGW_ID --tags Key=Name,Value=DEV-NAT-GW
```

#### 4. Tạo Routing Table

```bash
#Create custom routable
aws ec2 create-route-table --vpc-id $VPC_ID --output text 

export RTB_ID=<RouteTableId>

aws ec2 create-tags --resources $RTB_ID --tags Key=Name,Value=DEV-RouteTable-Internet


#Add route entry that direct traffic to internet through NAT Gateway
aws ec2 create-route --route-table-id $RTB_ID --destination-cidr-block 0.0.0.0/0 --nat-gateway-id $NATGW_ID

#Associate the custom routable to the subnet that required internet connection
aws ec2 associate-route-table --route-table-id $RTB_ID --subnet-id $SUBNET_ID_INTERNET
```

#### 5.Làm việc với Transit Gateway

```bash
#List Transit Gateway in system 
aws ec2 describe-transit-gateways

export TGW_ID=<TransitGatewayId>

#Create Transit Gateway attachment ( Require to list at least 1 subnet per availability zone )
aws ec2 create-transit-gateway-vpc-attachment --transit-gateway-id $TGW_ID --vpc-id $VPC_ID --subnet-ids $SUBNET_ID_WEB1 $SUBNET_ID_WEB2 --output text

export TGW_ATTACHMENT=<TransitGatewayAttachmentId>

aws ec2 create-tags --resources $TGW_ATTACHMENT --tags Key=Name,Value=DEV-Transitgateway-attachment
```

#### 6. Thiết lập Cloud Trail

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

#### 7. Tạo S3 Gateway VPC Endpoint

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

{{%attachments style="orange" title="Các script Tham khảo" pattern=".*(sh|txt)"/%}}