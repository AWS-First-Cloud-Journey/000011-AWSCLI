---
title : "Tạo EC2 sử dụng AWS CLI"
date :  "`r Sys.Date()`" 
weight : 9
chapter : false
pre : " <b> 9. </b> "
---

#### Tạo EC2 sử dụng AWS CLI

1. Từ hạ tầng mạng đã tạo bằng **CLI**, chúng ta sẽ tạo **EC2**. Trước hết, tạo **AWS Key pair**

```
aws ec2 create-key-pair --key-name MyKeyPair --query "KeyMaterial" --output text > MyKeyPair.pem
```

![AWS CLI](/images/ec2-net/0001.png?featherlight=false&width=90pc)

2. Kiểm tra trên giao diện, chúng ta xác nhận đã tạo thành công **Key pair**

![AWS CLI](/images/ec2-net/0002.png?featherlight=false&width=90pc)

3. Sử dụng lệnh để phân quyền:

```
chmod 400 MyKeyPair.pem
```

![AWS CLI](/images/ec2-net/0003.png?featherlight=false&width=90pc)

4. Tạo **Security group** cho **EC2**

```
aws ec2 create-security-group --group-name SSHAccess --description "Security group for SSH access" --vpc-id **VPC ID**
```

![AWS CLI](/images/ec2-net/0004.png?featherlight=false&width=90pc)

5. Sau đó, chúng ta kiểm tra **Security group** đã tạo.

![AWS CLI](/images/ec2-net/0005.png?featherlight=false&width=90pc)

6. Thực hiện cho phép để SSH:

```
aws ec2 authorize-security-group-ingress --group-id **SG ID** --protocol tcp --port 22 --cidr 0.0.0.0/0
```

![AWS CLI](/images/ec2-net/0006.png?featherlight=false&width=90pc)

7. Chuẩn bị hoàn tất, chúng ta thực hiện khởi tạo **EC2**

```
aws ec2 run-instances --image-id **AMI** --count 1 --instance-type t2.micro --key-name MyKeyPair --security-group-ids **SG ID** --subnet-id **Subnet ID**
```

![AWS CLI](/images/ec2-net/0007.png?featherlight=false&width=90pc)

8. Đợi khoảng 2 phút, xem trạng thái của **EC2 isntance**

```
aws ec2 describe-instances --instance-id **Instance ID** --query "Reservations[*].Instances[*].{State:State.Name,Address:PublicIpAddress}"
```

![AWS CLI](/images/ec2-net/0008.png?featherlight=false&width=90pc)

9. Khi instance đang ở trạng thái **running**. Chúng ta thực hiện kết nối

```
ssh -i "MyKeyPair.pem" ec2-user@IP Public
```

![AWS CLI](/images/ec2-net/0009.png?featherlight=false&width=90pc)

10. Sau khi đã sử dụng, chúng ta thực hiện **terminate** bằng lệnh:

```
aws ec2 terminate-instance --instances-ids **Instance ID**
```

![AWS CLI](/images/ec2-net/00010.png?featherlight=false&width=90pc)

11. Sau khoảng 2-3 phút sau. chúng ta kiểm tra lại trạng thái của **instance**

![AWS CLI](/images/ec2-net/00011.png?featherlight=false&width=90pc)
