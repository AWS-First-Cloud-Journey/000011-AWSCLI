---
title: "Getting Started with the AWS CLI"
date: "`r Sys.Date()`"
weight: 1
chapter: false
---

# Getting Started with the AWS CLI

In this workshop, you will learn how to use the AWS Command Line Interface (CLI) to interact with AWS services efficiently through the command line.

#### AWS Command Line Interface (CLI)

**ℹ️ Information**: The **AWS Command Line Interface (CLI)** is an open-source tool that enables you to interact with AWS services using commands in your command-line shell. With the AWS CLI, you can control multiple AWS services directly from the command line and automate them through scripts.

#### Supported Command Environments

The AWS CLI supports various command environments:

- **Linux and macOS Shells** – Use popular shells like Bash, Zsh, or Tcsh to run AWS CLI commands.
- **Windows Command Line** – Execute commands in Windows Command Prompt or PowerShell.
- **Remote Access** – Run commands on Amazon EC2 instances through PuTTY, SSH, or AWS Systems Manager.

**💡 Pro Tip**: All administrative tasks available in the AWS Management Console can be performed using the AWS CLI or AWS API. New AWS services and features are typically made available in the CLI and API either immediately upon release or within 180 days.

#### AWS CLI Profiles

AWS CLI profiles are collections of settings used to execute commands:

- The **default** profile is used when no specific profile is specified
- Multiple named profiles can be created for different AWS environments
- Profile settings are stored in configuration and credentials files
- Use the `--profile` parameter or set the `AWS_PROFILE` environment variable to switch profiles

#### AWS CLI Configuration

Configure the AWS CLI using the `aws configure` command, which prompts for:

1. **AWS Access Key ID**
2. **AWS Secret Access Key**
3. **Default region name**
4. **Default output format**

**🔒 Security Note**: Store your AWS access keys securely and follow the principle of least privilege when configuring IAM permissions for CLI access. Consider using IAM roles for Amazon EC2 or AWS IAM Identity Center for enhanced security.

#### Default Region

The default region determines where the AWS CLI sends requests. Select the region closest to your infrastructure or users for optimal performance and lower latency (e.g., `us-west-2` for US West Oregon).

#### Output Formats

The AWS CLI supports multiple output formats:

- **json**: JSON-formatted output (default)
- **yaml**: YAML-formatted output (AWS CLI v2 only)
- **yaml-stream**: Streamed YAML for processing large datasets (AWS CLI v2 only)
- **text**: Tab-delimited text output for parsing with Unix tools
- **table**: Human-readable tabular format

**💡 Pro Tip**: Use the `text` output format with Unix tools like `grep`, `awk`, and `sed` for powerful command-line processing of AWS resource information.

#### Conclusion

The AWS CLI is a powerful tool for managing cloud infrastructure efficiently and can be customized for advanced use cases. Throughout this workshop, you'll gain hands-on experience with essential AWS CLI commands and patterns.
