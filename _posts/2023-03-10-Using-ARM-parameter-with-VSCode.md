---
title:  "Using ARM parameters in VS Code"
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

> Note: 
> This article highlights the usage with VS Code. For more information on Parameters please check out the official documentation.
> [Create Resource Manager parameter file](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/parameter-files)

> Note: 
> You should also be aware that the parameter file stores parameter values in clear text. This is not a secure way to handle sensitive values like passwords. If you need to pass a parameter with a sensitive value, you should: store the value in a key vault. Then, use a reference to the key vault in your parameter file. This way, the sensitive value is safely retrieved during deployment.
> [Key Vault parameter](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/key-vault-parameter?tabs=azure-cli)

## Add parameters on a template
<!--add steps-->
Continueing from the storage account template from the [previous article](https://tommyshau.com/azure/Create-ARM-templates-using-Visual-Studio-Code/), we start by adding a carriage return on the "parameters" block and type ", and then selecting the ````new-parameter```` , which will generate the desired snippet. 

> Note: VS Code will not be able to determine if a Parameter value is valid. The conditions for validity need to be defined in the template itself. Examples are name length on resource names or allowed values on SKUs. For further information please check the [public documentaiton on parameters](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/parameter-files).
![image-center]({{ site.url }}{{ site.baseurl }}/assets/pics/parameter-vscode-03.png){: .align-center}

To use parameters in the template, replace any value on the "resources" bracket wtih ````[parameters('foo')]````.
If the naming of the parameters are accurate, VS Code will auto-suggest fitting parameters. 
As a universal tool ````CTRL + SPACE```` and ````TAB```` can also be used to get suggestions and quickly fill the template.

![image-center]({{ site.url }}{{ site.baseurl }}/assets/pics/parameter-vscode-01.gif){: .align-center}
## Create a paremeter file

With an ARM template parameter file, you can keep parameter values that are specific to different environments and use them on one and the same ARM template when you deploy. 
On VS Code, the generation of a template can be done by right-click on the code editor and ````Select/Create Parameter File...````

![image-center]({{ site.url }}{{ site.baseurl }}/assets/pics/parameter-vscode-01.png){: .align-center}
The default naming convention is  *template-name*.**parameters**.*json*. This is helpful to get a link between parameterfile and the corresponding ARM template. If different parameter files should be used for the same template, like in a scenario of development and production environment, then you can the parameter like **deploy.dev-parameters.json** and **deploy.prod-parameters.json**. 

Following image shows how the resulting parameter file looks like. 
The parameter file is mapped to the corresponding template and VS code will also validate both files together. If the parameter file is not matching the defined criteria of the template (e.g. "minLength" & "maxLength"), an error message will show up. 
![image-center]({{ site.url }}{{ site.baseurl }}/assets/pics/parameter-vscode-02.png){: .align-center}


## Deploy the template

Add **-TemplateParameterFile** to the Powershell command to make use of the parameter file.

```
New-AzResourceGroupDeployment -ResourceGroupName arm-vscode -TemplateFile ./deploy.json -TemplateParameterFile ./deploy.parameters.json
```



> Note: 
> This article highlights the usage with VS Code. For more information on Parameters please check out the official documentation.
> [Create Resource Manager parameter file](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/parameter-files)

> Note: 
> You should also be aware that the parameter file stores parameter values in clear text. This is not a secure way to handle sensitive values like passwords. If you need to pass a parameter with a sensitive value, you should: store the value in a key vault. Then, use a reference to the key vault in your parameter file. This way, the sensitive value is safely retrieved during deployment.
> [Key Vault parameter](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/key-vault-parameter?tabs=azure-cli)
