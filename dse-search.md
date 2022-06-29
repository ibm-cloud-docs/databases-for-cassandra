---

copyright:
  years: 2021, 2022
lastupdated: "2022-06-29"

keywords: search, gui, api, cli, cassandra, datastax, dse search, cassandra search

subcollection: databases-for-cassandra

---

{:external: .external target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# DSE Search 
{: #dse-search}

DSE Search is a separate scalable part of {{site.data.keyword.databases-for-cassandra_full}} (DSE) version 5.1. DSE Search enables data querying and filtering by using CQL Solr queries. Read more about DSE Search capabilities and benefits in the DataStax Enterprise documentation's [About DSE Search page](https://docs.datastax.com/en/dse/5.1/dse-dev/datastax_enterprise/search/searchAbout.html). 

## DSE Search Pricing
{: #dse-search-pricing}

DSE Search nodes incur added costs. DSE Search nodes are priced according to the {{site.data.keyword.databases-for-cassandra}} normal node price structure [outlined here](/docs/databases-for-cassandra?topic=databases-for-cassandra-pricing). 

## Enabling DSE Search
{: #enabling-dse-search}

To enable DSE Search, scale your Search nodes up from zero to a minimum of 3. Scaling up search nodes creates a three-member plus three-search-node base, if you are using the minimum requirements. Search nodes are only [scalable through the API](/docs/databases-for-cassandra?topic=databases-for-cassandra-horizontal-scaling#adding-nodes-through-the-api).

The DSE Search nodes are horizontally and vertically scalable independent of the DSE member nodes, allowing your indexing workloads to scale independently of your OLTP (online transactional processing) workloads.

## Connecting to the DSE Search Nodes
{: #connecting-dse-search-nodes}

You are able to use Astra-supported clients to communicate with the DSE Search nodes. It is your responsibility to define your key spaces, replication_factors, read/write consistency levels, and other configurations according to your specific needs. 

To support these connections, you are provided with two bundles: one for connecting to the "search" data center and one for connecting to the regular DSE nodes. These bundles are Base64-encoded compressed files and are accessible through the [connections API endpoint](https://pages.github.ibm.com/compose/apidocs/cloud-databases-api-static.html#tag/Connections).

Example instructions for connecting to DSE Search with a Java client can be found in the DataStax Enterprise documentation's [DataStax Java Driver 4.9 (Earlier version) page](https://docs.datastax.com/en/developer/java-driver/4.9/manual/core/statements/){: .external}.


## Scaling DSE Search nodes
{: #scaling-dse-search-nodes}

Refer to [Scaling in the API documentation](/docs/databases-for-cassandra?topic=databases-for-cassandra-resources-scaling#scaling-in-the-api) for examples of how to scale nodes in {{site.data.keyword.databases-for-cassandra}}. 

## DSE Search Recommendations
{: #dse-search-recs}

### Architecture
{: #dse-search-recs-architecture}

- Avoid use of tokenizer when not needed.
- Design your data model in a way that avoids the use of `joins`. See the DataStax documentation to learn how to [generate an index with joins disabled](https://docs.datastax.com/en/dse/5.1/dse-dev/datastax_enterprise/search/createSiDisableJoins.html){: .external}. 

### Sizing
{: #dse-search-recs=sizing}

- Keep your index under 250 GB.
- Use no more than 500 GB cumulated indexes per node.
- Index only what you need to search.
- For more information on managing search indexes, see [About search index management](https://docs.datastax.com/en/dse/5.1/dse-dev/datastax_enterprise/search/indexMgmt.html){: .external}.

## Resources
{: #dse-search-resources}

For more information, see [DSE Search documentation](https://docs.datastax.com/en/dse/5.1/dse-dev/datastax_enterprise/search/searchTOC.html){: .external} and [Capacity planning for DSE Search](https://docs.datastax.com/en/dse-planning/doc/planning/capacityPlanningSearch.html){: .external}
