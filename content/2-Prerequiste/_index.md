---
title : "Preparation"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### Preparation
This guide outlines the necessary steps to prepare for the exercise. We will be using Markdown format to write a blog post within an IDE environment.

#### Preparation Steps

Before getting started, follow these steps:

- **Create an AWS Account**: To complete this exercise, you'll need an AWS account. If you don't have one, create an account on the official Amazon Web Services website.

- **Create an IAM Group:**

- Log in to your AWS account.
- In the dashboard, navigate to the "IAM" (Identity and Access Management) service.
- Create a new IAM group, name the group, and define the required access permissions.

**Create an IAM User:**

- Continue in the IAM service.
- Create an IAM user within the previously created group from the previous step.
- Remember the login information for this user (Access Key ID and Secret Access Key).

**Generate AWS Access Keys:**

- In the IAM dashboard, select the user you just created.
- In the "Security credentials" tab, generate a new pair of Access Keys.
- Safely store the Access Key ID and Secret Access Key. This information is crucial for accessing your AWS account.

**Create an EC2 Instance for SSH Access:**

- Continue in the AWS dashboard and locate the EC2 (Elastic Compute Cloud) service.
- Create an EC2 virtual machine with your desired operating system.
- Ensure you have configured SSH key pair access to the EC2 instance for command-line access.
- With these preparation steps completed, you are ready to proceed with the exercise. Ensure that you securely store all login information and access keys to avoid losing access to your AWS account.