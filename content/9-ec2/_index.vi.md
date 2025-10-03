---
title : "Tạo EC2 sử dụng AWS CLI"
date : 2025-10-02
weight : 9
chapter : false
pre : " <b> 9. </b> "
---

#### Tạo EC2 sử dụng AWS CLI

1. Từ hạ tầng mạng đã tạo bằng **CLI**, chúng ta sẽ tạo **EC2**. Trước hết, tạo **AWS Key pair**:

    ```bash
    aws ec2 create-key-pair --key-name MyKeyPair --query "KeyMaterial" --output text > MyKeyPair.pem
    ```

    ![AWS CLI](/images/ec2-net/0001.png?featherlight=false&width=90pc)

2. Kiểm tra trên giao diện, xác nhận đã tạo thành công **Key pair**.

    ![AWS CLI](/images/ec2-net/0002.png?featherlight=false&width=90pc)

3. Phân quyền cho file **Key pair**:

    ```bash
    chmod 400 MyKeyPair.pem
    ```

    ![AWS CLI](/images/ec2-net/0003.png?featherlight=false&width=90pc)

4. Tạo **Security group** cho **EC2**:

    ```bash
    aws ec2 create-security-group --group-name SSHAccess --description "Security group for SSH access" --vpc-id <VPC ID>
    ```

    ![AWS CLI](/images/ec2-net/0004.png?featherlight=false&width=90pc)

5. Kiểm tra **Security group** vừa tạo.

    ![AWS CLI](/images/ec2-net/0005.png?featherlight=false&width=90pc)

6. Cấp quyền để SSH:

    ```bash
    aws ec2 authorize-security-group-ingress --group-id <SG ID> --protocol tcp --port 22 --cidr 0.0.0.0/0
    ```

    ![AWS CLI](/images/ec2-net/0006.png?featherlight=false&width=90pc)

7. Khởi tạo **EC2**:
   
    Bạn có thể lấy **AMI ID** bằng cách truy cập **EC2**, chọn **AMI Catalog**. Ở đây chúng ta sẽ lấy **AMI ID** của **Amazon Linux 2023 kenel-6.1 AMI**.

    ![AWS CLI](/images/0/019.png?featherlight=false&width=90pc)


     ```bash
    aws ec2 run-instances --image-id <AMI ID> --count 1 --instance-type t2.micro --key-name MyKeyPair --security-group-ids <SG ID> --subnet-id <Subnet ID>
    ```


    ![AWS CLI](/images/ec2-net/0007.png?featherlight=false&width=90pc)

8. Chờ khoảng 2 phút, kiểm tra trạng thái của **EC2 instance**:

    ```bash
    aws ec2 describe-instances --instance-id <Instance ID> --query "Reservations[*].Instances[*].{State:State.Name,Address:PublicIpAddress}"
    ```

    ![AWS CLI](/images/ec2-net/0008.png?featherlight=false&width=90pc)

9. Khi **instance** đang ở trạng thái **running**, thực hiện kết nối, nhớ thay thế IP của EC2 instance vừa tạo:

    ```bash
    ssh -i "MyKeyPair.pem" ec2-user@<IP Public>
    ```

    ![AWS CLI](/images/ec2-net/0009.png?featherlight=false&width=90pc)

10. Sau khi hoàn thành, **terminate** instance:

    ```bash
    aws ec2 terminate-instances --instance-ids <Instance ID>
    ```

    ![AWS CLI](/images/ec2-net/00010.png?featherlight=false&width=90pc)

11. Sau 2-3 phút, kiểm tra lại trạng thái **instance**:

    ```bash
    aws ec2 describe-instances --instance-id <Instance ID> --query "Reservations[*].Instances[*].State.Name"
    ```

    ![AWS CLI](/images/ec2-net/00011.png?featherlight=false&width=90pc)

{{% notice tip %}} 
Lưu ý: Hãy bảo mật key pair của bạn cẩn thận và xóa nó khi không sử dụng.
{{% /notice %}}

