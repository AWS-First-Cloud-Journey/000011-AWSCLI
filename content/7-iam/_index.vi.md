---
title : "AWS CLI với IAM"
date :  "`r Sys.Date()`" 
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

#### AWS CLI với IAM

Chúng ta có thể thực hiện tạo **IAM group**, **IAM user**,**policy** một cách nhanh chóng bằng **CLI**

1. Đầu tiên, chúng ta sẽ thực hiện tạo một **IAM group**

```
aws iam create-group --group-names dev
```

![AWS CLI](/images/5-iam/0001.png?featherlight=false&width=90pc)

2. Sau đó, chúng ta thực hiện tạo user

```
aws iam create-user --user-name dev-1
```

![AWS CLI](/images/5-iam/0002.png?featherlight=false&width=90pc)

3. Thêm user vào group đã tạo

```
aws iam add-user-to-group --user-name dev-1 --group-name dev
```

![AWS CLI](/images/5-iam/0003.png?featherlight=false&width=90pc)

4. Kiểm tra chi tiết user và group đã tạo.

```
aws iam get-group --group-name dev
```

![AWS CLI](/images/5-iam/0004.png?featherlight=false&width=90pc)

5. Thực hiện tạo **Access key**

```
aws iam create-access-key --user-name dev-1
```

![AWS CLI](/images/5-iam/0005.png?featherlight=false&width=90pc)

6. Để xóa **Accesskey** đã tạo, chúng ta làm như sau:

```
aws iam delete-access-key --user-name dev-1 --access-key-id AKIAIOSFODNN7EXAMPLE
```

![AWS CLI](/images/5-iam/0006.png?featherlight=false&width=90pc)



