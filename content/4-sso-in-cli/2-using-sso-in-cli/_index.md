+++
title = "Using AWS SSO in CLI"
date = 2020
weight = 2
chapter = false
pre = "<b>4.2 </b>"
+++
  
This section describes how to use the AWS SSO profile you created in the previous section.

**Contents**
- [1. Signing in and getting temporary credentials](#1-signing-in-and-getting-temporary-credentials)
- [2. Running a command with your AWS SSO enabled profile](#2-running-a-command-with-your-aws-sso-enabled-profile)
- [3. Signing out of your AWS SSO sessions](#3-signing-out-of-your-aws-sso-sessions)

#### 1. Signing in and getting temporary credentials
After you configure a named profile automatically or manually, you can invoke it to request temporary credentials from AWS. Before you can run an AWS CLI service command, you must retrieve and cache a set of temporary credentials. To get these temporary credentials, run the following command.
```shell
$ aws sso login --profile my-dev-profile
```

The AWS CLI opens your default browser and verifies your AWS SSO log in.
```shell
SSO authorization page has automatically been opened in your default browser. 
Follow the instructions in the browser to complete this authorization request.
Successully logged into Start URL: https://my-sso-portal.awsapps.com/start
```

If you are not currently signed in to your AWS SSO account, you must provide your AWS SSO user name and password.

If the AWS CLI can't open your browser, it prompts you to open it yourself and enter the specified code.
```shell
$ aws sso login --profile my-dev-profile
Using a browser, open the following URL:
 
https://my-sso-portal.awsapps.com/verify

and enter the following code:
QCFK-N451
```
The AWS CLI opens your default browser (or you manually open the browser of your choice) to the specified page, and enter the provided code. The webpage then prompts you for your AWS SSO credentials.

Your AWS SSO session credentials are cached and include an expiration timestamp. When the credentials expire, the AWS CLI requests you to sign in to AWS SSO again.

If your AWS SSO credentials are valid, the AWS CLI uses them to securely retrieve AWS temporary credentials for the IAM role specified in the profile.
```shell
Welcome, you have successfully signed-in to the AWS-CLI.
```

#### 2. Running a command with your AWS SSO enabled profile
You can use these temporary credentials to invoke an AWS CLI command with the associated named profile. The following example shows that the command was run under an assumed role that is part of the specified account.
```shell
$ aws sts get-caller-identity --profile my-dev-profile
{
    "UserId": "AROA12345678901234567:test-user@example.com",
    "Account": "123456789011",
    "Arn": "arn:aws:sts::123456789011:assumed-role/AWSPeregrine_readOnly_12321abc454d123/test-user@example.com"
}
```

As long as you signed in to AWS SSO and those cached credentials are not expired, the AWS CLI automatically renews expired AWS temporary credentials when needed. However, if your AWS SSO credentials expire, you must explicitly renew them by logging in to your AWS SSO account again.
```shell
$ aws s3 ls --profile my-sso-profile
Your short-term credentials have expired. Please sign-in to renew your credentials
SSO authorization page has automatically been opened in your default browser. 
Follow the instructions in the browser to complete this authorization request.
```

You can create multiple AWS SSO enabled named profiles that each point to a different AWS account or role. You can also use the aws sso login command on more than one profile at a time. If any of them share the same AWS SSO user account, you must log in to that AWS SSO user account only once and then they all share a single set of AWS SSO cached credentials.

```text
# The following command retrieves temporary credentials for the AWS account and role 
# specified in one named profile. If you are not yet signed in to AWS SSO or your 
# cached credentials have expired, it opens your browser and prompts you for your 
# AWS SSO user name and password. It then retrieves AWS temporary credentials for
# the IAM role associated with this profile.
$ aws sso login --profile my-first-sso-profile

# The next command retrieves a different set of temporary credentials for the AWS 
# account and role specified in the second named profile. It does not overwrite or 
# in any way compromise the first profile's credentials. If this profile specifies the
# same AWS SSO portal, then it uses the SSO credentials that you retrieved in the 
# previoius command. The AWS CLI then retrieves AWS temporary credentials for the
# IAM role associated with the second profile. You don't have to sign in to 
# AWS SSO again.
$ aws sso login --profile my-second-sso-profile

# The following command lists the Amazon EC2 instances accessible to the role 
# identified in the first profile.
$ aws ec2 describe-instances --profile my-first-sso-profile

# The following command lists the Amazon EC2 instances accessible to the role 
# identified in the second profile.
$ aws ec2 describe-instances --profile my-second-sso-profile
```

#### 3. Signing out of your AWS SSO sessions
When you are done using your AWS SSO enabled profiles, you can choose to do nothing and let the AWS temporary credentials and your AWS SSO credentials expire. However, you can also choose to run the following command to immediately delete all cached credentials in the SSO credential cache folder and all AWS temporary credentials that were based on the AWS SSO credentials. This makes those credentials unavailable to be used for any future command.
```shell
$ aws sso logout
Successfully signed out of all SSO profiles.
```
