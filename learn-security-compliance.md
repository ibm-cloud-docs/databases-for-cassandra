---
Copyright:
  years: 2018, 2020
lastupdated: "2020-08-06"

keywords: databases, soc, hipaa, gdpr, terms, cassandra, datastax, dse

subcollection: databases-for-cassandra

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:external .external}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Security and Compliance
{: #security-compliance}

## Protection Against Unauthorized Access

{{site.data.keyword.databases-for-cassandra_full}} use the following methods to protect data in transit or in storage.
- All {{site.data.keyword.databases-for-cassandra}} connections use TLS/SSL encryption for data in transit. The current supported version of this encryption is TLS 1.2.
- Access to the Account, Management Console UI, and API is secured via [Identity and Access Management (IAM)](/docs/databases-for-cassandra?topic=cloud-databases-iam).
- Access to the database is secured through the standard access controls provided by the database. These access controls are configured to require valid database-level credentials that are obtainable only through prior access to the database or through our Management Console UI or API.
- All {{site.data.keyword.databases-for-cassandra}} storage is provided on storage encrypted with LUKS by using AES-256. The default keys are managed by [{{site.data.keyword.keymanagementserviceshort}}](/docs/key-protect?topic=key-protect-about). Bring-your-own-key (BYOK) for encryption is also available through [Key Protect Integration](/docs/databases-for-cassandra?topic=cloud-databases-key-protect).
- IP Allowlisting - All deployments support [allowlisting IP addresses](/docs/databases-for-cassandra?topic=cloud-databases-allowlisting) to restrict access to the service.
- Public and Private Networking - {{site.data.keyword.databases-for-cassandra}} is integrated with [Service Endpoints](/docs/databases-for-cassandra?topic=cloud-databases-service-endpoints). You can select whether to use connections over the public network, the {{site.data.keyword.cloud_notm}} internal network, or both.
- Dedicated Cores - Allocating dedicated cores to your deployment introduces hypervisor-level isolation to your database instance, by using isolated virtual machines to ensure that your data processing remains separated from other customers. It also provides a guaranteed minimum number of CPUs to your deployment. Deployments with dedicated cores in the same Resource Group and {{site.data.keyword.cloud_notm}} Region might share a virtual machine.

## Data Resilience

- [Backups](/docs/databases-for-cassandra?topic=cloud-databases-dashboard-backups) are included in the service. {{site.data.keyword.databases-for-cassandra}} backups reside in [{{site.data.keyword.cos_full_notm}}](/docs/cloud-object-storage?topic=cloud-object-storage-about-cloud-object-storage&cloud-object-storage-about-cloud-object-storage) and are also [encrypted](/docs/cloud-object-storage?topic=cloud-object-storage-security).
- {{site.data.keyword.databases-for-cassandra}} deployments are configured with a leaderless architecture. Deployments contain only data token owners and replicas of that data.
- If you deploy to an {{site.data.keyword.cloud_notm}} Multi-Zone Region (MZR), the nodes are spread over the region's availability zone locations. 
- If you deploy to an {{site.data.keyword.cloud_notm}} Single-Zone Region (SZR), each database node resides on a different host in the data center. 


## ISO 27017, ISO 27018

{{site.data.keyword.databases-for-cassandra}} conforms to the guidelines for information security controls applicable to the provision and use of cloud services that are defined in [ISO 27017](https://www.iso.org/standard/43757.html) and [ISO 27018](https://www.iso.org/standard/76559.html).

## General Data Protection Regulation (GDPR) 

If you have an account with IBM Cloud, your personal data is held by {{site.data.keyword.cloud_notm}}. The {{site.data.keyword.IBM_notm}} Data Processing Addendum (Addendum) applies to the processing of client's personal data by {{site.data.keyword.IBM_notm}} on behalf of client in order to provide {{site.data.keyword.IBM_notm}} standard services.  
[IBM DPA](https://www.ibm.com/support/customer/zz/en/dpa.html){:new_window}

{{site.data.keyword.databases-for-cassandra}} processes limited client Personal Information (PI) in the course of running the service and optimizing the user experience. 

{{site.data.keyword.databases-for-cassandra}} provides a [Data Sheet Addendum (DSA)](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=CD09D2E06DC811E8A0B560E89C071ECC){:new_window} with its policies as a Data Processor regarding content and data protection. 

## HIPAA

{{site.data.keyword.databases-for-cassandra}} meets the required {{site.data.keyword.IBM_notm}} controls that are commensurate with the Health Insurance Portability and Accountability Act of 1996 (HIPAA) Security and Privacy Rule requirements. These requirements include the appropriate administrative, physical, and technical safeguards required of Business Associates in 45 CFR Part 160 and Subparts A and C of Part 164. HIPAA must be requested at the time of provisioning and requires a representative to sign a Business Associate Addendum (BAA) agreement with {{site.data.keyword.IBM_notm}}.

## Terms

- [The IBM Privacy Policy](https://www.ibm.com/privacy/us/en/)
- [The IBM Cloud Notices and Terms of Use](/docs/overview/terms-of-use?topic=overview-terms)


