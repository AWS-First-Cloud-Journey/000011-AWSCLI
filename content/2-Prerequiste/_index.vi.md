---
title: "Các bước chuẩn bị"
date: 2025-10-02
weight: 2
chapter: false
pre: "<b> 2. </b>"
---

#### Các bước chuẩn bị

**ℹ️ Information**: Trước khi bắt đầu bài thực hành, bạn cần hoàn thành các bước thiết lập cơ bản sau đây để đảm bảo môi trường AWS của bạn được cấu hình đúng cách.
- Tạo một tài khoản AWS để thực hiện bài thực hành.
- Tạo một **IAM User Group** để quản lý quyền hạn.
    - Truy cập **Identity and Access Management (IAM)**
    ![Prerequiste](/images/0/01.png?featherlight=false&width=90pc)

    - Click vào **User group**.
    - Chọn **Create group**.
     ![Prerequiste](/images/0/2.png?featherlight=false&width=90pc)

    - Nhập tên cho **User group**.
    - Kéo xuống **Attach permissions policies**, chọn **AdministratorAccess**.
    ![Prerequiste](/images/0/3.png?featherlight=false&width=90pc)
    ![Prerequiste](/images/0/4.png?featherlight=false&width=90pc)

- Tạo một **IAM User** với quyền truy cập thích hợp.
    - Truy cập **User**, chọn **Create User**.
    - Đặt tên **aws-cli-user**.
    - **Add user to group**, chọn **User group** vừa tạo.
    - Chọn **Next** và tạo user.
    ![Prerequiste](/images/0/5.png?featherlight=false&width=90pc)
    ![Prerequiste](/images/0/6.png?featherlight=false&width=90pc)
    ![Prerequiste](/images/0/7.png?featherlight=false&width=90pc)

- Tạo **AWS Access Key** để sử dụng cho AWS CLI hoặc SDK.

    - Chọn User vừa tạo.
    - Kéo xuống và chọn mục **Security credentials**, chọn **Create Access Key**.
    - Chọn **Command Line Interface (CLI)**.
    - Tick vào ô **I understand...**, chọn **Next**. 
    - Nhập mô tả và chọn **Create access key**.
    ![Prerequiste](/images/0/9.png?featherlight=false&width=90pc)
    ![Prerequiste](/images/0/10.png?featherlight=false&width=90pc)
    ![Prerequiste](/images/0/11.png?featherlight=false&width=90pc)
    ![Prerequiste](/images/0/12.png?featherlight=false&width=90pc)
    ![Prerequiste](/images/0/13.png?featherlight=false&width=90pc)
    
    - Sau khi có **Access key** và **Secret access key**, vui lòng copy vào notepad hoặc download **.csv file** để dùng cho các bước sau.
    ![Prerequiste](/images/0/14.png?featherlight=false&width=90pc)

- Hãy tạo thêm một user nữa tên **devops**, thêm user đó vào **aws-cli** và lặp lại các bước trên. 
    
- Khởi tạo một **EC2 Instance** và thiết lập quyền truy cập SSH để quản lý thông qua **AWS CLI**.
    - Truy cập EC2.
    - Chọn **Create instance**.
    - Đặt tên instance **aws-cli-instance**.
    ![Prerequiste](/images/0/15.png?featherlight=false&width=90pc)
    ![Prerequiste](/images/0/16.png?featherlight=false&width=90pc)

    - Giữ nguyên các giá trị mặc định, tiếp theo tiến hành tạo **Key pair**.
    ![Prerequiste](/images/0/17.png?featherlight=false&width=90pc)
    - Đảm bảo có quyền truy cập **SSH** để quản lý thông qua **AWS CLI**.
    ![Prerequiste](/images/0/18.png?featherlight=false&width=90pc)
    - Review lại và tiến hành **Create instance**, sau đó đợi 2 phút để instance **check passed**.


**🔒 Security Note**: Luôn tuân thủ nguyên tắc đặc quyền tối thiểu khi cấp quyền cho IAM User và đảm bảo bảo vệ AWS Access Key của bạn.

**💡 Pro Tip**: Sử dụng AWS CloudShell để tránh phải cài đặt AWS CLI trên máy tính cá nhân của bạn và để truy cập môi trường dòng lệnh AWS đã được xác thực sẵn.
