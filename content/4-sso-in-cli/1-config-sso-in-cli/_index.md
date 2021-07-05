+++
title = "Thiết lập SSO cho CLI"
date = 2020
weight = 1
chapter = false
pre = "<b>4.1 </b>"
+++

{{% notice note %}}
Trước khi làm phần thực hành này, bạn cần phải hoàn thành xong bài [Thiết lập AWS SSO](https://000012.awsstudygroup.com/vi/) để hiểu hơn về AWS SSO.
{{% /notice %}}

#### Tổng quan

Bạn có thể cấu hình một hoặc nhiều profile trong AWS CLI của mình để sử dụng role từ AWS SSO. Bạn cũng có thể tạo và thiết lập từng profile một để sử dụng AWS SSO user portal khác nhau hoặc role SSO khác nhau.

Bạn có thể định cấu hình cấu hình theo những cách sau:
- **Tự động**, sử dụng lệnh ```aws configure sso```
- **Thủ công**, bằng cách chỉnh sửa ```.aws/config``` chứa thông tin profile.

**Nội dung**
1. [Cấu hình Tự động](#cấu-hình-tự-động)
2. [Cấu hình Thủ công](#cấu-hình-thủ-công)

#### Cấu hình Tự động
1. Truy cập vào máy tính sử dụng AWS CLI của bạn và mở terminal
2. Bạn có thể thêm profile sử dụng AWS SSO vào AWS CLI của mình bằng cách chạy lệnh sau, cung cấp **AWS SSO start URL** và **AWS Region** đang chạy danh mục AWS SSO.
    ```bash
    $ aws configure sso
    SSO start URL [None]: https://d-9667182f21.awsapps.com/start
    SSO region [None]: ap-southeast-1
    ```
3. AWS CLI sẽ mở trình duyệt mặc định của bạn và bắt đầu quá trình đăng nhập tài khoản AWS SSO của bạn. Nếu AWS CLI không thể mở trình duyệt, thông báo hướng dẫn về cách bắt đầu quy trình đăng nhập thủ công sẽ xuất hiện như sau.
    ```bash
    Using a browser, open the following URL:  
    https://d-9667182f21.awsapps.com/verify  

    and enter the following code: 

    QCFK-N451  
    ```
4. AWS SSO sử dụng mã để liên kết phiên AWS SSO với phiên ở AWS CLI hiện tại của bạn. Trang AWS SSO sẽ yêu cầu bạn đăng nhập bằng AWS SSO User của bạn (Ví dụ: Super-User ở bài [Thiết lập AWS SSO](https://000012.awsstudygroup.com/vi/)). Việc này cho phép AWS CLI truy xuất và hiển thị các tài khoản AWS và role mà bạn được phép sử dụng với AWS SSO.
    ![4.1_LoginSuccess](../../../images/4.1_LoginSuccess.png?width=90pc)
5. Tiếp theo, AWS CLI hiển thị các tài khoản AWS có thế sử dụng để bạn chọn. Nếu chỉ được phép sử dụng một tài khoản, AWS CLI sẽ tự động chọn tài khoản đó cho bạn và bỏ qua bước chọn. Các tài khoản AWS có sẵn để bạn sử dụng được xác định bởi cấu hình của AWS SSO User. (Trong ví dụ này chúng ta có 4 Tài khoản có từ bài [Thiết lập AWS SSO](https://000012.awsstudygroup.com/vi/))
    ```bash
    There are 4 AWS accounts available to you.
    > Application One Account, App1@example.com (433335275042) 
      Shared Services, ShareServices@example.com (999068268442)
      Logging Account, Logging@example.com (595678361589)
      Security Account, Security@example.com (156859547066)
    ```

6. Sử dụng các phím mũi tên để chọn tài khoản bạn muốn sử dụng với profile này. Ký tự **">"** ở bên trái trỏ đến lựa chọn hiện tại. Nhấn **ENTER** để chọn.

7. Tiếp theo, AWS CLI xác nhận lựa chọn tài khoản của bạn và hiển thị các role IAM có thế sử dụng trong tài khoản vừa chọn. Nếu tài khoản đã chọn chỉ có một role, AWS CLI sẽ tự động chọn role đó cho bạn và bỏ qua bước chọn. Các role bạn có thể sử dụng tùy thuộc vào cấu hình user của bạn trong AWS SSO. (Trong ví dụ này chúng ta có 2 role để lựa chọn).
    ```bash
    Using the account ID 433335275042
    There are 2 roles available to you.
    > ReadOnly
      FullAccess
    ```

8. Như bước ở trên, sử dụng các phím mũi tên để chọn IAM role mà bạn muốn sử dụng trong profile này. Ký tự **">"** ở bên trái trỏ đến lựa chọn hiện tại. Nhấn **ENTER** để chọn.

9. AWS CLI sẽ xác nhận lựa chọn role của bạn.
    ```bash
    Using the role name "ReadOnly"
    ```

10. Bây giờ, bạn có thể hoàn thành thiết lập profile của mình bằng cách chỉ định Output Format, Region, và tên profile để bạn có thể tham chiếu đến profile này. Ngoài ra, bạn có thể nhấn **ENTER** để chọn bất kỳ giá trị mặc định nào được hiển thị giữa các dấu ngoặc vuông.
    ```bash
    CLI default client Region [None]: us-west-2
    CLI default output format [None]: json
    CLI profile name [433335275042_ReadOnly]: my-test-profile
    ```

11. Để kiểm tra profile này, ta chỉ định tên profile cho tham số ```--profile```, như bên dưới:
    ```bash
    aws s3 ls --profile my-test-profile
    ```

12. Profile vừa được tạo sẽ được thêm vào trong ```~/.aws/config``` có nội dung tương tự nhu sau:
    ```text
    [profile my-test-profile]
    sso_start_url = https://d-9667182f21.awsapps.com/start
    sso_region = ap-southeast-1
    sso_account_id = 433335275042
    sso_role_name = readOnly
    region = us-west-2
    output = json
    ```

Đến đây, bạn đã có profile mà bạn có thể sử dụng để yêu cầu thông tin xác thực tạm thời. Bạn phải sử dụng lệnh ```aws sso login``` để thực sự yêu cầu và truy xuất thông tin đăng nhập tạm thời cần thiết trước khi chạy lệnh.

#### Cấu hình Thủ công

1. Để thêm thủ công AWS SSO vào profile, bạn phải thêm các cặp khóa và giá trị (*Key-Value*) sau vào tập tin cấu hình profile ```~/.aws/config``` (Linux or macOS) or ```%USERPROFILE%/.aws/config``` (Windows).
    - **sso_start_url**: URL trỏ đến AWS SSO user portal của organization. Ví dụ: 
    ```sso_start_url = https://d-9667182f21.awsapps.com/start```
    - **sso_region**: AWS Region đang thiết lập sẵn AWS SSO portal. Giá trị này là riêng biệt và có thể khác với tham số Region khi cấu hình profile cho CLI. Ví dụ:
    ```sso_region = ap-southeast-1```
    - **sso_account_id**: AWS account ID chứa các IAM role mà bạn muốn sử dụng với profile này. Ví dụ:
    ```sso_account_id = 433335275042```
    - **sso_role_name**: Tên của IAM role xác định quyền của người dùng khi sử dụng profile này. Ví dụ:
    ```sso_role_name = ReadAccess```
{{% notice note %}}
Các key trên dùng để xác định rằng profile này là một profile sử dụng AWS SSO để xác thực người dùng.
{{% /notice %}}

2. Bạn cũng có thể bao gồm bất kỳ cặp khóa và giá trị (*Key-Value*) nào khác hợp lệ trong tập tin ```.aws/config```, như region và output. Tuy nhiên, bạn không thể thêm bất kì giá trị định danh nào như **role_arn** hoắc **aws_secret_access_key**. Nếu bạn làm vậy, AWS CLI sẽ xuất hiện lỗi.

3. Vậy là, một profile AWS SSO điển hình trong ```.aws/config``` có thể là tương tự với ví dụ sau:
    ```text
    [profile my-test-profile]
    sso_start_url = https://d-9667182f21.awsapps.com/start
    sso_region = ap-southeast-1
    sso_account_id = 433335275042
    sso_role_name = readOnly
    region = us-west-2
    output = json
    ```

Đến đây, giống như ở phần [Cấu hình Tự động](#cấu-hình-tự-động), bạn có một profile mà bạn có thể sử dụng để yêu cầu thông tin đăng nhập tạm thời. Tuy nhiên, bạn chưa thể chạy lệnh dịch vụ AWS CLI. Đầu tiên bạn phải sử dụng lệnh ```aws sso login``` để hoàn thiện yêu cầu và truy xuất thông tin đăng nhập tạm thời cần thiết để chạy lệnh.
Ở phần tiếp theo bạn sẽ biết cách sử dụng profile AWS SSO.