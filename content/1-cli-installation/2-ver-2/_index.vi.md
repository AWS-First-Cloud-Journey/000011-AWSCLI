+++
title = "AWS CLI phiên bản 2"
date = 2020
weight = 1
chapter = false
pre = "<b>1.2. </b>"
+++

Phần này cung cấp liên kết đến thông tin về cách cài đặt phiên bản 2 của AWS Command Line Interface (AWS CLI) trên hệ điều hành Windows và Ubuntu.

{{% notice warning %}}
AWS CLI versions 1 and 2 use the same ```aws``` command name. If you have both versions installed, your computer uses the first one found in your search path. If you previously installed AWS CLI version 1, we recommend that you do one of the following to use AWS CLI version 2:
AWS CLI phiên bản 1 và 2 sử dụng cùng một lệnh ```aws```. Nếu bạn đã cài đặt cả hai phiên bản, máy tính của bạn sẽ sử dụng phiên bản đầu tiên được tìm thấy. Nếu trước đây bạn đã cài đặt AWS CLI phiên bản 1, AWS khuyến nghị nên thực hiện một trong các thao tác sau để sử dụng AWS CLI phiên bản 2:
- **Khuyến nghị** – Gỡ cài đặt AWS CLI phiên bản 1 và chỉ sử dụng AWS CLI phiên bản 2.
- Sử dụng khả năng của hệ điều hành để tạo một symbolic link (symlink) hoặc alias với tên khác đi cho một trong hai lệnh ```aws```. Ví dụ: Bạn có thể sử dụng [symbolic link](https://www.linux.com/tutorials/understanding-linux-links/) hoặc [alias](https://www.linux.com/tutorials/aliases-diy-shell-commands/) trên Linux và macOS, hoặc [DOSKEY](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/doskey) trên Windows.
{{% /notice %}}

**Nội dung**
- [1. Cài đặt AWS CLI trên Windows](#1-cài-đặt-aws-cli-trên-windows)
- [2. Install AWS CLI on Ubuntu](#2-install-aws-cli-on-ubuntu)

#### 1. Cài đặt AWS CLI trên Windows
{{% notice info %}}
Trước khi cài đặt hoặc cập nhật AWS CLI phiên bản 2 trên Windows, hãy đảm bảo những điều sau:
- Phiên bản hệ điều hành là phiên bản **64-bit** của Windows XP hoặc mới hơn .
- Quyền **Administrator** để cài đặt phần mềm.
{{% /notice %}}

1. Tải bộ cài MSI tương ứng với hệ điều hành Windows (64-bit):
   - Bộ cài AWS CLI phiên bản mới nhất: https://awscli.amazonaws.com/AWSCLIV2.msi
   - Để tải phiên bản AWS CLI nhất định: Thêm dấu gạch nối và số phiên bản vào tên tập tin. (VD: phiên bản 2.0.30 sẽ là AWSCLIV2-2.0.30.msi và liên kết sẽ là https://awscli.amazonaws.com/AWSCLIV2-2.0.30.msi)
2. Chạy bộ cài MSI vừa tải và thực hiện theo các hướng dẫn trên màn hình. Mặc định, AWS CLI phiên bản 2 cài đặt tại đường dẫn ```C:\Program Files\Amazon\AWSCLIV2```.
3. Để kiểm tra lại kết quả cài đặt, ta dùng lệnh ```aws --version``` trong cửa sổ lệnh Windows (Mở **Start menu**, tìm **cmd** để chạy **Command prompt**).

{{% notice tip %}}
Nếu Windows không thể tìm thấy lệnh khi chạy lệnh, bạn có thể cần phải đóng và mở lại cửa sổ lệnh để làm mới đường dẫn hoặc phải tự tay [thêm thư mục cài đặt vào biến môi trường PATH của hệ điều hành](https://docs.aws.amazon.com/cli/latest/userguide/install-windows.html#awscli-install-windows-path).
{{% /notice %}}

#### 2. Install AWS CLI on Ubuntu
{{% notice info %}}
- Nếu bạn không có chương trình để giải nén các tập tin (unzip), hãy sử dụng trình quản lý gói của Ubuntu để cài đặt hoặc sử dụng phần mềm tương tự.
- AWS CLI version 2 sử dụng ```glibc```, ```groff```, and ```less```. Chúng được bao gồm theo mặc định trong hầu hết trong các Linux distro.
- AWS hỗ trợ AWS CLI phiên bản 2 trên phiên bản 64 bit của các Linux distro gần đây của CentOS, Fedora, Ubuntu, Amazon Linux 1 và Amazon Linux 2.
- AWS hỗ trợ AWS CLI phiên bản 2 trên Linux ARM.
- Because AWS doesn't maintain third-party repositories, we can’t guarantee that they contain the latest version of the AWS CLI.
- Vì AWS không quản lý các repository của bên thứ ba, AWS không đảm bảo rằng chúng chứa phiên bản AWS CLI mới nhất.
{{% /notice %}}

1. Download the installation file in one of the following ways:
   - **Sử dụng lệnh curl** – Tùy chọn ```-o``` chỉ định tên tệp mà gói đã tải xuống được ghi vào ```awscliv2.zip```.
     - **Tải phiên bản hiện tại của AWS CLI**, sử dụng lệnh sau:  
     ```bash
     curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
     ```
     - **Tải phiên bản cụ thể của AWS CLI**, thêm dấu gạch nối và số phiên bản vào tên tập tin. phiên bản 2.0.30 sẽ là awscli-exe-linux-x86_64-2.0.30.zip và câu lệnh sẽ là:  
     ```bash
     $ curl "https://awscli.amazonaws.com/*awscli-exe-linux-x86_64-2.0.30.zip*" -o "awscliv2.zip"
     ```
   - **Tải xuống bằng URL** – Để tải xuống bộ cài đặt bằng trình duyệt của bạn, hãy sử dụng một trong các URL sau. Bạn có thể xác minh tính toàn vẹn và tính xác thực của bộ cài đặt đã tải xuống trước khi giải nén (unzip).
     - **Tải phiên bản hiện tại của AWS CLI**: https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip
     - **Tải phiên bản cụ thể của AWS CLI**, thêm dấu gạch nối và số phiên bản vào tên tập tin. phiên bản 2.0.30 sẽ là awscli-exe-linux-x86_64-2.0.30.zip và liên kết sẽ là: https://awscli.amazonaws.com/awscli-exe-linux-x86_64-2.0.30.zip
2. Giải nén các tập tin từ gói. Nếu bạn không có chương trình để giải nén các tập tin, hãy sử dụng trình quản lý gói của Ubuntu để cài đặt.
```unzip awscliv2.zip```
3. Chạy bộ cài đặt. Lệnh cài đặt sử dụng tập tin ```install``` trong thư mục vừa giải nén. Mặc định, chương trình sẽ được cài đặt vào ```/usr/local/aws-cli```, và được tạo symbolic link trong ```/usr/local/bin```. Lệnh cài đặt sẽ cần đến ```sudo``` nhằm có quyền ghi tập tin vào các thư mục hệ thống.  
```sudo ./aws/install```
4. Chắc chắn rằng AWS CLI đã được cài đặt với ```aws --version```.