---
title : "Getting Started with the AWS CLI"
date : "`r Sys.Date()`"
weight : 1
chapter : false
---

# Getting Started with the AWS CLI

#### Overview

In this exercise, you will learn about the AWS CLI and how to use it to interact with AWS services.

#### AWS CLI

The AWS Command Line Interface (AWS CLI) is an open-source tool that enables you to interact with AWS services using command-line shell commands. With a straightforward setup process, the AWS CLI empowers you to execute commands that provide the same functionality as the AWS Management Console in your browser.

#### Supported Command Windows

- **Linux Shells**: Utilize popular command window programs such as bash, zsh, and tcsh to run commands on Linux or macOS.
- **Windows Command Line**: On Windows, run commands in the Windows command prompt (command prompt) or PowerShell.
- **Remote Access**: Execute commands on an Amazon Elastic Compute Cloud (Amazon EC2) virtual machine through command windows like PuTTY, SSH, or AWS Systems Manager.

All administrative, management, and resource access tasks within the AWS Management Console are accessible via the AWS API and CLI. Any new AWS features and services are promptly available on the AWS Management Console through the API and CLI upon launch or within 180 days.

The AWS CLI provides direct access to the public APIs of AWS services. You can explore the capabilities of an AWS service, develop shell scripts to manage your resources, and even utilize higher-level commands that simplify the use of services with complex APIs.

#### Profile

A profile is a collection of settings and identifiers that grant access to the commands within the AWS CLI. By default, the AWS CLI uses the default profile. Additionally, you can create multiple other profiles known as private profiles using the `--profile` parameter.
- AWS CLI stores profile information in configuration and credentials files. You can also create extra profiles by directly adding settings to these files.
- You can specify a particular profile for the AWS CLI to execute commands using the `--profile` parameter. Alternatively, you can set a profile in the `AWS_PROFILE` environment variable to replace the default profile for a specific session.

#### Basics of Configuration

We will use the `aws configure` command, which is the quickest method to set up the AWS CLI. The command prompt will prompt you for four pieces of information:

  - Access Key ID
  - Secret Access Key
  - AWS Region
  - Output Format (Export Format)

#### Access Key ID and Secret Access Key

The access key comprises the access key ID and secret access key. It is utilized to sign application requests sent to AWS.

#### Region

The default region name specifies the AWS Region where server requests are sent by default. This is usually the region closest to you, but it can be any region. For instance, you can input `us-west-2` to use US West (Oregon). This default region will be used for all future requests unless you specify otherwise.

#### Output Format

The default output format defines how the returned results are formatted. The type can be any value from the list below. If you don't specify an output format, JSON is used by default.

- **json**: Results are formatted as a JSON string.
- **yaml**: Results are formatted as a YAML string. (Only available in AWS CLI v2.)
- **yaml-stream**: Results are streamed and formatted as YAML. Streams enable faster processing of large data types. (Only available in AWS CLI version 2.)
- **text**: Results are formatted as multiple lines of tab-separated string values. This format can be useful for passing output to tools like `grep`, `sed`, or `awk`.
- **table**: Results are formatted as a table using `+` and `-` characters to create cell borders. This format is "human-friendly" and easier to read compared to other formats, though not as programmatically efficient.
