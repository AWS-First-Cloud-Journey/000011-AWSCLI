---
title: "Preparation"
date: 2025-10-02
weight: 2
chapter: false
pre: "<b>2.</b>"
---

#### Preparation

This guide outlines the necessary steps to prepare for the exercise. We'll use Markdown format to write a blog post within an IDE environment.

### Preparation Steps

Before you get started, follow these steps:

- **Create an AWS Account**: If you don't already have an AWS account, [sign up here](https://aws.amazon.com/). An AWS account is required to complete this exercise.

- **Create an IAM Group**:
  - Log in to your AWS Management Console.
  - Navigate to the **IAM** (Identity and Access Management) service.
  ![Prerequiste](/images/0/01.png?featherlight=false&width=90pc)
  - Create a new IAM group, assign a name, and define the necessary permissions for your use case.
   ![Prerequiste](/images/0/2.png?featherlight=false&width=90pc)
   ![Prerequiste](/images/0/3.png?featherlight=false&width=90pc)
    ![Prerequiste](/images/0/4.png?featherlight=false&width=90pc)

- **Create an IAM User**:
  - Still within the IAM service, create a new IAM user., named **aws-cli-user**.
  - Assign this user to the IAM group you just created.
  - Take note of the **Access Key ID** and **Secret Access Key** for future use.
  ![Prerequiste](/images/0/5.png?featherlight=false&width=90pc)
    ![Prerequiste](/images/0/6.png?featherlight=false&width=90pc)
    ![Prerequiste](/images/0/7.png?featherlight=false&width=90pc)

- **Generate AWS Access Keys**:
  - Select the IAM user you created.
  - Under the **Security Credentials** tab, generate a new pair of access keys.
  - Safely store the **Access Key ID** and **Secret Access Key**—you will need them to authenticate with AWS services.
  ![Prerequiste](/images/0/9.png?featherlight=false&width=90pc)
    ![Prerequiste](/images/0/10.png?featherlight=false&width=90pc)
    ![Prerequiste](/images/0/11.png?featherlight=false&width=90pc)
    ![Prerequiste](/images/0/12.png?featherlight=false&width=90pc)
    ![Prerequiste](/images/0/13.png?featherlight=false&width=90pc)

    - Create another user named **devops**, add that user to **aws-cli** and repeat the above steps.

- **Create an EC2 Instance for SSH Access**:
  - In the AWS Management Console, navigate to the **EC2** (Elastic Compute Cloud) service.
  - Launch a new EC2 instance with your preferred operating system (e.g., Amazon Linux, Ubuntu).
  - Configure SSH access by creating or using an existing key pair.
  - Ensure the security group allows SSH access (port 22) from your IP address or trusted sources.

   ![Prerequiste](/images/0/17.png?featherlight=false&width=90pc)
   ![Prerequiste](/images/0/18.png?featherlight=false&width=90pc)

### Final Notes

With these preparation steps completed, you are now ready to proceed with the exercise. Be sure to securely store all login credentials and access keys to avoid unauthorized access or loss of control over your AWS resources.
