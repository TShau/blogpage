---
layout: post
title:  "Create-Arm-Templates-Using-Visual-Studio-Code"
date:   2023-03-04 09:00:07
categories: Azure
description: "Quick Tutorial on how to create ARM templates using Visual Studio Code"

published: true
---
<!--write an introduction to a blog-->
In this article, you learn how to create an ARM template using Visual Studio Code. You learn how to create an ARM template from scratch, and how to use the Azure Resource Manager Tools for Visual Studio Code to create an ARM template. You also learn how to use the Azure Resource Manager Tools for Visual Studio Code to validate and deploy an ARM template.

You will need to install the Azure Resource Manager tools extension on VS code before you begin.
You can use Visual Studio Code to author and validate ARM templates. The Azure Resource Manager Tools extension for Visual Studio Code provides the following features:

* Syntax highlighting for ARM template files
* Code snippets for common ARM template resources
* IntelliSense for resource properties, functions, and parameters
* Resource property completion
* Resource property validation
* ARM template validation
* ARM template deployment

Another prequisity to author ARM templates is that you have the Azure CLI or Azure PowerShell module installed. You can use either the Azure CLI or Azure PowerShell module to deploy ARM templates. In this article, you use the Azure CLI.

<!--rewrite below text-->

Here are some steps you can follow to use ARM templates on VS Code:

Create an ARM template by creating and opening a new file named azuredeploy.json with Visual Studio Code.
Enter “arm” into the code editor, which initiates Azure Resource Manager snippets for scaffolding out an ARM template.
Select “arm!” to create a template scoped for an Azure resource group deployment.
Add an Azure resource by using snippets for many Azure resources included in the extension.
Completion and validation is one of the most powerful capabilities of the extension with its integration with Azure schemas.
Add template parameters.
Create a parameter file.
Deploy the template.
Clean up resources.
