+++
title = "AWS SSO in CLI"
date = 2020
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

#### Configuring the AWS CLI to use AWS Single Sign-On
{{% notice warning %}}
- The following feature is available only if you use AWS CLI version 2. It isn't available if you run AWS CLI version 1.  
- Đảm bảo rằng bạn đã thiết lập AWS SSO cho AWS Organization của mình. Nếu chưa hãy xem [Thiết lập AWS SSO]()
{{% /notice %}}

If your organization uses **AWS Single Sign-On (AWS SSO)**, your users can sign in to Active Directory, a built-in AWS SSO directory, or another iDP connected to AWS SSO and get mapped to an **AWS Identity and Access Management (IAM) role** that enables you to run AWS CLI commands. Regardless of which iDP you use, AWS SSO abstracts those distinctions away, and they all work with the AWS CLI.


**Contents**
1. [Configuring a named profile to use AWS SSO](./1-config-sso-in-cli/)
2. [Using an AWS SSO enabled named profile](./2-using-sso-in-cli/)