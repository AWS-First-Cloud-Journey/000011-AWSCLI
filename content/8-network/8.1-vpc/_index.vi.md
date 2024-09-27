---
title : "AWS CLI với VPC"
date : 2024-09-27
weight : 1
chapter : false
pre : " <b> 8.1 </b> "
---

#### AWS CLI với VPC

#### **Tạo VPC**

1. Thực hiện tạo VPC bằng **AWS CLI**:
    ```bash
    aws ec2 create-vpc --cidr-block 10.0.0.0/16 --query Vpc.VpcId --output text
    ```

    {{% notice note %}} Lệnh này sẽ trả về VPC ID, cần ghi lại để sử dụng cho các bước tiếp theo. {{% /notice %}}

    ![Tạo VPC](/images/vpc/0002.png?featherlight=false&width=90pc)

#### **Tạo Subnet**

2. Tiếp theo, chúng ta sẽ tạo subnet dựa theo **VPC ID** đã tạo:
    ```bash
    aws ec2 create-subnet --vpc-id VPC-ID --cidr-block 10.0.1.0/24
    ```

    {{% notice tip %}} Thay thế `VPC-ID` bằng giá trị thực tế đã nhận từ bước tạo VPC. {{% /notice %}}

    ![Tạo Subnet](/images/vpc/0003.png?featherlight=false&width=90pc)

3. Tạo một subnet thứ hai với CIDR khác:
    ```bash
    aws ec2 create-subnet --vpc-id VPC-ID --cidr-block 10.0.2.0/24
    ```

    {{% notice info %}} Đảm bảo các subnet không trùng CIDR để tránh xung đột mạng. {{% /notice %}}

    ![Tạo Subnet 2](/images/vpc/0004.png?featherlight=false&width=90pc)

#### **Chú ý khi sử dụng CLI**

5. Kiểm tra kết quả tạo subnet:
    ```bash
    aws ec2 describe-subnets --filters "Name=vpc-id,Values=VPC-ID"
    ```

    {{% notice warning %}} Đảm bảo rằng cấu hình mạng không xung đột với các tài nguyên khác trong cùng một VPC. {{% /notice %}}

#### **Bảng các lệnh phổ biến**

| Lệnh                                 | Mô tả                          |
|--------------------------------------|---------------------------------|
| `aws ec2 create-vpc`                 | Tạo một VPC mới                |
| `aws ec2 create-subnet`              | Tạo một subnet trong VPC        |
| `aws ec2 describe-subnets`           | Hiển thị thông tin về các subnet|

