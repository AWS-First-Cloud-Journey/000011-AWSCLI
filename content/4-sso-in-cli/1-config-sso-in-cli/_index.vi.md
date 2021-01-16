+++
title = "Thiết lập SSO cho CLI"
date = 2020
weight = 1
chapter = false
pre = "<b>4.1 </b>"
+++

Bạn có thể cấu hình một hoặc nhiều profile trong AWS CLI của mình sử dụng role từ AWS SSO. Bạn có thể tạo và cấu hình nhiều profile và cấu hình từng profile đó sử dụng AWS SSO user portal khác nhau hoặc role cấp bởi SSO khác nhau.

Bạn có thể định cấu hình cấu hình theo những cách sau:
- **Tự động**, sử dụng lệnh ```aws configure sso```
- **Thủ công**, bằng cách chỉnh sửa ```.aws/config``` chứa thông tin profile.

**Nội dung**
- [1. Cấu hình Tự động](#1-cấu-hình-tự-động)
- [2. Cấu hình Thủ công](#2-cấu-hình-thủ-công)

#### 1. Cấu hình Tự động
Bạn có thể thêm profile sử dụng AWS SSO vào AWS CLI của mình bằng cách chạy lệnh sau, cung cấp **AWS SSO start URL** và **AWS Region** đang chạy danh mục AWS SSO.
```bash
$ aws configure sso
SSO start URL [None]: [None]: https://d-9667182f21.awsapps.com/start
SSO region [None]: ap-southeast-1
```

AWS CLI sẽ mở trình duyệt mặc định của bạn và bắt đầu quá trình đăng nhập tài khoản AWS SSO của bạn.
```bash
SSO authorization page has automatically been opened in your default browser.  
Follow the instructions in the browser to complete this authorization request.
```

*Nếu AWS CLI không thể mở trình duyệt, thông báo sau sẽ xuất hiện với hướng dẫn về cách bắt đầu quy trình đăng nhập theo cách thủ công.*
```bash
Using a browser, open the following URL:  
https://d-9667182f21.awsapps.com/verify  

and enter the following code:  
QCFK-N451  
```
AWS SSO sử dụng mã để liên kết phiên AWS SSO với phiên ở AWS CLI hiện tại của bạn. Trang AWS SSO sẽ yêu cầu bạn đăng nhập bằng thông tin đăng nhập tài khoản AWS SSO của bạn. Việc này cho phép AWS CLI (thông qua các quyền sau khi được liên kết với tài khoản AWS SSO của bạn) truy xuất và hiển thị các tài khoản AWS và role mà bạn được phép sử dụng với AWS SSO.

Tiếp theo, AWS CLI hiển thị các tài khoản AWS có thế sử dụng để bạn chọn. Nếu chỉ được phép sử dụng một tài khoản, AWS CLI sẽ tự động chọn tài khoản đó cho bạn và bỏ qua bước chọn. Các tài khoản AWS có sẵn để bạn sử dụng được xác định bởi cấu hình user của bạn trong AWS SSO. (Trong ví dụ này chúng ta có 4 Tài khoản)
```bash
There are 2 AWS accounts available to you.
> Application One Account, App1@example.com (433335275042) 
  Shared Services, ShareServices@example.com (999068268442)
  Logging Account, Logging@example.com (595678361589)
  Security Account, Security@example.com (156859547066)
```

Sử dụng các phím mũi tên để chọn tài khoản bạn muốn sử dụng với profile này. Ký tự ">" ở bên trái trỏ đến lựa chọn hiện tại. Nhấn <ENTER> để chọn.

Tiếp theo, AWS CLI xác nhận lựa chọn tài khoản của bạn và hiển thị các role IAM có thế sử dụng cho bạn trong tài khoản vừa chọn. Nếu tài khoản đã chọn chỉ có một role, AWS CLI sẽ tự động chọn role đó cho bạn và bỏ qua bước chọn. Các role bạn có thể sử dụng tùy thuộc vào cấu hình user của bạn trong AWS SSO.
```bash
Using the account ID 433335275042
There are 2 roles available to you.
> ReadOnly
  FullAccess
```

Như bước ở trên, sử dụng các phím mũi tên để chọn IAM role mà bạn muốn sử dụng trong profile này. Ký tự ">" ở bên trái trỏ đến lựa chọn hiện tại. Nhấn <ENTER> để chọn.

AWS CLI sẽ xác nhận lựa chọn role của bạn.
```bash
Using the role name "ReadOnly"
```

Bây giờ, bạn có thể hoàn thành cấu hình profile của mình, bằng cách chỉ định định dạng đầu ra mặc định, AWS Region mặc định để gửi lệnh đến và cung cấp tên cho profile để bạn có thể tham chiếu đến profile này. Trong ví dụ sau, người dùng nhập default Region, định dạng đầu ra mặc định và tên của cấu hình.
Ngoài ra, bạn có thể nhấn <ENTER> để chọn bất kỳ giá trị mặc định nào được hiển thị giữa các dấu ngoặc vuông. Tên profile được đề xuất là <ID tài khoản_Role>_.
```bash
CLI default client Region [None]: us-west-2<ENTER>
CLI default output format [None]: json<ENTER>
CLI profile name [433335275042_ReadOnly]: my-test-profile<ENTER>
```

Thông báo cuối cùng mô tả cấu hình profile hoàn thành.

Để sử dụng profile này, ta chỉ định tên profile cho tham số --profile, như bên dưới:
```bash
aws s3 ls --profile my-test-profile
```

Ở các ví dụ trước đó sẽ dẫn đến một profile được thêm vào trong ```~/.aws/config``` có nội dung tương tự nhu sau:
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

#### 2. Cấu hình Thủ công

Để thêm thủ công AWS SSO vào profile, bạn phải thêm các khóa và giá trị sau vào tập tin cấu hình profile ```~/.aws/config``` (Linux or macOS) or ```%USERPROFILE%/.aws/config``` (Windows).

- **sso_start_url**: URL trỏ đến AWS SSO user portal của organization.  
```sso_start_url = https://d-9667182f21.awsapps.com/start```
- **sso_region**: AWS Region đang thiết lập sẵn AWS SSO portal. Giá trị này là riêng biệt và có thể khác với ```region``` (tham số Region khi cấu hình profile cho CLI).
```sso_region = ap-southeast-1```
- **sso_account_id**: AWS account ID chứa các IAM role mà bạn muốn sử dụng với profile này.  
```sso_account_id = 433335275042```
- **sso_role_name**: Tên của IAM role xác định quyền của người dùng khi sử dụng profile này.  
```sso_role_name = ReadAccess```

Các key này dùng để xác định profile này như một profile sử dụng AWS SSO để xác thực người dùng.

Bạn cũng có thể bao gồm bất kỳ khóa và giá trị nào khác hợp lệ trong tập tin ```.aws/config```, như region, outut hay s3. Tuy nhiên, bạn không thể thêm bất kì giá trị định danh nào như **role_arn** hoắc **aws_secret_access_key**. Nếu bạn làm vậy, AWS CLI sẽ xuất hiện lỗi.

Vậy là, một profile AWS SSO điển hình trong ```.aws/config``` có thể là tương tự với ví dụ sau:
```text
[profile my-test-profile]
sso_start_url = https://d-9667182f21.awsapps.com/start
sso_region = ap-southeast-1
sso_account_id = 433335275042
sso_role_name = readOnly
region = us-west-2
output = json
```

Đến đây, giống như ở cấu hình tự động, bạn có một profile mà bạn có thể sử dụng để yêu cầu thông tin đăng nhập tạm thời. Tuy nhiên, bạn chưa thể chạy lệnh dịch vụ AWS CLI. Đầu tiên bạn phải sử dụng lệnh ```aws sso login``` để hoàn thiện yêu cầu và truy xuất thông tin đăng nhập tạm thời cần thiết để chạy lệnh.
Ở phần tiếp theo bạn sẽ biết cách sử dụng profile AWS SSO.