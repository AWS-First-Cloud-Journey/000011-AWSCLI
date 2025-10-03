---
title: "Cài đặt AWS CLI"
date: 2025-10-02
weight: 3
chapter: false
pre: "<b>3.</b>"
---

## Cài đặt AWS CLI

AWS Command Line Interface (AWS CLI) có hai phiên bản. Trong bài hướng dẫn này, chúng ta sẽ cài đặt AWS CLI v2 trên cả Windows và Ubuntu, vì phiên bản này đơn giản và hỗ trợ đầy đủ hơn so với AWS CLI v1.

- **AWS CLI phiên bản 1 (v1)**: Phiên bản ban đầu của AWS CLI, vẫn được hỗ trợ bởi AWS.
- **AWS CLI phiên bản 2 (v2)**: Phiên bản mới nhất, hỗ trợ tất cả các tính năng mới của AWS. Một số tính năng chỉ có trên v2 và không có trên v1.

### 1. Cài đặt AWS CLI

#### Đối với Linux:

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

#### Đối với Windows:

```bash
msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi
```

#### Đối với macOS:

```bash
sudo ln -s /folder/installed/aws-cli/aws /usr/local/bin/aws
sudo ln -s /folder/installed/aws-cli/aws_completer /usr/local/bin/aws_completer
```

![AWS CLI](/images/1/0001.png?featherlight=false&width=90pc)

### 2. Kiểm tra cài đặt AWS CLI:

```bash
aws --version
```

![AWS CLI](/images/1/0002.png?featherlight=false&width=90pc)

## Cấu hình AWS CLI

### 3. Tạo Default Profile

Sử dụng lệnh `aws configure` để thiết lập AWS CLI. Lệnh này sẽ yêu cầu nhập các thông tin quan trọng:

- **Access Key ID**
- **Secret Access Key**
- **Vùng AWS (Region)**
- **Định dạng xuất (Output format)**

```bash
aws configure
```

Hãy nhập **Access key ID** và **Secret Acces Key** của **aws-cli-user**, các giá trị còn lại giữ nguyên:

```bash
AWS Access Key ID [None]: *aws-cli-user_Access Key ID*
AWS Secret Access Key [None]: *aws-cli-user_Secret Access Key*
Default region name [None]: *ap-southeast-1*
Default output format [None]: *json*
```

![AWS CLI](/images/1/0003.png?featherlight=false&width=90pc)

Cấu hình này được lưu trong file `credentials` dưới profile `default`. Profile `default` sẽ được AWS CLI sử dụng nếu không chỉ định profile khác.

## Tạo Profile Riêng

### 4. Cấu hình nhiều profile

Để tạo profile khác, ví dụ `devops`, sử dụng lệnh sau, nhập **Access Key ID** và **Secret Access Key** của user **devops**, các giá trị còn lại giữ nguyên:

```bash
aws configure --profile devops
```

![AWS CLI](/images/1/0005.png?featherlight=false&width=90pc)

Profile chứa **Access Key ID** và **Secret Access Key** để ký các yêu cầu gửi tới AWS.

### 5. Kiểm tra cấu hình profile

![AWS CLI](/images/1/0006.png?featherlight=false&width=90pc)

## Quản lý Nhiều Profile

### 6. Kiểm tra thông tin credentials

```bash
cd ~/.aws/
ls
cat config
```

![AWS CLI](/images/1/0007.png?featherlight=false&width=90pc)

### 7. Kiểm tra vùng (region) của profile

```bash
aws configure get region --profile devops
```

![AWS CLI](/images/1/0008.png?featherlight=false&width=90pc)

### 8. Liệt kê danh sách cấu hình

```bash
aws configure list
```

![AWS CLI](/images/1/0009.png?featherlight=false&width=90pc)

### 9. Liệt kê các profile

```bash
aws configure list-profiles
```

![AWS CLI](/images/1/00010.png?featherlight=false&width=90pc)

{{% notice tip %}}
Bạn có thể chỉnh sửa hoặc thêm profile bằng cách cập nhật trực tiếp các tệp **config** và **credentials** với trình soạn thảo trên hệ điều hành của bạn.
{{% /notice %}}

