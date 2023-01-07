---
title : "Cài đặt AWS CLI"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 3. </b> "
---


#### Cài đặt AWS CLI

- AWS Command Line Interface (AWS CLI) có hai phiên bản. Để đảm bảo tính thực tế của bài lab này, bạn sẽ chỉ thực hành cài đặt AWS CLI v2 cho Windows và Ubuntu vì nó đơn giản, thuận tiện, và đầy đủ hơn AWS CLI v1 rất nhiều.

- AWS CLI phiên bản 1 (AWS CLI v1): là bản AWS CLI nguyên bản đầu tiên và vẫn sẽ được AWS hỗ trợ.
- AWS CLI phiên bản 2 (AWS CLI v2): là bản AWS CLI mới nhất hỗ trợ tất cả các tính năng mới nhất của AWS. Một số tính năng có ở phiên bản 2 không được hỗ trợ tại phiên bản 1 và bạn cần phải nâng cấp phiên bản để sử dụng các tính năng đó.

1. Chúng ta sẽ bát đầu với CLI bằng cách cài đặt như sau:

- Đối với **Linux**:

```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```
- Đối với Windows:

```
msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi
```

- Đối với **MacOs**:

```
sudo ln -s /folder/installed/aws-cli/aws /usr/local/bin/aws
sudo ln -s /folder/installed/aws-cli/aws_completer /usr/local/bin/aws_completer
```

![AWS CLI](/images/1/0001.png?featherlight=false&width=10pc)

2. Kiểm tra đã cài đặt AWS CLI thành công:

```
aws --version
```

![AWS CLI](/images/1/0002.png?featherlight=false&width=10pc)

#### Tạo Default profile

3. Chúng ta sẽ sử dụng lệnh aws configure. Đây được xem là cách nhanh nhất để thiết lập cho AWS CLI. Cửa sổ lệnh sẽ xuất hiện yêu cầu về 4 thông tin như sau:

   - Access key ID
   - Secret access key
   - AWS Region (Vùng)
   - Output format (Định dạng xuất)

```
aws configure
```
```
AWS Access Key ID [None]: *AKIAIOSFODNN7EXAMPLE*
AWS Secret Access Key [None]: *wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY*
Default region name [None]: *ap-southeast-1*
Default output format [None]: *json*
```

![AWS CLI](/images/1/0003.png?featherlight=false&width=10pc)

AWS CLI lưu trữ bộ thông tin này trong profile (tập hợp các cài đặt) có tên default trong tập tin credentials. Theo mặc định, thông tin trong cấu hình này được AWS CLI sử dụng khi bạn chạy lệnh aws configure mà không chỉ định rõ ràng một profile.

#### Tạo profile riêng

4. Thực hiện cấu hình nhiều profile: trong trường hợp này cấu hình thêm một profile devops.

```
aws configure --profile devops
```

![AWS CLI](/images/1/0005.png?featherlight=false&width=10pc)

Access key bao gồm access key ID và secret access key, được sử dụng để ký các yêu cầu ứng dụng mà bạn gửi tới AWS.

5. Kiểm tra đã cấu hình.

![AWS CLI](/images/1/0006.png?featherlight=false&width=10pc)

#### Quản lý nhiều profile

6. Thực hiện kiểm tra credential cũa CLI.

```
cd ~/.aws/
ls
cat config
```

![AWS CLI](/images/1/0007.png?featherlight=false&width=10pc)

7. Ngoài ra chúng ta cũng có thể kiểm tra Region của một profile

```
aws configure get region --profile devops
```

![AWS CLI](/images/1/0008.png?featherlight=false&width=10pc)

8. Danh sách cấu hình:

```
aws configure list
```

![AWS CLI](/images/1/0009.png?featherlight=false&width=10pc)

9. Danh sách các profile:

```
aws configure list-profiles
```

![AWS CLI](/images/1/00010.png?featherlight=false&width=10pc)

{{% notice tip %}}
Bạn có thể thêm hoặc chỉnh sửa profile trực tiếp bằng cách chỉnh sửa hai tập tin **config** và **credentials** bằng trình chỉnh sửa của hệ điều hành của bạn.
{{% /notice %}}