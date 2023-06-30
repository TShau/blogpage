---
title:  "Finding Logs on Azure Cloud Services"
last_modified_at:   2017-04-25 21:13:43
categories: 
  - Azure
  - Azure Cloud Service
tags:
  - Azure Cloud Service
description: "Finding Logs on Azure Cloud Services"

toc: true
toc_label: "Azure Cloud Service"
---


Troubleshooting Azure Cloud Services on Plattform level can be quite overwhelming, as there are a multitude of logs that can be checked. 
This is a list of the logs location that are most commonly used for troubleshooting Plattform-as-a-Service issues.
[For reference](https://learn.microsoft.com/en-us/archive/blogs/kwill/windows-azure-paas-compute-diagnostics-data)
<!--TODO Bulletpoints-->
**Windows Azure Event Logs** – Event Viewer –> Applications and Services Logs –> Windows Azure
Contains key diagnostic output from the Windows Azure Runtime, including information such as Role starts/stops, startup tasks, OnStart start and stop, OnRun start, crashes, recycles, etc. 
This log is often overlooked because it is under the “Applications and Services Logs” folder in Event Viewer and thus not as visible as the standard Application or System event logs. 
This one diagnostic source will help you identify the cause of several of the most common issues with Azure roles failing to start correctly – startup task failures, and crashing in OnStart or OnRun.
Captures crashes, with callstacks, in the Azure runtime host processes that run your role entrypoint code (ie. WebRole.cs or WorkerRole.cs).

**Application Event Logs** – Event Viewer –> Windows Logs –> Application
This is standard troubleshooting for both Azure and on-premise servers.  You will often find w3wp.exe related errors in these logs.

**App Agent Runtime Logs** – C:\Logs\AppAgentRuntime.log
These logs are written by WindowsAzureGuestAgent.exe and contain information about events happening within the guest agent and the VM.  This includes information such as firewall configuration, role state changes, recycles, reboots, health status changes, role stops/starts, certificate configuration, etc.
This log is useful to get a quick overview of the events happening over time to a role since it logs major changes to the role without logging heartbeats.
If the guest agent is not able to start the role correctly (ie. a locked file preventing directory cleanup) then you will see it in this log.

**App Agent Heartbeat Logs** – C:\Logs\WaAppAgent.log
These logs are written by WindowsAzureGuestAgent.exe and contain information about the status of the health probes to the host bootstrapper. 
The guest agent process is responsible for reporting health status (ie. Ready, Busy, etc) back to the fabric, so the health status as reported by these logs is the same status that you will see in the Management Portal.
These logs are typically useful for determining what is the current state of the role within the VM, as well as determining what the state was at some time in the past.  With a problem description like “My website was down from 10:00am to 11:30am yesterday”, these heartbeat logs are very useful to determine what the health status of the role was during that time.

**Host Bootstrapper Logs** – C:\Resources\WaHostBootstrapper.log
This log contains entries for startup tasks (including plugins such as Caching or RDP) and health probes to the host process running your role entrypoint code (ie. WebRole.cs code running in WaIISHost.exe).
A new log file is generated each time the host bootstrapper is restarted (ie. each time your role is recycled due to a crash, recycle, VM restart, upgrade, etc) which makes these logs easy to use to determine how often or when your role recycled.

**IIS Logs** - C:\Resources\Directory\{DeploymentID}.{Rolename}.DiagnosticStore\LogFiles\Web
This is standard troubleshooting for both Azure and on-premise servers. 
One key problem scenario where these logs are often overlooked is the scenario of “My website was down from 10:00am to 11:30am yesterday”.  The natural tendency is to blame Azure for the outage (“My site has been working fine for 2 weeks, so it must be a problem with Azure!”), but the IIS logs will often indicate otherwise.  You may find increased response times immediately prior to the outage, or non-success status codes being returned from IIS, which would indicate a problem within the website itself (ie. in the ASP.NET code running in w3wp.exe) rather than an Azure issue.

**Performance Counters** – perfmon, or Windows Azure Diagnostics
This is standard troubleshooting for both Azure and on-premise servers.
The interesting aspect of these logs in Azure is that, assuming you have setup WAD ahead of time, you will often have valuable performance counters to troubleshoot problems which occurred in the past (ie. "My website was down from 10:00am to 11:30am yesterday").
Other than specific problems where you are gathering specific performance counters, the most common uses for the performance counters gathered by WAD is to look for regular performance counter entries, then a period of no entries, then resuming the regular entries (indicating a scenario where the VM was potentially not running), or 100% CPU (usually indicating an infinite loop or some other logic problem in the website code itself).

**HTTP.SYS Logs** – D:\WIndows\System32\LogFiles\HTTPERR
This is standard troubleshooting for both Azure and on-premise servers. 
Similar to the IIS Logs, these are often overlooked but very important when trying to troubleshoot an issue with a hosted service website not responding.  Often times it can be the result of IIS not being able to process the volume of requests coming in, the evidence of which will usually show up in the HTTP.SYS logs.

**IIS Failed Request Log Files** - C:\Resources\Directory\{DeploymentID}.{Rolename}.DiagnosticStore\FailedReqLogFiles
This is standard troubleshooting for both Azure and on-premise servers. 
This is not turned on by default in Windows Azure and is not frequently used.  But if you are troubleshooting IIS/ASP.NET specific issues you should consider turning FREB tracing on in order to get additional details.

**Windows Azure Diagnostics Tables and Configuration** - C:\Resources\Directory\{DeploymentID}.{Rolename}.DiagnosticStore\Monitor
This is the local on-VM cache of the Windows Azure Diagnostics (WAD) data.  WAD captures the data as you have configured it, stores in in custom .TSF files on the VM, then transfers it to storage based on the scheduled transfer period time you have specified.
Unfortunately because they are in a custom .TSF format the contents of the WAD data are of limited use, however you can see the diagnostics configuration files which are useful to troubleshoot issues when Windows Azure Diagnostics itself is not working correctly.  Look in the Configuration folder for a file called config.xml which will include the configuration data for WAD.  If WAD is not working correctly you should check this file to make sure it is reflecting the way that you are expecting WAD to be configured.

**Windows Azure Caching Log Files** - C:\Resources\Directory\{DeploymentID}.{Rolename}.DiagnosticStore\AzureCaching
These logs contain detailed information about Windows Azure role-based caching and can help troubleshoot issues where caching is not working as expected.

**WaIISHost Logs** - C:\Resources\Directory\{DeploymentID}.{Rolename}.DiagnosticStore\WaIISHost.log
This contains logs from the WaIISHost.exe process which is where your role entrypoint code (ie. WebRole.cs) runs for WebRoles.  The majority of this information is also included in other logs covered above (ie. the Windows Azure Event Logs), but you may occasionally find additional useful information here.

**IISConfigurator Logs** - C:\Resources\Directory\{DeploymentID}.{Rolename}.DiagnosticStore\IISConfigurator.log
This contains information about the IISConfigurator process which is used to do the actual IIS configuration of your website per the model you have defined in the service definition files. 
This process rarely fails or encounters errors, but if IIS/w3wp.exe does not seem to be setup correctly for your service then this log is the place to check.

**Role Configuration Files** – C:\Config\{DeploymentID}.{DeploymentID.{Rolename}.{Version}.xml
This contains information about the configuration for your role such as settings defined in the ServiceConfiguration.cscfg file, LocalResource directories, DIP and VIP IP addresses and ports, certificate thumbprints, Load Balancer Probes, other instances, etc.
Similar to the Role Model Definition File, this is not a log file which contains runtime generated information, but can be useful to ensure that your service is being configured in the way that you are expecting.

**Role Model Definition File** – E:\RoleModel.xml (or F:\RoleModel.xml)
This contains information about how your service is defined according to the Azure Runtime, in particular it contains entries for every startup task and how the startup task will be run (ie. background, environment variables, location, etc).  You will also be able to see how your <sites> element is defined for a web role. 
This is not a log file which contains runtime generated information, but it will help you validate that Azure is running your service as you are expecting it to.  This is often helpful when a developer has a particular version of a service definition on his development machine, but the build/package server is using a different version of the service definition files.

  
<!--Note-->  
If you look in the C:\Logs folder you will find RuntimeEvents_{iteration}.etl and WaAppAgent_{iteration}.etl files.  These are ETW traces which contain a compilation of the information found in the Windows Azure Event Logs, Guest Agent Logs, and other logs.  This is a very convenient compilation of all of the most important log data in an Azure VM, but because they are in ETL format it requires a few extra steps to consume the information.  If you have a favorite ETW viewing tool then you can ignore several of the above mentioned log files and just look at the information in these two ETL files.  
