---
title: "Giới thiệu"
date: "`r Sys.Date()`"
weight: 1 
chapter: false
pre: "<b> 1. </b>"
---

#### Tổng quan

Trong bài thực hành này, bạn sẽ được giới thiệu về AWS Command Line Interface (AWS CLI) và cách sử dụng nó để tương tác với các dịch vụ AWS.

#### AWS CLI

**ℹ️ Information**: **AWS Command Line Interface (AWS CLI)** là một công cụ mã nguồn mở cho phép bạn tương tác với các dịch vụ AWS thông qua các lệnh trong giao diện dòng lệnh (command-line). Với quá trình thiết lập đơn giản, AWS CLI giúp bạn triển khai các chức năng tương tự như trên AWS Management Console.

#### Môi trường hỗ trợ

AWS CLI hỗ trợ nhiều môi trường dòng lệnh khác nhau:

- **Linux Shells**: Sử dụng các shell phổ biến như Bash, Zsh, và Tcsh để chạy lệnh trên Linux hoặc macOS.
- **Windows Command Line**: Trên Windows, bạn có thể sử dụng Command Prompt hoặc PowerShell để chạy các lệnh.
- **Remote Access**: Bạn có thể chạy lệnh trên Amazon Elastic Compute Cloud (Amazon EC2) thông qua PuTTY, SSH hoặc AWS Systems Manager.

#### Khả năng và tính năng

AWS CLI cung cấp quyền truy cập trực tiếp vào API của các dịch vụ AWS, cho phép bạn:

- Khám phá và sử dụng các dịch vụ AWS một cách linh hoạt
- Viết các tập lệnh (scripts) để quản lý tài nguyên
- Thực hiện các tác vụ như triển khai, quản lý, và giám sát hệ thống

💡 **Pro Tip**: Ngoài các lệnh tương đương với API, một số dịch vụ AWS cung cấp các lệnh cấp cao được **tùy chỉnh** (customization) trên AWS CLI, giúp đơn giản hóa việc sử dụng những dịch vụ có API phức tạp.

#### Lợi ích của AWS CLI

1. **Tiện lợi**: Thao tác trên dòng lệnh dễ dàng, linh hoạt, và có thể được tự động hóa qua scripts.
2. **Tiết kiệm thời gian**: Chạy các lệnh đồng thời hoặc script phức tạp mà không cần thao tác thủ công qua AWS Management Console.
3. **🔒 Security Note**: Dễ dàng tích hợp với các dịch vụ bảo mật của AWS như AWS Identity and Access Management (IAM) để quản lý quyền truy cập và tuân thủ nguyên tắc đặc quyền tối thiểu.
4. **Tự động hóa**: Tích hợp vào các quy trình CI/CD và các công cụ DevOps khác.

⚠️ **Warning**: Khi sử dụng AWS CLI, hãy luôn đảm bảo bảo vệ thông tin xác thực của bạn và không bao giờ chia sẻ khóa truy cập trong mã nguồn công khai hoặc repositories.

#### Kết luận

AWS CLI là công cụ mạnh mẽ và tiện lợi cho quản trị viên, nhà phát triển, và những người quản lý hệ thống. Thông qua việc sử dụng AWS CLI, bạn có thể tận dụng toàn bộ tiềm năng của AWS API để tự động hóa và quản lý hạ tầng một cách hiệu quả.
