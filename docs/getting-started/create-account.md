---
layout: default
title: Managing Commandeer Accounts
parent: Getting Started
nav_order: 3
---

# Managing Commandeer Accounts

There are two different types of accounts in Commandeer. The first is a local account, which connects to LocalStack instead of directly to AWS. This let’s you run all your AWS services locally. The second is a cloud account, which connects directly to AWS.

There are two different use cases that we have run across in this type of setup. The first is if you are running a development and production in the same AWS account but in different regions. You would either set this up as having two Commandeer Account called something like `my-company-dev` and `my-company-prod` where dev is in US West 1 and prod is in US East 1. You would then not need to switch between regions in the top section, but just switch accounts.

Alternatively, you could just setup one account called `my-company`. And then switch between US West 1 and US East 2 in the top section. 

Both ways are valid, and it is more of a personal preference as to how you would like to operate. Also remember, there are a few services like IAM and S3 that are actually global, so the users, roles, groups, and S3 buckets will show up regardless of which region you select.

If you are a developer that works for multiple clients, or have multiple environments, this setup can be very helpful. Let’s say you use Dynamo, S3, and Lambda for a system you have built. You can then add an account called acme-dev that uses keys to connect to the AWS development accounts. You can also then connect your staging environment as another account named acme-stg that has keys to a staging environment for AWS.

The third setup in this situation could then be acme-lcl which if it is set to Local, it will point all AWS services to LocalStack to a copy of the AWS system. 

## Setting up Accounts
There are 5 ways to create accounts in Commandeer.  You can begin the process by pressing the `+` button in the top left of the app.

![Commandeer](/assets/images/add-commandeer-account.png)

### Create LocalStack Account

This allows you to connect to a running instance of LocalStack in a Docker Container. This allows full mocking of AWS on your local machine.

### Create AWS Account

You can enter in your AWS credentials and get underway, by connecting directly to your AWS account via Commandeer.

### Import account.json file

You can also upload the account.json file from someone else's Commandeer account. This can be handy to let someone be connected to their system the same way you are.  

> Always be careful when sharing these files, as they do contain keys to your system.

### Import .aws/credentials

The way most peoople who use the AWS cli or sdk's is to have a .aws/credentials with credentials that they use to connect.  We allow you to import and synchronize your credential profiles directly with your Commandeer accounts.  We also provide a full IDE experience for managing these to make it easier.

### Link LocalStack Containers

If you come into Commandeer, and already have a running instnace of LocalStack that you are connected to, then this is an easy way to get it added into the system.

## Backing up your Commandeer Accounts to GitHub

Your account settings for each account you create in Commandeer is stored in flat file on your computer. You can go to the top right help icon in the app, to view the location of this directory. Below you can see the help menu, with a link to your data directory.

![Commandeer Help Menu](/assets/images/accounts/commandeer-help-menu.png)

Once you click on the Data Path link, it will open up your Finder or Windows Explorer. If you navigate to the accounts folder, you will see json files for each account that you have in Commandeer.

![Commandeer Data Folder](/assets/images/accounts/commandeer-data-folder.png)

Clicking into the folder will bring you to the json files.

![Commandeer Accounts Folder](/assets/images/accounts/commandeer-accounts-folder.png)

You can simply setup a repo in GitHub to track this folder. Because these files are stored in plaintext, you do want to be careful with this. We recommend not connecting to production through Commandeer, and if you must, we recommend using a Session Token so that your keys are short-lived. If we open that local account file, you can see the json data.

```
{
    "autoExecuteHistory": true,
    "isLocal": true,
    "isProduction": false,
    "id": "d9fa2188-7e9d-46d8-b8fc-062474727f1a",
    "name": "local",
    "createdAt": "2021-02-13T12:27:55.027Z",
    "algolia": {
        "applicationId": "",
        "apiKey": ""
    },
    "appSync": {
        "id": "408cd8d3-53a1-410f-979f-b1b4daabbee9"
    },
    "athena": {
        "id": "0629364f-4130-4663-81e1-f9e2eda21333",
        "s3OutputLocation": ""
    },
    "aws": {
        "localKey": "LOCAL",
        "id": "8f203d44-9c64-4c7d-a096-198421ad6c10",
        "region": "us-east-1",
        "accessKeyId": "NO_LOCAL_ACCESS_KEY_ID",
        "secretAccessKey": "NO_LOCAL_SECRET_ACCESS_KEY",
        "apigatewayEndpoint": "http://localhost:4566",
        "appSyncEndpoint": "http://localhost:4566",
        "billingEndpoint": "http://localhost:4566",
        "cloudFormationEndpoint": "http://localhost:4566",
        "cloudwatchEndpoint": "http://localhost:4566",
        "cloudwatchLogsEndpoint": "http://localhost:4566",
        "cloudwatchEventsEndpoint": "http://localhost:4566",
        "cognitoEndpoint": "http://localhost:4566",
        "dynamoEndpoint": "http://localhost:4566",
        "ec2Endpoint": "http://localhost:4566",
        "ecsEndpoint": "http://localhost:4566",
        "iamEndpoint": "http://localhost:4566",
        "lambdaEndpoint": "http://localhost:4566",
        "snsEndpoint": "http://localhost:4566",
        "sqsEndpoint": "http://localhost:4566",
        "s3Endpoint": "http://localhost:4566",
        "s3Prefix": ""
    },
    "dynamo": {
        "id": "96f11161-799d-4027-8a1a-1a4054b2b488",
        "autoLoadRelationshipData": false,
        "streamTesterTimeoutSeconds": 15
    },
    "postgres": {
        "id": "0e966c78-6a63-4f6e-b086-80ac230b6e0b",
        "host": "",
        "port": 5432,
        "initialDatabase": "",
        "username": "",
        "password": "",
        "type": "POSTGRES"
    },
    "sendgrid": {
        "apiKey": "",
        "fromEmailAddress": ""
    },
    "slack": {
        "token": ""
    },
    "twilio": {
        "accountSid": "",
        "authToken": "",
        "fromPhoneNumber": ""
    },
    "dockerCompose": {
        "environmentVariables": [],
        "id": "03826cde-1500-48c1-a77c-2b035b65fdb7",
        "verbose": false,
        "noAnsi": false,
        "tls": false,
        "tlsVerify": false,
        "skipHostnameCheck": false,
        "compatibility": false
    },
    "dockerExec": {
        "id": "56d18bb5-3768-49bc-89b3-a01b45ad8f50",
        "attachStdin": false,
        "attachStdout": true,
        "attachStderr": true,
        "tty": false,
        "environmentVariables": [],
        "privileged": false
    },
    "localstack": {
        "id": "39599bc2-af36-4b2b-b0bd-b7296fb63196",
        "autoRemove": false,
        "dockerImageName": "localstack/localstack:0.12.5",
        "dockerContainerId": "478b922708f7e6c607a3f27b6cbe38b39a9593f929df81c42c7240fccf259db3",
        "url": "http://localhost:4566",
        "environmentVariables": []
    }
}
```

> These files are never stored on our servers, they only exist in your environment, so how you want to back them up is up to you.
