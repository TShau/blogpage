---
title:  "troubleshooting-azure-cloud-services-series"
last_modified_at:   2017-04-25 21:13:43
categories: 
  - Azure
  - Azure Cloud Service
tags:
  - Azure Cloud Service
description: "Troubleshooting Azure Cloud Service series"

toc: true
toc_label: "Azure Cloud Service"
---

Archived from https://learn.microsoft.com/en-us/troubleshoot/azure/cloud-services/dev-troubleshoot-series
https://learn.microsoft.com/en-us/archive/blogs/kwill/windows-azure-paas-compute-diagnostics-data

Cloud service is one of most popular Azure PaaS service among web developers. These blog series includes some of the common problems faced by the customers while dealing with cloud service and how to troubleshoot those issues using various tools and logs. This blog focuses on some more common scenarios that you may face while developing and deploying cloud service solution to Azure.

In order to simulate the issues we have developed three cloud service applications and below are the links for instructions that you need to follow to set up the labs for each application:

[Compressor](https://github.com/prchanda/compressor)

[Super Converter](https://github.com/prchanda/superconvertor)

[Visitor Tracker](https://github.com/prchanda/visitortracker)

Let's deep dive into the troubleshooting series on Azure Cloud Service:

[Scenario 1: An instance of ZipEngine role is looping between Restarting and Busy state throwing an unhandled exception.](https://learn.microsoft.com/de-DE/troubleshoot/azure/cloud-services/dev-zipengine-role-stuck-busy-restart)
[Scenario 2: AssemblyBinder role instances is throwing System.IO.IOException.](https://learn.microsoft.com/de-DE/troubleshoot/azure/cloud-services/dev-assemblybinder-role-instance-stuck-busy-restart)
[Scenario 3: Autoscale is not triggering for FileUploader role.](https://learn.microsoft.com/de-DE/troubleshoot/azure/cloud-services/dev-assemblybinder-role-instance-stuck-busy-restart)
[Scenario 4 : ProcessorEngine role is stuck in Busy state.](https://learn.microsoft.com/de-DE/troubleshoot/azure/cloud-services/dev-processorengine-role-stuck-busy-state)
[Scenario 5 : My website is throwing HTTP Error 503.](https://learn.microsoft.com/de-DE/troubleshoot/azure/cloud-services/dev-http-error-503-cannot-access-website)
[Scenario 6 : Can't RDP to only 'HealthMonitor' worker role instance.](https://learn.microsoft.com/de-DE/troubleshoot/azure/cloud-services/dev-connect-healthmonitor-worker-role-rdp)
[Scenario 7 : Can't access the website, although all role instances are in running state.](https://learn.microsoft.com/de-DE/troubleshoot/azure/cloud-services/dev-asp-net-signair-app-cannot-access)
[Scenario 8 : ASP.NET SignalR application is not working.](https://learn.microsoft.com/de-DE/troubleshoot/azure/cloud-services/dev-aspnet-signalr-application-not-work)
