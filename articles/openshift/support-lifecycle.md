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

Azure Red Hat OpenShift is built from specific releases of OCP. This article covers the versions of OCP that are supported for Azure Red Hat OpenShift and details about upgrades, deprecations, and support policy.

## Red Hat OpenShift versions

Red Hat OpenShift Container Platform uses semantic versioning. Semantic versioning uses different levels of version numbers to specify different levels of versioning. The following table illustrates the different parts of a semantic version number, in this case using the example version number 4.14.16.

|Major version (x)|Minor version (y)|Patch (z)|
|-|-|-|
|4|14|16|

Each number in the version indicates general compatibility with the previous version:

* **Major version**: No major version releases are planned at this time. Major versions change when incompatible API changes or backwards compatibility may be broken.
* **Minor version**: Released approximately every four months. Minor version upgrades can include feature additions, enhancements, deprecations, removals, bug fixes, security enhancements, and other improvements.
* **Patches**: Typically released each week, or as needed. Patch version upgrades can include bug fixes, security enhancements, and other improvements.

Customers should aim to run the latest minor release of the major version they're running. For example, if your production cluster is on 4.13, and 4.14 is the latest generally available minor version for the 4 series, you should upgrade to 4.14 as soon as you can. 

### Upgrade channels

Upgrade channels are tied to a minor version of Red Hat OpenShift Container Platform (OCP). An upgrade channel never includes a minor version above the the channel version, but may include a version below. For instance, the OCP `stable-4.13` upgrade channel never includes an upgrade to a 4.14 release, but will include 4.12. Upgrade channels control only release selection and don't impact the version of the cluster.

Azure Red Hat OpenShift provides support for stable channels only. For example: `stable-4.14`.

You can use the `stable-4.14` channel to upgrade from a previous minor version of Azure Red Hat OpenShift. Clusters upgraded using fast, prerelease, and candidate channels could put your cluster in Limited Support. 

If you change to a channel that doesn't include your current release, an alert displays and no updates can be recommended. However, you can safely change back to your original channel at any point.

## Red Hat OpenShift Container Platform version support policy

Azure Red Hat OpenShift supports generally available (GA) minor versions of Red Hat OpenShift Container Platform for at least 14-months from when it became available as a stable release. In other words, an OpenShift version will be supported on Azure Red Hat OpenShift for at least 14 months from the date it became available as an upgrade.

If available in a stable upgrade channel, newer minor releases (N+1, N+2, etc...) available in upstream OCP, are supported.

In extreme circumstances a critical patch update may be applied to clusters automatically by Azure Red Hat OpenShift Site Reliability Engineers (SRE). Generally, customers are encouraged to install patch (z-stream) updates as soon as they are available.

> [!NOTE]
> Please note that if customers are running an unsupported Red Hat OpenShift version, they may be asked to upgrade when requesting support for the cluster. Clusters running unsupported Red Hat OpenShift releases are not covered by the Azure Red Hat OpenShift SLA.

## Limited support status

When a cluster transitions to a limited support status (or also called outside of support) Azure Red Hat OpenShift SREs no longer proactively monitor the cluster.  Furthermore the SLA is no longer applicable and credits requested against the SLA are denied. Though it does not mean that you no longer have product support. In some cases, the cluster can return to a fully-supported status if you remediate the violating factors. However, in other cases, you might have to delete and recreate the cluster.

A cluster might transition to a Limited Support status for many reasons, including the following scenarios:
- If you do not upgrade a cluster to a supported version before the end-of-life date. 
  - There are no runtime or SLA guarantees for versions after their end-of-life date. To receive continued support, upgrade the cluster to a supported version prior to the end-of-life date. If you do not upgrade the cluster prior to the end-of-life date, the cluster transitions to a Limited Support status until it is upgraded to a supported version.
  - Azure Red Hat OpenShift SREs provide commercially reasonable support to upgrade from an unsupported version to a supported version. However, if a supported upgrade path is no longer available, you might have to create a new cluster and migrate your workloads.

- If you remove or replace any native Azure Red Hat OpenShift components or any other component that is installed and managed by the service.
  - If admin permissions were used, Azure Red Hat OpenShift is not responsible for any of your or your authorized users’ actions, including those that affect infrastructure services, service availability, or data loss. If any such actions are detected, the cluster might transition to a Limited Support status. You should then either revert the action or create a support case to explore remediation steps that might require you to delete and recreate the cluster.

## Release and deprecation process

You can reference upcoming version releases and deprecations on the [Azure Red Hat OpenShift release calendar](#azure-red-hat-openshift-release-calendar).

For new minor versions of Red Hat OpenShift Container Platform:
* The Azure Red Hat OpenShift SRE team publishes an announcement with the planned date of a new version release, and respective old version deprecation, in the [Azure Red Hat OpenShift Release notes](https://github.com/Azure/OpenShift/releases) at least 30 days prior to removal.
* The Azure Red Hat OpenShift SRE team publishes a service health notification available to all customers with Azure Red Hat OpenShift and portal access, and sends an email to the subscription administrators with the planned version removal dates.
* Customers have 30 days from version removal to upgrade to a supported minor version release to continue receiving support. Bug fixes or CVEs encountered during this period will require an upgrade to a currently supported version.

For new patch versions of Red Hat OpenShift Container Platform:
* Because of the urgent nature of patch versions, these can be introduced into the service by Azure Red Hat OpenShift SRE team as they become available.
* In general, the Azure Red Hat OpenShift SRE team doesn't perform broad communications for the installation of new patch versions. However, the team constantly monitors and validates available CVE patches to support them in a timely manner. If customer action is required, the team will notify customers about the upgrade.

## Supported versions policy exceptions

The Azure Red Hat OpenShift SRE team reserves the right to add or remove new/existing versions or delay upcoming minor release versions that have been identified to have one or more critical production impacting bugs or security issues without advance notice.

Specific patch releases may be skipped, or rollout may be accelerated depending on the severity of the bug or security issue.

## Azure Red Hat OpenShift release calendar

See the following guide for the [past Red Hat OpenShift Container Platform (upstream) release history](https://access.redhat.com/support/policy/updates/openshift/#dates).

|OCP Version|Upgrade Availability|Install Availability|End of Life|
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

## FAQ

**What happens when a user upgrades an OpenShift cluster with a minor version that is not supported?**

Azure Red Hat OpenShift supports installing minor versions consistent with the dates in the table above. A version is supported as soon as an upgrade path to that version is available in the stable channel. If you are running a version past the EOL date above, you are outside of support and will be asked to upgrade to continue receiving support. Upgrading from an older version to a supported version can be challenging, and in some cases not possible. We recommend you keep your cluster on the latest OpenShift version to avoid potential upgrade issues.

For example:
* If the oldest supported Azure Red Hat OpenShift version is 4.12.z and you are on 4.11.z or older, you are outside of support.
* When the upgrade from 4.11.z to 4.12.z or higher succeeds, you're back within our support policies. 

Reverting your cluster to a previous version, or a rollback, isn't supported. Only upgrading to a newer version is supported.

**What does "Outside of Support" mean?**

If your ARO cluster is running an OpenShift version that isn't on the supported versions list, or is using an [unsupported cluster configuration](./support-policies-v4.md), your cluster is "outside of support". As a result:
- When opening a support ticket for your cluster, you'll be asked to upgrade the cluster to a supported version before receiving support, unless you are within the 30-day grace period after version support ends. 
- Any runtime or SLA guarantees for clusters outside of support are voided.
- Clusters outside of support will be patched only on a best effort basis.
- Clusters outside of support won't be monitored.

**I don't see a newer version of OpenShift in the release calendar, can I still upgrade and be supported?**

If a newer version of OpenShift is available in the "stable" upgrade channel, then you can upgrade to that new version and be fully supported.  For example, if your cluster is currently on 4.14.z and now version 4.15.z is available in the OCP `stable-4.15` channel, even though 4.15 is not listed in the release calendar, you can upgrade to 4.15.z and be fully supported.
