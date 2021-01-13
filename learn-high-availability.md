---

Copyright:
  years: 2018, 2020
lastupdated: "2020-09-25"

keywords: databases, connection limits, cassandra, datastax, dse

subcollection: databases-for-cassandra

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:external .external}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# High-Availability
{: #high-availability}

{{site.data.keyword.databases-for-cassandra_full}} is a managed cloud database service that is fully integrated into the {{site.data.keyword.cloud_notm}} environments. The database, storage, and supporting infrastructure all run in {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.databases-for-cassandra}} provides replication and high-availability features to protect your databases and data from infrastructure maintenance, upgrades, and failures.  

## Application-level High-Availability

Applications that communicate over networks and cloud services are subject to transient connection failures. You want to design your applications to retry connections when errors are caused by a temporary loss in connectivity to your deployment or to {{site.data.keyword.cloud_notm}}.

Because {{site.data.keyword.databases-for-cassandra}} is a managed service, regular updates and database maintenance occurs as part of normal operations. This maintenance can occasionally cause short intervals where your database is unavailable. 

Your applications must be designed to handle temporary interruptions to the database, implement error handling for failed database commands, and implement retry logic to recover from a temporary interruption.

Several minutes of database unavailability or connection interruption are not expected. Open a [support ticket](https://cloud.ibm.com/unifiedsupport/cases/add) with details if you have time periods longer than a minute with no connectivity so we can investigate.

## Replication, keystores, and High-Availability

To help ensure availability of data, setting the replication factor that matches your deployment is necessary. When you create keyspaces, make sure to set the replication factor to the number of nodes (or members) in your cluster. The following example shows this set to 3, where `eu-gb` is the region set based on the location of the formation in the CRN: 
```
create keyspace if not exists ibm with replication = {'class' : 'NetworkTopologyStrategy', 'eu-gb' : 3};
```
{: pre} 

Setting a replication factor of `1` results in your data becoming unavailable at times due to routine internal maintenance or other interruptions. To help ensure availability of data, it is recommended to set a replication factor of at least 3.
{: note} 

Use [Sysdig](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-platform_metrics_enabling) to monitor your deployment. Adjust either by [manually scaling](/docs/databases-for-cassandra?topic=databases-for-cassandra-resources-scaling), or by using the [autoscaling feature](/docs/databases-for-cassandra?topic=databases-for-cassandra-autoscaling) to ensure continued high availability.  

## High availability, disaster recovery, and SLA resources

{{site.data.keyword.databases-for-cassandra}} deployments conform to the {{site.data.keyword.cloud_notm}} Databases [HA, DR, and SLA](/docs/cloud-databases?topic=cloud-databases-ha-dr) terms.

