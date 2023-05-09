---
title:  "Using Arm parameters in VS Code"
last_modified_at:   2023-03-10 00:31:55
categories: 
  - Azure
tags:
  - Azure
  - VS Code
  - ARM
description: "Quick Tutorial on how to create ARM templates using Visual Studio Code part 2"

toc: true
toc_label: "Getting Started with ARM"
---

As a continuation of [Create ARM templates using VS Code](https://tommyshau.com/azure/Create-ARM-templates-using-Visual-Studio-Code/), I want to add how to add parameters in ARM templates through VS Code.

##Add parameters on a template
<!--add steps-->
##Create a paremeter file

With an ARM template parameter file, you can keep parameter values that are specific to different environments and use them together when you deploy. For example, you can have one parameter file with values for a test environment and another one with values for a production environment.

<!--add steps-->

Add '-TemplateParameterFile' to the Powershell command to make use of the parameter file.

'''New-AzResourceGroupDeployment -ResourceGroupName arm-vscode -TemplateFile ./deploy.json -TemplateParameterFile ./deploy.parameters.json'''

Note: 
https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/parameter-files

Note: 
You should be aware that the parameter file stores parameter values in clear text. This is not a secure way to handle sensitive values like passwords. If you need to pass a parameter with a sensitive value, you should: store the value in a key vault. Then, use a reference to the key vault in your parameter file. This way, the sensitive value is safely retrieved during deployment.
https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/key-vault-parameter?tabs=azure-cli
