---
title:  "Azure Cloud Service Allocation failures - How to troubleshoot"
last_modified_at:   2017-05-20 16:29:01
categories: 
  - Azure
  - Azure Cloud Service
tags:
  - Azure Cloud Service
description: "Azure Cloud Service Allocation failures - How to troubleshoot"

toc: true
toc_label: "Azure Cloud Service"
---

Sometimes you may get errors when you create or add more instances to a Cloud Service or a web or worker role, even if you have not reached the Azure subscription limits. 
This article helps you understand and fix some of the common **allocation failures**. The information can also help you plan your service deployment better.
For reference check out the [public documentation](https://learn.microsoft.com/en-us/azure/cloud-services/cloud-services-allocation-failures).

## How Allocation works
Azure datacenters have servers grouped into clusters. A new cloud service request tries to find a cluster with enough resources. 
When the first instance of a cloud service is deployed (in staging or production), it stays in that cluster. Any more deployments for the same cloud service will also go to the very same cluster. 
The cloud service is essencially pinned to this cluster
The diagrams below show how this works. 
Diagram 1 shows a normal allocation that tries multiple clusters; Diagram 2 shows an allocation that goes to Cluster 2 because that’s where Cloud Service CS_1 already is.

<!--Image01-->

## Why allocation failures happen

When a request is pinned to a cluster, it may not find enough resources in that cluster. 
Also, if the cluster does not support the type of resource you want, your request will fail even if the cluster has some resources left. 
The diagrams below show how this can happen. 
Diagram 3 shows a pinned request that fails, because the cluster is full. 
Diagram 4 shows a pinned request that fails, because the cluster does not have the right VM size, even though it has some resources left.
<!--Image02-->

## Toubleshooting allocation failure


## Common Issues
Here some common scenarios that can cause an allocation error. The rootcause on all of those is the cluster nearing it's full capacity.

- **Deploying to Staging Slot** - A cloud service with a deployment in any slot stays in one cluster. If you have a production deployment, you can only deploy to staging in the same cluster. If the cluster is almost full, you may get an error.
- **Scaling** - Adding more instances to a cloud service must use the same cluster. Small scaling requests usually work, but not always. If the cluster is almost full, you may get an error.
- **Deploying to Staging Slot** - A cloud service with a deployment in any slot stays in one cluster. If you have a production deployment, you can only deploy to staging in the same cluster. If the cluster is almost full, you may get an error.
- **Scaling** - Adding more instances to a cloud service must use the same cluster. Small scaling requests usually work, but not always. If the cluster is almost full, you may get an error.
- **Affinity Group** - A new deployment to an empty cloud service can go to any cluster in that region, unless the cloud service is in an affinity group. Deployments in the same affinity group try to use the same cluster. If the cluster is almost full, you may get an error.
- **Affinity Group vNet** - Old Virtual Networks were linked to affinity groups, not regions, and cloud services in these Virtual Networks stayed in the affinity group cluster. Deployments to this kind of virtual network try to use the pinned cluster. If the cluster is almost full, you may get an error. - A new deployment to an empty cloud service can go to any cluster in that region, unless the cloud service is in an affinity group. Deployments in the same affinity group try to use the same cluster. If the cluster is almost full, you may get an error. Affinity groups are no longer a recommended practice. Instead use VNets as described [here](https://learn.microsoft.com/en-us/previous-versions/azure/virtual-network/virtual-networks-migrate-to-regional-vnet).

## Solutions
**Redeploy to a new cloud service** - This solution has the best chance of success because it lets the platform pick any cluster in that region. You are also less likely to be allocated towards a close-to-full cluster.
Keep in mind that a new deployment will incur downtimes. Here is a workaround that involves a custom domain that acts as the frontline to route traffic from the old deployment to the new one. 
- Deploy your workload to a new cloud service
- Change the CNAME or A record to direct traffic to the new cloud service
- When no traffic goes to the old site, you can delete the old cloud service. This solution should have no downtime.

**Delete both production and staging slots** - This solution keeps your existing DNS name, but will stop your application for a while.
- Delete the production and staging slots of an existing cloud service so that the cloud service is empty, and then
- Make a new deployment in the existing cloud service. This will try to allocate on all clusters in the region. Make sure the cloud service is not in an affinity group.

**Reserved IP** - Alternatively a reserved IP can be preserved, using following command. 
´´´´New-AzureReservedIP -ReservedIPName {new reserved IP name} -Location {location} -ServiceName {existing service name}´´´´
- After that Delete and redeploy just like in the previous solution.




