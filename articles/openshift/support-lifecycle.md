---
title: Azure Red Hat OpenShift support lifecycle
description: Understand the support lifecycle and supported versions for Azure Red Hat OpenShift
author: joharder
ms.author: joharder
ms.service: azure-redhat-openshift
ms.topic: conceptual
ms.date: 12/18/2023
---

# Support lifecycle for Azure Red Hat OpenShift 4

Red Hat releases minor versions of Red Hat OpenShift Container Platform (OCP) roughly every four months. These releases include new features and improvements. Patch releases are more frequent (typically weekly) and are only intended for critical bug fixes within a minor version. These patch releases may include fixes for security vulnerabilities or major bugs.

Azure Red Hat OpenShift is built from specific releases of OCP. This article covers the versions of OCP that are supported for Azure Red Hat OpenShift and details about updates, deprecations, and support policy.

## Red Hat OpenShift versions

Red Hat OpenShift Container Platform uses semantic versioning. Semantic versioning uses different levels of version numbers to specify different levels of versioning. The following table illustrates the different parts of a semantic version number, in this case using the example version number 4.15.14.

|Major version (x)|Minor version (y)|Patch (z)|
|-|-|-|
|4|15|14|

Each number in the version indicates general compatibility with the previous version:

* **Major version**: No major version releases are planned at this time. Major versions change when incompatible API changes or backwards compatibility may be broken.
* **Minor version**: Released approximately every four months. Minor version updates can include feature additions, enhancements, deprecations, removals, bug fixes, security enhancements, and other improvements.
* **Patches**: Typically released each week, or as needed. Patch version updates can include bug fixes, security enhancements, and other improvements.

Customers should aim to run the latest minor release of the major version they're running. For example, if your production cluster is on 4.14, and 4.15 is the latest generally available minor version for the 4 series, you should update to 4.15 as soon as you can. 

### Update channels

Update channels are the mechanism by which users declare the OpenShift Container Platform minor version they intend to update their clusters to. Update channels are tied to a minor version of Red Hat OpenShift Container Platform (OCP). An update channel never includes a minor version above the the channel version, but may include a version below. For instance, the OCP `stable-4.14` update channel never includes an update to a 4.15 release, but will include 4.13. Update channels control only release selection and don't impact the version of the cluster.

Azure Red Hat OpenShift provides support for stable channels only. For example: `stable-4.15`.

You can use the `stable-4.15` channel to update from a previous minor version of Azure Red Hat OpenShift. Clusters updated using fast or candidate channels could put your cluster in Limited Support. 

If you change to a channel that doesn't include your current release, an alert displays and no updates can be recommended. However, you can safely change back to your original channel at any point.

## Azure Red Hat OpenShift version support policy

### Version availability

Versions in Azure Red Hat OpenShift have two distict parts; when an update to a newer version is available, and when a new version is available as an install target for a new cluster.

#### Update availability
Azure Red Hat OpenShift supports generally available (GA) minor versions of Red Hat OpenShift Container Platform from when an update is available in the OpenShift `stable` channel.  Update availability can be checked at the following page, [Red Hat OpenShift Container Platform Update Graph](https://access.redhat.com/labs/ocpupgradegraph/update_path). 

#### Install availability
A version is available as an install target at a later point in time, which can be checked using the [Azure Red Hat OpenShift release calendar](#azure-red-hat-openshift-release-calendar) below or the following command: `az aro get-versions -l [region]`

### Version end-of-life
The end-of-life date for a version of Azure Red Hat OpenShift can be found in the [Azure Red Hat OpenShift release calendar](#azure-red-hat-openshift-release-calendar) below.

> [!NOTE]
> Please note that if customers are running an unsupported Red Hat OpenShift version, they may be asked to update when requesting support for the cluster. Clusters running unsupported Red Hat OpenShift releases are not covered by the Azure Red Hat OpenShift SLA.

### Mandatory ugrades
In extreme circumstances and based on the assessment of the CVE criticality to the environment, a critical patch update may be applied to clusters automatically by Azure Red Hat OpenShift Site Reliability Engineers (SRE). It is a best practice to install patch (z-stream) updates as soon as they are available.

## Limited support status

When a cluster transitions to a limited support status (or also called outside of support) Azure Red Hat OpenShift SREs no longer proactively monitor the cluster.  Furthermore the SLA is no longer applicable and credits requested against the SLA are denied. Though it does not mean that you no longer have product support. In some cases, the cluster can return to a fully-supported status if you remediate the violating factors. However, in other cases, you might have to delete and recreate the cluster.

A cluster might transition to a Limited Support status for many reasons, including the following scenarios:
- If you do not update a cluster to a supported version before the end-of-life date. 
  - There are no runtime or SLA guarantees for versions after their end-of-life date. To receive continued support, update the cluster to a supported version prior to the end-of-life date. If you do not update the cluster prior to the end-of-life date, the cluster transitions to a Limited Support status until it is updated to a supported version.
  - Azure Red Hat OpenShift SREs provide commercially reasonable support to update from an unsupported version to a supported version. However, if a supported update path is no longer available, you might have to create a new cluster and migrate your workloads.

- If you remove or replace any native Azure Red Hat OpenShift components or any other component that is installed and managed by the service.
  - If admin permissions were used, Azure Red Hat OpenShift is not responsible for any of your or your authorized users’ actions, including those that affect infrastructure services, service availability, or data loss. If any such actions are detected, the cluster might transition to a Limited Support status. You should then either revert the action or create a support case to explore remediation steps that might require you to delete and recreate the cluster.

<!--
## Release and deprecation process

You can reference upcoming version releases and deprecations on the [Azure Red Hat OpenShift release calendar](#azure-red-hat-openshift-release-calendar).

For new minor versions of Red Hat OpenShift Container Platform:
* The Azure Red Hat OpenShift SRE team publishes an announcement with the planned date of a new version release, and respective old version deprecation, in the [Azure Red Hat OpenShift Release notes](https://github.com/Azure/OpenShift/releases) at least 30 days prior to removal.
* The Azure Red Hat OpenShift SRE team publishes a service health notification available to all customers with Azure Red Hat OpenShift and portal access, and sends an email to the subscription administrators with the planned version removal dates.

For new patch versions of Red Hat OpenShift Container Platform:
* Because of the urgent nature of patch versions, these can be introduced into the service by Azure Red Hat OpenShift SRE team as they become available.
* In general, the Azure Red Hat OpenShift SRE team doesn't perform broad communications for the installation of new patch versions. However, the team constantly monitors and validates available CVE patches to support them in a timely manner. If customer action is required, the team will notify customers about the update.
-->

## Supported versions policy exceptions

The Azure Red Hat OpenShift SRE team reserves the right to add or remove new/existing versions or delay upcoming minor release versions that have been identified to have one or more critical production impacting bugs or security issues without advance notice.

Specific patch releases may be skipped, or rollout may be accelerated depending on the severity of the bug or security issue.

## Azure Red Hat OpenShift release calendar

See the following guide for the [past Red Hat OpenShift Container Platform (upstream) release history](https://access.redhat.com/support/policy/updates/openshift/#dates).

|OCP Version|OCP GA Availability|Install Availability|End of Life|
|-|-|-|-|
|4.4|May 2020|July 2020|4.6 GA|
|4.5|July 2020| November 2020|4.7 GA|
|4.6|October 2020| February 2021|4.8 GA|
|4.7|February 2021| July 15 2021|4.9 GA|
|4.8|July 2021| Sept 15 2021|4.10 GA|
|4.9|November 2021| February 1 2022|4.11 GA|
|4.10|March 2022| June 21 2022|4.12 GA|
|4.11|August 2022| March 2 2023|February 10 2024|
|4.12|January 2023| August 19 2023|July 17 2024|
|4.13|May 2023| December 15 2023|November 17 2024|
|4.14|October 2023| April 25 2024|May 1 2025|
|4.15|February 2024| Coming soon|June 27 2025|

## FAQ

**What happens when a user updates an OpenShift cluster with a minor version that is not supported?**

Azure Red Hat OpenShift supports installing minor versions consistent with the dates in the table above. A version is supported as soon as an update path to that version is available in the stable channel. If you are running a version past the EOL date above, you are outside of support and will be asked to update to continue receiving support. Updating from an older version to a supported version can be challenging, and in some cases not possible. We recommend you keep your cluster on the latest OpenShift version to avoid potential update issues.

For example:
* If the oldest supported Azure Red Hat OpenShift version is 4.12.z and you are on 4.11.z or older, you are outside of support.
* When the update from 4.11.z to 4.12.z or higher succeeds, you're back within our support policies. 

Reverting your cluster to a previous version, or a rollback, isn't supported. Only updating to a newer version is supported.

**What does "Outside of Support" or "Limited Support" mean?**

If your ARO cluster is running an OpenShift version that isn't on the supported versions list, or is using an [unsupported cluster configuration](./support-policies-v4.md), your cluster is "outside of support". As a result:
- When opening a support ticket for your cluster, you'll be asked to update the cluster to a supported version before receiving support. 
- Any runtime or SLA guarantees for clusters outside of support are voided.
- Clusters outside of support will be patched only on a best effort basis.
- Clusters outside of support won't be monitored.
