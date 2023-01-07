---
title : "Getting Started with the AWS CLI"
date : "`r Sys.Date()`"
weight : 1
chapter : false
---

# Getting Started with the AWS CLI

#### Overview

In this exercise, you will learn about the AWS CLI and use it to interact with AWS services.

#### AWS CLI

The AWS Command Line Interface (AWS CLI) is an open source tool that allows you to interact with AWS services using command-line shell commands. With a simple setup process, the AWS CLI allows you to run commands that deploy functionality equivalent to that provided by the AWS Management Console in the browser.

AWS CLI supports the following command windows:

- **Linux shells** – Use popular command window programs like bash, zsh, and tcsh to run commands in Linux or macOS.
- **Windows command line** – On Windows, run the command in the Windows command prompt (command prompt) or PowerShell.
- **Remotely** – Run commands in an Amazon Elastic Compute Cloud (Amazon EC2) virtual machine through a command window such as PuTTY or SSH or AWS Systems Manager.

All administration, management, and access to AWS resources in the AWS Management Console are available in the AWS API and CLI. New AWS features and services will be made available in full on the AWS Management Console via API and CLI immediately upon launch or within 180 days thereafter.

AWS CLI provides direct access to public APIs of AWS services. You can explore the capabilities of an AWS service with the AWS CLI and develop shell scripts to manage your resources. In addition to the API-equivalent low-level commands, many AWS services allow customizations on the AWS CLI. Customizations can include higher-level commands that simplify the use of services with complex APIs.

#### Profile

The profile is a set of settings and identifiers that allow you to use the commands contained in the AWS CLI. By default, the AWS CLI uses the default profile. In addition, you can also create many other profiles called private profiles with the --profile parameter.
- AWS CLI stores profile information in config and credentials files. In addition to creating additional profiles with the --profile parameter, you can create additional profiles by adding settings directly to the config and credentials files.
- With the --profile parameter, you can specify a specific profile for it to execute commands in the AWS CLI. In addition, you can also specify a profile in the environment variable (AWS_PROFILE) to replace the default profile in a certain session.

#### Basics of configuration

We will use the aws configure command. This is considered the fastest way to set up the AWS CLI. The command window will appear asking for 4 information as follows:

  - Access key ID
  - Secret access key
  - AWS Region
  - Output format (Export format)

#### Access key ID and secret access key

The access key includes the access key ID and secret access key, which is used to sign application requests that you send to AWS.

#### Region (Region)

The default region name identifies the AWS Region where by default the server you want to send your requests. This is usually the Region closest to you, but it can be any Region. For example, you can type us-west-2 to use US West (Oregon). This is the default Region to which all future requests will be sent unless you specify otherwise.

#### Output format (Output format)

The default output format specifies how the returned results are formatted. Type can be any value in the list below. If you do not specify the output format then json is used by default.

- **json** – Output formatted as a JSON string.
- **yaml** – Output formatted as YAML string. (Only available in AWS CLI v2.)
- **yaml-stream** – Output is stream and formatted as YAML string. Streams allow faster processing of large data types. (Only available in AWS CLI version 2.)
- **text** – Output formatted as multiple lines of tab-separated string values. This format can be useful for passing output to a word processor, like grep, sed, or awk.
- **table** – Output formatted as a table using +|- characters to form cell borders. It typically presents information in a "human-friendly" format, which is much easier to read than other formats, but is not programmatically efficient.

