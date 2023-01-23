---
layout: default
title: Docker
nav_order: 2
parent: User Guides
has_children: true
has_toc: false
---

# Docker

Docker is a tool designed to make it easier to create, deploy, and run applications by using containers. Containers allow a developer to package up an application with all of the parts it needs, such as libraries and other dependencies, and ship it all out as one package. By doing so, thanks to the container, the developer can rest assured that the application will run on any other Linux machine regardless of any customized settings that machine might have that could differ from the machine used for writing and testing the code.

Docker has developed an easy process for installing Docker providing the ability to build and share your containerized applications. Whether you install Docker on a macOS, Linux or Windows platform, Commandeer assists you in this process and provides insight into the Docker Installation process status.

## Docker Installation

You can use Commandeer for managing your cloud resources without having Docker running. That being said, if you would like to use LocalStack, you'll need to have Docker installed and running on your machine. Commandeer also displays the status of your Docker process for better visibility.

### Install Docker on macOS

There are multiple ways to install Docker on your machine, we recommend using Docker for Mac desktop application. The installation is straightforward and it's developed by Docker itself. You can [download](https://docs.docker.com/desktop/install/mac-install/) Docker for Mac from DockerHub.

### Install Docker on Linux

After you download and install Docker using the [repository method](https://docs.docker.com/engine/install/ubuntu/) you'll need to follow these [post-install instructions](https://docs.docker.com/engine/install/linux-postinstall/) to add the Docker user to the group. This will allow you to run Docker from the command line without using the sudo

### Install Docker on Windows

Installing Docker on Windows requires running Windows Professional Edition which comes with Hyper-V enabled. [Download](https://docs.docker.com/desktop/install/windows-install/) and install Docker Desktop for Windows from DockerHub. Make sure to keep the Hyper-V option on during the installation. Then start Docker by double-clicking on the shortcut created on your desktop.

![Docker](/assets/images/docker.png)

