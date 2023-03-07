---
layout: default
title: Okta and AWS SSO
grand_parent: User Guides
parent: AWS
nav_order: 2
---

# Using Okta and AWS SSO

As the cloud continues to be relied upon by businesses, many companies are relying on Okta to help manage all the integrations between each service. For this discussion, we will be talking about how a developer can use the Okta to AWS SSO integration to efficiently access their AWS system locally on their desktop from Commandeer.

This example will assume you have a [chiclet for AWS SSO](https://aws.amazon.com/about-aws/whats-new/2020/05/manage-access-to-aws-centrally-for-okta-users-with-aws-single-sign-on/) setup in Okta.

## 1. Login to your Okta portal

This will give you access to all your company chiclets. Many companies will have quite a bit of services that are available to SSO into. This is really helpful, as your users will be able to redirect into the other service without having to login. Most major SaaS offerings large and small offer this feature.

![Okta Dashboard](/assets/images/okta/okta-login.png)

## 2. Click the AWS SSO Chiclet in your Okta portal

On the dashboard, you will be presented with the AWS SSO chiclet like below. Click it to get redirected into the corresponding AWS Account.

![Okta Dashboard](/assets/images/okta/okta-aws-chiclet.png)

## 3. Click the 'Command line or programmatic access' link

Once authenticated into the AWS Console, you will be presented with two different options. The first is the Management Console, which will take you into your system in the AWS Console within your browser. We want to connect via our computer however, so we will choose the second link, 'Command line or programmatic access'

![AWS SSO](/assets/images/okta/aws-sso.png)

Clicking this will then open up a modal.

## 4. Copy the contents of 'Option 2: Add a profile to your AWS credentials file'

You will be presented with a number of options for using your keys. In this case, we will use option 2.

AWS allows you to have a .aws/credentials file on your computer. This is normally located in the root of your user account on your computer. Add this profile to that file, or update your existing profile in there with the new credentials.

> You can learn more about AWS Credentials and Config [here](https://docs.aws.amazon.com/sdk-for-php/v3/developer-guide/guide_credentials_profiles.html).

![AWS SSO](/assets/images/okta/aws-sso-2.png)

## 5. Save this to your local .aws/credentials file

Open your credentials file or create one locally like below. This is where you can store all your AWS keys.

![Credentials File](/assets/images/okta/aws-creds.png)

Below you can see that we have an acme and an acme-dev profile inside our file. You can have many different profiles, and it makes it easier to manage them. Also take note that the top one has a session token. This is how access to important accounts should always be done, so that regardless if your keys are ever compromised, the usage will still be limited to a certain amount of time by requiring a short-lived session token.

![Credentials File Open](/assets/images/okta/aws-creds-display.png)

The token will be much longer when you copy it from the AWS Console, but the idea is that now you are storing these creds in one place on your computer.

## 6. Setup up your corresponding account in Commandeer

### 6a. Create a new Account in Commandeer

In Commandeer, you have one identity (under the hood we actually use [Auth0](https://auth0.com/), which was recently aquired by Okta). You can then have many accounts that are pointed either locally to LocalStack or to AWS. Each account might point to a different region in the same AWS Account, or point to a dev AWS account and a production AWS account for example.

Click the + button in the top left of the app to create your account, or edit an existing account by clicking the edit button.

![Account Select](/assets/images/okta/account-select.png)

In the modal that then appears. Select your profile from the dropdown. In this example, we are selecting the acme profile we just created.

![Profile Select](/assets/images/okta/profile-select.png)

Now your system is connected to AWS. You can verify it by going to one of your services that you have data in like S3 or DynamoDB, or go to the AWS Dashboard and view your system hollistcally.

![AWS Service Breakdown](/assets/images/okta/aws-service-breakdown.png)

### 6b. Auto-updating of an existing account in Commandeer

Now, that was quick and easy. But, guess what. Your DevOps team makes sure that there are not leaks into your AWS dev environment, so they make sure to kill your session after only 12 hours. So, when you come into the office tomorrow, you will need to repeat steps 1-5. But, you won't have to do anything in Commandeer.

Once you save the updated session token to your .aws/credentials file, simply open Commandeer, and you will be presented with a modal informing you that the token has changed.

![Session Token Changed](/assets/images/okta/session-token-changed.png)

Click the 'Yes' button and your system is now using the new token, and you can continue on building our your system.

Okta to AWS SSO is an excellent solution to managing AWS access for developers. In order to streamline this process, we have made the relationship between your .aws profiles in your credentials and config files tightly coupled with accounts in Commandeer. This means less time fumbling with keys, and more time building awesome things!
