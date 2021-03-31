---
copyright:
  years: 2020, 2021
lastupdated: "2020-03-30"

keywords: monitoring, metrics, iops, disk usage, memory usage, connection usage, cassandra, datastax, dse

subcollection: databases-for-cassandra

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:external .external}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}

# Monitoring Integration
{: #monitoring}

Monitoring for {{site.data.keyword.databases-for-cassandra_full}} deployments is provided through integration with the {{site.data.keyword.monitoringfull}} service. Your deployments forward selected information so you can monitor deployment health and resource usage. To see your {{site.data.keyword.databases-for-cassandra}} dashboards in {{site.data.keyword.monitoringfull_notm}}, you must [Enable Platform Metrics](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-platform_metrics_enabling) in the same region as your deployment. If you have deployments in more than one region, you must provision {{site.data.keyword.monitoringfull_notm}} and enable platform metrics in each region.

To access {{site.data.keyword.monitoringfull_notm}} from your deployment, use the _Monitoring_ link from the right menu. (If you do not already have a monitoring service in the same region as your deployment it says _Add monitoring_.)

The default dashboards are not shown until database instances begin emitting metrics.
{: .tip}

![The Monitoring link in a deployment](images/monitoring-ui-link.png)

To access your deployment's monitoring dashboard from {{site.data.keyword.monitoringfull_notm}}, it's in the sidebar, under _IBM_.

![Cloud databases dashboard in monitoring](images/monitoring-ibm-db-list.png)

## Monitoring Availability

{{site.data.keyword.monitoringfull_notm}} is available for deployments in every region. Deployments in Multi-zone Regions (MZRs) - `eu-gb`, `eu-de`, `us-east`, `us-south`, `jp-tok`, `au-syd` - have their metrics in the corresponding region.

If you have deployments that are in a Single-zone Region (SZR) - `osl01`, `che01`, or `seo01` - then your logs are forwarded to an {{site.data.keyword.monitoringfull_notm}} instance in another region. You need to provision monitoring instances in the region where your metrics are forwarded to. Metrics for deployments in `osl01` go to `eu-gb`. Metrics for deployments in `seo01` and `che01` go to `jp-tok`. 

## Available Metrics
{: metrics-by-plan}

| Metric Name |
|-----------|
| [Disk read latency mean](#ibm_databases_for_cassandra_disk_read_latency_mean) | 
| [Disk write latency mean](#ibm_databases_for_cassandra_disk_write_latency_mean) | 
| [IO utilization in percent 5-minute average](#ibm_databases-for-cassandra_disk_io_utilization_percent_average_5m) |
| [IO utilization in percent 15-minute average](#ibm_databases-for-cassandra_disk_io_utilization_percent_average_15m) | 
| [IO utilization in percent 30-minute average](#ibm_databases-for-cassandra_disk_io_utilization_percent_average_30m) | 
| [IO utilization in percent 60-minute average](#ibm_databases-for-cassandra_disk_io_utilization_percent_average_60m) | 
| [IOPS read and write total count for an instance.](#ibm_databases-for-cassandra_disk_iops_read_write_total) | 
| [Max allowed memory for an instance.](#ibm_databases-for-cassandra_memory_limit_bytes) | 
| [The total number of connections used.](#ibm_databases-for-cassandra_total_connections) | 
| [Total disk space for an instance.](#ibm_databases-for-cassandra_disk_total_bytes) | 
| [Used CPU for an instance.](#ibm_databases-for-cassandra_cpu_used_percent) | 
| [Used disk space for an instance.](#ibm_databases-for-cassandra_disk_used_bytes) | 
| [Used memory for an instance.](#ibm_databases-for-cassandra_memory_used_bytes) | 
{: caption="Table 1. Available Metrics" caption-side="top"}

### Disk read latency mean
{: #ibm_databases_for_cassandra_disk_read_latency_mean}

Disk read latency mean

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_databases_for_cassandra_disk_read_latency_mean`|
| `Metric Type` | `gauge` |
| `Value Type`  | `count` |
| `Segment By` | `Service instance` |
{: caption="Table 24: Disk read latency mean metric metadata" caption-side="top"}
### Disk write latency mean
{: #ibm_databases_for_cassandra_disk_write_latency_mean}

Disk write latency mean

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_databases_for_cassandra_disk_write_latency_mean`|
| `Metric Type` | `gauge` |
| `Value Type`  | `count` |
| `Segment By` | `Service instance` |
{: caption="Table 26: Disk write latency mean metric metadata" caption-side="top"}

### IO utilization in percent 5-minute average
{: #ibm_databases-for-cassandra_disk_io_utilization_percent_average_5m}

How much disk I/O was used over 5 minutes as a percentage of total disk I/O available.

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_databases-for-cassandra_disk_io_utilization_percent_average_5m`|
| `Metric Type` | `gauge` |
| `Value Type`  | `percent` |
| `Segment By` | `Service instance` |
{: caption="Table 2. IO utilization in percent 5 minute average metric metadata" caption-side="top"}

### IO utilization in percent 15-minute average
{: #ibm_databases-for-cassandra_disk_io_utilization_percent_average_15m}

How much disk I/O was used over 15 minutes as a percentage of total disk I/O available.

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_databases-for-cassandra_disk_io_utilization_percent_average_15m`|
| `Metric Type` | `gauge` |
| `Value Type`  | `percent` |
| `Segment By` | `Service instance` |
{: caption="Table 3. IO utilization in percent 15 minute average metric metadata" caption-side="top"}

### IO utilization in percent 30-minute average
{: #ibm_databases-for-cassandra_disk_io_utilization_percent_average_30m}

How much disk I/O was used over 30 minutes as a percentage of total disk I/O available.

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_databases-for-cassandra_disk_io_utilization_percent_average_30m`|
| `Metric Type` | `gauge` |
| `Value Type`  | `percent` |
| `Segment By` | `Service instance` |
{: caption="Table 4. IO utilization in percent 30 minute average metric metadata" caption-side="top"}

### IO utilization in percent 60-minute average
{: #ibm_databases-for-cassandra_disk_io_utilization_percent_average_60m}

How much disk I/O was used over 60 minutes as a percentage of total disk I/O available.

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_databases-for-cassandra_disk_io_utilization_percent_average_60m`|
| `Metric Type` | `gauge` |
| `Value Type`  | `percent` |
| `Segment By` | `Service instance` |
{: caption="Table 5. IO utilization in percent 60 minute average metric metadata" caption-side="top"}

### IOPS read and write total count for an instance
{: #ibm_databases-for-cassandra_disk_iops_read_write_total}

How many input/output operations per second your deployment is performing.

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_databases-for-cassandra_disk_iops_read_write_total`|
| `Metric Type` | `gauge` |
| `Value Type`  | `count` |
| `Segment By` | `Service instance` |
{: caption="Table 6. IOPS read and write total count for an instance metric metadata" caption-side="top"}

### Max allowed memory for an instance
{: #ibm_databases-for-cassandra_memory_limit_bytes}

The maximum amount of memory available to your deployment.

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_databases-for-cassandra_memory_limit_bytes`|
| `Metric Type` | `gauge` |
| `Value Type`  | `byte` |
| `Segment By` | `Service instance` |
{: caption="Table 7. Max allowed memory for an instance metric metadata" caption-side="top"}

### The total number of connections in use
{: #ibm_databases-for-cassandra_total_connections}

The total number of connections in use.

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_databases-for-cassandra_total_connections`|
| `Metric Type` | `gauge` |
| `Value Type`  | `count` |
| `Segment By` | `Service instance` |
{: caption="Table 9. The total number of connections in use metric metadata" caption-side="top"}

### Total disk space for an instance
{: #ibm_databases-for-cassandra_disk_total_bytes}

Represents the total amount of disk available to your deployment.

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_databases-for-cassandra_disk_total_bytes`|
| `Metric Type` | `gauge` |
| `Value Type`  | `byte` |
| `Segment By` | `Service instance` |
{: caption="Table 10. Total disk space for an instance metric metadata" caption-side="top"}

### Used CPU for an instance
{: #ibm_databases-for-cassandra_cpu_used_percent}

How much CPU is used as a percentage of total CPU available.

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_databases-for-cassandra_cpu_used_percent`|
| `Metric Type` | `gauge` |
| `Value Type`  | `percent` |
| `Segment By` | `Service instance` |
{: caption="Table 11. Used CPU for an instance metric metadata" caption-side="top"}

### Used disk space for an instance
{: #ibm_databases-for-cassandra_disk_used_bytes}

How much disk your deployment is using.

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_databases-for-cassandra_disk_used_bytes`|
| `Metric Type` | `gauge` |
| `Value Type`  | `byte` |
| `Segment By` | `Service instance` |
{: caption="Table 12. Used disk space for an instance metric metadata" caption-side="top"}

### Used memory for an instance
{: #ibm_databases-for-cassandra_memory_used_bytes}

How much memory your deployment is using.

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_databases-for-cassandra_memory_used_bytes`|
| `Metric Type` | `gauge` |
| `Value Type`  | `byte` |
| `Segment By` | `Service instance` |
{: caption="Table 13. Used memory for an instance metric metadata" caption-side="top"}

### Used JVM heap percent 
{: #ibm_databases_for_cassandra_jvm_heap_percent}

How much Java Virtual Machine (JVM) heap memory your deployment is using.

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_databases_for_cassandra_jvm_heap_percent`|
| `Metric Type` | `graph` |
| `Value Type`  | `percent` |
| `Segment By` | `Service instance` |
{: caption="Table 13. Used JVM percent for an instance metric metadata" caption-side="top"}

### Garbage collection percent 15-minute average
{: #ibm_cassandra_garbage_collection_percent_average_15m}

How much garbage collection has been used over 15 minutes as a percentage of total your deployment is using.

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_cassandra_garbage_collection_percent_average_15m`|
| `Metric Type` | `graph` |
| `Value Type`  | `percent` |
| `Segment By` | `Service instance` |
{: caption="Table 13. Used JVM percent for an instance metric metadata" caption-side="top"}

## Attributes for Segmentation
{: #attributes-for-segmentation}

### Global Attributes
{: #global-attributes}

The following attributes are available for segmenting all of the metrics listed.

| Attribute | Attribute Name | Attribute Description |
|-----------|----------------|-----------------------|
| `Cloud Type` | `ibm_ctype` | The cloud type is a value of public, dedicated, or local. |
| `Location` | `ibm_location` | The location of the monitored resource - might be a region, data center, or global. |
| `Resource` | `ibm_resource` | The resource that is measured by the service - typically an identifying name or GUID. |
| `Resource Type` | `ibm_resource_type` | The type of the resource that is measured by the service. |
| `Scope` | `ibm_scope` | The scope is the account, organization, or space GUID associated with this metric. |
{: caption="Table 14. Global Attributes Metadata" caption-side="top"}

### Additional Attributes
{: #additional-attributes}

The following attributes are available for segmenting one or more attributes as described in the previous references.  See the individual metrics for segmentation options.

| Attribute | Attribute Name | Attribute Description |
|-----------|----------------|-----------------------|
| `Service instance` | `ibm_service_instance` | The service instance segment identifies the instance that the metric is associated with. |
{: caption="Table 15. Additional Attributes Metadata" caption-side="top"}

