---
title: "AWS CLI with IAM"
date: "`r Sys.Date()`"
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

#### AWS CLI with IAM

We can quickly create **IAM group**, **IAM user**, and **policy** using **CLI**.

- [AWS CLI with IAM](#aws-cli-with-iam)
- [1. Create an IAM Group](#1-create-an-iam-group)
- [2. Create an IAM User](#2-create-an-iam-user)
- [3. Add User to Group](#3-add-user-to-group)
- [4. Check Group Details](#4-check-group-details)
- [5. Generate Access Key](#5-generate-access-key)
- [6. Delete Access Key](#6-delete-access-key)

---

#### 1. Create an IAM Group

Use the following command to create a new **IAM group**:

```bash
aws iam create-group --group-name dev
```

![AWS CLI](/images/5-iam/0001.png?featherlight=false&width=90pc)

{{% notice tip %}} You can name the group whatever fits your use case. {{% /notice %}}

#### 2. Create an IAM User

Next, create a new **IAM user**:

```bash
aws iam create-user --user-name dev-1
```

![AWS CLI](/images/5-iam/0002.png?featherlight=false&width=90pc)

{{% notice info %}} Ensure that each user is properly assigned unique permissions. {{% /notice %}}

#### 3. Add User to Group

Now, add the user to the created group:

```bash
aws iam add-user-to-group --user-name dev-1 --group-name dev
```

![AWS CLI](/images/5-iam/0003.png?featherlight=false&width=90pc)

#### 4. Check Group Details

You can verify the group and user details with:

```bash
aws iam get-group --group-name dev
```

![AWS CLI](/images/5-iam/0004.png?featherlight=false&width=90pc)

#### 5. Generate Access Key

Generate the **Access Key** for the user with:

```bash
aws iam create-access-key --user-name dev-1
```

![AWS CLI](/images/5-iam/0005.png?featherlight=false&width=90pc)

#### 6. Delete Access Key

To delete an **Access Key**, use the following command:

```bash
aws iam delete-access-key --user-name dev-1 --access-key-id AKIAIOSFODNN7EXAMPLE
```

![AWS CLI](/images/5-iam/0006.png?featherlight=false&width=90pc)

{{% notice warning %}} Always ensure to securely manage and delete access keys that are no longer in use. {{% /notice %}}

