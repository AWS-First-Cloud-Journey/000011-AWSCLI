+++
title = "Dùng AWS SSO trong CLI"
date = 2020
weight = 2
chapter = false
pre = "<b>4.2 </b>"
+++
  
Phần này mô tả cách sử dụng profile AWS SSO mà bạn đã tạo trong phần trước.

**Nội dung**
- [1. Đăng nhập và lấy danh tính tạm thời](#1-đăng-nhập-và-lấy-danh-tính-tạm-thời)
- [2. Sử dụng lệnh với profile được thiết lập AWS SSO](#2-sử-dụng-lệnh-với-profile-được-thiết-lập-aws-sso)
- [3. Đăng xuất khỏi phiên AWS SSO](#3-đăng-xuất-khỏi-phiên-aws-sso)

#### 1. Đăng nhập và lấy danh tính tạm thời
Sau khi bạn cấu hình profile tự động hoặc thủ công, bạn có thể sử dụng profile đó để yêu cầu thông tin xác thực tạm thời từ AWS. Trước khi có thể chạy lệnh thao tác với dịch vụ bằng AWS CLI, bạn phải truy xuất và lưu vào bộ nhớ cache một bộ thông tin xác thực tạm thời. Để có các thông tin xác thực tạm thời này, hãy chạy lệnh sau.
```bash
$ aws sso login --profile my-test-profile
```

AWS CLI sẽ mở trình duyệt mặc định của bạn và xác minh thông tin đăng nhập AWS SSO của bạn.
```bash
SSO authorization page has automatically been opened in your default browser. 
Follow the instructions in the browser to complete this authorization request.
Successully logged into Start URL: https://d-9667182f21.awsapps.com/start
```

Nếu bạn hiện chưa đăng nhập vào tài khoản AWS SSO của mình, bạn phải cung cấp username và password AWS SSO của mình.

*Nếu AWS CLI không thể mở trình duyệt, thông báo sau sẽ xuất hiện với hướng dẫn về cách bắt đầu quy trình đăng nhập theo cách thủ công.*
```bash
$ aws sso login --profile my-test-profile
Using a browser, open the following URL:
 
https://d-9667182f21.awsapps.com/verify

and enter the following code:
QCFK-N451
```

AWS CLI sẽ mở trình duyệt mặc định của bạn (hoặc bạn sẽ mở thủ công) và truy cập đến trang yêu cầu và nhập mã xác thực được cung cấp. Trang web hỏi bạn về tài khoản AWS SSO.

Phiên đăng nhập SSO của bạn lúc này đã được cache và sẽ có thời gian vô hiệu. Khi bị vô hiệu, AWS CLI sẽ yêu cầu bạn đăng nhập trở lại vào AWS SSO.

Nếu thông tin đăng nhập SSO chính xác, AWS CLI sẽ sử dụng chúng để truy xuất thông tin đăng nhập tạm thời nhằm sử dụng IAM role được chỉ định trong profile.
```bash
Welcome, you have successfully signed-in to the AWS-CLI.
```

#### 2. Sử dụng lệnh với profile được thiết lập AWS SSO
Bạn có thể sử dụng các thông tin đăng nhập tạm thời này để gọi lệnh AWS CLI với profile được thiết lập. Ví dụ sau cho thấy rằng lệnh được chạy thông qua role đã được assume từ tài khoản được chỉ định.
```bash
$ aws sts get-caller-identity --profile my-test-profile
{
    "UserId": "AROA12345678901234567:App1@example.com",
    "Account": "433335275042",
    "Arn": "arn:aws:sts::433335275042:assumed-role/AWSPeregrine_readOnly_12321abc454d123/App1@example.com"
}
```

Trong thời gian bạn đã đăng nhập vào AWS SSO và các thông tin đăng nhập được lưu trong bộ nhớ cache sẽ chưa hết hạn, AWS CLI sẽ tự động gia hạn thông tin đăng nhập tạm thời này khi cần. Tuy nhiên, nếu thông tin đăng nhập AWS SSO của bạn hết hạn (thoát phiên, đổi mật khẩu hoặc quá thời gian giữ kết nối), bạn phải làm mới chúng bằng cách đăng nhập lại vào tài khoản AWS SSO của mình.
```bash
$ aws s3 ls --profile my-sso-profile
Your short-term credentials have expired. Please sign-in to renew your credentials
SSO authorization page has automatically been opened in your default browser. 
Follow the instructions in the browser to complete this authorization request.
```

You can create multiple AWS SSO enabled named profiles that each point to a different AWS account or role. You can also use the aws sso login command on more than one profile at a time. If any of them share the same AWS SSO user account, you must log in to that AWS SSO user account only once and then they all share a single set of AWS SSO cached credentials.
Bạn có thể tạo nhiều profile sử dụng AWS SSO với mỗi profile sử dụng tài khoản hoặc role khác nhau. Bạn cũng có thể sử dụng lệnh ```aws sso login``` trên nhiều profile cùng một lúc. Nếu bất kỳ profile trong số chúng có cùng một tài khoản người dùng AWS SSO, bạn phải đăng nhập vào tài khoản người dùng AWS SSO đó một lần và sau đó tất cả profile đều chia sẻ một thông tin đăng nhập AWS SSO được lưu trong bộ nhớ cache.
```text
# The following command retrieves temporary credentials for the AWS account and role 
# specified in one named profile. If you are not yet signed in to AWS SSO or your 
# cached credentials have expired, it opens your browser and prompts you for your 
# AWS SSO user name and password. It then retrieves AWS temporary credentials for
# the IAM role associated with this profile.
$ aws sso login --profile my-first-sso-profile

# The next command retrieves a different set of temporary credentials for the AWS 
# account and role specified in the second named profile. It does not overwrite or 
# in any way compromise the first profile's credentials. If this profile specifies the
# same AWS SSO portal, then it uses the SSO credentials that you retrieved in the 
# previoius command. The AWS CLI then retrieves AWS temporary credentials for the
# IAM role associated with the second profile. You don't have to sign in to 
# AWS SSO again.
$ aws sso login --profile my-second-sso-profile

# The following command lists the Amazon EC2 instances accessible to the role 
# identified in the first profile.
$ aws ec2 describe-instances --profile my-first-sso-profile

# The following command lists the Amazon EC2 instances accessible to the role 
# identified in the second profile.
$ aws ec2 describe-instances --profile my-second-sso-profile
```

#### 3. Đăng xuất khỏi phiên AWS SSO
Khi bạn hoàn tất làm việc với các profile thiết lập SSO, bạn có thể chọn không làm gì cả và để thông tin đăng nhập tạm thời vào AWS và thông tin đăng nhập AWS SSO tự hết hạn. Tuy nhiên, bạn cũng có thể chọn chạy lệnh sau để xóa ngay lập tức tất cả thông tin đăng nhập đã lưu trong thư mục cache và tất cả thông tin đăng nhập tạm thời vào AWS dựa trên AWS SSO. Việc này sẽ vô hiệu hóa những thông tin đăng nhập đó, làm chúng không thể dùng cho bất kỳ lệnh nào sau đó.
```bash
$ aws sso logout
Successfully signed out of all SSO profiles.
```
