+++
title = "AWS SSO trong CLI"
date = 2020
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

#### Thiết lập AWS CLI để sử dụng AWS Single Sign-On
{{% notice warning %}}
Tính năng này chỉ xuất hiện nếu bạn sử dụng AWS CLI v2. Hãy đảm bảo rằng bạn đã thiết lập AWS SSO cho AWS Organization của mình. Nếu chưa hãy xem [Thiết lập AWS SSO](https://000012.awsstudygroup.com/vi/)
{{% /notice %}}

Nếu organization của bạn sử dụng **AWS Single Sign-On (AWS SSO)**, người dùng của bạn có thể đăng nhập vào tài khoản AWS thuộc AWS SSO và chạy các lệnh AWS CLI thông qua *Active Directory* (danh mục tích hợp sẵn tích hợp sẵn trong AWS SSO) hoặc một *Identity Provider* (nhà cung cấp nhận dạng) khác đã được thiết lập phù hợp. Bất kể bạn sử dụng nhà cung cấp nhận dạng nào, AWS SSO sẽ loại bỏ những điểm khác biệt đó và hỗ trợ hoạt động với AWS CLI một cách bình thường.

**Nội dung**

1. [Thiết lập Profile sử dụng AWS SSO](./1-config-sso-in-cli/)
2. [Sử dụng Profile đã thiết lập SSO](./2-using-sso-in-cli/)