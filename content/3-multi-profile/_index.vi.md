+++
title = "Thiết lập Multi-profile"
date = 2020
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

#### Tổng quan

Ở phần này, bạn sẽ tìm hiểu về khái niệm profile trong AWS CLI và làm các bài tập thực hành như tạo **default profile**, tạo **profile riêng**, cập nhật profile, và quản lý nhiều profile (*multi-profile management*)

#### Profile
- **Profile** là tập các thiết lập và định danh cho phép bạn sử dụng các lệnh có trong AWS CLI. Mặc định, AWS CLI sử dụng **default profile**. Ngoài ra, bạn còn có thể tạo thêm nhiều profile khác gọi là **profile riêng** với thông số ```--profile```.
- AWS CLI lưu trữ thông tin của các profile trong tập tin **config** và **credentials**. Ngoài việc tạo thêm profile với thông số ```--profile```, bạn có thể tạo thêm các profile khác bằng cách thêm các thiết lập trực tiếp vào các tập tin **config** và **credentials**.
- Với thông số ```--profile```, bạn có thể chỉ định một profile cụ thể để nó thực hiện những câu lệnh trong AWS CLI. Ngoài ra, bạn cũng có thể chỉ định một profile trong biến môi trường (AWS_PROFILE) để thay thế default profile ở một session nào dó.

**Nội dung**
1. [Tạo Default Profile](#tạo-default-profile)
2. [Tạo profile riêng](#tạo-profile-riêng)
3. [Cập nhật profile](#cập-nhật-profile)
4. [Quản lý nhiều profile (*multi-profile management*)](#quản-lý-nhiều-profile-multi-profile-management)

#### Tạo Default Profile
1. Truy cập vào máy tính mà bạn đã cài đặt AWS CLI và khởi chạy Terminal
    - **Linux shells** cho các máy sử dụng Linux hoặc MacOS
    - **Windows Command Line** cho các máy sử dụng Windows
2. Nhập dòng lệnh sau để khởi tạo **default profile**:
    ```bash
    $ aws configure
    ```
3. Lần lượt nhập những thông tin về Access Key, Region, và Output Format mà bạn muốn *(Lưu ý: bạn nên sử dụng Access Key mà bạn đã tạo)*. Sau đây là ví dụ:
    ```bash
    AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
    AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
    Default region name [None]: us-west-2
    Default output format [None]: json
    ```
4. Như vậy, default profile của bạn đã được tạo thành công

#### Tạo profile riêng
1. Truy cập vào máy tính mà bạn đã cài đặt AWS CLI và khởi chạy Terminal
    - **Linux shells** cho các máy sử dụng Linux hoặc MacOS
    - **Windows Command Line** cho các máy sử dụng Windows
2. Để khởi tạo **profile riêng** có tên là **testuser**, bạn cần thêm thông số ```--profile```:
    ```bash
    $ aws configure --profile testuser
    ```
3. Lần lượt nhập những thông tin về Access Key, Region, và Output Format mà bạn muốn *(Lưu ý: bạn nên sử dụng Access Key mà bạn đã tạo)*. Sau đây là ví dụ:
    ```bash
    AWS Access Key ID [None]: AKIAI44QH8DHBEXAMPLE
    AWS Secret Access Key [None]: je7MtGbClwBF/2Zp9Utk/h3yCo8nvbEXAMPLEKEY
    Default region name [None]: us-east-1
    Default output format [None]: text
    ```
4. Như vậy, profile riêng có tên là **testuser** của bạn đã được tạo thành công

#### Cập nhật profile
1. Truy cập vào máy tính mà bạn đã cài đặt AWS CLI và khởi chạy Terminal
    - **Linux shells** cho các máy sử dụng Linux hoặc MacOS
    - **Windows Command Line** cho các máy sử dụng Windows
2. Nhập dòng lệnh sau để cập nhật profile:
    ```bash
    $ aws configure #nếu bạn muốn cập nhật default profile
    $ aws configure --profile testuser #nếu bạn muốn cập nhật profile riêng có tên là testuser. Bạn có thể thay thế tên testuser với một profile khác
    ```
3. Lần lượt nhập những thông tin về Access Key, Region, và Output Format mà bạn muốn cập nhật. Sau đây là ví dụ:
    ```bash
    AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
    AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
    Default region name [None]: ap-southeast-1
    Default output format [None]: yaml
    ```
4. Như vậy, bạn đã cập nhật profile thành công.

#### Quản lý nhiều profile (*multi-profile management*)

Ở bước này, bạn sẽ truy cập vào hai tập tin **config** và **credentials** để xem thông tin lưu trữ của các profile vừa được tạo. 

Địa chỉ của hai tập tin trên sẽ được tìm thấy ở đường dẫn:

|      HĐH         |              Địa chỉ            |
|:---------------:|:--------------------------------:|
| Linux và MacOS    |```~/.aws/config``` và ```~/.aws/credentials```|
|  Windows  | ```%USERPROFILE%\.aws\config``` và ```%USERPROFILE%\.aws\credentials```      |

1. Truy cập vào máy tính mà bạn đã cài đặt AWS CLI và khởi chạy Terminal
    - **Linux shells** cho các máy sử dụng Linux hoặc MacOS
    - **Windows Command Line** cho các máy sử dụng Windows
2. Đi tới thư mục chứa hai tập tin **config** và **credentials** bằng câu lệnh sau:
    - **Linux và MacOS**
      ```bash
      $ cd ~/.aws/
      ```
    - **Windows**
      ```bash
      $ cd %USERPROFILE%\.aws\
      ```
3. Xem nội dung của hai tập tin **config** và **credentials** bằng lệnh:
    - **Linux và MacOS**
      ```bash
      $ cat config
      $ cat credentials
      ```
    - **Windows**
      ```bash
      $ more config
      $ more credentials  
      ```
4. Màn hình của bạn sẽ hiện ra kết quả tương tự như hình sau:
    - **Linux và MacOS**
        ![3_Linux](../../images/3_Linux.png?width=90pc)
    - **Windows**
        ![3_Windows](../../images/3_Windows.png?width=90pc)

{{% notice info %}}
Bạn có thể thêm hoặc chỉnh sửa profile trực tiếp bằng cách chỉnh sửa hai tập tin **config** và **credentials** bằng trình chỉnh sửa của hệ điều hành của bạn.
{{% /notice %}}
