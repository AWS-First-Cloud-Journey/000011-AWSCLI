+++
title = "AWS CLI version 2"
date = 2020
weight = 1
chapter = false
pre = "<b>1.2. </b>"
+++

This section provides links to information about how to install version 2 of the AWS Command Line Interface (AWS CLI) on the Windows and Ubuntu operating systems.
{{% notice warning %}}
AWS CLI versions 1 and 2 use the same ```aws``` command name. If you have both versions installed, your computer uses the first one found in your search path. If you previously installed AWS CLI version 1, we recommend that you do one of the following to use AWS CLI version 2:
- **Recommended** – Uninstall AWS CLI version 1 and use only AWS CLI version 2.
- Use your operating system's ability to create a symbolic link (symlink) or alias with a different name for one of the two aws commands. For example, you can use a [symbolic link](https://www.linux.com/tutorials/understanding-linux-links/) or [alias](https://www.linux.com/tutorials/aliases-diy-shell-commands/) on Linux and macOS, or [DOSKEY](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/doskey) on Windows.
{{% /notice %}}

**Contents**
- [1. Install AWS CLI on Windows](#1-install-aws-cli-on-windows)
- [2. Install AWS CLI on Ubuntu](#2-install-aws-cli-on-ubuntu)

#### 1. Install AWS CLI on Windows
{{% notice info %}}
Before you can install or update the AWS CLI version 2 on Windows, be sure you have the following:
- A **64-bit** version of Windows XP or later.
- **Admin rights** to install software.
{{% /notice %}}

1. Download the AWS CLI MSI installer for Windows (64-bit):
   - For the latest version of the AWS CLI: https://awscli.amazonaws.com/AWSCLIV2.msi
   - For a specific version of the AWS CLI: Append a hyphen and the version number to the filename. (For this example the filename for version 2.0.30 would be AWSCLIV2-2.0.30.msi resulting in the following link https://awscli.amazonaws.com/AWSCLIV2-2.0.30.msi)
2. Run the downloaded MSI installer and follow the on-screen instructions. By default, the AWS CLI installs to C:\Program Files\Amazon\AWSCLIV2.
3. To confirm the installation, use the ```aws --version``` command at a command prompt (open the **Start** menu and search for **cmd** to start a **Command prompt**).

{{% notice tip %}}
If Windows is unable to find the program, you might need to close and reopen the command prompt to refresh the path, or [add the installation directory to your PATH](https://docs.aws.amazon.com/cli/latest/userguide/install-windows.html#awscli-install-windows-path) environment variable manually.
{{% /notice %}}

#### 2. Install AWS CLI on Ubuntu
{{% notice info %}}
- You must be able to extract or "unzip" the downloaded package. If your operating system doesn't have the built-in ```unzip``` command, use an equivalent.
- The AWS CLI version 2 uses ```glibc```, ```groff```, and ```less```. These are included by default in most major distributions of Linux.
- AWS support the AWS CLI version 2 on 64-bit versions of recent distributions of CentOS, Fedora, Ubuntu, Amazon Linux 1, and Amazon Linux 2.
- AWS support the AWS CLI version 2 on Linux ARM.
- Because AWS doesn't maintain third-party repositories, we can’t guarantee that they contain the latest version of the AWS CLI.
{{% /notice %}}

1. Download the installation file in one of the following ways:
   - **Use the curl command** – The ```-o``` option specifies the file name that the downloaded package is written to. The options on the following example command write the downloaded file to the current directory with the local name ```awscliv2.zip```.
     - **For the current version of the AWS CLI**, use the following command:  
     ```curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"```
     - **For a specific version of the AWS CLI**, append a hyphen and the version number to the filename. For this example the filename for version 2.0.30 would be awscli-exe-linux-x86_64-2.0.30.zip resulting in the following command:  
     ```curl "https://awscli.amazonaws.com/*awscli-exe-linux-x86_64-2.0.30.zip*" -o "awscliv2.zip"```
   - **Downloading from the URL** – To download the installer with your browser, use one of the following URLs. You can verify the integrity and authenticity of your downloaded installation file before you extract (unzip) the package.
     - **For the latest version of the AWS CLI**: https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip
     - **For a specific version of the AWS CLI**, append a hyphen and the version number to the filename. For this example the filename for version 2.0.30 would be awscli-exe-linux-x86_64-2.0.30.zip resulting in the following url: https://awscli.amazonaws.com/awscli-exe-linux-x86_64-2.0.30.zip
2. Unzip the installer. If you don't have a built-in unzip command, use an equivalent to unzip it. The following example command unzips the package and creates a directory named aws under the current directory.  
```unzip awscliv2.zip```
3. Run the install program. The installation command uses a file named install in the newly unzipped aws directory. By default, the files are all installed to ```/usr/local/aws-cli```, and a symbolic link is created in ```/usr/local/bin```. The command includes ```sudo``` to grant write permissions to those directories.  
```sudo ./aws/install```
4. Confirm the installation with ```aws --version```.