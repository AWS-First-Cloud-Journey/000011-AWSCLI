---
title : "Clean up resources"
date : 2025-10-02
weight : 11
chapter : false
pre : " <b> 11. </b> "
---

#### Clean up resources

⚠️ **Warning**: Make sure to delete resources in the correct order to avoid dependency errors. Resources with dependencies must be deleted after their dependent resources.

#### Delete Security Group

```bash
aws ec2 delete-security-group --group-id <SECURITY_GROUP_ID>
```

![AWS CLI](/images/ec2-net/00012.png?featherlight=false&width=90pc)

#### Delete Subnet

```bash
aws ec2 delete-subnet --subnet-id <SUBNET_ID>
```

![AWS CLI](/images/ec2-net/00013.png?featherlight=false&width=90pc)

#### Delete Route Table

```bash
aws ec2 delete-route-table --route-table-id <ROUTE_TABLE_ID>
```

![AWS CLI](/images/ec2-net/00014.png?featherlight=false&width=90pc)

#### Detach Internet Gateway

💡 **Pro Tip**: You must detach the Internet Gateway from the VPC before you can delete it.

```bash
aws ec2 detach-internet-gateway --internet-gateway-id <INTERNET_GATEWAY_ID> --vpc-id <VPC_ID>
```

![AWS CLI](/images/ec2-net/00015.png?featherlight=false&width=90pc)

#### Delete Internet Gateway

```bash
aws ec2 delete-internet-gateway --internet-gateway-id <INTERNET_GATEWAY_ID>
```

![AWS CLI](/images/ec2-net/00016.png?featherlight=false&width=90pc)

#### Delete VPC

ℹ️ **Information**: This should be the final step after all resources within the VPC have been deleted.

```bash
aws ec2 delete-vpc --vpc-id <VPC_ID>
```

![AWS CLI](/images/ec2-net/00017.png?featherlight=false&width=90pc)

#### Delete **aws-cli-instance**
     
        aws ec2 terminate-instances --instance-ids <aws-cli-instance ID>

#### Delete Access Key of **aws-cli-user** and **devops**

        aws iam delete-access-key --user-name aws-cli-user --access-key-id *aws-cli-user-Access key*

        aws iam delete-access-key --user-name devops --access-key-id *devops-Access key*
🔒 **Security Note**: To ensure complete cleanup and prevent unexpected charges, verify all resources have been successfully deleted by checking the AWS Management Console or using the CLI list commands.