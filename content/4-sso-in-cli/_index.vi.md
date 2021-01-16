+++
title = "AWS SSO trong CLI"
date = 2020
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

#### Cấu hình AWS CLI để sử dụng AWS Single Sign-On
{{% notice warning %}}
- Tính năng sau chỉ xuất hiện nếu bạn sử dụng AWS CLI phiên bản 2. Tính năng này không hỗ trợ ở AWS CLI phiên bản 1.
- Đảm bảo rằng bạn đã thiết lập AWS SSO cho AWS Organization của mình. Nếu chưa hãy xem [Thiết lập AWS SSO]()
{{% /notice %}}

Nếu organization của bạn sử dụng **AWS Single Sign-On (AWS SSO)**, người dùng của bạn có thể đăng nhập vào Active Directory, danh mục tích hợp sẵn tích hợp sẵn trong AWS SSO, hoặc một iDP khác kết nối vào AWS SSO và được áp vào phù hợp với **AWS Identity and Access Management (IAM) role** cho phép bạn chạy các lệnh AWS CLI. Bất kể bạn sử dụng iDP nào, AWS SSO sẽ loại bỏ những điểm khác biệt đó và tất cả chúng đều hoạt động với AWS CLI.

**Nội dung**

1. [Thiết lập Profile sử dụng AWS SSO](./1-config-sso-in-cli/)
2. [Sử dụng Profile đã thiết lập SSO](./2-using-sso-in-cli/)