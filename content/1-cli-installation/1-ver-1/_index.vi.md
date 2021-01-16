+++
title = "AWS CLI phiên bản 1"
date = 2020
weight = 1
chapter = false
pre = "<b>1.1. </b>"
+++

AWS CLI phiên bản 1 là AWS CLI ban đầu và AWS tiếp tục hỗ trợ nó. Tuy nhiên, các tính năng mới chính được giới thiệu trong AWS CLI phiên bản 2 có thể không được hỗ trợ o AWS CLI phiên bản 1. Để sử dụng các tính năng đó, bạn phải cài đặt AWS CLI phiên bản 2.

**Nội dung**
- [1. Cài đặt AWS CLI trên Windows](#1-cài-đặt-aws-cli-trên-windows)
  - [Cài đặt sử dụng bộ cài MSI](#cài-đặt-sử-dụng-bộ-cài-msi)
  - [Cài đặt sử dụng Python và pip trên Windows](#cài-đặt-sử-dụng-python-và-pip-trên-windows)
- [2. Cài đặt AWS CLI trên Ubuntu](#2-cài-đặt-aws-cli-trên-ubuntu)
  - [Cài đặt AWS CLI phiên bản 1 dùng bộ cài đặt đóng gói với quyền superuser](#cài-đặt-aws-cli-phiên-bản-1-dùng-bộ-cài-đặt-đóng-gói-với-quyền-superuser)
  - [Cài đặt AWS CLI phiên bản 1 dùng bộ cài đặt đóng gói không có quyền superuser](#cài-đặt-aws-cli-phiên-bản-1-dùng-bộ-cài-đặt-đóng-gói-không-có-quyền-superuser)

### 1. Cài đặt AWS CLI trên Windows
Bạn có thể cài đặt phiên bản 1 của AWS Command Line Interface (AWS CLI) trên Windows bằng cách sử dụng bộ cài đặt độc lập (khuyên dùng) hoặc pip - trình quản lý gói cho Python. (Nếu bạn đã cài đặt pip.)

Đừng thêm vào biểu tượng dấu nhắc (C: \>) khi bạn nhập lệnh. Chúng được thêm vào trong các đoạn lệnh để phân biệt các lệnh mà bạn nhập với kết quả trả về bởi CLI. Phần còn lại của hướng dẫn này sử dụng biểu tượng dấu nhắc chung ($), ngoại trừ các trường hợp lệnh dành riêng cho Windows.

{{% notice warning %}}
AWS CLI phiên bản 1 không còn hỗ trợ phiên bản Python 2.6 và 3.3. Tất cả các phiên bản AWS CLI phiên bản 1 được phát hành sau ngày 10 tháng 1 năm 2020, bắt đầu từ bản 1.17, yêu cầu Python 2.7, Python 3.4 hoặc mới hơn.

Thay đổi này không ảnh hưởng đến phiên bản bộ cài đặt Windows MSI của AWS CLI phiên bản 1 và AWS CLI phiên bản 2.

Để biết thêm chi tiết, xem thêm tài liệu [Sử dụng AWS CLI phiên bản 1 với các phiên bản Python cũ](https://docs.aws.amazon.com/cli/latest/userguide/deprecate-old-python-versions.html) và bài viết [Thông báo ngừng sử dụng](https://aws.amazon.com/blogs/developer/deprecation-of-python-2-6-and-python-3-3-in-botocore-boto3-and-the-aws-cli/).
{{% /notice %}}

#### Cài đặt sử dụng bộ cài MSI
1. Tải bộ cài MSI tương ứng với hệ điều hành:
   - Bộ cài MSI AWS CLI cho Windows (64-bit): https://s3.amazonaws.com/aws-cli/AWSCLI64PY3.msi
   - Bộ cài MSI AWS CLI cho Windows (32-bit): https://s3.amazonaws.com/aws-cli/AWSCLI32PY3.msi
   - Bộ cài AWS CLI kết hợp cho Windows: https://s3.amazonaws.com/aws-cli/AWSCLISetup.exe (bao gồm cả bộ cài đặt MSI 32 bit và 64 bit và tự động cài đặt phiên bản phù hợp)
2. Chạy bộ cài MSI vừa tải.
3. Thực hiện theo các hướng dẫn trên màn hình. Mặc định, AWS CLI phiên bản 1 cài đặt tại đường dẫn ```C:\Program Files\Amazon\AWSCLI``` (bản 64-bit) hoặc ```C:\Program Files (x86)\Amazon\AWSCLI``` (bản 32-bit).
4. Để kiểm tra lại kết quả cài đặt, ta dùng lệnh ```aws --version``` trong cửa sổ lệnh Windows (Mở **Start menu**, tìm **cmd** để chạy **Command prompt**).

{{% notice tip %}}
Nếu Windows không thể tìm thấy lệnh khi chạy lệnh, bạn có thể cần phải đóng và mở lại cửa sổ lệnh để làm mới đường dẫn hoặc phải tự tay [thêm thư mục cài đặt vào biến môi trường PATH của hệ điều hành](https://docs.aws.amazon.com/cli/latest/userguide/install-windows.html#awscli-install-windows-path).
{{% /notice %}}

#### Cài đặt sử dụng Python và pip trên Windows
{{% notice info %}}
Đảm bảo rằng bạn đã cài đặt **Python 3** trong hệ thống.
{{% /notice %}}

1. Để cài đặt AWS CLI phiên bản 1, sử dụng lệnh ```pip3``` (nếu sử dụng Python 3 hoặc mới hơn) hoặc lệnh ```pip```.  
```pip3 install awscli``` hoặc ```pip3 install --user --upgrade awscli``` (Để nâng cấp phiên bản mới)
2. Xác minh rằng AWS CLI phiên bản 1 đã được cài đặt.
```aws --version```
{{% notice info %}}
Sau khi cài đặt AWS CLI phiên bản 1 sử dụng ```pip```, hãy thêm thư mục cài đặt vào biến môi trường ```PATH``` của hệ điều hành. Với cài đặt sử dụng bộ cài MSI, việc này sẽ tự được thực hiện. Nhưng nếu lệnh ```aws``` vẫn không chạy sau khi bạn cài đặt, bạn có thể cần phải thiết lập theo cách thủ công.
{{% /notice %}}
3. Nhấn phím Windows và nhập ```environment variables```.
4. Chọn **Edit environment variables for your account**.
5. Chọn **PATH**, và sau đó chọn **Edit**.
6. Thêm đường dẫn bạn tìm thấy vào ô **Variable value**, VD: *C:\Program Files\Amazon\AWSCLI\bin\aws.exe*.
7. Chọn **OK** hai lần để áp dụng thiết lập mới.
8. Đóng mọi cửa sổ lệnh đang chạy và mở lại.

### 2. Cài đặt AWS CLI trên Ubuntu
{{% notice tip %}}
Bạn phải cài đặt Python 2 phiên bản 2.7 trở lên hoặc Python 3 phiên bản 3.4 trở lên. Để biết xem hướng dẫn cài đặt, hãy xem trang [Tải Python](https://wiki.python.org/moin/BeginnersGuide/Download) ở trong **Hướng dẫn cơ bản về Python**.
{{% /notice %}}

#### Cài đặt AWS CLI phiên bản 1 dùng bộ cài đặt đóng gói với quyền superuser
1. Tải bộ cài đặt AWS CLI version 1 sử dụng các cách sau:
   - Tải xuống bằng lệnh ```curl```  
   ```bash
   $ curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip"
   ```
   - Tải xuống bằng liên kết trực tiếp: https://s3.amazonaws.com/aws-cli/awscli-bundle.zip
2. Giải nén các tập tin từ gói. Nếu bạn không có chương trình để giải nén các tập tin, hãy sử dụng trình quản lý gói của Ubuntu để cài đặt.
```bash
$ unzip awscli-bundle.zip
```
3. Chạy bộ cài đặt. Bộ cài đặt cài đặt AWS CLI tại đường dẫn ```/usr/local/aws``` và tạo symlink cho ```aws``` tại đường dẫn ```/usr/local/bin```. Sử dụng tùy chọn ```-b``` để tạo symlink không cần chỉ định thư mục cài đặt trong biến ```PATH``` của người dùng. Điều này sẽ cho phép tất cả người dùng gọi AWS CLI bằng cách nhập ```aws``` từ bất kỳ thư mục nào.
```bash
$ sudo <path to Python> ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws
```
4. Chắc chắn rằng AWS CLI đã được cài đặt với ```aws --version```.

#### Cài đặt AWS CLI phiên bản 1 dùng bộ cài đặt đóng gói không có quyền superuser
1. Tải bộ cài đặt AWS CLI version 1 sử dụng các cách sau:
   - Tải xuống bằng lệnh ```curl```  
   ```bash
   $ curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip"
   ```
   - Tải xuống bằng liên kết trực tiếp: https://s3.amazonaws.com/aws-cli/awscli-bundle.zip
2. Giải nén các tập tin từ gói. Nếu bạn không có chương trình để giải nén các tập tin, hãy sử dụng trình quản lý gói của Ubuntu để cài đặt.
```bash
$ unzip awscli-bundle.zip
```
3. Chạy bộ cài đặt. Bộ cài đặt cài đặt AWS CLI tại đường dẫn ```/usr/local/aws``` và tạo symlink cho ```aws``` tại đường dẫn ```/usr/local/bin```. Sử dụng tùy chọn ```-b``` để chỉ định đường dẫn bộ cài sẽ đặt sẽ lưu tập tin symlink của lệnh ```aws```. Bạn phải có quyền ghi vào thư mục được chỉ định.
```bash
$ ./awscli-bundle/install -b ~/bin/aws
```
4. Đảm bảo thư mục chứa AWS CLI phiên bản 1 là một phần biến ```PATH``` của bạn.
   - Tìm tập tin cấu hình cửa sổ lệnh trong thư mục của người dùng. Nếu không chắc loại script của cửa sổ lệnh, bạn có thể chạy ```echo $SHELL```.  
   ```bash
   $ ls -a ~
   .  ..  .bash_logout  .bash_profile  .bashrc  Desktop  Documents  Downloads
   ```
     - **Bash** – .bash_profile, .profile, or .bash_login (Ubuntu default)
     - **Zsh** – .zshrc
     - **Tcsh** – .tcshrc, .cshrc or .login
   - Thêm lệnh ```export``` vào cuối tập tin cấu hình cửa sổ lệnh theo ví dụ bên dưới.
   ```bash
   export PATH=~/.local/bin:$PATH
   ```
   - Áp dụng lại cấu hình cửa sổ lệnh để sử dụng cấu hình vừa thay đổi.
   ```bash
   $ source ~/.bash_profile
   ```
5. Xác minh rằng AWS CLI đã được cài đặt bằng lệnh ```$ aws --version```.