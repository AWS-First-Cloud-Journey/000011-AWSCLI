+++
title = "SSO Configuration for CLI"
date = 2020
weight = 1
chapter = false
pre = "<b>4.1 </b>"
+++
  
You can configure one or more of your AWS CLI named profiles to use a role from AWS SSO You can create and configure multiple profiles and configure each one to use a a different AWS SSO user portal or SSO-defined role.

You can configure the profile in the following ways:
- **Automatically**, using the command ```aws configure sso```
- **Manually**, by editing the ```.aws/config``` file that stores the named profiles.

**Contents**
- [1. Automatic configuration](#1-automatic-configuration)
- [2. Manual configuration](#2-manual-configuration)

#### 1. Automatic configuration
You can add an AWS SSO enabled profile to your AWS CLI by running the following command, providing your **AWS SSO start URL** and the **AWS Region** that hosts the AWS SSO directory.
```bash
$ aws configure sso
SSO start URL [None]: [None]: https://my-sso-portal.awsapps.com/start
SSO region [None]:us-east-1
```

The AWS CLI attempts to open your default browser and begin the login process for your AWS SSO account.
```bash
SSO authorization page has automatically been opened in your default browser.  
Follow the instructions in the browser to complete this authorization request.
```

*If the AWS CLI cannot open the browser, the following message appears with instructions on how to manually start the login process.*  

```bash
Using a browser, open the following URL:  
https://my-sso-portal.awsapps.com/verify  

and enter the following code:  
QCFK-N451  
```

AWS SSO uses the code to associate the AWS SSO session with your current AWS CLI session. The AWS SSO browser page prompts you to sign in with your AWS SSO account credentials. This enables the AWS CLI (through the permissions associated with your AWS SSO account) to retrieve and display the AWS accounts and roles that you are authorized to use with AWS SSO.

Next, the AWS CLI displays the AWS accounts available for you to use. If you are authorized to use only one account, the AWS CLI selects that account for you automatically and skips the prompt. The AWS accounts that are available for you to use are determined by your user configuration in AWS SSO.

```bash
There are 2 AWS accounts available to you.
> DeveloperAccount, developer-account-admin@example.com (123456789011) 
  ProductionAccount, production-account-admin@example.com (123456789022)
```

Use the arrow keys to select the account you want to use with this profile. The ">" character on the left points to the current choice. Press ENTER to make your selection.

Next, the AWS CLI confirms your account choice, and displays the IAM roles that are available to you in the selected account. If the selected account lists only one role, the AWS CLI selects that role for you automatically and skips the prompt. The roles that are available for you to use are determined by your user configuration in AWS SSO.

```bash
Using the account ID 123456789011
There are 2 roles available to you.
> ReadOnly
  FullAccess
```

As before, use the arrow keys to select the IAM role you want to use with this profile. The ">" character on the left points to the current choice. Press <ENTER> to make your selection.

The AWS CLI confirms your role selection.

Using the role name "ReadOnly"

Now you can finish the configuration of your profile, by specifying the default output format, the default AWS Region to send commands to, and providing a name for the profile so you can reference this profile from among all those defined on the local computer. In the following example, the user enters a default Region, default output format, and the name of the profile. You can alternatively press <ENTER> to select any default values that are shown between the square brackets. The suggested profile name is the account ID number followed by an underscore followed by the role name.

```bash
CLI default client Region [None]: us-west-2<ENTER>
CLI default output format [None]: json<ENTER>
CLI profile name [123456789011_ReadOnly]: my-dev-profile<ENTER>
```

A final message describes the completed profile configuration.

To use this profile, specify the profile name using --profile, as shown:

```bash
aws s3 ls --profile my-dev-profile
```

The previous example entries would result in a named profile in ```~/.aws/config``` that looks like the following example.

```text
[profile my-dev-profile]
sso_start_url = https://my-sso-portal.awsapps.com/start
sso_region = us-east-1
sso_account_id = 123456789011
sso_role_name = readOnly
region = us-west-2
output = json
```

At this point, you have a profile that you can use to request temporary credentials. You must use the **aws sso login** command to actually request and retrieve the temporary credentials needed to run commands.

#### 2. Manual configuration

To manually add AWS SSO support to a named profile, you must add the following keys and values to the profile definition in the file ```~/.aws/config``` (Linux or macOS) or ```%USERPROFILE%/.aws/config``` (Windows).

- **sso_start_url**: The URL that points to the organization's AWS SSO user portal.  
```sso_start_url = https://my-sso-portal.awsapps.com/start```
- **sso_region**: The AWS Region that contains the AWS SSO portal host. This is separate from, and can be a different ```region``` than the default CLI region parameter.  
```sso_region = us-west-2```
- **sso_account_id**: The AWS account ID that contains the IAM role that you want to use with this profile.  
```sso_account_id = 123456789011```
- **sso_role_name**: The name of the IAM role that defines the user's permissions when using this profile.  
```sso_role_name = ReadAccess```

The presence of these keys identify this profile as one that uses AWS SSO to authenticate the user.

You can also include any other keys and values that are valid in the ```.aws/config``` file, such as region, output, or s3. However, you can't include any credential related values, such as **role_arn** or **aws_secret_access_key**. If you do, the AWS CLI produces an error.

So a typical AWS SSO profile in ```.aws/config``` might look similar to the following example.

```text
[profile my-dev-profile]
sso_start_url = https://my-sso-portal.awsapps.com/start
sso_region = us-east-1
sso_account_id = 123456789011
sso_role_name = readOnly
region = us-west-2
output = json
```

At this point, same as automatic config, you have a profile that you can use to request temporary credentials. However, you can't yet run an AWS CLI service command. You must first use the aws sso login command to actually request and retrieve the temporary credentials needed to run commands.
Next section will tell you how to use AWS SSO named profile.