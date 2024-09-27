---
title: "AWS CLI với Amazon S3"
date: "2024-09-27"
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

#### **Mục lục**
<!-- TOC created with Markdown All in One -->
<!-- toc -->

- [**Mục lục**](#mục-lục)
- [Sử dụng AWS CLI để khởi tạo tài nguyên S3](#sử-dụng-aws-cli-để-khởi-tạo-tài-nguyên-s3)

<!-- /TOC -->

#### Sử dụng AWS CLI để khởi tạo tài nguyên S3

{{% notice info %}} **Giới thiệu**: Trong phần này, chúng ta sẽ sử dụng AWS CLI để tương tác với dịch vụ S3 của AWS. Các thao tác bao gồm việc tạo và quản lý các **bucket** và **object** trong S3. {{% /notice %}}

1. **Tạo S3 bucket**

   Để tạo một **S3 bucket**, sử dụng lệnh sau:

   ```bash
   aws s3 mb s3://aws-cli-2000
   ```

   ![AWS CLI Tạo Bucket](/images/3-s3/0001.png?featherlight=false&width=90pc)

{{% notice tip %}} Đảm bảo rằng bạn chọn một tên bucket duy nhất trên toàn cầu. {{% /notice %}}

2. **Liệt kê danh sách các S3 bucket**

   Để xem danh sách các **bucket** hiện có trong tài khoản của bạn:

   ```bash
   aws s3 ls
   ```

   ![AWS CLI Liệt Kê Bucket](/images/3-s3/0002.png?featherlight=false&width=90pc)

{{% notice warning %}} Nếu không thấy bucket nào, bạn cần đảm bảo rằng bạn đã có quyền truy cập vào AWS S3. {{% /notice %}}

3. **Kiểm tra object trong S3 bucket**

   Để liệt kê các **object** trong một bucket cụ thể:

   ```bash
   aws s3 ls s3://bucket-name
   ```

   ![AWS CLI Kiểm Tra Object](/images/3-s3/0004.png?featherlight=false&width=90pc)

4. **Xóa object trong S3 bucket**

   Khi cần xóa một **object** từ bucket:

   ```bash
   aws s3 rm s3://bucket-name/object
   ```

   ![AWS CLI Xóa Object](/images/3-s3/0005.png?featherlight=false&width=90pc)

{{% notice note %}} **Lưu ý**: Việc xóa object không thể hoàn tác, hãy cẩn thận khi thực hiện lệnh này. {{% /notice %}}

5. **Xóa S3 bucket**

   Sau khi đã xóa toàn bộ object trong bucket, bạn có thể xóa bucket bằng lệnh sau:

   ```bash
   aws s3 rb s3://bucket-name
   ```

   ![AWS CLI Xóa Bucket](/images/3-s3/0006.png?featherlight=false&width=90pc)

{{% notice warning %}} **Cảnh báo**: Chỉ có thể xóa bucket nếu nó rỗng. {{% /notice %}}

