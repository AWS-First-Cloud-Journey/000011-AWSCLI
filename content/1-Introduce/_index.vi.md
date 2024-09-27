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

**AWS Command Line Interface (AWS CLI)** là một công cụ mã nguồn mở cho phép bạn tương tác với các dịch vụ AWS thông qua các lệnh trong giao diện dòng lệnh (command-line). Với quá trình thiết lập đơn giản, AWS CLI giúp bạn triển khai các chức năng tương tự như trên AWS Management Console.

##### Các môi trường dòng lệnh hỗ trợ AWS CLI:

- **Linux Shells**: Sử dụng các shell phổ biến như Bash, Zsh, và Tcsh để chạy lệnh trên Linux hoặc macOS.
- **Windows Command Line**: Trên Windows, bạn có thể sử dụng Command Prompt hoặc PowerShell để chạy các lệnh.
- **Remote Access**: Bạn có thể chạy lệnh trên Amazon Elastic Compute Cloud (Amazon EC2) thông qua PuTTY, SSH hoặc AWS Systems Manager.

AWS CLI cung cấp quyền truy cập trực tiếp vào API của các dịch vụ AWS, cho phép bạn khám phá và sử dụng các dịch vụ này một cách linh hoạt. Bạn có thể viết các tập lệnh (scripts) để quản lý tài nguyên, đồng thời thực hiện các tác vụ như triển khai, quản lý, và giám sát hệ thống.

Ngoài các lệnh tương đương với API, một số dịch vụ AWS cho phép **tùy chỉnh** (customization) trên AWS CLI, cung cấp các lệnh cấp cao nhằm đơn giản hóa việc sử dụng những dịch vụ có API phức tạp.

#### Lợi ích của AWS CLI

1. **Tiện lợi**: Thao tác trên dòng lệnh dễ dàng, linh hoạt, và có thể được tự động hóa qua scripts.
2. **Tiết kiệm thời gian**: Chạy các lệnh đồng thời hoặc script phức tạp mà không cần thao tác thủ công qua AWS Management Console.
3. **Bảo mật**: Dễ dàng tích hợp với các dịch vụ bảo mật của AWS như IAM để quản lý quyền truy cập.

#### Kết luận

AWS CLI là công cụ mạnh mẽ và tiện lợi cho quản trị viên, nhà phát triển, và những người quản lý hệ thống. Thông qua việc sử dụng AWS CLI, bạn có thể tận dụng toàn bộ tiềm năng của AWS API để tự động hóa và quản lý hạ tầng một cách hiệu quả.
