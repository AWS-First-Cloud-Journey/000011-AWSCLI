---
title: "Các bước chuẩn bị"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: "<b> 2. </b>"
---

#### Các bước chuẩn bị

**ℹ️ Information**: Trước khi bắt đầu bài thực hành, bạn cần hoàn thành các bước thiết lập cơ bản sau đây để đảm bảo môi trường AWS của bạn được cấu hình đúng cách.

- Tạo một tài khoản AWS để thực hiện bài thực hành.
- Tạo một **IAM User Group** để quản lý quyền hạn.
- Tạo một **IAM User** với quyền truy cập thích hợp.
- Tạo **AWS Access Key** để sử dụng cho AWS CLI hoặc SDK.
- Khởi tạo một **EC2 Instance** và thiết lập quyền truy cập SSH để quản lý thông qua **AWS CLI**.

**🔒 Security Note**: Luôn tuân thủ nguyên tắc đặc quyền tối thiểu khi cấp quyền cho IAM User và đảm bảo bảo vệ AWS Access Key của bạn.

**💡 Pro Tip**: Sử dụng AWS CloudShell để tránh phải cài đặt AWS CLI trên máy tính cá nhân của bạn và để truy cập môi trường dòng lệnh AWS đã được xác thực sẵn.
