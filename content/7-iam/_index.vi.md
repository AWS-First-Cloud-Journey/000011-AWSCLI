---
title: "AWS CLI với IAM"
date: "2024-09-27"
weight: 7
chapter: false
pre: "<b>7.</b>"
---


#### AWS CLI với IAM

Chúng ta có thể thực hiện tạo **IAM group**, **IAM user**, và **policy** một cách nhanh chóng bằng **CLI**. Các bước thực hiện như sau:

#### Table of Contents
<!-- TOC created using Markdown All in One -->
- [AWS CLI với IAM](#aws-cli-với-iam)
- [Table of Contents](#table-of-contents)
- [Tạo IAM Group](#tạo-iam-group)
- [Tạo IAM User](#tạo-iam-user)
- [Thêm User vào Group](#thêm-user-vào-group)
- [Kiểm tra Chi Tiết Group và User](#kiểm-tra-chi-tiết-group-và-user)
- [Tạo Access Key cho User](#tạo-access-key-cho-user)
- [Xóa Access Key](#xóa-access-key)

---

#### Tạo IAM Group

Đầu tiên, chúng ta sẽ thực hiện tạo một **IAM group** mới với CLI:

```bash
aws iam create-group --group-name dev
```

![Tạo IAM Group](/images/5-iam/0001.png?featherlight=false&width=90pc)

{{% notice info %}} Lưu ý rằng tên của group phải là duy nhất trong tài khoản AWS của bạn. {{% /notice %}}

---

#### Tạo IAM User

Tiếp theo, chúng ta sẽ tạo một user mới và đặt tên cho user là **dev-1**:

```bash
aws iam create-user --user-name dev-1
```

![Tạo IAM User](/images/5-iam/0002.png?featherlight=false&width=90pc)

---

#### Thêm User vào Group

Bước tiếp theo là thêm user vừa tạo vào group **dev**:

```bash
aws iam add-user-to-group --user-name dev-1 --group-name dev
```

![Thêm User vào Group](/images/5-iam/0003.png?featherlight=false&width=90pc)

---

#### Kiểm tra Chi Tiết Group và User

Chúng ta có thể kiểm tra chi tiết của group và user bằng lệnh sau:

```bash
aws iam get-group --group-name dev
```

![Kiểm tra Chi Tiết Group và User](/images/5-iam/0004.png?featherlight=false&width=90pc)

---

#### Tạo Access Key cho User

Tiếp theo, chúng ta sẽ tạo **Access Key** cho user **dev-1**:

```bash
aws iam create-access-key --user-name dev-1
```

![Tạo Access Key](/images/5-iam/0005.png?featherlight=false&width=90pc)

{{% notice tip %}} Đảm bảo lưu trữ Access Key ID và Secret Access Key một cách an toàn. {{% /notice %}}

---

#### Xóa Access Key

Cuối cùng, nếu muốn xóa **Access Key** đã tạo, chúng ta có thể thực hiện với lệnh sau:

```bash
aws iam delete-access-key --user-name dev-1 --access-key-id AKIAIOSFODNN7EXAMPLE
```

![Xóa Access Key](/images/5-iam/0006.png?featherlight=false&width=90pc)

