---
layout: default
title: Create Account
parent: Getting Started
nav_order: 3
---

# Create a Commandeer Account

There are two different types of accounts in Commandeer. The first is a local account, which connects to LocalStack instead of directly to AWS. This let’s you run all your AWS services locally. The second is a cloud account, which connects directly to AWS.

There are two different use cases that we have run across in this type of setup. The first is if you are running a development and production in the same AWS account but in different regions. You would either set this up as having two Commandeer Account called something like `my-company-dev` and `my-company-prod` where dev is in US West 1 and prod is in US East 1. You would then not need to switch between regions in the top section, but just switch accounts.

Alternatively, you could just setup one account called `my-company`. And then switch between US West 1 and US East 2 in the top section. 

Both ways are valid, and it is more of a personal preference as to how you would like to operate. Also remember, there are a few services like IAM and S3 that are actually global, so the users, roles, groups, and S3 buckets will show up regardless of which region you select.

If you are a developer that works for multiple clients, or have multiple environments, this setup can be very helpful. Let’s say you use Dynamo, S3, and Lambda for a system you have built. You can then add an account called acme-dev that uses keys to connect to the AWS development accounts. You can also then connect your staging environment as another account named acme-stg that has keys to a staging environment for AWS.

The third setup in this situation could then be acme-lcl which if it is set to Local, it will point all AWS services to LocalStack to a copy of the AWS system. 

## Local Account (Connection to LocalStack)

## Cloud Account (Connection to AWS)



