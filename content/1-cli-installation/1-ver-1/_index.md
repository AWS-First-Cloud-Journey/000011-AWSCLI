+++
title = "AWS CLI version 1"
date = 2020
weight = 1
chapter = false
pre = "<b>1.1. </b>"
+++

The AWS CLI version 1 is the original AWS CLI, and we continue to support it. However, major new features that are introduced in the AWS CLI version 2 might not be backported to the AWS CLI version 1. To use those features, you must install the AWS CLI version 2.

**Contents**
- [1. Install AWS CLI on Windows](#1-install-aws-cli-on-windows)
  - [Install using the MSI installer](#install-using-the-msi-installer)
  - [Install using Python and pip on Windows](#install-using-python-and-pip-on-windows)
- [2. Install AWS CLI on Ubuntu](#2-install-aws-cli-on-ubuntu)
  - [Install the AWS CLI version 1 using the bundled installer with sudo](#install-the-aws-cli-version-1-using-the-bundled-installer-with-sudo)
  - [Install the AWS CLI version 1 using the bundled installer without sudo](#install-the-aws-cli-version-1-using-the-bundled-installer-without-sudo)

### 1. Install AWS CLI on Windows
You can install version 1 of the AWS Command Line Interface (AWS CLI) on Windows by using a standalone installer (recommended) or pip, which is a package manager for Python. If you already have pip.

Don't include the prompt symbol (C:\>) when you type a command. These are included in program listings to differentiate commands that you type from output returned by the CLI. The rest of this guide uses the generic prompt symbol ($), except in cases where a command is Windows-specific.

{{% notice warning %}}
AWS CLI version 1 no longer supports Python versions 2.6 and 3.3. All versions of the AWS CLI version 1 released after January 10th, 2020, starting with 1.17, require Python 2.7, Python 3.4, or a later version.

This change does not affect the Windows MSI installer version of the AWS CLI version 1 and the AWS CLI version 2.

For more information, see [Using the AWS CLI version 1 with earlier versions of Python](https://docs.aws.amazon.com/cli/latest/userguide/deprecate-old-python-versions.html), and the [deprecation announcement](https://aws.amazon.com/blogs/developer/deprecation-of-python-2-6-and-python-3-3-in-botocore-boto3-and-the-aws-cli/) blog post.
{{% /notice %}}

#### Install using the MSI installer
1. Download the appropriate MSI installer:
   - AWS CLI MSI installer for Windows (64-bit): https://s3.amazonaws.com/aws-cli/AWSCLI64PY3.msi
   - AWS CLI MSI installer for Windows (32-bit): https://s3.amazonaws.com/aws-cli/AWSCLI32PY3.msi
   - AWS CLI combined setup file for Windows: https://s3.amazonaws.com/aws-cli/AWSCLISetup.exe (includes both the 32-bit and 64-bit MSI installers, and automatically installs the correct version)
2. Run the downloaded MSI installer or the setup file.
3. Follow the on-screen instructions. By default, the AWS CLI version 1 installs to C:\Program Files\Amazon\AWSCLI (64-bit version) or C:\Program Files (x86)\Amazon\AWSCLI (32-bit version).
4. To confirm the installation, use the ```aws --version``` command at a command prompt (open the **Start** menu and search for **cmd** to start a **Command prompt**).

{{% notice tip %}}
If Windows is unable to find the program, you might need to close and reopen the command prompt to refresh the path, or [add the installation directory to your PATH](https://docs.aws.amazon.com/cli/latest/userguide/install-windows.html#awscli-install-windows-path) environment variable manually.
{{% /notice %}}

#### Install using Python and pip on Windows
{{% notice info %}}
Make sure you already install **Python 3** on system.
{{% /notice %}}

1. To Install the AWS CLI version 1, use the ```pip3``` command (if you use Python version 3 or later) or the ```pip``` command.  
```pip3 install awscli``` or ```pip3 install --user --upgrade awscli``` (To upgrade to the latest version)
2. Verify that the AWS CLI version 1 is installed correctly.  
```bash
aws --version
```
{{% notice info %}}
After installing the AWS CLI version 1 with ```pip```, add the aws program to your operating system's ```PATH``` environment variable. With an MSI installation, this should happen automatically. But if the ```aws``` command doesn't run after you install it, you might need to set it manually.
{{% /notice %}}
3. Press the Windows key and enter ```environment variables```.
4. Choose **Edit environment variables for your account**.
5. Choose **PATH**, and then choose **Edit**.
6. Add the path you found into the **Variable value** field, for example, *C:\Program Files\Amazon\AWSCLI\bin\aws.exe*.
7. Choose **OK** twice to apply the new settings.
8. Close any running command prompts and reopen the command prompt window.

### 2. Install AWS CLI on Ubuntu
{{% notice tip %}}
You must have Python 2 version 2.7 or later, or Python 3 version 3.4 or later installed. For installation instructions, see the [Downloading Python](https://wiki.python.org/moin/BeginnersGuide/Download) page in Python's Beginner Guide.
{{% /notice %}}

#### Install the AWS CLI version 1 using the bundled installer with sudo
1. Download the AWS CLI version 1 bundled installer using one of the the following methods.
   - Download using the curl command  
   ```bash
   $ curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip"
   ```
   - Download using the direct link: https://s3.amazonaws.com/aws-cli/awscli-bundle.zip
2. Extract the files from the package. If you don't have unzip to extract the files, use your Linux distribution's built-in package manager to install it.unzip awscli-bundle.zip
```bash
$ unzip awscli-bundle.zip
```
3. Run the install program. The installer installs the AWS CLI at /usr/local/aws and creates the symlink aws at the /usr/local/bin directory. Using the -b option to create a symlink eliminates the need to specify the install directory in the user's $PATH variable. This should enable all users to call the AWS CLI by entering aws from any directory.
```bash
$ sudo <path to Python> ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws
```
4. Verify that the AWS CLI installed correctly with ```aws --version```.

#### Install the AWS CLI version 1 using the bundled installer without sudo
1. Download the AWS CLI version 1 bundled installer using one of the the following methods.
   - Download using the curl command  
```bash
$ curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip"
```
   - Download using the direct link: https://s3.amazonaws.com/aws-cli/awscli-bundle.zip
2. Extract the files from the package. If you don't have unzip to extract the files, use your Linux distribution's built-in package manager to install it.unzip awscli-bundle.zip
```bash
$ unzip awscli-bundle.zip
```
3. Run the install program. The installer installs the AWS CLI at ```/usr/local/aws``` and creates the symlink ```aws``` at the ```/usr/local/bin``` directory. The command uses the ```-b ```parameter to specify the directory where the installer places the aws symlink file. You must have write permissions to the specified folder.
```bash
$ ./awscli-bundle/install -b ~/bin/aws
```
This installs the AWS CLI to the default location (```~/.local/lib/aws```) and creates a symbolic link (symlink) at ```~/bin/aws```. Make sure that ````~/bin```` is in your ```PATH``` environment variable for the symlink to work.
```bash
$ echo $PATH | grep ~/bin     // See if $PATH contains ~/bin (output will be empty if it does not)
$ export PATH=~/bin:$PATH     // Add ~/bin to $PATH if necessary
```
4. Ensure the directory that the AWS CLI version 1 is part of your PATH variable.
   - Find your shell's profile script in your user folder. If you're not sure which shell you have, run ```echo $SHELL```.  
   ```bash
   $ ls -a ~
   .  ..  .bash_logout  .bash_profile  .bashrc  Desktop  Documents  Downloads
   ```
     - **Bash** – .bash_profile, .profile, or .bash_login (Ubuntu default)
     - **Zsh** – .zshrc
     - **Tcsh** – .tcshrc, .cshrc or .login
   - Add an export command at the end of your profile script that's similar to the following example.
   ```bash
   export PATH=~/.local/bin:$PATH
   ```
   - Reload the profile into your current session to put those changes into effect.
   ```bash
   $ source ~/.bash_profile
   ```
5. Verify that the AWS CLI installed correctly with ```$ aws --version```.