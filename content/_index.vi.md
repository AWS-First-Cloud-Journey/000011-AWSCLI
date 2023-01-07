---
title : "Làm quen với AWS CLI"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---

# Làm quen với AWS CLI

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

#### Profile

- Profile là tập các thiết lập và định danh cho phép bạn sử dụng các lệnh có trong AWS CLI. Mặc định, AWS CLI sử dụng default profile. Ngoài ra, bạn còn có thể tạo thêm nhiều profile khác gọi là profile riêng với thông số --profile.
- AWS CLI lưu trữ thông tin của các profile trong tập tin config và credentials. Ngoài việc tạo thêm profile với thông số --profile, bạn có thể tạo thêm các profile khác bằng cách thêm các thiết lập trực tiếp vào các tập tin config và credentials.
- Với thông số --profile, bạn có thể chỉ định một profile cụ thể để nó thực hiện những câu lệnh trong AWS CLI. Ngoài ra, bạn cũng có thể chỉ định một profile trong biến môi trường (AWS_PROFILE) để thay thế default profile ở một session nào đó.

#### Cơ bản về cấu hình

Chúng ta sẽ sử dụng lệnh aws configure. Đây được xem là cách nhanh nhất để thiết lập cho AWS CLI. Cửa sổ lệnh sẽ xuất hiện yêu cầu về 4 thông tin như sau:

  - Access key ID
  - Secret access key
  - AWS Region (Vùng)
  - Output format (Định dạng xuất)

#### Access key ID và secret access key

Access key bao gồm access key ID và secret access key, được sử dụng để ký các yêu cầu ứng dụng mà bạn gửi tới AWS.

#### Region (Vùng)

Default region name xác định Khu vực AWS có máy chủ mà bạn muốn gửi yêu cầu của mình theo mặc định. Đây thường là Region gần bạn nhất, nhưng nó có thể là bất kỳ Region nào. Ví dụ: bạn có thể nhập us-west-2 để sử dụng US West (Oregon). Đây là Region mặc định mà tất cả các yêu cầu sau này sẽ được gửi đến, trừ khi bạn chỉ định khác.

#### Output format (Định dạng xuất)

Default output format chỉ định cách các kết quả trả về được định dạng. Loại có thể là bất kỳ giá trị nào trong danh sách bên dưới. Nếu bạn không chỉ định định dạng đầu ra thì json được sử dụng mặc định.

- **json** – Đầu ra được định dạng dưới dạng chuỗi JSON.
- **yaml** – Đầu ra được định dạng dưới dạng chuỗi YAML. (Chỉ hỗ trợ ở AWS CLI v2.)
- **yaml-stream** – Đầu ra là luồng và được định dạng dưới dạng chuỗi YAML. Luồng cho phép xử lý nhanh hơn các loại dữ liệu lớn. (Chỉ hỗ trợ ở AWS CLI phiên bản 2.)
- **text** – Đầu ra được định dạng dưới dạng nhiều dòng giá trị chuỗi được phân tách bằng tab. Định dạng này có thể hữu ích để chuyển đầu ra tới trình xử lý văn bản, như grep, sed hoặc awk.
- **table** – Đầu ra được định dạng dưới dạng bảng sử dụng các ký tự +|- để tạo thành các đường viền ô. Nó thường trình bày thông tin ở định dạng “thân thiện với con người”, dễ đọc hơn nhiều so với các định dạng khác, nhưng không hiệu quả về mặt lập trình.

#### Nội dung chính:

1. [ Giới thiệu]()
2. [Chuẩn bị]()
3. [Cài đặt AWS CLI]()
4. [Kiểm tra tài nguyên]()
5. [AWS CLI với Amazon S3]()
6. [AWS SNS với AWS CLI]()
7. [AWS CLI với IAM]()
8. [AWS CLI với VPC]()
9. [AWS CLI với EC2]()
10. [Khắc phục lỗi]()
11. [Dọn dẹp tài nguyên]()