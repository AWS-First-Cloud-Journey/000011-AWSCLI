+++
title = "AWS CLI Basic Setup"
date = 2020
weight = 2
chapter = false
pre = "<b>2. </b>"
+++

This section explains how to quickly configure basic settings that the AWS Command Line Interface (AWS CLI) uses to interact with AWS. These include your security credentials, the default output format, and the default AWS Region.

**Contents**
- [1. Quick configuration](#1-quick-configuration)
- [2. Access key ID and secret access key](#2-access-key-id-and-secret-access-key)
- [3. Region](#3-region)
- [4. Output format](#4-output-format)

#### 1. Quick configuration
For general use, the ```aws configure``` command is the fastest way to set up your AWS CLI installation.
This quick configuration will prompt to ask you four pieces of information:
- Access key ID
- Secret access key
- AWS Region
- Output format
These information will be explained clearly in next parts.

The AWS CLI stores this information in a *profile* (a collection of settings) named **default** in the **credentials** file. By default, the information in this profile is used when you run an AWS CLI command that **doesn't explicitly** specify a profile to use.
```bash
$ aws configure
AWS Access Key ID [None]: *AKIAIOSFODNN7EXAMPLE*
AWS Secret Access Key [None]: *wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY*
Default region name [None]: *us-west-2*
Default output format [None]: *json*
```

#### 2. Access key ID and secret access key
Access keys consist of an **access key ID** and **secret access key**, which are used to sign programmatic requests that you make to AWS. If you don't have access keys, you can create them from the **AWS Management Console**. As a best practice, **do not use** the AWS account root user access keys for any task where it's not required. Instead, create a new administrator IAM user with access keys for yourself.

The **only time** that you can view or download the secret access key is when you create the keys. You **cannot recover** them later. However, you can create new access keys at any time. You must also have permissions to perform the required IAM actions. 

**Create access keys for an IAM user**
1. Sign in to the **AWS Management Console** and open the **IAM console** at https://console.aws.amazon.com/iam/.
2. In the navigation pane, choose **Users**.
3. Choose the name of the user whose access keys you want to create, and then choose the **Security credentials** tab.
4. In the **Access keys** section, choose **Create access key**.
5. To view the new access key pair, choose **Show**. You **will not have access** to the secret access key again after this dialog box closes. Your credentials will look something like this:
    - **Access key ID**: AKIAIOSFODNN7EXAMPLE
    - **Secret access key**: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
6. To download the key pair, choose **Download .csv file**. Store the keys in a secure location. You will not have access to the secret access key again after this dialog box closes.  
Keep the keys confidential in order to protect your AWS account and never email them. Do not share them outside your organization, even if an inquiry appears to come from AWS or Amazon.com. No one who legitimately represents Amazon will ever ask you for your secret key.
7. After you download the .csv file, choose **Close**. When you create an access key, the key pair is **active by default**, and you can use the pair right away.

#### 3. Region
The **Default region name** identifies the AWS Region whose servers you want to send your requests to by default. This is typically the Region closest to you, but it can be any Region. For example, you can type **us-west-2** to use **US West (Oregon)**. This is the Region that all later requests are sent to, unless you specify otherwise in an individual command.
{{% notice info %}}
You must specify an AWS Region when using the AWS CLI, either explicitly or by setting a default Region.
{{% /notice %}}

#### 4. Output format
The **Default output format** specifies how the results are formatted. The value can be any of the values in the following list. If you don't specify an output format, **json is used as the default**.
- **json** – The output is formatted as a JSON string.
- **yaml** – The output is formatted as a YAML string. **(Available in the AWS CLI version 2 only.)**
- **yaml-stream** – The output is streamed and formatted as a YAML string. Streaming allows for faster handling of large data types. **(Available in the AWS CLI version 2 only.)**
- **text** – The output is formatted as multiple lines of tab-separated string values. This can be useful to pass the output to a text processor, like grep, sed, or awk.
- **table** – The output is formatted as a table using the characters +|- to form the cell borders. It typically presents the information in a "human-friendly" format that is much easier to read than the others, but not as programmatically useful.
