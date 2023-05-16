---
title:  "Working with Azure Policy with VS Code"
last_modified_at:   2020-08-04 09:27:07
categories: 
  - Azure
tags:
  - Azure
  - VS Code
  - Azure Policy
description: "Working with Azure Policy with VS Code"

toc: true
toc_label: "Getting Started with ARM"
---

This feature is still in preview mode, but it aims to make policy writing easier by allowing you to access alias properties within the resource or policy definition. I think it’s great to create policies in Visual Studio Code, especially since I can view my existing policy definitions from the tool itself.
Let’s try it out and see how our Azure policies look like.![image](https://github.com/TShau/blogpage/assets/17855499/997e20fc-524c-4bcc-b2ab-17632294c893)



1. Open Visual Studio Code.
2. From the menu bar, go to View > Extensions.
3. In the search box, enter Azure Policy.
4. Select Azure Policy from the search results, and then select Install.
5. Select Reload when necessary.
For a national cloud user, follow these steps to set the Azure environment first:
6. Select File > Preferences > Settings.
7. Search on the following string: Azure: Cloud
Select the nation cloud from the list:

## Find aliases for resource properties

On the Azure Resource Explorer on the left pane you will be able to find a tree of all of your Resource Groups along with their Resources. These resources will show you the JSON representation with all its property values. 
Hovering your cursor over the properties will disply the **Azure Policy alias** that you need to create your own policy definitions. 


For more information check the [public documentation](https://learn.microsoft.com/en-us/azure/governance/policy/how-to/extension-for-vscode)
