+++
title = "Cài đặt AWS CLI"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

#### Tổng quan

AWS Command Line Interface (AWS CLI) có hai phiên bản. Để đảm bảo tính thực tế của bài lab này, bạn sẽ chỉ thực hành cài đặt AWS CLI v2 cho Windows và Ubuntu vì nó đơn giản, thuận tiện, và đầy đủ hơn AWS CLI v1 rất nhiều.
- **AWS CLI phiên bản 1** (AWS CLI v1): là bản AWS CLI nguyên bản đầu tiên và vẫn sẽ được AWS hỗ trợ.
- **AWS CLI phiên bản 2** (AWS CLI v2): là bản AWS CLI mới nhất hỗ trợ tất cả các tính năng mới nhất của AWS. Một số tính năng có ở phiên bản 2 không được hỗ trợ tại phiên bản 1 và bạn cần phải nâng cấp phiên bản để sử dụng các tính năng đó.

{{% notice note %}}
Nếu bạn đã cài đặt cả hai phiên bản, máy tính của bạn sẽ sử dụng phiên bản đầu tiên được tìm thấy vì AWS CLI phiên bản 1 và 2 sử dụng cùng một lệnh ```aws```. Do đó, AWS khuyến nghị gỡ cài đặt AWS CLI phiên bản 1 và chỉ sử dụng AWS CLI phiên bản 2.
{{% /notice %}}

**Nội dung**
- [Tổng quan](#tổng-quan)
- [Cài đặt AWS CLI trên Windows](#cài-đặt-aws-cli-trên-windows)
- [Cài đặt AWS CLI trên Ubuntu](#cài-đặt-aws-cli-trên-ubuntu)

#### Cài đặt AWS CLI trên Windows

Trước khi cài đặt hoặc cập nhật AWS CLI phiên bản 2 trên Windows, hãy đảm bảo rằng bạn có phiên bản hệ điều hành là **64-bit** của Windows XP hoặc mới hơn và Quyền **Administrator** để cài đặt phần mềm.

1. Tải bộ cài MSI tương ứng với hệ điều hành Windows (64-bit):
   - Bộ cài AWS CLI phiên bản mới nhất: https://awscli.amazonaws.com/AWSCLIV2.msi
   - Để tải phiên bản AWS CLI nhất định: Thêm dấu gạch nối và số phiên bản vào tên tập tin. (VD: phiên bản 2.0.30 sẽ là AWSCLIV2-2.0.30.msi và liên kết sẽ là https://awscli.amazonaws.com/AWSCLIV2-2.0.30.msi)
2. Chạy bộ cài MSI vừa tải và thực hiện theo các hướng dẫn trên màn hình. Mặc định, AWS CLI phiên bản 2 cài đặt tại đường dẫn **C:\Program Files\Amazon\AWSCLIV2**.
3. Để kiểm tra lại kết quả cài đặt, dùng lệnh ```aws --version``` trong cửa sổ lệnh Windows (Mở **Start menu**, tìm **cmd** để chạy **Command prompt**).

![Success Windows](../../images/1_SuccessWindows.png?width=60pc)
{{% notice tip %}}
Nếu Windows không thể tìm thấy lệnh khi chạy lệnh, bạn có thể cần phải đóng và mở lại cửa sổ lệnh để làm mới đường dẫn hoặc phải tự tay [thêm thư mục cài đặt vào biến môi trường PATH của hệ điều hành](https://docs.aws.amazon.com/cli/latest/userguide/install-windows.html#awscli-install-windows-path).
{{% /notice %}}

#### Cài đặt AWS CLI trên Ubuntu

Bạn có thể thử cài đặt AWS CLI trên Ubuntu bằng cách khởi tạo một EC2 chạy hệ điều hành Ubuntu.

{{% notice info %}}
AWS CLI v2 sử dụng **glibc**, **groff**, và **less**. AWS hỗ trợ AWS CLI v2 trên phiên bản 64 bit của các Linux distro của CentOS, Fedora, Ubuntu, Linux ARM, Amazon Linux 1 và Amazon Linux 2. Ngoài ra, vì AWS không quản lý các repository của bên thứ ba, AWS không đảm bảo rằng chúng chứa phiên bản AWS CLI mới nhất.
{{% /notice %}}

1. Tải file cài đặt AWS CLI v2:
   - **Sử dụng lệnh curl** – Tùy chọn **-o** chỉ định gói được tải xuống từ URL sẽ được ghi vào tệp tên **awscliv2.zip**.
     - Tải phiên bản hiện tại của AWS CLI, sử dụng lệnh sau:  
        ```bash
        $ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
        ```
     - Tải phiên bản cụ thể của AWS CLI, thêm dấu gạch nối và số phiên bản vào tên tập tin. Phiên bản 2.0.30 sẽ là **awscli-exe-linux-x86_64-2.0.30.zip** và câu lệnh sẽ là:  
        ```bash
        $ curl "https://awscli.amazonaws.com/*awscli-exe-linux-x86_64-2.0.30.zip*" -o "awscliv2.zip"
        ```
2. Tải chương trình giải nén tập tin của Ubunut bằng lệnh
    ```bash
    $ Sudo apt install unzip
    ```
3. Giải nén file **awscliv2.zip**. 
    ```bash 
    $ unzip awscliv2.zip
    ```
3. Chạy bộ cài đặt. Lệnh cài đặt sử dụng tập tin **install** trong thư mục vừa giải nén. Mặc định, chương trình sẽ được cài đặt vào **/usr/local/aws-cli** và được tạo symbolic link trong **/usr/local/bin**. Lệnh cài đặt sẽ cần đến **sudo** nhằm có quyền ghi tập tin vào các thư mục hệ thống.  
    ```bash
    $ sudo ./aws/install
    ```
4. Chắc chắn rằng AWS CLI đã được cài đặt với 
    ```bash
    $ aws --version
    ```
![Success Ubuntu](../../images/1_SuccessUbuntu.png?width=60pc)