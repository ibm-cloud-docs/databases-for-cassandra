---

copyright:
  years: 2018, 2023
lastupdated: "2023-04-28"

keywords: nodesync, repair, cassandra, datastax, dse, cassandra external application, nodesync, cassandra migration
subcollection: databases-for-cassandra

content-type: tutorial
services: 
account-plan: paid
completion-time: 20m

---

{{site.data.keyword.attribute-definition-list}}

# Getting Started with {{site.data.keyword.databases-for-cassandra}}
{: #getting-started}
{: toc-content-type="tutorial"} 
{: toc-services=""} 
{: toc-completion-time="20m"}

The {{site.data.keyword.cloud_notm}}{{site.data.keyword.databases-for-cassandra_full}} Getting started tutorial demonstrates how to use the {{site.data.keyword.cloud_notm}} Dashboard to create an {{site.data.keyword.databases-for-cassandra_full}} service instance. You also see essential information to enable your application to work with the database.

This tutorial is a short introduction to using an {{site.data.keyword.databases-for-cassandra_full}} deployment. 

## Before you begin
{: #before-begin}
{: step}

- You need to have an [{{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/registration){: external}.

## Create a service instance
{: #creating-an-icd-datastax-instance-on-ibm-cloud}
{: step}

1. Navigate to the [{{site.data.keyword.databases-for-cassandra_full}} service](https://cloud.ibm.com/databases/databases-for-cassandra/create) in the {{site.data.keyword.cloud_notm}} Catalog.

1. Give your service a memorable name that will later appear in your account's Resource List.
1. Choose a resource group.
1. Choose a location.
1. Choose your resource allocation, using one of the provided templates or a custom allocation. 
1. Configure your service.
   - Database version
   - Encryption
   - Endpoints: Select which endpoints you'd like to be initially enabled, either public or private. 
1. Click **Create**.

   After you click `Create`, the system displays a message to say that the instance is being provisioned, which returns you to the Resource list. From the Resource list, you see that the status for your instance is, `Provision in progress`. 

1.  When the status changes to `Active`, select the instance.

## Set your admin password
{: #datastax-set-admin-password}
{: step}

- [Set the Admin Password](/docs/databases-for-cassandra?topic=databases-for-cassandra-admin-password) for your deployment.

Review the [`Getting to production`](/docs/cloud-databases?topic=cloud-databases-best-practices) documentation for general guidance on setting up a basic {{site.data.keyword.databases-for-cassandra_full}} deployment.

## Connect with DataStax drivers
{: #connecting-datastax-drivers}
{: step}

Drivers are a key component to connecting external applications to your {{site.data.keyword.databases-for-cassandra}} deployment. Review the information on [Connecting an external application](/docs/databases-for-cassandra?topic=databases-for-cassandra-external-app){: external} for details on compatible drivers. Further details on specific drivers, including upgrade guides, can be found at [Developing applications with Apache Cassandra and DataStax Enterprise](https://docs.datastax.com/en/devapp/doc/devapp/aboutDrivers.html){: external}. 
 
Only DataStax drivers that are explicitly listed in the [Connecting an external application](/docs/databases-for-cassandra?topic=databases-for-cassandra-external-app) table function correctly for connecting to {{site.data.keyword.databases-for-cassandra}}.
{: .tip} 

## Node repairs with NodeSync
{: #node-repairs-nodesync}
{: step}

[NodeSync](https://docs.datastax.com/en/dse/6.7/dse-admin/datastax_enterprise/config/aboutNodesync.html){: external} is a continuous repair service that runs automatically in the background to validate that your data is in sync on all replicas and reduces the need for manual repairs. For operational simplicity and performance, {{site.data.keyword.databases-for-cassandra}} enables the NodeSync service on all key spaces and tables to handle node repairs. Traditional repairs are unnecessary, as the automation ensures that NodeSync handles the repairs for you.  

While the automation enables NodeSync, you can also manually create tables with NodeSync enabled so that the service can repair the tables' data when necessary: 
```sh
CREATE TABLE myTable (...) WITH nodesync = { 'enabled': 'true'};
```
{: .pre}


For more information, see [enabling the NodeSync service](https://docs.datastax.com/en/dse/6.7/dse-admin/datastax_enterprise/config/enablingNodesync.html){: external}.  

Nodetool is unsupported. Manual repairs that are issued against any table that is enabled with the NodeSync service [are ignored](https://docs.datastax.com/en/opscenter/6.5/opsc/online_help/services/opscNodeSyncService.html#NodeSyncServiceversusRepairService){: external}. See error:
{: .tip}

```text
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

Detailed information on CQL, the Cassandra Query Language, can be found by consulting [CQL for DSE Documentation](https://docs.datastax.com/en/dse/6.0/cql/){: external}. 

Looking to administer your deployment? Consult DataStax's documentation on using the [stand-alone CQLSH client](https://docs.datastax.com/en/astra/docs/connecting-to-databases-using-standalone-cqlsh.html){: external}. 

You can manage your deployment with [IBM Cloud CLI](/docs/cli?topic=cli-install-ibmcloud-cli), the [Cloud Databases CLI plug-in](/docs/databases-cli-plugin?topic=databases-cli-plugin-cdb-reference), or by using the [Cloud Databases API](https://cloud.ibm.com/apidocs/cloud-databases-api){: external}.

If you are planning to use {{site.data.keyword.databases-for-cassandra}} for your applications, check out [Connecting an external application](/docs/databases-for-cassandra?topic=databases-for-cassandra-external-app) and [Connecting an IBM Cloud application](/docs/databases-for-cassandra?topic=databases-for-cassandra-ibmcloud-app).

To ensure the stability of your applications and your database, check out [High-Availability](/docs/databases-for-cassandra?topic=databases-for-cassandra-high-availability and [Performance](/docs/databases-for-cassandra?topic=databases-for-cassandra-performance).
