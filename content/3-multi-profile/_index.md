+++
title = "Multi-profile Setup"
date = 2020
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

**Contents**
- [1. Profile](#1-profile)
- [2. Multiple Profiles](#2-multiple-profiles)
  - [Create Named Profile](#create-named-profile)
  - [Manage Configuration with Multiple Profile](#manage-configuration-with-multiple-profile)

### 1. Profile
A collection of settings is called a profile. By default, the AWS CLI uses the **default** profile. You can create and use additional named profiles with varying credentials and settings by specifying the --profile option and assigning a name.
You can save your frequently used configuration settings and credentials in files that are maintained by the AWS CLI.

The following example creates the **default** profile.
```bash
$ aws configure
AWS Access Key ID [None]: *AKIAIOSFODNN7EXAMPLE*
AWS Secret Access Key [None]: *wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY*
Default region name [None]: *us-west-2*
Default output format [None]: *json*
```

### 2. Multiple Profiles
The AWS CLI supports using any of multiple named profiles that are stored in the config and credentials files. You can configure additional profiles by using aws configure with the --profile option, or by adding entries to the config and credentials files.
The files are divided into profiles. A named profile is a collection of settings and credentials that you can apply to a AWS CLI command. When you specify a profile to run a command, the settings and credentials are used to run that command. You can specify one profile that is the "default", and is used when no profile is explicitly referenced. Other profiles have names that you can specify as a parameter on the command line for individual commands. Alternatively, you can specify a profile in an environment variable (AWS_PROFILE) which essentially overrides the default profile for commands that run in that session.

#### Create Named Profile
The following example creates a profile named **testuser**.
```bash
$ aws configure *--profile testuser*
AWS Access Key ID [None]: AKIAI44QH8DHBEXAMPLE
AWS Secret Access Key [None]: je7MtGbClwBF/2Zp9Utk/h3yCo8nvbEXAMPLEKEY
Default region name [None]: us-east-1
Default output format [None]: text
```

So, you can then specify a ```--profile *profilename*``` and use the credentials and settings stored under that name.
```bash
aws s3 ls --profile produser
```

To update these settings, run ```aws configure``` again (with or without the ```--profile *profilename*``` parameter, depending on which profile you want to update) and enter new values as appropriate. The next sections contain more information about the files that **aws configure** creates, additional settings, and named profiles.

#### Manage Configuration with Multiple Profile 
The following example shows a credentials file with two profiles. The first [default] is used when you run a CLI command with no profile. The second is used when you run a CLI command with the --profile user1 parameter. 
```~/.aws/credentials``` (Linux & Mac) or ```%USERPROFILE%\.aws\credentials``` (Windows).
```
[default]
aws_access_key_id=AKIAIOSFODNN7EXAMPLE
aws_secret_access_key=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY

[testuser]
aws_access_key_id=AKIAI44QH8DHBEXAMPLE
aws_secret_access_key=je7MtGbClwBF/2Zp9Utk/h3yCo8nvbEXAMPLEKEY
```

Each profile can specify different credentials—perhaps from different IAM users—and can also specify different AWS Regions and output formats.
```~/.aws/config``` (Linux & Mac) or ```%USERPROFILE%\.aws\config``` (Windows).
```
[default]
region=us-west-2
output=json

[profile testuser]
region=us-east-1
output=text
```