---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

#### Tổng quan

Ở bài thực hành này, bạn sẽ được tìm hiểu về AWS CLI và sử dụng nó để tương tác với dịch vụ AWS.

#### AWS CLI

AWS Command Line Interface (AWS CLI) là một công cụ mã nguồn mở (open source) cho phép bạn tương tác với các dịch vụ AWS bằng cách sử dụng các lệnh trong cửa sổ lệnh (command-line shell). Với quá trình thiết lập đơn giản, AWS CLI cho phép bạn chạy các lệnh triển khai các chức năng tương đương với chức năng được cung cấp bởi AWS Management Console trên trình duyệt.

AWS CLI hỗ trợ các cửa sổ lệnh sau:

- **Linux shells** – Sử dụng các chương trình cửa sổ lệnh phổ biến như bash, zsh và tcsh để chạy các lệnh trong Linux hoặc macOS.
- **Windows command line** – Trên Windows, chạy lệnh trong cửa sổ lệnh Windows (command prompt) hoặc trong PowerShell.
- **Remotely** – Chạy lệnh trong máy ảo Amazon Elastic Compute Cloud (Amazon EC2) thông qua cửa sổ lệnh như PuTTY hoặc SSH hoặc AWS Systems Manager.

Tất cả các chức năng quản trị, quản lý và truy cập tài nguyên AWS trong AWS Management Console đều có sẵn trong AWS API và CLI. Các tính năng và dịch vụ AWS mới sẽ được cung cấp đầy đủ như trên AWS Management Console thông qua API và CLI ngay sau khi ra mắt hoặc trong vòng 180 ngày sau đó.

AWS CLI cung cấp quyền truy cập trực tiếp vào các API công khai của các dịch vụ AWS. Bạn có thể khám phá khả năng của một dịch vụ AWS với AWS CLI và phát triển các tập lệnh shell scripts để quản lý tài nguyên của bạn. Ngoài các lệnh cấp thấp tương đương với API, nhiều dịch vụ AWS cho phép các tùy chỉnh (customization) trên AWS CLI. Các tùy chỉnh có thể bao gồm các lệnh cấp cao hơn giúp đơn giản hóa việc sử dụng dịch vụ có API phức tạp.
