---

copyright:
  years: 2015, 2023
lastupdated: "2023-06-20"

keywords: databases for datastax, deprecation

subcollection: databases-for-cassandra

---

{{site.data.keyword.attribute-definition-list}}

# Deprecation of IBM Cloud Databases for DataStax
{: #deprecation}

{{site.data.keyword.databases-for-cassandra_full}} is deprecated and no longer supported as of 30 June 2024. For more information, see the [deprecation details](#dep_details).
{: deprecated}

## Overview
{: #dep_ov}

{{site.data.keyword.cloud}} is announcing the full deprecation of {{site.data.keyword.databases-for-cassandra}} on 30 June 2024. Then, any deployments of {{site.data.keyword.databases-for-cassandra}} still running will be permanently disabled and deprovisioned. See the [deprecation details](#dep_details) for specific implications.
{: shortdesc}

The following describes the details of the deprecation, possible migration targets for your applications, and additional information.

## Timeline
{: #dep_timeline}

The timeline for this deprecation is as follows:

| Stage | Date | Description |
| ---------------- | ----------------- | ------------------------------------------------------------ |
| Announcement     | 30 June 2023      | Announcement of the {{site.data.keyword.databases-for-cassandra}} deprecation. All current {{site.data.keyword.databases-for-cassandra}} users as of June 2023 will receive an email with information about the deprecation. Notifications will be put into the {{site.data.keyword.cloud}} console and related screens. |
| End-of-Marketing | 30 December 2023 | All {{site.data.keyword.cloud}} users, other than those who have an {{site.data.keyword.databases-for-cassandra}} application that is deployed, will be blocked from new application deployments. |
| Reminders        | Ongoing           | Periodic reminders will be sent to all users with running {{site.data.keyword.databases-for-cassandra}} applications that the end-of-support date is coming, with increasing frequency as the date approaches. |
| End-of-Support   | 30 June 2024      | Running deployments of {{site.data.keyword.databases-for-cassandra}} will be permanently disabled and deprovisioned by the {{site.data.keyword.databases-for}} team. |
{: caption="Table 1. Deprecation timeline" caption-side="bottom"}

## {{site.data.keyword.databases-for-cassandra}} deprecation details
{: #dep_details}

Some details of this announcement:

* A "deprecation" is a process, and we've announced the beginning of that process. It begins with the "Announcement" (this page), continues with "End-of-Marketing", and ends with "End-of-Support". Nothing happens until those announced dates above.

* At the "End-of-Marketing", users that don't have {{site.data.keyword.databases-for-cassandra}} running workloads will be blocked from deploying new applications. All users that have {{site.data.keyword.databases-for-cassandra}} instances that are deployed can still keep using them and restoring from backups if necessary. 

* At the "End-of-Support", all {{site.data.keyword.databases-for-cassandra}} deployments will be stopped and deleted.

* All other services that you have been using in {{site.data.keyword.cloud_notm}} are unaffected - the {{site.data.keyword.databases-for-cassandra}} deprecation refers only to the specific {{site.data.keyword.databases-for-cassandra}} deployed instances.

* Reminders of the approaching "End-of-Support" date will continue to be sent periodically by email to all users that have {{site.data.keyword.databases-for-cassandra}} deployments.


## {{site.data.keyword.databases-for-cassandra}} user next steps
{: #dep_nextsteps}

The following is a suggested checklist to plan your migration:

1. Understand and plan for the timeline and key milestone dates.
2. Evaluate the {{site.data.keyword.cloud}} database migration options.
3. Pick an {{site.data.keyword.cloud}} service migration database target that best meets your requirements and goals.
4. Migrate your data to the target {{site.data.keyword.cloud}} service and compare the operation of your applications.
5. When ready, move application traffic as appropriate. 
6. When ready, delete your {{site.data.keyword.databases-for-cassandra}} deployments before the End-of-Support date.

## Customer Support
{: #dep_mig_assist}

If you need help with your {{site.data.keyword.databases-for-cassandra}} migration, [open a support ticket](https://www.ibm.com/cloud/support){: external} in the first instance and we will be in touch.
