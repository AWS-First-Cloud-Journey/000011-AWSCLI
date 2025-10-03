---
title : "AWS CLI with Amazon SNS"
date : 2025-10-02
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### AWS CLI with Amazon SNS

We will get acquainted with **CLI** via **SNS** service.

1. To create an SNS topic, we do the following:

```
aws sns create-topic --name aws-cli
```

![AWS CLI](/images/4-sns/0001.png?featherlight=false&width=90pc)

2. After successfully creating the SNS topic, we will subscribe

```
 aws sns subscribe --topic-arn **ARN Topic** --protocol email --notification-endpoint aws@example.com
```

![AWS CLI](/images/4-sns/0002.png?featherlight=false&width=90pc)

3. Check the mail we used in the previous command. Then select **Confirm subscription**.

![AWS CLI](/images/4-sns/0003.png?featherlight=false&width=90pc)

4. Complete **subscription**

![AWS CLI](/images/4-sns/0004.png?featherlight=false&width=90pc)

5. After the subscriber, we try to push the message to check.

```
 aws sns publish --topic-arn **ARN Topic** --message "Hello"
```

![AWS CLI](/images/4-sns/0005.png?featherlight=false&width=90pc)

6. We will receive a message by mail.

![AWS CLI](/images/4-sns/0006.png?featherlight=false&width=90pc)

