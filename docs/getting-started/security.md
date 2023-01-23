---
layout: default
title: Security
parent: Getting Started
nav_order: 4
---

# Security

At Commandeer we take security seriously. Many companies are built on ingesting data, but our mantra is that we don't want your data.  This is a very important fact about how Commandeer is setup. Because it is a desktop app, under the hood, we are able to use local SDKs and Docker running on your machine. The calls to the services you are using, like AWS, happen between your local computer and your cloud. We never store your data or your keys on our servers. This is a very important fact, and can not be understated.

By having the system set up this way, you or your dev ops department can best manage your system security. You might be running on a VPN, or run Commandeer on a VM. However you choose to do it, you can then rest assure, that your data is not being transmitted out to our systems.

## User Authentication

We chose to use Auth0 to handle our SSO system. We feel that they are the best service out there to handle single sign-on, and have great SDKs to integrate into both our desktop app and web portal.

{: .highlight }
We recommend using the GitHub style of having one personal user account with Commandeer, and then belonging to one or more teams. This works especially well if you are a consultant or freelancer.

This single user then enables us to have you authenticated into the website for managing your profile and plan information. And in the app, this enables you to authenticate in to use Commandeer. Having a single SSO user, and getting it right was very important for us. We have personally used many products, that once you have to switch between companies, it is very cumbersome.

## Subscription

We chose to use Stripe to handle our subscriptions. They not only have the best API to make integration a snap for our developers, but they also provide a complete billing portal, so that you can manage your subscription, see your past invoices, and have piece of mind that your credit card information is safely stored.

## Your Data

When you connect to an AWS account and view all your services and resources, we pull that down directly from AWS to your machine via the app on your computer. It never goes to our servers. It is then intelligently cached locally so that you don't incur extra costs for retrieving data. Also, things like S3 and DynamoDB data pulls are only done on-demand, when you access an actual file on S3 for instance. And whenever possible, we only bring back the pointer to the files, not all the actual file data.

Again, this data never goes to our servers. It is just passed between your cloud provider and your local computer. You can also see all the data stored by Commandeer very easily by going to the help menu, and opening up the local files. Under the hood, Commandeer is using a file based data lake for all local data.

## Your Keys

Your keys are stored on your machine, but never on our servers. For AWS, to heighten security, we recommend using a short-lived token as well. But for dev accounts, having long-lived keys is usually fine. You should always be very careful with your keys, and not pass them to anyone in plain text. For tools like LocalStack, you don't even need keys, which is one of the great features of it, that you get an AWS environment running locally.

The keys are stored in a json file, and any calls to the service, be it AWS, SendGrid, Algolia, etc. use the keys. Again, because this is a desktop app, we are able to utilize server level SDK's, allowing your computer to interact with the services in the best ways possible.

## Usage Analytics

We do store usage analytics for page views and button presses to our servers. This data is currently used in two ways, and soon will be used in two more ways.

The first way it has been used over the last two years is to help determine what to build next. By seeing what you are using, we are better able to focus our dev time on building out those services or streamlining certain processes. This has been invaluable.

Secondly, we show you your page and button analytics, so you can see what you have been working on. Even when working on features for Commaneer, it is interesting to see how I am using the system.

In the next few months, we will start to provide you with more content around services you might be using or may want to explore. We will also begin to summarize usage stats across a whole team. So, you or your manager can start to see who is working on what parts of the system, and to help better calculate how long something might take to build or where to put more resources on to help in certain areas.

## Production System

Can you connect to production systems with Commandeer? Yes. Should you? Maybe. The real power of Commandeer is the ability to view, manage, and update your infrastructure and data at the local and development level. You can certainly use it to connect to production, but in most of the systems that we have worked on in the past, production is really locked down. This is especially true at larger organizations.

Commandeer really shines when you are deploying some code with the Serverless runner, and then testing it with our Lambda Invoke Runner. Or when you are saving data to DynamoDB, and then viewing the Lambda Invocation logs.

If you do want to connect to a production environment for AWS. We recommend using short-lived tokens, so that your access is limited. Within the app, we let you mark an account as production, which will then give you a big banner at the top of the app, when you switch to it. We always try to get in and out of production as quickly as possible, only going in under the hood when something is a problem. Otherwise, we really only want to see production via API's or web portals.

## ARN Obfuscation

AWS is built entirely n the concept that all services talk to other services via proper API's. There are no back doors in AWS land. They use what is called an arn to do this, which is basically just an endpoint like http://, but instead it is arn://. Ths one thing with this is that your account number is passed in through this url. And thus, while not exposing your passwords to your system, you are exposing the account number. Inside our app, we obfuscate this whenever possible. You will see *** in locations that show this, and you can click a button to view or copy this url. Just remember, this is important data, so you do not want to share it with people.