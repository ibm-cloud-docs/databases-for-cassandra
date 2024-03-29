---

copyright:
  years: 2020, 2023
lastupdated: "2023-06-30"

keywords: troubleshooting for Datastax, cassandra, datastax, dse

subcollection: databases-for-cassandra

content-type: troubleshoot

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:support: data-reuse='support'}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{{site.data.keyword.attribute-definition-list}}

# Why can’t I connect to my DataStax deployment?
{: #troubleshoot-connect}
{: #troubleshoot}
{: #support}

{{site.data.keyword.databases-for-cassandra_full}} is deprecated and no longer supported as of 30 June 2024. For more information, see the [deprecation details](/docs/databases-for-cassandra?topic=databases-for-cassandra-deprecation#dep_details).
{: deprecated}

If you encounter errors when connecting to your {{site.data.keyword.databases-for-cassandra_full}} deployment, review these common causes and resolutions.
{: #shortdesc}

You receive an error message or fail to connect to a {{site.data.keyword.databases-for-cassandra}} deployment.  If reviewing application logs, you might see errors that mention intermittent connection timeouts or unable to connect.
{: #tsSymptoms}

Review the following information to troubleshoot and resolve common connectivity problems:
{: #tsResolve}

* An unsecured connection is a common cause of connectivity errors.  All {{site.data.keyword.databases-for-cassandra}} connections use TLS/SSL encryption; {{site.data.keyword.databases-for-cassandra}} rejects unsecured connections.  To avoid errors, make sure you configured a secure connection.  Refer to [Getting Started](/docs/databases-for-cassandra?topic=databases-for-cassandra-getting-started) for an example of a secure connection.
* If you are using a private endpoint, make sure that you specify connection strings that contain the private endpoint (see [Credentials for Private Endpoints](/docs/databases-for-cassandra?topic=cloud-databases-service-endpoints#credentials-for-private-endpoints)) and that you followed the steps in [Connecting through Private Endpoints](/docs/databases-for-cassandra?topic=cloud-databases-service-endpoints#private-endpoint-connections).
* If your application log captures a short connection interruption, that behavior is expected as a normal part of operations for this managed service. You want to design your applications to retry connections when errors are caused by a temporary loss in connectivity to your deployment or to IBM Cloud. However, if you experience several minutes of connection interruption check the Cloud Status for the service. For more information, see [Application-level High-Availability](/docs/databases-for-cassandra?topic=databases-for-cassandra-high-availability#application-level-high-availability).

