---
title : "Kiểm tra tài nguyên qua CLI"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Kiểm tra tài nguyên qua CLI

1. Chúng ta có thể kiểm tra tài nguyên của profile thông qua CLI:

```
aws ec2 describe-instances --profile devops
```

![AWS CLI](/images/2-ec2/0001.png?featherlight=false&width=10pc)

2. Kiểm tra số lượng s3 bucket của profile

```
aws s3 ls --profile devops
```

![AWS CLI](/images/2-ec2/0002.png?featherlight=false&width=10pc)

3. Sử dụng **CLI Auto Prompt**

```
aws --cli-auto-prompt
```

![AWS CLI](/images/2-ec2/0003.png?featherlight=false&width=10pc)

4. Xem mô tả chi tiết ec2 dạng bảng 

```
aws ec2 describe-instances --output table --region ap-southeast-1
```

![AWS CLI](/images/2-ec2/0004.png?featherlight=false&width=10pc)

