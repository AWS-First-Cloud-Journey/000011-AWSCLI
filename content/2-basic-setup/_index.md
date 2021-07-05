+++
title = "Thiết Lập AWS CLI Cơ Bản"
date = 2020
weight = 2
chapter = false
pre = "<b>2. </b>"
+++
#### Tổng quan

Ở phần này, chúng ta sẽ đi qua việc thiết lập nhanh các cài đặt cơ bản mà AWS CLI sử dụng để tương tác với AWS. Các thiết lập bao gồm thông tin định danh (*security credentials*), định dạng đầu ra mặc định (*default output format*) và vùng mặc định (*default AWS Region*).

**Nội dung**
1. [Cơ bản về cấu hình](#thiết-lập-cấu-hình-cơ-bản)
2. [Access key ID và secret access key](#access-key-id-và-secret-access-key)
3. [Region (Vùng)](#region-vùng)
4. [Output format (Định dạng xuất)](#output-format-định-dạng-xuất)

#### Cơ bản về cấu hình
Chúng ta sẽ sử dụng lệnh ```aws configure```. Đây được xem là cách nhanh nhất để thiết lập cho AWS CLI.
Cửa sổ lệnh sẽ xuất hiện yêu cầu về 4 thông tin như sau:
- Access key ID 
- Secret access key
- AWS Region (Vùng)
- Output format (Định dạng xuất)

Ví dụ:

```bash
AWS Access Key ID [None]: *AKIAIOSFODNN7EXAMPLE*
AWS Secret Access Key [None]: *wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY*
Default region name [None]: *us-west-2*
Default output format [None]: *json*
```

AWS CLI lưu trữ bộ thông tin này trong *profile* (tập hợp các cài đặt) có tên **default** trong tập tin **credentials**. Theo mặc định, thông tin trong cấu hình này được AWS CLI sử dụng khi bạn chạy lệnh ```aws configure``` mà **không** chỉ định rõ ràng một **profile**.

#### Access key ID và secret access key

```bash
AWS Access Key ID [None]: *AKIAIOSFODNN7EXAMPLE*
AWS Secret Access Key [None]: *wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY*
```

Access key bao gồm **access key ID** và **secret access key**, được sử dụng để ký các yêu cầu ứng dụng mà bạn gửi tới AWS. 

{{% notice note %}}
**Đừng sử dụng** các access key của *root user* cho bất kỳ tác vụ nào không cần thiết. Thay vào đó, hãy tạo user IAM Administrator mới với các access key để sử dụng.
{{% /notice %}}

**Tạo access key cho IAM user**
1. Đăng nhập vào **AWS Management Console** và truy cập vào [IAM console](https://console.aws.amazon.com/iam/)
2. Ở thanh điều hướng, chọn **Users**, sau đó chọn tên của user bạn muốn tạo access key.
![IAMUser](../../images/2_IAMUser.png?width=90pc)
3. Chọn **Security credentials**.
4. Trong mục **Access keys**, chọn **Create access key**.
![IAMUser](../../images/2_CreateAccessKey.png?width=90pc)
5. Để xem access key pair mới, chọn **Show**. Bạn sẽ **không thể** truy cập xem lại secret access key sau khi đóng hộp thoại này.
{{% notice note %}}
Thời điểm **duy nhất** mà bạn có thể xem và tải secret access key là lúc tạo ra nó. Bạn **không thể khôi phục** chúng về sau. Tuy vậy, bạn có thể tạo mới một access key bất kì lúc nào. Bạn cũng buộc phải có quyền để thao tác với IAM.
{{% /notice %}}
6. Để tải xuống key pair, chọn **Download .csv file**. Cất giữ key ở một nơi an toàn. Bạn sẽ **không thể** truy cập xem lại secret access key sau khi đóng hộp thoại này.  
{{% notice warning %}}
Giữ bí mật các key để bảo vệ tài khoản AWS của bạn và không bao giờ gửi chúng qua email. Không chia sẻ chúng ra bên ngoài doanh nghiệp của bạn, ngay cả khi gặp một câu hỏi dường như đến từ AWS hoặc Amazon.com. Không ai đại diện hợp pháp cho Amazon sẽ yêu cầu bạn cung cấp key của bạn.
{{% /notice %}}
7. Sau khi bạn tải xuống tập tin .csv, chọn **Close**. Khi bạn tạo access key, cặp key này sẽ được **kích hoạt mặc định** và bạn có thể sử dụng key pair này ngay lập tức.

#### Region (Vùng)

```bash
Default region name [None]: *us-west-2*
```

**Default region name** xác định Khu vực AWS có máy chủ mà bạn muốn gửi yêu cầu của mình theo mặc định. Đây thường là Region gần bạn nhất, nhưng nó có thể là bất kỳ Region nào. Ví dụ: bạn có thể nhập **us-west-2** để sử dụng **US West (Oregon)**. Đây là Region mặc định mà tất cả các yêu cầu sau này sẽ được gửi đến, trừ khi bạn chỉ định khác.

{{% notice info %}}
Bạn phải truyền vào Region khi sử dụng lệnh trong AWS CLI một cách rõ ràng hoặc bằng cách thiết lập trước một Region mặc định.
{{% /notice %}}

#### Output format (Định dạng xuất)

```bash
Default output format [None]: *json*
```

**Default output format** chỉ định cách các kết quả trả về được định dạng. Loại có thể là bất kỳ giá trị nào trong danh sách bên dưới. Nếu bạn không chỉ định định dạng đầu ra thì **json được sử dụng mặc định**.
- **json** – Đầu ra được định dạng dưới dạng chuỗi JSON.
- **yaml** – Đầu ra được định dạng dưới dạng chuỗi YAML. **(Chỉ hỗ trợ ở AWS CLI v2.)**
- **yaml-stream** – Đầu ra là luồng và được định dạng dưới dạng chuỗi YAML. Luồng cho phép xử lý nhanh hơn các loại dữ liệu lớn. **(Chỉ hỗ trợ ở AWS CLI phiên bản 2.)**
- **text** – Đầu ra được định dạng dưới dạng nhiều dòng giá trị chuỗi được phân tách bằng tab. Định dạng này có thể hữu ích để chuyển đầu ra tới trình xử lý văn bản, như grep, sed hoặc awk.
- **table** – Đầu ra được định dạng dưới dạng bảng sử dụng các ký tự +|- để tạo thành các đường viền ô. Nó thường trình bày thông tin ở định dạng "thân thiện với con người", dễ đọc hơn nhiều so với các định dạng khác, nhưng không hiệu quả về mặt lập trình.