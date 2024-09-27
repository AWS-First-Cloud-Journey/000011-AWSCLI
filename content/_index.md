---
title: "Getting Started with the AWS CLI"
date: "`r Sys.Date()`"
weight: 1
chapter: false
---

# Getting Started with the AWS CLI

## Overview

In this guide, you will learn how to get started with the AWS CLI and use it to interact with AWS services.

## AWS CLI Overview

The AWS Command Line Interface (AWS CLI) is an open-source tool that enables you to interact with AWS services using command-line shell commands. The AWS CLI provides the same functionality as the AWS Management Console but allows for automation and scripting.

### Supported Command Line Interfaces

- **Linux and macOS**: You can use shells like `bash`, `zsh`, or `tcsh` to run AWS CLI commands.
- **Windows**: The AWS CLI can be run in Command Prompt or PowerShell.
- **Remote Access**: You can also run AWS CLI commands on Amazon EC2 instances through tools like PuTTY, SSH, or AWS Systems Manager.

The AWS CLI allows you to perform administrative and resource management tasks on AWS, offering direct access to AWS services' public APIs. The CLI is updated as AWS releases new features and services, often within 180 days of launch.

### AWS CLI Profiles

Profiles are collections of settings that the AWS CLI uses to execute commands. By default, the AWS CLI uses the **default** profile, but you can define multiple custom profiles.

- Profile settings are stored in configuration and credentials files.
- To specify a profile for a command, use the `--profile` parameter or set the `AWS_PROFILE` environment variable to switch profiles for the current session.

## AWS CLI Configuration

You can configure the AWS CLI using the `aws configure` command. This command will prompt you for four pieces of information:

1. **AWS Access Key ID**
2. **AWS Secret Access Key**
3. **Default region name**
4. **Default output format**

### AWS Access Key ID and Secret Access Key

Your AWS access keys consist of the **Access Key ID** and **Secret Access Key**. These are used to authenticate and sign requests made to AWS.

### Default Region

The **default region** is where the AWS CLI will send requests unless a region is explicitly specified in a command. You should select the region closest to your infrastructure or where most of your AWS services reside, e.g., `us-west-2` for the US West (Oregon) region.

### Output Format

The **default output format** determines how the results of AWS CLI commands are displayed. The available formats are:

- **json**: Outputs results in JSON format (default).
- **yaml**: Outputs results in YAML format (only available in AWS CLI v2).
- **yaml-stream**: Streams large datasets in YAML format for faster processing (only available in AWS CLI v2).
- **text**: Outputs tab-delimited text, useful for parsing with tools like `grep`, `sed`, or `awk`.
- **table**: Displays results in a human-readable table format.

## Conclusion

The AWS CLI is a powerful tool that can simplify AWS management through scripting and automation. Configuring the CLI properly allows you to efficiently manage AWS resources from your command line environment.

