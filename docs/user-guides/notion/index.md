---
layout: default
title: Notion
nav_order: 3
parent: User Guides
has_children: true
has_toc: false
---

# Notion

Notion is a comprehensive documentation system that has gained popularity in recent years due to its versatility and user-friendly interface. It is a software application that allows individuals and teams to organize and collaborate on various projects and tasks. Notion's unique approach to documentation combines the features of note-taking, project management, and knowledge management into a single platform. With its customizable templates and intuitive drag-and-drop interface, users can easily create and organize notes, tasks, wikis, databases, and more. In this way, Notion has become a go-to solution for individuals and teams seeking a streamlined and efficient way to manage their work and stay organized.

With the Commandeer integration into Notion, you can instantly send all your resources into your documentation system quickly and easily.  This can then be used to allow your whole company to document, comment, and understand your true system.  If yhou are also using the scrum board system within Notion, you can easily tag resources such as Lambda's or DynamoDB tables from within a ticket, making it more powerful than ever to track how your changes to the system effect the actual resources in AWS.

## Helpful Links

- [Notion Home Page](https://notion.so?utm_source=commandeer "Notion is the connected workspace where better, faster work happens.")

## Setting up the integration

### Step 1 - Setup an integration on Notion

In order to connect to Notion from Commandeer, you need to first setup an [integration](https://www.notion.so/my-integrations) on Notion.  This allows you to obtain a secret token, that will be needed.  You can name the integration anything you want, the only real requirement is that you give it read, update, and insert permissions.

![Notion Integration](/assets/images/notion/commandeer-aws-export-notion-integration.png)

> Note the integration token above, you will need that when connecting from Commandeer.

Below you can see te permissions that you can give it.  Currently, the Commandeer integration does not have comments enabled, but will shortly, so I would suggest enabling it.

![Notion Integration](/assets/images/notion/notion-integration-capabilities.png)

### Step 2 - Create a main page for your AWS documentation

Now, in order for Commandeer to connect to Notion, you will need to enable this integration on a page in Notion.  So firstly, just create a page.  In this case we called the page Commmandeer Dev Environment Export.  But you can call it whatever you want.  Then in the top right ellipsis, go down to Connections, and press 

![Notion Integration Page](/assets/images/notion/commandeer-aws-export-notion-page.png)

With that selected, look in your url bar on your browser, and take note of the page id. This page id along with your token from step 1 is what you will need to access Notion from within Commandeer.

![Notion Page Id](/assets/images/notion/notion-page-id.png)

### Step 3 - Enter your secret token and page Id into Commandeer

We will assume that you have Commandeer installed on your computer.  If you have not, please head over to our [getting started](https://commandeer.github.io/docs/getting-started/) guide or [download](https://app.getcommandeer.com/download) the app now.

Once setup, make sure to connect to the AWS account you want to use.

> We recommend connecting to your dev or staging environment for this rather than directly to production.

On the left-hand side of the app, you can see the Notion menu item.  Select that and then you can press the settings button to bring up the dialog to add your Page Id and Token from steps 1 and 2.

![Notion Settings](/assets/images/notion/commandeer-notion-settings.png)

With these added, you will then be presented with a button to export your system.Currently, we allow you to export CloudFormation, CloudWatch Logs, DynamoDB, Lambda, and S3.  We will be adding support for more services shortly.

![AWS Notion Export](/assets/images/notion/aws-notion-export.png)

Press the button and you will see the dialog to select which resources you want to export.

![AWS Notion Export](/assets/images/notion/notion-export.png)

Press the export button, and Boom!, your entire system is now in Notion.  As you can see below, this is really handy!

![AWS Export](/assets/images/notion/aws-commandeer-notion-export.gif)

### Step 4 - Checkout your newly created docs

![AWS Notion Dashboard](/assets/images/notion/aws-export-notion-dashboard.png)

You can see that there are separate pages for each resource in the Notion database.  Drilling into the Lambdas page, you can then see that there is every Lambda in your system.

![AWS Lambdas](/assets/images/notion/aws-export-lambdas.png)

It containes import information as properties for each lambda, and then when you drill into a particular Lambda, you can see that it shows tags, environment variables, and what might trigger the Lambda, for example, the API Gateway, or a DynamoDB stream.

![AWS Lambda](/assets/images/notion/aws-export-lambda-example.png)

## Conclusion

Having a powerful documentation system for you system is difficult.  While having docs related to your code base is helpful for developers, bringing your AWS system out of the cloud and onto everyone in your companies laptops is an amazing way to get the entire company understanding what is being built.  Stay tuned as we continue to expand on this concept by adding the ability to comment on lambda's from within Commandeer, send CloudWatch Log invocation log samples directly to Notion, and much much more.  






