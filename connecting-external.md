---
copyright:
  years: 2017, 2020
lastupdated: "2020-08-06"

keywords: drivers, python, java, javascript, certificate, cassandra, datastax, dse

subcollection: databases-for-cassandra

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:external .external}
{:screen: .screen}
{:codeblock: .codeblock}
{:generic: .ph data-hd-programlang='generic'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:javascript: .ph data-hd-programlang='javascript'}
{:pre: .pre}

# Connecting an external application
{: #external-app}

Your applications and drivers use connection strings to make a connection to {{site.data.keyword.databases-for-cassandra_full}}. The service provides connection strings specifically for drivers and applications. Connection strings are displayed in the _Connections_ pane of your deployment's _Overview_, and can also be retrieved from the [cloud databases CLI plug-in](/docs/databases-cli-plugin?topic=databases-cli-plugin-cdb-reference#deployment-connections), and the [API](https://{DomainName}/apidocs/cloud-databases-api#discover-connection-information-for-a-deployment-f-e81026).

The connection strings can be used by any of the credentials you created on your deployment. While you can use the admin user for all of your connections and applications, it might be better to create users specifically for your applications to connect with. Documentation on generating credentials is on the [Getting Connection Strings](/docs/databases-for-cassandra?topic=databases-for-cassandra-connection-strings) page.

Connecting to a {{site.data.keyword.databases-for-cassandra}} deployment: 
- Use the `<formation_id>_<endpoint_type>.zip` file from [Getting Connection Strings](/docs/databases-for-cassandra?topic=databases-for-cassandra-connection-strings) to set up a connection. This file contains the metadata required to connect to your {{site.data.keyword.databases-for-cassandra}} services including connection strings and self-signed certificates.  It does not contain credentials.
- Select and install a supported driver from the list in table 1.
- The driver communicates with the metadata service to retrieve the endpoint
- The driver automatically connects to the appropriate endpoint 

## Connecting with a language's driver

 Drivers are a key component to connecting external applications to your {{site.data.keyword.databases-for-cassandra}} deployment. The following table outlines the drivers that are available from DataStax for this type of connection:  

DataStax Drivers|{{site.data.keyword.databases-for-cassandra}} connection capable
----------|------------
[C/C++ driver](https://docs.datastax.com/en/developer/cpp-driver-dse/latest){: external}| Yes
[C# driver](https://docs.datastax.com/en/developer/csharp-driver-dse/latest){: external}| Yes
[Java driver](https://docs.datastax.com/en/developer/java-driver-dse/latest){: external}| Yes
[Node.js driver](https://docs.datastax.com/en/developer/nodejs-driver-dse/latest){: external}| Yes
[Python driver](https://docs.datastax.com/en/developer/python-dse-driver/latest){: external}| Yes
{: caption="Table 1. DataStax driver connection information" caption-side="top"}

More details on these drivers, including upgrade guides, can be found on the [Developing applications with Apache Cassandra and DataStax Enterprise](https://docs.datastax.com/en/devapp/doc/devapp/aboutDrivers.html) page. 

Nodetool, and other drivers that are not explicitly stated in the connection capable table, are not supported by {{site.data.keyword.databases-for-cassandra}}. 
{: .note} 

## Connecting using CQLSH

The Cassandra Query Language SHell (CQLSH) is a shell that uses the Cassandra Query Language (CQL) to interact with your database. 
You can use CQLSH to interact with your database through CQL commands:
```
./bin/cqlsh -u username -p password -b /path/to/secure-connectdatabase_name.zip
```
{: pre} 

See the following DataStax documentation to get started with CQL:
- [Introduction to CQL](https://docs.datastax.com/en/dse/6.7/cql/cql/cql_using/introTOC.html){: external}
- [CQL quick reference](https://docs.datastax.com/en/dse/6.8/cql/cql/cqlQuickReference.html){: external}
- [Full CQL shell (cqlsh) command reference](https://docs.datastax.com/en/dse/6.8/cql/cql/cql_reference/cqlsh_commands/cqlshCommandsTOC.html){: external}
- [Connecting to databases by using stand-alone CQLSH](https://docs.astra.datastax.com/docs/connecting-to-databases-using-standalone-cqlsh){: external}

## Connecting with Java

Review the GitHub repository for DataStax-Examples specific to [Getting Started with Apache Cassandra and Java using DataStax Astra](https://github.com/DataStax-Examples/getting-started-with-astra-java){: external}

## Connecting with Python

Review the GitHub repository for DataStax-Examples specific to [Getting Started with Apache Cassandra and Python using DataStax Astra](https://github.com/DataStax-Examples/getting-started-with-astra-python){: external}

## Driver TLS and self-signed certificate support

All connections to {{site.data.keyword.databases-for-cassandra}} are TLS 1.2 enabled, so the driver you use to connect needs to be able to support encryption. Your deployment also comes with a self-signed certificate (provided in the secure connect bundle downloadable from the [Connections pane](/docs/databases-for-cassandra?topic=databases-for-cassandra-connection-strings)), so the driver can verify the server upon connection. 

### Using the self-signed certificate

1. Download the secure connect bundle compressed file from the _Connections_ pane of the endpoint information. (You can use the Name that is provided or your own file name).
2. Provide the path to the compressed file that contains the certificate to the CQLSH command to connect the driver or client: 
```
./bin/cqlsh -u admin -p <password> -b /<path_to_secure-connect-bundle.zip>
```
{: .pre}


### CLI plug-in support for the self-signed certificate

You can display the decoded certificate for your deployment with the CLI plug-in with the command `ibmcloud cdb deployment-cacert "your-service-name"`. It decodes the base64 into text. Copy and save the command's output to a file and provide the file's path to the driver.

## Other Drivers

DataStax had a vast array of language drivers that are now built in to a single DataStax driver. This new unified driver can also be used to connect to a {{site.data.keyword.databases-for-cassandra}} deployment. This unified DataStax driver is available at the same locations as their existing OSS drivers. Review the following references: 

- [DataStax Downloads](https://downloads.datastax.com/#datastax-apache-cassandra-drivers){: external} for direct links to download locations 
- [Developing applications with DataStax drivers](https://docs.datastax.com/en/devapp/doc/devapp/aboutDrivers.html){: external} for driver overview details 
- [DataStax Documentation](https://docs.datastax.com/en/developer/driver-matrix/doc/common/driverMatrix.html){: external} for installation information
- [Better Drivers for Cassandra](https://www.datastax.com/blog/2020/01/better-drivers-for-cassandra){: external} blog post that details the move to a unified driver. 

