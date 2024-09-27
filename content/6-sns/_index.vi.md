---

title : "AWS CLI với Amazon SNS"  
date : "`r Sys.Date()`"  
weight : 6  
chapter : false  
pre : " <b> 6. </b> "

---

#### AWS CLI với Amazon SNS

Chúng ta sẽ làm quen với **CLI** qua dịch vụ **SNS**.  

#### Mục lục  
<!-- TOC created automatically using Markdown All in One -->
<!-- 
Ctrl + Shift + P -> Create Table of Contents 
-->

- [AWS CLI với Amazon SNS](#aws-cli-với-amazon-sns)
- [Mục lục](#mục-lục)
- [Tạo một topic SNS](#tạo-một-topic-sns)
- [Thực hiện đăng ký subscriber](#thực-hiện-đăng-ký-subscriber)
- [Xác nhận đăng ký](#xác-nhận-đăng-ký)
- [Hoàn thành đăng ký](#hoàn-thành-đăng-ký)
- [Push một tin nhắn để kiểm tra](#push-một-tin-nhắn-để-kiểm-tra)
- [Nhận tin nhắn qua email](#nhận-tin-nhắn-qua-email)

---

#### Tạo một topic SNS

Để tạo một topic SNS, chúng ta làm như sau:

```bash
aws sns create-topic --name aws-cli
```

{{% notice info %}} Đây là lệnh để tạo một topic SNS với tên là `aws-cli`. {{% /notice %}}

![AWS CLI](/images/4-sns/0001.png?featherlight=false&width=90pc)

#### Thực hiện đăng ký subscriber

Sau khi đã tạo thành công topic SNS, ta thực hiện đăng ký subscriber bằng lệnh sau:

```bash
aws sns subscribe --topic-arn **ARN Topic** --protocol email --notification-endpoint aws@example.com
```

{{% notice tip %}} Đừng quên thay thế **ARN Topic** bằng ARN của topic bạn đã tạo ở bước trước. {{% /notice %}}

![AWS CLI](/images/4-sns/0002.png?featherlight=false&width=90pc)

#### Xác nhận đăng ký

Kiểm tra email mà bạn đã sử dụng trong lệnh trước. Sau đó, chọn **Confirm subscription** trong email để hoàn tất đăng ký.

![AWS CLI](/images/4-sns/0003.png?featherlight=false&width=90pc)

#### Hoàn thành đăng ký

Khi bạn đã xác nhận đăng ký, trạng thái **subscription** sẽ hoàn tất.

![AWS CLI](/images/4-sns/0004.png?featherlight=false&width=90pc)

#### Push một tin nhắn để kiểm tra

Sau khi đăng ký thành công, chúng ta sẽ thử push một tin nhắn để kiểm tra:

```bash
aws sns publish --topic-arn **ARN Topic** --message "Hello"
```

{{% notice warning %}} Lệnh này gửi một tin nhắn có nội dung `"Hello"` đến tất cả các subscriber đã đăng ký. {{% /notice %}}

![AWS CLI](/images/4-sns/0005.png?featherlight=false&width=90pc)

#### Nhận tin nhắn qua email

Nếu mọi thứ hoạt động đúng, bạn sẽ nhận được tin nhắn đã gửi qua email.

![AWS CLI](/images/4-sns/0006.png?featherlight=false&width=90pc)

