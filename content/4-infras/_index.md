---
title : "View resource via CLI"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### View resource via CLI

1. We can check the profile's resources via CLI:

```
aws ec2 describe-instances --profile devops
```

![AWS CLI](/images/2-ec2/0001.png?featherlight=false&width=10pc)

2. Check the number of s3 buckets of the profile

```
aws s3 ls --profile devops
```

![AWS CLI](/images/2-ec2/0002.png?featherlight=false&width=10pc)

3. Using **CLI Auto Prompt**

```
aws --cli-auto-prompt
```

![AWS CLI](/images/2-ec2/0003.png?featherlight=false&width=10pc)

4. View detailed ec2 tabular description

```
aws ec2 describe-instances --output table --region ap-southeast-1
```

![AWS CLI](/images/2-ec2/0004.png?featherlight=false&width=10pc)

