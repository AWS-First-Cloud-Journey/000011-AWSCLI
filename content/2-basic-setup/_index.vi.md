+++
title = "Thiết Lập AWS CLI Cơ Bản"
date = 2020
weight = 2
chapter = false
pre = "<b>2. </b>"
+++

This section explains how to quickly configure basic settings that the AWS Command Line Interface (AWS CLI) uses to interact with AWS. These include your security credentials, the default output format, and the default AWS Region.

Ở phần này, chúng ta sẽ đi qua việc thiết lập nhanh các cài đặt cơ bản mà AWS Command Line Interface (AWS CLI) sử dụng để tương tác với AWS. Thông tin bao gồm thông tin định danh, Định dạng đầu ra mặc định và Vùng mặc định.

**Nội dung**
- [1. Thiết lập cấu hình cơ bản](#1-thiết-lập-cấu-hình-cơ-bản)
- [2. Access key ID và secret access key](#2-access-key-id-và-secret-access-key)
- [3. Region (Vùng)](#3-region-vùng)
- [4. Output format (Định dạng xuất)](#4-output-format-định-dạng-xuất)

#### 1. Thiết lập cấu hình cơ bản
Chúng ta sẽ sử dụng lệnh ```aws configure```, được xem là cách nhanh nhất để thiết lập cho AWS CLI.
Cửa sổ lệnh sẽ xuất hiện yêu cầu về 4 thông tin như sau:
- Access key ID 
- Secret access key
- AWS Region (Vùng)
- Output format (Định dạng xuất)
Những thông tin này sẽ được làm rõ ở bên dướidưới

AWS CLI lưu trữ thông tin này trong *profile* (tập hợp các cài đặt) có tên **default** trong tập tin **credentials**. Mặc định, thông tin trong cấu hình này được sử dụng khi bạn chạy lệnh ```aws configure``` mà **không** chỉ định rõ ràng một **profile**.
```bash
$ aws configure
AWS Access Key ID [None]: *AKIAIOSFODNN7EXAMPLE*
AWS Secret Access Key [None]: *wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY*
Default region name [None]: *us-west-2*
Default output format [None]: *json*
```

#### 2. Access key ID và secret access key
Access key bao gồm **access key ID** và **secret access key**, được sử dụng để ký các yêu cầu ứng dụng mà bạn gửi tới AWS. Nếu bạn chưa có access keys, bạn có thể tạo chúng từ **AWS Management Console**. Và best practice, **đừng sử dụng** các access key của tài khoản root cho bất kỳ tác vụ nào không cần thiết. Thay vào đó, hãy tạo user IAM Administrator mới với các access key để sử dụng.

Thời điểm **duy nhất** mà bạn có thể xem và tải secret access key là lúc tạo ra nó. Bạn **không thể khôi phục** chúng về sau. Tuy vậy, bạn có thể tạo mới một access key bất kì lúc nào. Bạn cũng buộc phải có quyền để thao tác với IAM.

**Tạo access key cho IAM user**
1. Đăng nhập vào **AWS Management Console** và truy cập vào **IAM console** tại https://console.aws.amazon.com/iam/.
2. Ở thanh điều hướng, chọn **Users**.
3. Chọn tên của user bạn muốn tạo access key, sau đó chọn **Security credentials**.
4. Trong mục **Access keys**, chọn **Create access key**.
5. Để xem access key pair mới, chọn **Show**. Bạn sẽ **không thể** truy cập xem lại secret access key sau khi đóng hộp thoại này. Thông tin định danh của bạn sẽ như ví dụ sau:
    - **Access key ID**: AKIAIOSFODNN7EXAMPLE
    - **Secret access key**: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
6. Để tải xuống key pair, chọn **Download .csv file**. Cất giữ key ở một nơi an toàn. Bạn sẽ **không thể** truy cập xem lại secret access key sau khi đóng hộp thoại này.  
Giữ bí mật các key để bảo vệ tài khoản AWS của bạn và không bao giờ gửi chúng qua email. Không chia sẻ chúng ra bên ngoài doanh nghiệp của bạn, ngay cả khi một câu hỏi dường như đến từ AWS hoặc Amazon.com. Không ai đại diện hợp pháp cho Amazon sẽ yêu cầu bạn cung cấp secret key của bạn.
7. Sau khi bạn tải xuống tập tin .csv, chọn **Close**. Khi bạn tạo access key, cặp key này sẽ được **kích hoạt mặc định** và bạn có thể sử dụng key pair này ngay lập tức.

#### 3. Region (Vùng)
**Default region name** xác định Khu vực AWS có máy chủ mà bạn muốn gửi yêu cầu của mình theo mặc định. Đây thường là Vùng gần bạn nhất, nhưng nó có thể là bất kỳ Vùng nào. Ví dụ: bạn có thể nhập **us-west-2** để sử dụng **US West (Oregon)**. Đây là Vùng mà tất cả các yêu cầu sau này sẽ được gửi đến, trừ khi bạn chỉ định khác trong một lệnh.

{{% notice info %}}
Bạn phải truyền vào Region khi sử dụng lệnh trong AWS CLI, một cách rõ ràng hoặc bằng cách đặt Region mặc định.
{{% /notice %}}

#### 4. Output format (Định dạng xuất)
**Default output format** chỉ định cách các kết quả trả về được định dạng. Loại có thể là bất kỳ giá trị nào trong danh sách bên dưới. Nếu bạn không chỉ định định dạng đầu ra thì **json được sử dụng mặc định**.
- **json** – Đầu ra được định dạng dưới dạng chuỗi JSON.
- **yaml** – Đầu ra được định dạng dưới dạng chuỗi YAML. **(Chỉ hỗ trợ ở AWS CLI phiên bản 2.)**
- **yaml-stream** – Đầu ra là luồng và được định dạng dưới dạng chuỗi YAML. Luồng cho phép xử lý nhanh hơn các loại dữ liệu lớn. **(Chỉ hỗ trợ ở AWS CLI phiên bản 2.)**
- **text** – Đầu ra được định dạng dưới dạng nhiều dòng giá trị chuỗi được phân tách bằng tab. Định dạng này có thể hữu ích để chuyển đầu ra tới trình xử lý văn bản, như grep, sed hoặc awk.
- **table** – Đầu ra được định dạng dưới dạng bảng sử dụng các ký tự +|- để tạo thành các đường viền ô. Nó thường trình bày thông tin ở định dạng "thân thiện với con người", dễ đọc hơn nhiều so với các định dạng khác, nhưng không hữu ích về mặt lập trình.