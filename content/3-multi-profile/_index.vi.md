+++
title = "Thiết lập Multi-profile"
date = 2020
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

**Nội dung**
- [1. Profile](#1-profile)
- [2. Multiple Profiles](#2-multiple-profiles)
  - [Tạo một Named Profile](#tạo-một-named-profile)
  - [Quản lý thiết lập với Multiple Profile](#quản-lý-thiết-lập-với-multiple-profile)

### 1. Profile
Tập hợp các cài đặt được gọi là profile. Mặc định, AWS CLI sử dụng profile **default**. Bạn có thể tạo và sử dụng thêm các profile với tên khác chứa thông tin định danh khác nhau và các thiết lập khác nhau bằng thông số --profile và gán tên.
Bạn có thể lưu các thiết lập cấu hình thường dùng và thông tin định danh vào tập tin quản lý bởi AWS CLI.

Ví dụ sau sẽ là cấu hình profile **default**.
```bash
$ aws configure
AWS Access Key ID [None]: *AKIAIOSFODNN7EXAMPLE*
AWS Secret Access Key [None]: *wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY*
Default region name [None]: *us-west-2*
Default output format [None]: *json*
```

### 2. Multiple Profiles
AWS CLI hỗ trợ sử dụng bất kỳ các profile riêng nào được lưu trữ trong tập tin **config** và **credentials**. Bạn có thể tạo và sử dụng thêm các profile với tên khác chứa thông tin định danh khác nhau và các thiết lập khác nhau bằng thông số --profile và gán tên hoặc thêm các thiết lập trực tiếp vào tập tin credentials.

Tập tin chia thành các profile. Profile riêng là tập các thiết lập và định danh mà bạn có thể sử dụng trong các lệnh ở AWS CLI. Khi bạn chỉ định một profile để chạy một lệnh, thiết lập và thông tin định danh được lưu trữ sẽ được sử dụng để chạy lệnh. Bạn có chỉ định một profile được gọi là "default" và được sử dụng khi không có profile nào được chỉ định trực tiếp trong lệnh. Các profile riêng khác bạn có thể chỉ định trong các tham số của từng lệnh riêng biệt. Thay vào đó, bạn có thể chỉ định ra một profile trong biến môi trường (AWS_PROFILE) thay thế default profile chạy lệnh ở session dó.

The files are divided into profiles. A named profile is a collection of settings and credentials that you can apply to a AWS CLI command. When you specify a profile to run a command, the settings and credentials are used to run that command. You can specify one profile that is the "default", and is used when no profile is explicitly referenced. Other profiles have names that you can specify as a parameter on the command line for individual commands. Alternatively, you can specify a profile in an environment variable (AWS_PROFILE) which essentially overrides the default profile for commands that run in that session.

#### Tạo một Named Profile
Ví dụ sau tạo một profile có tên **testuser**.
```bash
$ aws configure --profile testuser
AWS Access Key ID [None]: AKIAI44QH8DHBEXAMPLE
AWS Secret Access Key [None]: je7MtGbClwBF/2Zp9Utk/h3yCo8nvbEXAMPLEKEY
Default region name [None]: us-east-1
Default output format [None]: text
```

Bạn có thể sử dụng tham số ```--profile <ProfileName>``` và sử dụng các định danh và thiết lập ở profile đó cho các lệnh.
```bash
aws s3 ls --profile produser
```

Để cập nhật các thiết lập này, chạy ```aws configure``` một lần nữa (có hoặc không có tham số ```--profile *profilename*```, tùy vào profile bạn muốn cập nhật) và nhập vào các giá trị mới phù hợp . Ở mục tiếp theo sẽ đi sâu hơn về tập tin mà khi chạy lệnh ```aws configure``` sẽ được tạo ra, các thông tin bổ sung và named profile.

#### Quản lý thiết lập với Multiple Profile 
The following example shows a credentials file with two profiles. The first [default] is used when you run a CLI command with no profile. The second is used when you run a CLI command with the --profile user1 parameter. 

Ví dụ sau cho thấy một tập tin credentials với hai profile. Đầu tiên là profile [default] được sử dụng khi bạn chạy lệnh CLI không truyền profile cụ thể. Lệnh thứ hai được sử dụng khi bạn chạy lệnh CLI với tham số --profile user1.  
```~/.aws/credentials``` (Linux & Mac) hoặc ```%USERPROFILE%\.aws\credentials``` (Windows).

```
[default]
aws_access_key_id=AKIAIOSFODNN7EXAMPLE
aws_secret_access_key=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY

[testuser]
aws_access_key_id=AKIAI44QH8DHBEXAMPLE
aws_secret_access_key=je7MtGbClwBF/2Zp9Utk/h3yCo8nvbEXAMPLEKEY
```

Each profile can specify different credentials—perhaps from different IAM users—and can also specify different AWS Regions and output formats.
Mỗi hồ sơ có thể chỉ định các thông tin xác thực khác nhau — từ những người dùng IAM khác nhau — và cũng có thể chỉ định các AWS Region và định dạng đầu ra khác nhau.
```~/.aws/config``` (Linux & Mac) hoặc ```%USERPROFILE%\.aws\config``` (Windows).
```
[default]
region=us-west-2
output=json

[profile testuser]
region=us-east-1
output=text
```