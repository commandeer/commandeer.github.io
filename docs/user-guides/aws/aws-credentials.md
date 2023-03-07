---
layout: default
title: AWS Credentials
grand_parent: User Guides
parent: AWS
nav_order: 1
---

# AWS Credentials

We are always modifying our credentials and config files. And with Commandeer, we actually allow you to drive your Commandeer accounts with the files. Meaning that you can use session tokens, assume roles, and other features driven by the files. In order to manipulate this file, we were always jumping back into the finder and a text editor. This is fine for working with one project, but starts to get cumbersome for many.  Under the AWS menu item, you can click on the .aws/credentials menu item.

![.aws/credentials](/assets/images/credentials/aws-creds-nav.png)

Once there, you can see the full list of your profiles.

![.aws/credentials list](/assets/images/credentials/aws-creds.png)

Green means that the profile seems to be configured correctly, and is connected to a Commandeer account. If you see a warning, there are a couple different reasons you might be seeing it.

- A profile in your credentials file does not match one in Commandeer
- There are duplicate profiles in your credentials file that have the same keys

There are also two more sections in the navigation as well.

1. Assume Role Profiles - these are assume role setups inside the config file, where a profile has a source_profile and a role_arn, so that when using them, they actually assume a role, and get fresh keys based on the parent keys.

2. Dangling Configs - these are profiles in your config file that don't have a corresponding profile in the credentials file.

![.aws/credentials roles](/assets/images/credentials/roles.png)

Clicking into a profile, you can then see a nice breakdown of of the keys associated with it.

![.aws/credentials profile](/assets/images/credentials/creds.png)

If you want to make edits to the configuration, you can press the File Editor menu item, and edit in a monaco editor.

![.aws/credentials edit](/assets/images/credentials/file-edit.png)

Lastly, if you do not have a credentials and config file setup on your computer. We have that covered too. Go to the credentials page, and we will give you the option of setting one up.

![.aws/credentials zero state](/assets/images/credentials/creds-zero-state.png)

## Obtaining AWS Credentials

To obtain AWS access keys from AWS, follow these steps:

1. Sign in to the AWS Management Console and open the IAM console.
2. In the navigation pane, choose "Users."
3. Select the IAM user for whom you want to create access keys.
4. Choose the "Security credentials" tab.
5. In the "Access keys" section, choose "Create access key."
6. To see the new access key, choose "Download .csv file." The CSV file includes the access key ID and secret access key.
7. Keep the access key ID and secret access key in a secure location. You will not be able to see the secret access key again after this step.

> Note that access keys provide programmatic access to AWS resources, and you should treat them like a password. Keep them secret and secure, and do not share them with anyone.

## Assume Role access to AWS

The concept of assuming a role in AWS is pretty straightforward. You as a developer will have your IAM user with access keys, but this user will not have access to any resources. Your sysadmin will then give you access to different roles in the system. For instance, you might get access to a lambda role that allows you to view lambdas and the services they talk to like S3 or DynamoDB.

Your main user access keys need to be setup in the .aws/credentials file, and then the roles are in the .aws/config file. You can see an example of this below.

![Assume Role Credentials](/assets/images/credentials/assume-role-credentials.png)

The top is the keys that will be used to assume the role, your user keys. In the bottom section, you can see that there is a lambda-role-connection profile. This has a reference to commandeer-dev-base via the source_profile. It also contains the role__arn of the role you would like to assume.

In Commandeer, when you create an account to connect to your system, you will be able to select these. Below you can see the Edit Account dialog.

![Edit Account Assume Role](/assets/images/credentials/edit-account-assume-role.png)

By selecting the top profile, it will automatically populate the keys. And if there are roles associated with the profile, then the assume role will be populated. Now, once saved, in the top of the app, you can see that now you are able to select a role to assume.

![Select Assume Role](/assets/images/credentials/assume-role-select.png)

Under the hood, we use AWS STS (Security Token Service). It takes in your base keys, and the role arn you want to connect to, and then gives you back new keys, and a session token. These are short lived keys, so it also let's you know when they will expire.

You can view these all on the account detail page.

![Commandeer Account Dashboard](/assets/images/credentials/commandeer-account-dashboard.png)

Now, this account in Commandeer will use the assume role keys, and voila, you will be able to see your system.
