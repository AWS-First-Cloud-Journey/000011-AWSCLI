---
title: "Install AWS CLI"  
date: "`r Sys.Date()`"  
weight: 3  
chapter: false  
pre: " <b> 3. </b> "
---

#### Install AWS CLI

**AWS Command Line Interface (AWS CLI)** is available in two versions. To ensure a smooth experience, this guide covers the installation of AWS CLI v2 for Windows and Ubuntu, as it is simpler, more convenient, and feature-complete compared to v1.

- **AWS CLI version 1 (AWS CLI v1)**: The original AWS CLI, still supported by AWS.
- **AWS CLI version 2 (AWS CLI v2)**: The latest version supporting all the newest AWS features. Some features available in v2 are not supported in v1, so upgrading is necessary to use those features.

1. Let's begin by installing the AWS CLI on different platforms.

- For **Linux**:

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

- For **Windows**:

```bash
msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi
```

- For **MacOS**:

```bash
sudo ln -s /folder/installed/aws-cli/aws /usr/local/bin/aws
sudo ln -s /folder/installed/aws-cli/aws_completer /usr/local/bin/aws_completer
```

![AWS CLI](/images/1/0001.png?featherlight=false&width=90pc)

2. Verify that AWS CLI is installed:

```bash
aws --version
```

![AWS CLI](/images/1/0002.png?featherlight=false&width=90pc)

#### Create Default Profile

3. Use the `aws configure` command to set up the AWS CLI. This is the fastest way to configure it. You will be prompted for the following details:

   - Access key ID
   - Secret access key
   - AWS Region
   - Output format (e.g., JSON)

```bash
aws configure
```

```bash
AWS Access Key ID [None]: *AKIAIOSFODNN7EXAMPLE*
AWS Secret Access Key [None]: *wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY*
Default region name [None]: *ap-southeast-1*
Default output format [None]: *json*
```

![AWS CLI](/images/1/0003.png?featherlight=false&width=90pc)

The AWS CLI stores this information in a profile named **default** in the credentials file. This profile is used when no specific profile is specified.

#### Create Custom Profile

4. To configure multiple profiles, create another profile (e.g., devops).

```bash
aws configure --profile devops
```

![AWS CLI](/images/1/0005.png?featherlight=false&width=90pc)

The access key (Access Key ID and Secret Access Key) is used to authenticate requests to AWS.

5. Verify that the profile is configured:

![AWS CLI](/images/1/0006.png?featherlight=false&width=90pc)

#### Manage Multiple Profiles

6. Check the configuration of CLI credentials:

```bash
cd ~/.aws/
ls
cat config
```

![AWS CLI](/images/1/0007.png?featherlight=false&width=90pc)

7. You can also verify the region for a specific profile:

```bash
aws configure get region --profile devops
```

![AWS CLI](/images/1/0008.png?featherlight=false&width=90pc)

8. List the current configuration:

```bash
aws configure list
```

![AWS CLI](/images/1/0009.png?featherlight=false&width=90pc)

9. List all profiles:

```bash
aws configure list-profiles
```

![AWS CLI](/images/1/00090.png?featherlight=false&width=90pc)

{{% notice tip %}}  
You can add or edit profiles directly by editing the **config** and **credentials** files using a text editor.  
{{% /notice %}}

