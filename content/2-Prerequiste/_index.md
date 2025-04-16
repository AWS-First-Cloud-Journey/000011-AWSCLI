---
title: "Preparation"
date: "`r Sys.Date()`"
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
  - Create a new IAM group, assign a name, and define the necessary permissions for your use case.

- **Create an IAM User**:
  - Still within the IAM service, create a new IAM user.
  - Assign this user to the IAM group you just created.
  - Take note of the **Access Key ID** and **Secret Access Key** for future use.

- **Generate AWS Access Keys**:
  - Select the IAM user you created.
  - Under the **Security Credentials** tab, generate a new pair of access keys.
  - Safely store the **Access Key ID** and **Secret Access Key**—you will need them to authenticate with AWS services.

- **Create an EC2 Instance for SSH Access**:
  - In the AWS Management Console, navigate to the **EC2** (Elastic Compute Cloud) service.
  - Launch a new EC2 instance with your preferred operating system (e.g., Amazon Linux, Ubuntu).
  - Configure SSH access by creating or using an existing key pair.
  - Ensure the security group allows SSH access (port 22) from your IP address or trusted sources.

### Final Notes

With these preparation steps completed, you are now ready to proceed with the exercise. Be sure to securely store all login credentials and access keys to avoid unauthorized access or loss of control over your AWS resources.
