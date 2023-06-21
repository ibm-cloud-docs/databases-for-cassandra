---
copyright:
  years: 2017, 2023
lastupdated: "2023-06-20"

keywords: databases, pricing, resources, scaling, cassandra, datastax, dse, backup pricing, cassandra pricing, datastax pricing

subcollection: databases-for-cassandra

---

{{site.data.keyword.attribute-definition-list}}

# Pricing
{: #pricing}

{{site.data.keyword.databases-for-cassandra_full}} is deprecated and no longer supported as of 30 June 2024. For more information, see the [deprecation details](/docs/databases-for-cassandra?topic=databases-for-cassandra-deprecation#dep_details).
{: deprecated}

A {{site.data.keyword.databases-for-cassandra_full}} Standard plan deploys as one highly available cluster with three data members. Your data is replicated on all three members. The Standard plan is priced based on the total amount of disk storage, RAM, dedicated cores, and backup storage that is allocated to deployments, prorated hourly. {{site.data.keyword.databases-for-cassandra}} deployments have a minimum of 20 GB of disk and 12 GB of RAM per data member.

## Using the Pricing Calculator
{: #pricing-calc}

Templates are provided for ease of use and provide balanced resource allocations appropriate for general-purpose workloads. The **Custom** tab can be used to configure Disk, RAM, and vCPU, as wanted.

For pricing estimation, click **Add to Estimate** on the [{{site.data.keyword.databases-for-cassandra}} catalog page](https://cloud.ibm.com/catalog/databases-for-cassandra). Input your total consumption across three data members into the calculator. This is roughly tripled the size of your data because the data is replicated to all three members. For example, 20 GB of disk and 12 GB of RAM across three data members would be priced at 60 GB of disk and 36 GB of RAM. 

## Backups Pricing
{: #pricing-backup}

You receive your total disk space purchased, per database, in free backup storage. For example, in a month, if you have a {{site.data.keyword.databases-for-cassandra}} deployment that has 20 GB of disk per member, and has three data members, you receive 60 GB of backup storage free for that month. If your backup storage utilization is greater than 60 GB for the month (in this scenario), you are charged an overage of $0.03 / month per gigabyte. 

By default, {{site.data.keyword.databases-for}} provides a daily backup that is stored for 30 days. These backups, and any on-demand backups you make, all count toward the above allocation.

In the above example, if your database contains 2 GB of data and you no on-demand backups, then your total backup size is 2 GB x 30 = 60 GB. Your backup costs are nil.

If your database contains 15 GB of data and you have no on-demand backups, then your total backup size is 15 GB x 30 = 450 GB. In this scenario, your backup costs are (450 GB - 60 GB) * 0.03 = $11.7 per month.

Most deployments will not ever go over the allotted credit.

## Dedicated Cores Pricing
{: #pricing-cores}

You have the option of selecting the CPU allocation for your deployment. With dedicated cores, your resource group is given a single-tenant host with a guaranteed minimum reserve of cpu shares. Your deployments are then allocated the number of CPUs you specify. The cost of dedicated cores is $100 per core per month, and each member gets the selected number of cores. For example, if you provision a deployment with six dedicated cores per member, that is a total of 18 cores, and billed at $1,800 per month. 

Dedicated cores are an optional feature.{: .note}

## Scaling per Member
{: #pricing-scaling}

{{site.data.keyword.databases-for-cassandra}} deployments have minimum and maximum allocation for disk and RAM as shown. Scaling deployments through the API/CLI provides more granularity and also allows a user to scale a database instance up to 4 TB of disk per member.

| Resource | Minimum | Maximum | Scaling Granularity (API/CLI) |
| ---------- | ----- | ----- | ------- |
| Disk | 20 GB per member | 4 TB per member | 1024 MB per member |
| RAM | 12 GB per member | 112 GB per member | 128 MB per member |
| CPU (if enabled) | 6 CPUs per member | 28 CPUs per member| 1 CPU per member |
{: caption="Table 1. Per Member Scaling Limits" caption-side="top"}
