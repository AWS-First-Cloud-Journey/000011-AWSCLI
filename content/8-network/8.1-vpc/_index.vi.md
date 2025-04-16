---
title : "AWS CLI với VPC"
date : 2024-09-27
weight : 1
chapter : false
pre : " <b> 8.1 </b> "
---

#### AWS CLI với Amazon VPC

#### Tạo VPC

1. Thực hiện tạo VPC bằng **AWS CLI**:
    ```bash
    aws ec2 create-vpc --cidr-block 10.0.0.0/16 --query Vpc.VpcId --output text
    ```

    ℹ️ **Information**: Lệnh này sẽ trả về VPC ID, cần ghi lại để sử dụng cho các bước tiếp theo. VPC ID là định danh duy nhất cho Virtual Private Cloud của bạn.

    ![Tạo VPC](/images/vpc/0002.png?featherlight=false&width=90pc)

#### Tạo Subnet

2. Tiếp theo, chúng ta sẽ tạo subnet dựa theo **VPC ID** đã tạo:
    ```bash
    aws ec2 create-subnet --vpc-id vpc-xxxxxxxxxxxxxxxxx --cidr-block 10.0.1.0/24
    ```

    💡 **Pro Tip**: Thay thế `vpc-xxxxxxxxxxxxxxxxx` bằng giá trị VPC ID thực tế đã nhận từ bước tạo VPC. Sử dụng tham số `--availability-zone` nếu bạn muốn chỉ định AZ cụ thể.

    ![Tạo Subnet](/images/vpc/0003.png?featherlight=false&width=90pc)

3. Tạo một subnet thứ hai với CIDR khác:
    ```bash
    aws ec2 create-subnet --vpc-id vpc-xxxxxxxxxxxxxxxxx --cidr-block 10.0.2.0/24
    ```

    ⚠️ **Warning**: Đảm bảo các subnet không trùng CIDR để tránh xung đột mạng. Mỗi subnet phải có dải địa chỉ IP riêng biệt trong VPC.

    ![Tạo Subnet 2](/images/vpc/0004.png?featherlight=false&width=90pc)

#### Kiểm tra và quản lý tài nguyên VPC

4. Kiểm tra kết quả tạo subnet:
    ```bash
    aws ec2 describe-subnets --filters "Name=vpc-id,Values=vpc-xxxxxxxxxxxxxxxxx"
    ```

    🔒 **Security Note**: Khi thiết kế VPC, hãy xem xét các yếu tố bảo mật như Network ACLs và Security Groups để bảo vệ tài nguyên của bạn.

5. Tạo Internet Gateway và gắn vào VPC:
    ```bash
    # Tạo Internet Gateway
    aws ec2 create-internet-gateway --query InternetGateway.InternetGatewayId --output text
    
    # Gắn Internet Gateway vào VPC
    aws ec2 attach-internet-gateway --vpc-id vpc-xxxxxxxxxxxxxxxxx --internet-gateway-id igw-xxxxxxxxxxxxxxxxx
    ```

    ℹ️ **Information**: Internet Gateway cho phép các tài nguyên trong VPC giao tiếp với internet. Đây là thành phần cần thiết cho các ứng dụng public-facing.

#### Bảng các lệnh AWS CLI phổ biến cho VPC

| Lệnh | Mô tả |
|------|-------|
| `aws ec2 create-vpc` | Tạo một VPC mới |
| `aws ec2 create-subnet` | Tạo một subnet trong VPC |
| `aws ec2 create-internet-gateway` | Tạo Internet Gateway |
| `aws ec2 attach-internet-gateway` | Gắn Internet Gateway vào VPC |
| `aws ec2 create-route-table` | Tạo Route Table mới |
| `aws ec2 describe-subnets` | Hiển thị thông tin về các subnet |
| `aws ec2 describe-vpcs` | Liệt kê tất cả VPC trong region |
| `aws ec2 delete-vpc` | Xóa một VPC |
