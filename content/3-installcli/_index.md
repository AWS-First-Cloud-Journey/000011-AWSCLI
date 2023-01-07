---
title : "Install AWS CLI"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

#### Install AWS CLI

**AWS Command Line Interface (AWS CLI)** is in two versions. To ensure the practicality of this lab, you will only practice installing AWS CLI v2 for Windows and Ubuntu because it is simpler, more convenient, and more complete than AWS CLI v1.

- **AWS CLI version 1 (AWS CLI v1)**: was the original AWS CLI and will still be supported by AWS.
- **AWS CLI version 2 (AWS CLI v2)**: is the latest version of AWS CLI that supports all the latest AWS features. However, some features available in version 2 are not supported in version 1, and you need to upgrade your version to use those features.

1. We'll start with the CLI by installing the following:

- For **Linux**:

```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```
- For Windows:

```
msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi
```

- For **MacOs**:

```
sudo ln -s /folder/installed/aws-cli/aws /usr/local/bin/aws
sudo ln -s /folder/installed/aws-cli/aws_completer /usr/local/bin/aws_completer
```

![AWS CLI](/images/1/0001.png?featherlight=false&width=10pc)

2. Check AWS CLI installed successfully:

```
aws --version
```

![AWS CLI](/images/1/0002.png?featherlight=false&width=10pc)

#### Create Default profile

3. We will use the AWS configure command. This is considered the fastest way to set up the AWS CLI. The command window will appear asking for four information as follows:

   - Access key ID
   - Secret access key
   - AWS Region
   - Output format (Export format)

```
aws configure
```
```
AWS Access Key ID [None]: *AKIAIOSFODNN7EXAMPLE*
AWS Secret Access Key [None]: *wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY*
Default region name [None]: *ap-southeast-1*
Default output format [None]: *json*
```

![AWS CLI](/images/1/0003.png?featherlight=false&width=10pc)

The AWS CLI stores this set of information in a profile (set of settings) named default in the credentials. By default, the information in this configuration is used by the AWS CLI when you run the aws configure command without explicitly specifying a profile.

#### Create your own profile

4. Configure multiple profiles: in this case configure one more devops profile.

```
aws configure --profile devops
```

![AWS CLI](/images/1/0005.png?featherlight=false&width=10pc)

The access key includes the access key ID and secret access key, which is used to sign application requests that you send to AWS.

5. Check configured.

![AWS CLI](/images/1/0006.png?featherlight=false&width=10pc)

#### Manage multiple profiles

6. Perform CLI credential check.

```
cd ~/.aws/
ls
cat config
```

![AWS CLI](/images/1/0007.png?featherlight=false&width=10pc)

7. Also we can also check the Region of a profile

```
aws configure get region --profile devops
```

![AWS CLI](/images/1/0008.png?featherlight=false&width=10pc)

8. Configuration list:

```
aws configure list
```

![AWS CLI](/images/1/0009.png?featherlight=false&width=10pc)

9. List of profiles:

```
aws configure list-profiles
```

![AWS CLI](/images/1/00010.png?featherlight=false&width=10pc)

{{% notice tip %}}
You can add or edit profiles directly by editing the two files **config** and **credentials** with your operating system's editor.
{{% /notice %}}