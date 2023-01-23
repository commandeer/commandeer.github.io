---
layout: default
title: Overview
nav_order: 1
---

# Overview

Commandeer is a desktop IDE used to manage AWS, LocalStack, and Docker. It gives you to work in a clean UI to manage many cloud services. Commandeer is a bottom up solution, meaning you can go down to the granular level for everything. For example, you can search for a file in S3, look up a record in DynamoDB, PostgreSQL, or Athena, or see CloudWatch Logs for a Lambda Invocation that you just invoked.

![Commandeer](/assets/images/commandeer-system-diagram.png)

While other tools take a top down approach where you can see high level pieces of information, but once you actually try to manage your system, you quickly realize it is not for you. What differentiates other IDE's from Commandeer is that we provide a true interface into your services. Most IDE's have extensions that you can supposedly see things like Lambda with, but once you start to work with them, you will notice that they don't have all the complex interconnections between services that are crucial to managing your system.

Visualize your lambda connections and the interactions between them. Advanced event runners for SQS, SNS, API Gateway, DynamoDB Streams, S3 files and more, let you actually run the event, and view the triggered Lambda's invocation logs. If you are connected to LocalStack you can also view the Docker Containers logs. You can also invoke a Lambda directly to test your code. This is one of the most important aspects of Commandeer. Rather than having to deal with running these things on the Web or in the CLI, you can now easily do them in an IDE.



