---
copyright:
  years: 2017, 2020
lastupdated: "2020-08-06"

keywords: databases, pricing, resources, scaling, cassandra, datastax, dse

subcollection: databases-for-cassandra

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:external .external}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}


# Pricing
{: #pricing}

A {{site.data.keyword.databases-for-cassandra_full}} Standard plan deploys as one highly available cluster with three data members. Your data is replicated on all three members. The Standard plan is priced based on the total amount of disk storage, RAM, dedicated cores, and backup storage that is allocated to deployments, prorated hourly. {{site.data.keyword.databases-for-cassandra}} deployments have a minimum of 20 GB of disk and 1 GB of RAM per data member.

## Cost Breakdown

**Disk storage per data member** - gigabytes of disk that are allocated to a {{site.data.keyword.databases-for-cassandra}} data member, or the size of your data.  
**RAM per data member** - gigabytes of RAM that are allocated to a {{site.data.keyword.databases-for-cassandra}} data member.  
**Backup storage** - amount of storage used for backups by a {{site.data.keyword.databases-for-cassandra}} deployment.  
**Virtual processor core** - number of virtual processor cores that are allocated to a {{site.data.keyword.databases-for-cassandra}} data member.

![Standard pricing](images/standard-pricing.png)

Resources | Breakdown | Price
-------|-------|-------
20 GB-Month disk | 3 members x 20 GB x $0.58 | $34.80
20 GB-Month backup| 3 members x 20 GB x $0.03| $1.80
12 GB-Month RAM | 3 members x 12 GB x $10.00 | $360.00
6 Virtual processor Cores | 3 members x 6 cores x $100 | $1800
 
{: caption="Table 1. Pricing example for two data members" caption-side="top"}

Total per month = $2196.60/Month  
Total per hour = $2.95/Hour

All prices here are in US dollars. To see pricing in your local currency, you can to use the pricing calculator.
{: .tip}

## Using the Pricing Calculator

Templates are provided for ease of use and provide balanced resource allocations appropriate for general purpose workloads. The **Custom** tab can be used to configure Disk, RAM, and vCPU, as desired.

For pricing estimation, click **Add to Estimate** on the [{{site.data.keyword.databases-for-cassandra}} catalog page](https://cloud.ibm.com/catalog/databases-for-cassandra). Input your total consumption across three data members into the calculator. This is roughly tripled the size of your data because your data is replicated to all three members. For example, 20 GB of disk and 12 GB of RAM across three data members would be priced at 60 GB of disk and 36 GB of RAM respectively. 

![Pricing calculator estimation with 20 GB of disk and 12 GB of RAM, per member](images/pricing-estimate.png)

## Backups Pricing

Users also receive their total disk space purchased, per database, in free backup storage. For example, in a specific month, if you have a {{site.data.keyword.databases-for-cassandra}} deployment that has 20 GB of disk per member, and has three data members, you receive 60 GB of backup storage free for that month. If your backup storage utilization is greater than 60 GB for the month in this scenario, each gigabyte is charged at an overage $0.03/month. Most deployments will not exceed the allotted credit.

## Dedicated Cores Pricing

You have the option of selecting the CPU allocation for your deployment. With dedicated cores, your resource group is given a single-tenant host with a guaranteed minimum reserve of cpu shares. Your deployments are then allocated the number of CPUs you specify. The cost of dedicated cores is $100 per core per month, and each member gets the selected number of cores. For example, if you provision a deployment with 6 dedicated cores per member, that is a total of 18 cores, and billed at $1800 per month. 

Dedicated cores are an optional feature. The default `Shared CPU` setting provisions your deployment on hosts with shared compute resources and incurs no additional charge.

## Scaling per Member

{{site.data.keyword.databases-for-cassandra}} deployments have minimum and maximum allocation for disk and RAM as shown. Scaling deployments through the API/CLI provides more granularity and also allows a user to scale a database instance up to 3.5 TB of disk per member.

Resource | Minimum | Maximum | Scaling Granularity (API/CLI)
----------|-----|-----|-------
Disk | 20 GB per member | 3.5 TB per member | 1024 MB per member
RAM | 12 GB per member | 112 GB per member | 128 MB per member
CPU (if enabled) | 6 CPUs per member | 28 CPUs per member| 1 CPU per member
{: caption="Table 2. Per Member Scaling Limits" caption-side="top"}

