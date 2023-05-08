---
title:  "Create Arm Templates with Visual Studio Code"
last_modified_at:   2023-03-04 09:00:07
categories: 
  - Azure
tags:
  - Azure
  - VS Code
  - ARM
description: "Quick Tutorial on how to create ARM templates using Visual Studio Code"

toc: true
toc_label: "Getting Started with ARM"
---

In this article, you learn how to create an ARM template using Visual Studio Code. You learn how to create an ARM template from scratch, and how to use the Azure Resource Manager Tools for Visual Studio Code to create an ARM template. You also learn how to use the Azure Resource Manager Tools for Visual Studio Code to validate and deploy an ARM template.

## Prequisities 
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


## Using VS code for creating resources

Here are some steps you can follow to use ARM templates on VS Code:

Create the ARM template by creating a new file named deploy.json with Visual Studio Code.
Enter 'arm' into the code editor, which shows you options for generating a basic building block of an ARM template.

![image-center]({{ site.url }}{{ site.baseurl }}/assets/pics/vs-arm-01.png){: .align-center}
Select 'arm!' for a regular ARM template. 
Next, we will create a storage account as an example. Go to the "resources" block and type 'storage'. Notice that the VS extension will offer snippets that can be used to quickly generate the barebone of a resource. In this case, we select 'arm-storage'. 

![image-center]({{ site.url }}{{ site.baseurl }}/assets/pics/vs-arm-02.png){: .align-center}
## Completion and validation

The ARM tools Extension offers integration with Azure schemas, which provide completion and validation capabilities. 
E.g. if you were to write a invalid value on the attribute 'kind', you will get a warning indication and you will get a message box by hovering the cursor on it. 

![image-center]({{ site.url }}{{ site.baseurl }}/assets/pics/vs-arm-04.png){: .align-center}
To use the completion capbabilities, you can use the hotkey ctrl + space. 
Leveraging that is to be useful when it comes to writing the template in a fast and failsave manner.

![image-center]({{ site.url }}{{ site.baseurl }}/assets/pics/vs-arm-03.png){: .align-center}
## Deploy the template
Deployment in VS code is done quickly by opening the integrated terminal. A requirement here is the Azure PowerShell module or the Azure CLI module. 

```ruby
New-AzResourceGroup -Name test-RG -Location eastus
New-AzResourceGroupDeployment -ResourceGroupName test-RG -TemplateFile ./deploy.json 
```

