---
title : "AWS CLI với Amazon S3"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

#### Sử dụng AWS CLI để khởi tạo tài nguyên S3.

1. Thực hiện sử dụng **CLI** để tương tác với S3. Tạo **S3** bucket.

```
aws s3 mb s3://aws-cli-2000
```

![AWS CLI](/images/3-s3/0001.png?featherlight=false&width=10pc)

2. Kiểm tra danh sách **s3 bucket**

```
aws s3 ls
```

![AWS CLI](/images/3-s3/0002.png?featherlight=false&width=10pc)

3. Kiểm tra object trong s3 bucket.

```
aws s3 ls s3://bucket-name
```

![AWS CLI](/images/3-s3/0004.png?featherlight=false&width=10pc)

4. Sau đó chúng ta sẽ xóa object

```
aws s3 rm s3://bucket-name/object
```

![AWS CLI](/images/3-s3/0005.png?featherlight=false&width=10pc)

5. Sau đó chúng ta xóa bucket.

```
aws s3 rb s3://bucket-name
```

![AWS CLI](/images/3-s3/0006.png?featherlight=false&width=10pc)

