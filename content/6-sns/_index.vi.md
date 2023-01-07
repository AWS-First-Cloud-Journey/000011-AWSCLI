---
title : "AWS CLI với Amazon SNS"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### AWS CLI với Amazon SNS

Chúng ta sẽ làm quen với **CLI** qua dịch vụ **SNS**

1. Để tạo một topic SNS, chúng ta làm như sau:

```
aws sns create-topic --name aws-cli
```

![AWS CLI](/images/4-sns/0001.png?featherlight=false&width=10pc)

2. Sau khi đã tạo thành công topic SNS, ta thực hiện subscriber

```
 aws sns subscribe --topic-arn **ARN Topic** --protocol email --notification-endpoint aws@example.com
```

![AWS CLI](/images/4-sns/0002.png?featherlight=false&width=10pc)

3. Kiểm tra mail, chúng ta sử dụng ở lệnh trước. Sau đó, chọn **Confirm subscription**.

![AWS CLI](/images/4-sns/0003.png?featherlight=false&width=10pc)

4. Hoàn thành **subscription**

![AWS CLI](/images/4-sns/0004.png?featherlight=false&width=10pc)

5. Sau khi đã subscriber, chúng ta thử push message để kiểm tra.

```
 aws sns publish --topic-arn **ARN Topic** --message "Hello"
```

![AWS CLI](/images/4-sns/0005.png?featherlight=false&width=10pc)

6. Chúng ta sẽ nhận được tin nhắn qua mail.

![AWS CLI](/images/4-sns/0006.png?featherlight=false&width=10pc)


