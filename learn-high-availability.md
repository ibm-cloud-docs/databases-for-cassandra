---

copyright:
  years: 2018, 2023
lastupdated: "2023-06-20"

keywords: databases, connection limits, cassandra, datastax, dse, datastax replication, datastax high availability

subcollection: databases-for-cassandra

---

{{site.data.keyword.attribute-definition-list}}

# High-Availability
{: #high-availability}

{{site.data.keyword.databases-for-cassandra_full}} is deprecated and no longer supported as of 30 June 2024. For more information, see the [deprecation details](/docs/databases-for-cassandra?topic=databases-for-cassandra-deprecation#dep_details).
{: deprecated}

{{site.data.keyword.databases-for-cassandra_full}} is a managed cloud database service that is fully integrated into the {{site.data.keyword.cloud_notm}} environments. The database, storage, and supporting infrastructure all run in {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.databases-for-cassandra}} provides replication and high-availability features to protect your databases and data from infrastructure maintenance, upgrades, and failures.  

## Application-level High-Availability
{: #app-level-high-availability}

Applications that communicate over networks and cloud services are subject to transient connection failures. You want to design your applications to retry connections when errors are caused by a temporary loss in connectivity to your deployment or to {{site.data.keyword.cloud_notm}}.

Because {{site.data.keyword.databases-for-cassandra}} is a managed service, regular updates and database maintenance occurs as part of normal operations. This maintenance can occasionally cause short intervals where your database is unavailable. 

Your applications must be designed to handle temporary interruptions to the database, implement error handling for failed database commands, and implement retry logic to recover from a temporary interruption.

Several minutes of database unavailability or connection interruption are not expected. Open a [support ticket](https://cloud.ibm.com/unifiedsupport/cases/add) with details if you have time periods longer than a minute with no connectivity so we can investigate.

## Replication, keystores, and High-Availability
{: #repl-keys-high-availability}

When you create the keyspace, it is up to you to define the number of replicas and strategy. Setting the value to `NetworkTopologyStrategy` and number of replicas matching your deployment, the distribution across zones occur automatically (except within single zone regions like Chennai, Oslo, Seoul where replication is contained to that single zone). You can read more about the [replication strategies](https://docs.datastax.com/en/dse/6.0/dse-arch/datastax_enterprise/dbArch/archDataDistributeReplication.html) in the DataStax Enterprise documentation.

To help ensure availability of data, setting the replication factor that matches your deployment is necessary. When you create key spaces, make sure to set the replication factor to the number of nodes (or members) in your cluster. The following example shows this set to 3, where `eu-gb` is the region set based on the location of the formation in the CRN: 
```sh
create keyspace if not exists ibm with replication = {'class' : 'NetworkTopologyStrategy', 'eu-gb' : 3};
```
{: pre} 

Setting a replication factor of `1` results in your data becoming unavailable at times due to routine internal maintenance or other interruptions. To help ensure availability of data, it is recommended to set a replication factor of 3. NetworkTopologyStrategy attempts to place replicas on distinct racks because nodes in the same rack (or similar physical grouping) often fail at the same time due to power, cooling, or network issues. 

For your {{site.data.keyword.databases-for-cassandra_full}} deployment, the “data center” attribute equates to a region (for example, `eu-gb`) and the “rack” attribute reflects the actual {{site.data.keyword.cloud_notm}} data center (for example, `lon04/lon05`). Setting a replication factor of `3` helps ensure that replicas are distributed across availability zones.

Using `NetworkTopologyStrategy` and setting a replication factor greater than `1` ensures that replicas are distributed across data centers in multi-zone regions. 
{: .tip}

Use [{{site.data.keyword.monitoringfull}}](/docs/monitoring?topic=monitoring-platform_metrics_enabling) to monitor your deployment. Adjust either by [manually scaling](/docs/databases-for-cassandra?topic=databases-for-cassandra-resources-scaling), or by using the [autoscaling feature](/docs/databases-for-cassandra?topic=databases-for-cassandra-autoscaling) to ensure continued high availability.  

## High availability, disaster recovery, and SLA resources
{: #ha-dr-high-availability}

{{site.data.keyword.databases-for-cassandra}} deployments conform to the {{site.data.keyword.cloud_notm}} Databases [HA, DR, and SLA](/docs/cloud-databases?topic=cloud-databases-ha-dr) terms.
