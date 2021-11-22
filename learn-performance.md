---

copyright:
  years: 2020, 2021
lastupdated: "2021-11-22"

keywords: databases, monitoring, scaling, autoscaling, resources, connection limits, cassandra, datastax, dse

subcollection: databases-for-cassandra

---

{:external: .external target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Performance
{: #performance}

{{site.data.keyword.databases-for-cassandra_full}} deployments can be both manually [scaled to your usage](/docs/databases-for-cassandra?topic=databases-for-cassandra-resources-scaling), or configured to [autoscale](/docs/databases-for-cassandra?topic=databases-for-cassandra-autoscaling) under certain resource conditions. Following are a few factors to consider when you are tuning the performance of your deployment.

## Monitoring your deployment
{: #mon-deployment}

{{site.data.keyword.databases-for-cassandra}} deployments offer an integration with the [{{site.data.keyword.monitoringfull}} service](/docs/databases-for-cassandra?topic=databases-for-cassandra-monitoring) for basic monitoring of resource usage on your deployment. Many of the available metrics, like disk usage and Input-Output Operations Per Second (IOPS), are presented to help you configure [autoscaling](/docs/databases-for-cassandra?topic=databases-for-cassandra-autoscaling) on your deployment. Observing trends in your usage and configuring the autoscaling to respond to them can help alleviate performance problems before your databases become unstable due to resource exhaustion.

## Disk Input-Output Operations Per Second (IOPS)
{: #iops}

The number of IOPS is limited by the type of storage volume. Storage volumes for {{site.data.keyword.databases-for-cassandra}} deployments are provisioned on [Block Storage Endurance Volumes in the 10 IOPS per GB tier](/docs/BlockStorage?topic=BlockStorage-orderingthroughConsole#orderingthroughConsoleEndurance). If your operational load saturates or exceeds the IOPS limit, database requests and operations are delayed until the disk can catch up. Extended periods of heavy-load can cause your deployment to be unable to process queries and become effectively unavailable. If you experience delayed responses and failing operations, you might be exceeding the disk's IOPS limit. You can increase the number IOPS available to your deployment by increasing disk space.

## Memory Management
{: #mem-manage}

DataStax memory is divided into two categories: Java virtual machine (JVM) heap size, and system memory. It uses heap for internal caching. It uses the rest of the system memory for the operating system, file system caches, and garbage collection. The more memory that is allocated to the heap, the less is allocated to the rest of the system.
