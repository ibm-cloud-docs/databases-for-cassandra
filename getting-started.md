---

copyright:
  years: 2018, 2022
lastupdated: "2022-06-29"

keywords: nodesync, repair, cassandra, datastax, dse, cassandra external application, nodesync, cassandra migration
subcollection: databases-for-cassandra

---

{:shortdesc: .shortdesc}
{:external: .external target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Getting Started
{: #getting-started}

This tutorial is a short introduction to using an {{site.data.keyword.databases-for-cassandra_full}} deployment. 

## Before you begin
{: #before-begin}

- You need to have an [{{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/registration){: external}.
- You also need a {{site.data.keyword.databases-for-cassandra}} deployment. You can provision a deployment from the [{{site.data.keyword.cloud_notm}} catalog](https://cloud.ibm.com/catalog/services/databases-for-cassandra). Give your deployment a memorable name that appears in your account's Resource List.
- [Set the Admin Password](/docs/databases-for-cassandra?topic=databases-for-cassandra-admin-password) for your deployment.

Review the [`Getting to production`](/docs/cloud-databases?topic=cloud-databases-best-practices) documentation for general guidance on setting up a basic {{site.data.keyword.databases-for-cassandra_full}} deployment.

## Connecting with DataStax drivers
{: #connecting-datastax-drivers}

Drivers are a key component to connecting external applications to your {{site.data.keyword.databases-for-cassandra}} deployment. Review the information on [Connecting an external application](/docs/databases-for-cassandra?topic=databases-for-cassandra-external-app){: external} for details on compatible drivers. Further details on specific drivers, including upgrade guides, can be found at [Developing applications with Apache Cassandra and DataStax Enterprise](https://docs.datastax.com/en/devapp/doc/devapp/aboutDrivers.html){: external}. 
 
Only DataStax drivers that are explicitly listed in the [Connecting an external application](/docs/databases-for-cassandra?topic=databases-for-cassandra-external-app) table function correctly for connecting to {{site.data.keyword.databases-for-cassandra}}.
{: .tip} 

## Node repairs with NodeSync
{: #node-repairs-nodesync}

[NodeSync](https://docs.datastax.com/en/dse/6.7/dse-admin/datastax_enterprise/config/aboutNodesync.html){: external} is a continuous repair service that runs automatically in the background to validate that your data is in sync on all replicas and reduces the need for manual repairs. For operational simplicity and performance, {{site.data.keyword.databases-for-cassandra}} enables the NodeSync service on all key spaces and tables to handle node repairs. Traditional repairs are unnecessary, as the automation ensures that NodeSync handles the repairs for you.  

While the automation enables NodeSync, you can also manually create tables with NodeSync enabled so that the service can repair the tables' data when necessary: 
```sh
CREATE TABLE myTable (...) WITH nodesync = { 'enabled': 'true'};
```
{: .pre}


For more information, see [enabling the NodeSync service](https://docs.datastax.com/en/dse/6.7/dse-admin/datastax_enterprise/config/enablingNodesync.html){: external}.  

Nodetool is unsupported. Manual repairs that are issued against any table that is enabled with the NodeSync service [are ignored](https://docs.datastax.com/en/opscenter/6.5/opsc/online_help/services/opscNodeSyncService.html#NodeSyncServiceversusRepairService){: external}. See error:
{: .tip}

```sh
WARNING: A manual nodetool repair or a repair operation from the OpsCenter node administration menu fails to run if a NodeSync-enabled table is targeted.
```

## Recommendations
{: #datastax-recs}

### Benchmark before production
{: #datastax-recs-benchmark}

- Do not use `cqlsh` and `COPY` for benchmarking, as `COPY` does not mimic typical client behavior. Instead, [`nosqlbench`](https://github.com/nosqlbench/nosqlbench){: external} can be used for benchmarking. 

### Data migrations
{: #datastax-recs-data-migrations}

- `DSBULK` is recommended for data migration. For more information, see [DSBULK documentation](https://docs.datastax.com/en/dsbulk/doc/dsbulk/reference/dsbulkCmd.html){: external}. 

### Resource configurations
{: #datastax-recs-resource-configs}

- The recommended configuration for a node is: 
    - 16 CPUs 
    - 32 GB to 64 GB RAM 
    - 16 K disk IOPS (16 k IOPS == 1.6 TB disk)


## Next steps
{: #datastax-next-steps}

* Detailed information on CQL, the Cassandra Query Language, can be found by consulting [CQL for DSE Documentation](https://docs.datastax.com/en/dse/6.0/cql/){: external}. 

* Looking to administer your deployment? Consult DataStax's documentation on using the [stand-alone CQLSH client](https://docs.datastax.com/en/astra/docs/connecting-to-databases-using-standalone-cqlsh.html){: external}. 

* You can manage your deployment with [IBM Cloud CLI](/docs/cli?topic=cli-install-ibmcloud-cli), the [Cloud Databases CLI plug-in](/docs/databases-cli-plugin?topic=databases-cli-plugin-cdb-reference), or by using the [Cloud Databases API](https://cloud.ibm.com/apidocs/cloud-databases-api){: external}.

* If you are planning to use {{site.data.keyword.databases-for-cassandra}} for your applications, check out:
   - [Connecting an external application](/docs/databases-for-cassandra?topic=databases-for-cassandra-external-app)
   - [Connecting an IBM Cloud application](/docs/databases-for-cassandra?topic=databases-for-cassandra-ibmcloud-app)

* To ensure the stability of your applications and your database, check out:
   - [High-Availability](/docs/databases-for-cassandra?topic=databases-for-cassandra-high-availability)
   - [Performance](/docs/databases-for-cassandra?topic=databases-for-cassandra-performance)
