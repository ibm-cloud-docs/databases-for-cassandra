---

copyright:
  years: 2019, 2023
lastupdated: "2023-06-20"

keywords: databases, scaling, memory, disk IOPS, CPU, cassandra, datastax, dse, datastax dedicated cores, cassandra dedicated cores

subcollection: databases-for-cassandra

---

{{site.data.keyword.attribute-definition-list}}

# Scaling Disk, RAM, and CPU
{: #resources-scaling}

{{site.data.keyword.databases-for-cassandra_full}} is deprecated and no longer supported as of 30 June 2024. For more information, see the [deprecation details](/docs/databases-for-cassandra?topic=databases-for-cassandra-deprecation#dep_details).
{: deprecated}

You can manually adjust the amount of resources available to your {{site.data.keyword.databases-for-cassandra_full}} deployment to suit your workload and the size of your data.

## Resource Breakdown
{: #resources-scaling-resource-breakdown}

{{site.data.keyword.databases-for-cassandra}} deployments have three data members in a cluster, and resources are allocated to all members equally. For example, the minimum storage of a {{site.data.keyword.databases-for-cassandra}} deployment is 20480 MB per member, which equates to an initial size of 61440 MB. The minimum RAM for a {{site.data.keyword.databases-for-cassandra}} deployment is 12288 MB per member, which equates to an initial allocation of 36864 MB. The minimum dedicated cores per deployment are 6 per member, for an initial allocation of 18. 

Billing is based on the _total_ amount of resources that are allocated to the service.
{: .tip}

### Disk
{: #resources-scaling-disk}

Your disk allocation must be enough to store all of your data. Your data is replicated to all data members so the total amount of disk that you use is at least twice the size of your data set. 

Disk allocation also affects the performance of the disk, with larger disks experiencing higher performance. Baseline input/output operations per second (IOPS) performance for disk is 10 IOPS for each GB. Scale disk to increase the IOPS that your deployment can handle.

You cannot scale down storage.
{: .tip} 

### RAM
{: #resources-scaling-ram}

If you find that your deployment is suffering from performance issues due to a lack of memory, you can scale the amount of RAM allocated to it. The amount of memory you allocate to your deployment is split between all members. Adding memory to the total allocation adds memory to all members equally.

### Dedicated Cores
{: #resources-scaling-dedicated-cores}

You can increase or decrease the CPU shares to the deployment. With dedicated cores, your resource group is given a single-tenant host with a reserve of CPU shares. Your deployment is then guaranteed a number of CPUs you specify over the six dedicated cores per member, minimum.

## Scaling Considerations
{: #resources-scaling-scale-consider}

- With a minimum of 3 members, allocation minimums begin with 12 Gb RAM, 20 GB Disk, and 6 dedicated cores per member. 
   
- Scaling your deployment up might cause your databases to restart. If your deployment needs to be moved to a host with more capacity, then the databases are restarted as part of the move.

- Scaling down RAM or CPU does not trigger database restarts.

- Disk cannot be scaled down.

- A few scaling operations can be more long running than others.  Similarly, drastically increasing CPU, RAM, or Disk can take longer than smaller increases to account for provisioning more underlying hardware resources.

- Scaling operations are logged in [{{site.data.keyword.at_full}}](/docs/databases-for-cassandra?topic=databases-for-cassandra-activity-tracker).

- If you find consistent trends in resource usage or would like to set up scaling when certain resource thresholds are reached, consider enabling [autoscaling](/docs/databases-for-cassandra?topic=databases-for-cassandra-autoscaling) on your deployment.

## Scaling in the UI
{: #resources-scaling-ui}
{: ui}

A visual representation of your data members and their resource allocation is available on the _Resources_ tab of your deployment's _Manage_ page. 

![The Scale Resources Pane in _Resources_](images/scaling-update.png){: caption="Figure 1. The Scale Resources Pane" caption-side="bottom"}

Adjust the slider to increase or decrease the resources that are allocated to your service. The slider controls how much memory or disk is allocated per member. The UI shows the total allocated memory or disk for the position of the slider. Click **Scale** to trigger the scaling operations and return to the dashboard overview. 

The UI currently uses a coarser-grained resolution for scaling than the CLI or API commands. Use the API or CLI to scale if the stops on the slider do not meet your size requirements.
{: .tip}

## Scaling in the CLI 
{: #resources-scaling-cli}
{: cli}

[{{site.data.keyword.cloud_notm}} CLI cloud databases plug-in](/docs/databases-cli-plugin?topic=databases-cli-plugin-cdb-reference) supports viewing and scaling the resources on your deployment. To scale any of the available resource groups, use `cdb deployment-groups-set` command. 

For example, the command to view the resource groups for a deployment named "example-deployment" is, 
```sh
ibmcloud cdb deployment-groups example-deployment
```
{: pre}

This command produces the output,
```sh
Group   member
Count   3
|
+   Memory
|   Allocation              36864mb
|   Allocation per member   12288mb
|   Minimum                 36864mb
|   Step Size               1024mb
|   Adjustable              true
|
+   CPU
|   Allocation              18
|   Allocation per member   6
|   Minimum                 18
|   Step Size               1
|   Adjustable              true
|
+   Disk
|   Allocation              61440mb
|   Allocation per member   20480mb
|   Minimum                 20480mb
|   Step Size               1024mb
|   Adjustable              true
```

The deployment has three members, with 36864 MB of RAM and 61440 MB of disk allocated in total. The "per member" allocation is 12288 MB of RAM and 20480 MB of disk. The minimum value is the lowest the total allocation that can be set. The step size is the smallest amount by which the total allocation can be adjusted.

The `cdb deployment-groups-set` command allows either the total RAM or total disk allocation to be set, in MB. For example, to scale the memory of the "example-deployment" to 13312 MB of RAM for each memory member (for a total memory of 39936 MB), you use the command 
```sh
ibmcloud cdb deployment-groups-set example-deployment member --memory 39936
```
{: pre}

## Scaling in the API
{: #resources-scaling-api}
{: api}

The _Foundation Endpoint_ that is shown on the _Overview_ pane of your service provides the base URL to access this deployment through the API. Use it with the `/groups` endpoint if you need to manage or automate scaling programmatically. 

To view the current and scalable resources on a deployment, use
```sh
curl -X GET -H "Authorization: Bearer $APIKEY" 'https://api.{region}.databases.cloud.ibm.com/v4/ibm/deployments/{id}/groups'
```
{: pre}

To scale the memory of a deployment to 13312 MB of RAM for each memory member (for a total memory of 39936 MB).
```sh
curl -X PATCH 'https://api.{region}.databases.cloud.ibm.com/v4/ibm/deployments/{id}/groups/member' \
-H "Authorization: Bearer $APIKEY" \
-H "Content-Type: application/json" \
-d '{"memory": {
        "allocation_mb": 39936
      }
    }'
```
{: pre}

More information is in the [API Reference](https://{DomainName}/apidocs/cloud-databases-api#get-currently-available-scaling-groups-from-a-depl).
