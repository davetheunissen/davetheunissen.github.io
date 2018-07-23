---
layout: post
title: "Deploy and configure an Azure Container Registry"
excerpt: "Learn how to deploy and configure an Azure Container Registry"
tags: [Azure Container Registry, Docker, Containers, Azure]
share: true
---

## What you will learn

In this post you will learn how to provision a new Azure Container Registry instance & publish a Docker image to the registry.

## What you will need

To follow along with this post you will need;

- [Microsft Azure Account](https://azure.microsoft.com/en-us/free/)
- [Azure CLI 2.0](http://)
- [Docker CLI](http://)

This post uses the [Azure Cloud Shell](https://shell.azure.com/) which already has the Azure and Docker CLIs pre-configured.

If you are not that comfortable with the command line, the [Azure Portal](https://portal.azure.com) provides a rich user experience that is a really great tool for quickly setting up Azure resources however this post won't be covering the portal.

### Provision Azure Container Registry

To get started, go ahead and launch the Azure Cloud Shell.

[![Launch Cloud Shell](https://shell.azure.com/images/launchcloudshell.png "Launch Cloud Shell")](https://shell.azure.com)

If you are running these scripts from your machine, you will need to authenticate with Azure first.

```azurecli-interactive
az login
```

### Create a new Resource Group

If you don't already have a resource group setup, you can create one as follows.

```bash
location="WestUS"
az group create --location $location --name <YourResourceGroupName>
```

`--location` - The region this resource group will reside in. (I've used `WestUs` here but you can set this to anything you prefer)

`--name` - The name of your resource group.

### Create a new Azure Container Registry

```bash
az acr create --name <YourResourceName> --resource-group <YourResourceGroupName> --sku Basic
```

`--name` - The name of your ACR instance. (Must be alphanumeric with a minimum of 5 characters)

`--resource-group` - The name of your resource group

`--sku` - The tier of your resource. (Stock Keeping Unit)

Running the following will output details of your new ACR instance and thats it all there is to it for now.

```bash
az acr list
```

### Part 2 - Publish Docker Image to ACR