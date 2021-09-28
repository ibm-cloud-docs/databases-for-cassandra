---

Copyright:
  years: 2021
lastupdated: "2021-04-22"

keywords: search, gui, api, cli, cassandra, datastax, dse

subcollection: databases-for-cassandra

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:external .external}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# DSE Search 

DSE Search is a separate scalable part of {{site.data.keyword.databases-for-cassandra_full}} (DSE) version 5.1. DSE Search enables data querying and filtering by using CQL Solr queries. Read more about DSE Search capabilities and benefits in the DataStax Enterprise documentation's [About DSE Search page](https://docs.datastax.com/en/dse/5.1/dse-dev/datastax_enterprise/search/searchAbout.html). 

## DSE Search Pricing

DSE Search nodes incur added costs. DSE Search nodes are priced according to the {{site.data.keyword.databases-for-cassandra}} normal node price structure [outlined here](/docs/databases-for-cassandra?topic=databases-for-cassandra-pricing). 

## Enabling DSE Search

To enable DSE Search, scale your Search nodes up from zero to a minimum of 3. Scaling up search nodes creates a three-member plus three-search-node base, if you are using the minimum requirements. Search nodes are only [scalable through the API](/docs/databases-for-cassandra?topic=databases-for-cassandra-horizontal-scaling#adding-nodes-through-the-api).

The DSE Search nodes are horizontally and vertically scalable independent of the DSE member nodes, allowing you to scale your indexing workloads independent of your OLTP (online transactional processing) workloads.

## Connecting to the DSE Search Nodes

You are able to use Astra supported clients to communicate with the DSE Search nodes. It is your responsibility to define your keyspaces, replication_factors, read/write consistency levels, and other configurations according to your specific needs. 

To support these connections, you are provided with two bundles: one for connecting to the "search" data center and one for connecting to the regular DSE nodes. These bundles are Base64-encoded zip files and are accessible via the [connections API endpoint](https://pages.github.ibm.com/compose/apidocs/cloud-databases-api-static.html#tag/Connections).

Example instructions for connecting to DSE Search with a Java client can be found in the DataStax Enterprise documentation's [DataStax Java Driver 4.9 (Earlier version) page](https://docs.datastax.com/en/developer/java-driver/4.9/manual/core/statements/).


## Scaling DSE Search nodes

Refer to [Scaling in the API documentation](/docs/databases-for-cassandra?topic=databases-for-cassandra-resources-scaling#scaling-in-the-api) for examples of how to scale nodes in {{site.data.keyword.databases-for-cassandra}}. 

## DSE Search Recommendations
### Architecture

- Avoid using tokenizer when not needed.
- Design your data model in a way that avoids the use of `joins`. See the DataStax documentation to learn how to [generate an index with joins disabled](https://docs.datastax.com/en/dse/5.1/dse-dev/datastax_enterprise/search/createSiDisableJoins.html). 

### Sizing
- Keep your index under 250 GB.
- Use no more than 500 GB cumulated indexes per node.
- Index only what you need to search.
- See the DataStax documentation on [managing search indexes](https://docs.datastax.com/en/dse/5.1/dse-dev/datastax_enterprise/search/indexMgmt.html) for more information.


## Resources

For more detailed information on configuration and use of DSE Search, refer to the following external links to the DataStax Enterprise documentation:

- [DSE Search documentation](https://docs.datastax.com/en/dse/5.1/dse-dev/datastax_enterprise/search/searchTOC.html)
- [Capacity planning for DSE Search](https://docs.datastax.com/en/dse-planning/doc/planning/capacityPlanningSearch.html)


