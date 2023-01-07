---
title : "AWS CLI with IAM"
date : "`r Sys.Date()`"
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

#### AWS CLI with IAM

We can quickly create **IAM group**, **IAM user**,**policy** using **CLI**

1. First, we will create an **IAM group**

```
aws iam create-group --group-names dev
```

![AWS CLI](/images/5-iam/0001.png?featherlight=false&width=90pc)

2. Then, we create a user

```
aws iam create-user --user-name dev-1
```

![AWS CLI](/images/5-iam/0002.png?featherlight=false&width=90pc)

3. Add a user to the created group

```
aws iam add-user-to-group --user-name dev-1 --group-name dev
```

![AWS CLI](/images/5-iam/0003.png?featherlight=false&width=90pc)

4. Check the created user and group details.

```
aws iam get-group --group-name dev
```

![AWS CLI](/images/5-iam/0004.png?featherlight=false&width=90pc)

5. Generate **Access key**

```
aws iam create-access-key --user-name dev-1
```

![AWS CLI](/images/5-iam/0005.png?featherlight=false&width=90pc)

6. To delete the created **Accesskey**, we do the following:

```
aws iam delete-access-key --user-name dev-1 --access-key-id AKIAIOSFODNN7EXAMPLE
```

![AWS CLI](/images/5-iam/0006.png?featherlight=false&width=90pc)

