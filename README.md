# Getting Started with the AWS CLI

A comprehensive workshop for learning how to use the AWS Command Line Interface (CLI) to interact with AWS services efficiently through the command line.

## 📋 Overview

This workshop provides hands-on experience with the AWS CLI, covering installation, configuration, and practical usage with various AWS services. You'll learn to automate tasks and manage AWS resources more efficiently than using the AWS Management Console.

## 🎯 Learning Objectives

By the end of this workshop, you will be able to:

- Install and configure AWS CLI v2 on different platforms
- Set up and manage multiple AWS CLI profiles
- Interact with core AWS services using CLI commands
- Automate AWS resource management through scripts
- Apply security best practices for CLI access

## 🏗️ Workshop Structure

### 1. Introduction
- Overview of AWS CLI capabilities
- Understanding command environments
- Benefits of CLI over console management

### 2. Prerequisites
- AWS account setup requirements
- IAM user creation and permissions
- Security group configuration

### 3. Install AWS CLI
- Installation on Linux, Windows, and macOS
- Version verification
- Profile configuration and management

### 4. Infrastructure Setup
- Basic infrastructure provisioning
- Resource preparation for CLI exercises

### 5. AWS CLI with Amazon S3
- Creating and managing S3 buckets
- Uploading and downloading objects
- Bucket policies and permissions

### 6. AWS CLI with Amazon SNS
- Creating SNS topics
- Managing subscriptions
- Publishing messages

### 7. AWS CLI with IAM
- User and role management
- Policy creation and attachment
- Access key management

### 8. AWS CLI with Networking
- VPC creation and management
- Internet Gateway configuration
- Security group management

### 9. AWS CLI with EC2
- Instance launch and management
- Key pair creation
- Instance monitoring and control

### 10. Troubleshooting
- Common CLI errors and solutions
- Debug techniques
- Best practices

### 11. Cleanup
- Resource cleanup procedures
- Cost optimization
- Environment reset

## 🚀 Quick Start

### Prerequisites

- AWS Account with appropriate permissions
- Terminal/Command Prompt access
- Basic understanding of AWS services

### Installation

**Linux:**
```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

**Windows:**
```bash
msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi
```

**macOS:**
```bash
sudo ln -s /folder/installed/aws-cli/aws /usr/local/bin/aws
sudo ln -s /folder/installed/aws-cli/aws_completer /usr/local/bin/aws_completer
```

### Configuration

1. **Basic Configuration:**
```bash
aws configure
```

2. **Multiple Profiles:**
```bash
aws configure --profile devops
```

3. **Verify Installation:**
```bash
aws --version
aws configure list
```

## 🛠️ Key Features Covered

### AWS CLI Profiles
- Default profile configuration
- Named profiles for different environments
- Profile switching and management
- Credentials file organization

### Output Formats
- **JSON**: Default structured output
- **YAML**: Human-readable format (v2 only)
- **Text**: Tab-delimited for Unix tools
- **Table**: Human-readable tabular format

### Security Best Practices
- IAM user setup with minimal permissions
- Access key rotation
- Profile-based access control
- Secure credential storage

### Service Integration
- **S3**: Bucket and object management
- **EC2**: Instance lifecycle management
- **IAM**: Identity and access management
- **VPC**: Network infrastructure
- **SNS**: Notification services

## 📚 Workshop Content

This workshop is built using Hugo with the Learn theme and includes:

- **Bilingual Support**: English and Vietnamese content
- **Interactive Examples**: Step-by-step CLI commands
- **Visual Guides**: Screenshots and diagrams
- **Hands-on Labs**: Practical exercises
- **Best Practices**: Security and efficiency tips

## 🌐 Supported Environments

### Command Environments
- **Linux Shells**: Bash, Zsh, Tcsh
- **Windows**: Command Prompt, PowerShell
- **Remote Access**: SSH, PuTTY, AWS Systems Manager

### AWS Regions
- Optimized for Asia Pacific (Singapore) - `ap-southeast-1`
- Configurable for any AWS region
- Multi-region best practices

## 🔧 Technical Requirements

- **AWS CLI v2** (recommended)
- **Hugo** (for local development)
- **Git** (for version control)
- **Web Browser** (for viewing workshop content)

## 📖 Usage Instructions

### Local Development
```bash
# Clone the repository
git clone https://github.com/AWS-First-Cloud-Journey/000011-AWSCLI.git

# Navigate to the project directory
cd 000011-AWSCLI

# Start Hugo development server
hugo server -D

# Access the workshop at http://localhost:1313
```

### Building for Production
```bash
# Generate static site
hugo

# Deploy the public/ directory to your web server
```

## 🤝 Contributing

We welcome contributions to improve this workshop! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

### Content Guidelines
- Follow the existing structure and formatting
- Include both English and Vietnamese translations
- Add screenshots for new CLI commands
- Test all commands before submitting

## 📝 License

This workshop is part of the AWS First Cloud Journey series and is available under the MIT License.

## 🆘 Support

For questions or issues:

- **AWS Study Group Blog**: [AWS Blogs](https://aws.amazon.com/blogs)
- **Facebook Community**: [AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj)
- **Email**: journeyoftheaverageguy@gmail.com

## 🏷️ Tags

`AWS` `CLI` `Command Line` `Cloud Computing` `Infrastructure` `Automation` `DevOps` `Tutorial` `Workshop` `Hands-on`

---

**Note**: This workshop provides practical, hands-on experience with the AWS CLI. All administrative tasks available in the AWS Management Console can be performed using the AWS CLI, making it an essential tool for cloud automation and management.
