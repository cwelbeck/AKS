# Azure Kubernetes Service Changelog

## Release 2021-04-05

This release is rolling out to all regions - ETA for conclusion 2021-04-14 for public cloud.

### Announcements

* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.
* Kubernetes version 1.17 has now been deprecated since March 31st.
* Before k8s 1.20 a bug would allow exec probes to run indefinitely, ignoring any timeoutSeconds configuration value. The previous buggy behavior has been fixed, and timeouts are now enforced. Additionally, this change introduces a new default timeout of 1 second. Please audit all your existing exec probes to make sure that it is appropriate to enforce a 1 second timeout. If not, please provide an explicit timeoutSeconds value that is appropriate for each [exec probe](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/#configure-probes).
* CSI Drivers will become default for [Kubernetes versions 1.21+](https://docs.microsoft.com/azure/aks/csi-storage-drivers).
* Previous [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) deprecation was June 30th 2021. To better align with Kubernetes Upstream pod security policy (preview) deprecation will begin with Kubernetes version 1.21, with its removal in version 1.25. As Kubernetes Upstream approaches that milestone, the Kubernetes community will be working to document viable alternatives.
* For all AKS clusters using Kubernetes v1.20+, CoreDNS will be upgraded to version 1.8.3. This will remove `resyncperiod` and `upstream`from the Kubernetes plugin.

### Release Notes

* Bug Fixes
  * Fixed a bug in runc that caused pods to be stuck in container creation in containerd 1.4.3 and 1.4.4.
  * Fixed a bug in VMAS that accidently enabled VMAS to be scaled down to 0.
* Behavioral Changes
  * Increased nslookup/nc timeout to 10s for Provisioning CSE in nodes.
* Component Updates
  * Removed Cross-namespace owner references in Azure Policy on AKS v1.20+.
  * Updated omsagent to [ciprod03262021](https://github.com/microsoft/Docker-Provider/blob/ci_prod/ReleaseNotes.md#03262021--).
  * Updated Azure Confidential Compute Image to 1.16 with updated webhook and plugin version, to include a liveness probe.
  * Calico will upgrade to 3.18.1 to correct the policy for Tigera operator which requires hostPath. For the base Calico on linux, we will automatically upgrade cluster with Calico 3.17.2. For the Windows node pools, calico will be upgraded to v3.18.1 in any agent pool update/upgrade operations, for example, upgrade the cluster, update the node image, or upgrade the node pool. For detailed updates on Calico, please read more [here](https://docs.projectcalico.org/archive/v3.18/release-notes/).
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1817.210330](vhd-notes/AKSWindows/2019/17763.1817.210330.txt).
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2021.03.31](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2021.03.31.txt).
  * AKS Ubuntu 18.04 image updated to [AKSUbuntu-1804-2021.03.31](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2021.03.31.txt).

## Release 2021-03-29

This release is rolling out to all regions - ETA for conclusion 2021-04-07 for public cloud.

### Announcements

* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.
* Kubernetes version 1.17 has now been deprecated since March 31st.
* Before k8s 1.20 a bug would allow exec probes to run indefinitely, ignoring any timeoutSeconds configuration value. The previous buggy behavior has been fixed, and timeouts are now enforced. Additionally, this change introduces a new default timeout of 1 second. Please audit all your existing exec probes to make sure that it is appropriate to enforce a 1 second timeout. If not, please provide an explicit timeoutSeconds value that is appropriate for each [exec probe](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/#configure-probes).
* CSI Drivers will become default for [Kubernetes versions 1.21+](https://docs.microsoft.com/azure/aks/csi-storage-drivers).
* Previous [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) deprecation was June 30th 2021. To better align with Kubernetes Upstream pod security policy (preview) deprecation will begin with Kubernetes version 1.21, with its removal in version 1.25. As Kubernetes Upstream approaches that milestone, the Kubernetes community will be working to document viable alternatives.
* For all AKS clusters using Kubernetes v1.20+, CoreDNS will be upgraded to version 1.8.3. This will remove `resyncperiod` and `upstream`from the Kubernetes plugin.

### Release Notes

* New Features
  * `brazilsouth`, `centralindia`, `eastasia` and `francecentral` are all new supported regions for Virtual Node. The `southindia` region has been removed from the supported region list.
* Preview Features
  * Open Service Mesh (OSM), as a managed AKS add-on, is now in public preview.
* Component Updates
  * Calico will upgrade to 3.18.1 to correct the policy for Tigera operator which requires hostPath. For the base Calico on linux, we will automatically upgrade cluster with Calico 3.17.2. For the Windows node pools, calico will be upgraded to v3.18.1 in any agent pool update/upgrade operations, for example, upgrade the cluster, update the node image, or upgrade the node pool. For detailed updates on Calico, please read more [here](https://docs.projectcalico.org/archive/v3.18/release-notes/).

## Release 2021-03-22

This release is rolling out to all regions - ETA for conclusion 2021-03-31 for public cloud.

### Announcements

* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.
* Next week, Kubernetes version 1.17 will be deprecated on March 31st.
* Before k8s 1.20 a bug would allow exec probes to run indefinitely, ignoring any timeoutSeconds configuration value. The previous buggy behavior has been fixed, and timeouts are now enforced. Additionally, this change introduces a new default timeout of 1 second. Please audit all your existing exec probes to make sure that it is appropriate to enforce a 1 second timeout. If not, please provide an explicit timeoutSeconds value that is appropriate for each [exec probe](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/#configure-probes).
* CSI Drivers will become default for [Kubernetes versions 1.21+](https://docs.microsoft.com/azure/aks/csi-storage-drivers).
* Previous [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) deprecation was June 30th 2021. To better align with Kubernetes Upstream pod security policy (preview) deprecation will begin with Kubernetes version 1.21, with its removal in version 1.25. As Kubernetes Upstream approaches that milestone, the Kubernetes community will be working to document viable alternatives.
* For all AKS clusters using Kubernetes v1.20+, CoreDNS will be upgraded to version 1.8.3. This will remove `resyncperiod` and `upstream`from the Kubernetes plugin.

### Release Notes

* Bug Fixes
  * Fixed an issue regarding indecisiveness in Kubernetes versions and the auto-upgrade feature in ARM templates. Read more [here](https://github.com/Azure/AKS/issues/2138).
* Component Updates
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1817.210310](vhd-notes/AKSWindows/2019/17763.1817.210310.txt).
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2021.03.17](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2021.03.17.txt).
  * AKS Ubuntu 18.04 image updated to [AKSUbuntu-1804-2021.03.17](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2021.03.17.txt).

## Release 2021-03-15

This release is rolling out to all regions - ETA for conclusion 2021-03-24 for public cloud.

### Announcements

* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on June 30th, 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.
* Kubernetes version 1.17 will be deprecated in the last week of March 2021.
* Before k8s 1.20 a bug would allow exec probes to run indefinitely, ignoring any timeoutSeconds configuration value. The previous buggy behavior has been fixed, and timeouts are now enforced. Additionally, this change introduces a new default timeout of 1 second. Please audit all your existing exec probes to make sure that it is appropriate to enforce a 1 second timeout. If not, please provide an explicit timeoutSeconds value that is appropriate for each [exec probe](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/#configure-probes).
* CSI Drivers will become default for [Kubernetes versions 1.21+](https://docs.microsoft.com/azure/aks/csi-storage-drivers).

### Release Notes

* Bug Fixes
  * Fixed an issue with using a managed identity created in a different subscription from the cluster while using pod identity [github](https://github.com/Azure/aad-pod-identity/issues/1003#issuecomment-802574090).
* Behavioral Changes
  * Made improvements to Cluster AutoScaler for ignoring pods that are stuck in Terminating state to be considered for scale down after exhausting their grace period.
  * WinDSR is enabled by default for [Kubernetes versions 1.20+]
* Component Updates
  * Updated image tunnel-front to v1.9.2-v3.0.22
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1817.210310](vhd-notes/AKSWindows/2019/17763.1817.210310.txt).
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2021.03.10](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2021.03.10.txt).
  * AKS Ubuntu 18.04 image updated to [AKSUbuntu-1804-2021.03.10](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2021.03.10.txt).

## Release 2021-03-08

This release is rolling out to all regions - ETA for conclusion 2021-03-17 for public cloud.

### Announcements

* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on June 30th, 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.
* Kubernetes version 1.17 will be deprecated in the last week of March 2021.
* Before k8s 1.20 a bug would allow exec probes to run indefinitely, ignoring any timeoutSeconds configuration value. The previous buggy behavior has been fixed, and timeouts are now enforced. Additionally, this change introduces a new default timeout of 1 second. Please audit all your existing exec probes to make sure that it is appropriate to enforce a 1 second timeout. If not, please provide an explicit timeoutSeconds value that is appropriate for each [exec probe](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/#configure-probes).

### Release Notes

* Features
  * Azure monitor for containers now supports Pods & Replica set live logs in AKS resource view. Read more [here](https://azure.microsoft.com/updates/azmon-livelogs-pods/)
  * Confidential computing addon for confidential computing nodes (DCSv2) on AKS is updated to align with Intel SGX's future initiatives.
* Bug Fixes
  * The latest Windows image fixes a bug where Windows could break nodes at the CNI level and cause all pods scheduled on that node to be permanently stuck, or blocked during deployment. If you have questions about this fix, please contact the [Windows Container Team](https://github.com/microsoft/Windows-Containers).
  * Fixed an issue where duplicate packets were sent for kubenet on clusters with k8s 1.19+ and containerd-based clusters. This was cased when the traffic is sent to another pod on the same node over cluster service IP."
  * Fixed bug in the addon profile API that caused crashes on build using Terraform in [sov clouds](https://github.com/terraform-providers/terraform-provider-azurerm/issues/6462).
* Behavioral Change
  * The maximum number of managed identities for the Pod Identity addon was increased from 50 to 200.
  * Systemd-resolved will no longer be used in AKS Ubuntu 18.04 images. This weeks image, [AKSUbuntu-1804-2021.03.09](https://github.com/Azure/AgentBaker/blob/master/vhdbuilder/release-notes/AKSUbuntu/gen1/1804/2021.03.03.txt) resolves past issues regarding private DNS with .local entries not working with [Kubernetes 1.18 and Ubuntu 18.04](https://github.com/Azure/AKS/issues/2052).
* Preview Features
  * Kubenet support for Pod Identity.
* Component Updates
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1790.210302](vhd-notes/AKSWindows/2019/17763.1790.210302.txt).
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2021.03.03](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2021.03.03.txt).
  * AKS Ubuntu 18.04 image updated to [AKSUbuntu-1804-2021.03.03](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2021.03.03.txt).

## Release 2021-03-01

This release is rolling out to all regions - ETA for conclusion 2021-03-10 for public cloud.

### Announcements

* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on June 30th, 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.
* Starting last week, the week of Feb 22nd (Azure China Cloud and Azure Government Cloud users will get this update in the following weeks), we will upgrade AKS clusters Calico network policy from Calico version v3.8.9 to v3.17.2 for cluster 1.20.2 and above. This upgrade will cause a breaking change to the default behavior of all-interfaces Host Endpoints. For customers that use Host Endpoints, and only these, this version brings a change. Please follow our [guidance](https://github.com/Azure/AKS/issues/2089) to apply the appropriate label and Global Network Policy if you want to keep the v3.8.9 default behavior of all-interfaces Host Endpoints.
* Systemd-resolved will no longer be used in AKS Ubuntu 18.04 images starting on next week's release. This resolves past issues regarding private DNS with .local entries not working with [Kubernetes 1.18 and Ubuntu 18.04](https://github.com/Azure/AKS/issues/2052).

### Release Notes

* Features
  * AKS Managed AAD now supports Just-in-Time Access is now Generally Available [GA](https://docs.microsoft.com/azure/aks/managed-aad#configure-just-in-time-cluster-access-with-azure-ad-and-aks).
  * Application Gateway Ingress Controller (AGIC) AKS Add-On is now Generally Available [GA].
  * Confidential Computing Nodes (DCSv2) AKS Add-on is now Generally Available [GA].
  * HTTP Application Routing addon now Generally Available in Gov Cloud.
  * Encrypted customer managed keys policy for AKS is now Generally Available [GA].
  * Public IP per node capability in AKS is now Generally Available [GA].
  * Deploy WebLogic on Azure Kubernetes Service (AKS) using custom Docker images is now Generally Available [GA](https://docs.microsoft.com/azure/virtual-machines/workloads/oracle/weblogic-aks).
  * Persistent Volume monitoring & Reports tab in Container Insights is now Generally Available [GA]. Read more here:
    * <https://docs.microsoft.com/azure/azure-monitor/containers/container-insights-persistent-volumes>.
    * <https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-reports>.
* Preview Features
  * Calico Windows support in AKS 1.20 for new clusters.
  * Planned Maintenance Windows in AKS.
  * Dynamic IP allocation & enhanced subnet support in AKS.
  * Containerize and migrate apps to Azure Kubernetes Service with Azure Migrate: App Containerization. [Read More Here](https://docs.microsoft.com/azure/migrate/tutorial-containerize-java-kubernetes).
* Behavioral Change
  * Windows Containers may fail to resolve DNS names in ~1 seconds after it is created successfully and the status is showing running. This may not affect all customers but only those with applications that requires FQDN resolution when starting up the container. The workaround is retry or sleep ~1 seconds. For feedback, please go to [Windows Container GitHub](https://github.com/microsoft/Windows-Containers).
* Component Updates
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1757.210220.](vhd-notes/AKSWindows/2019/17763.1757.210220.txt).
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2021.02.24](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2021.02.24.txt).
  * AKS Ubuntu 18.04 image updated to [AKSUbuntu-1804-2021.02.24](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2021.02.24.txt).

## Release 2021-02-22

This release is rolling out to all regions - ETA for conclusion 2021-03-03 for public cloud.

### Announcements

* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on June 30th, 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.
* Starting this week (Azure China Cloud and Azure Government Cloud users will get this update in the following weeks), we will upgrade AKS clusters Calico network policy from Calico version v3.8.9 to v3.17.2 for cluster 1.20.2 and above. This upgrade will cause a breaking change to the default behavior of all-interfaces Host Endpoints. For customers that use Host Endpoints, and only these, this version brings a change. Please follow our [guidance](https://github.com/Azure/AKS/issues/2089) to apply the appropriate label and Global Network Policy if you want to keep the v3.8.9 default behavior of all-interfaces Host Endpoints.
* Systemd-resolved will no longer be used in AKS Ubuntu 18.04 images starting on next week's release. This resolves past issues regarding private DNS with .local entries not working with [Kubernetes 1.18 and Ubuntu 18.04](https://github.com/Azure/AKS/issues/2052).
* CSI Drivers will become default for [Kubernetes versions 1.21+](https://docs.microsoft.com/azure/aks/csi-storage-drivers).

### Release Notes

* Component Updates
  * Calico updated to v3.17.2 for Kubernetes versions 1.20+.
  * NMI image updated to 1.7.4.
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2021.02.17](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2021.02.17.txt).
  * AKS Ubuntu 18.04 image updated to [AKSUbuntu-1804-2021.02.17](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2021.02.17.txt).

## Release 2021-02-15

This release is rolling out to all regions - ETA for conclusion 2021-02-24 for public cloud.

### Announcements

* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on June 30th, 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.
* Starting this week on 22 February 2021 (Azure China Cloud and Azure Government Cloud users will get this update in the following weeks), we will upgrade AKS clusters Calico network policy from Calico version v3.8.9 to v3.17.1 for cluster 1.20.2 and above. This upgrade will cause a breaking change to the default behavior of all-interfaces Host Endpoints. For customers that use Host Endpoints, and only these, this version brings a change. Please follow our [guidance](https://github.com/Azure/AKS/issues/2089) to apply the appropriate label and Global Network Policy if you want to keep the v3.8.9 default behavior of all-interfaces Host Endpoints.

### Release Notes

* Behavioral Change
  * Date/Time removed from tunnel-front log entries. Timestamps can still be viewed by adding --timestamps to your kubectl logs command.
* Bug Fixes
  * Fixed Auto Scaling issues with 1.19 Preview Clusters where no image is found for a distro to scale from. 
  * A previous release defaulted to Gen2 VHDs for Kubernetes versions below 1.18.0. This implicitly changed the Ubuntu version from 16.04 to 18.04 for users still below 1.18.0. This has been fixed and users will only receive Gen2 VHDs for Kubernetes versions greater than or equal to 1.18.0.
  * Fixed AuthorizationFailed errors on cluster deletion operations to better expose to users.
  * Fixed case sensivity problem when specifying "--os-type"
  * Fixed an Error Handling issue when provisioning node pools with Ephemeral OS and a VM size with no cache disk.
  * Fixed an issue with Azure Policy pods not getting scheduled with CriticalAddonsOnly taint [GithubIssue](https://github.com/Azure/AKS/issues/1963)

* Component Updates
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1697.210210](vhd-notes/AKSWindows/2019/17763.1697.210210.txt).
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2021.02.10](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2021.02.10.txt).
  * AKS Ubuntu 18.04 image updated to [AKSUbuntu-1804-2021.02.10](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2021.02.10.txt).

## Release 2021-02-08

This release is rolling out to all regions - ETA for conclusion 2021-02-17 for public cloud.

### Announcements

* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st, 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.
* Starting on the week of 22 February 2021 (Azure China Cloud and Azure Government Cloud users will get this update in the following weeks), we will upgrade AKS clusters Calico network policy from Calico version v3.8.9 to v3.17.1 for any cluster 1.20.0 or above. This upgrade will cause a breaking change to the default behavior of all-interfaces Host Endpoints. For customers that use Host Endpoints, and only these, this version brings a change. Please follow our [guidance](https://github.com/Azure/AKS/issues/2089) to apply the appropriate label and Global Network Policy if you want to keep the v3.8.9 default behavior of all-interfaces Host Endpoints.

### Release Notes

* Features
  * Cluster Start/Stop is now [GA](https://docs.microsoft.com/azure/aks/start-stop-cluster).
* Preview Features
  * AKS now supports Private Clusters created with a custom DNS zone (BYO DNS zone). Read more [here](https://docs.microsoft.com/azure/aks/private-clusters#configure-private-dns-zone).
  * AKS now allows you to re-use your standard LoadBalancer outbound IP (created by AKS) as Inbound IP to your services (and vice-versa) from Kubernetes v1.20+.
  * AKS now supports re-using the same Load Balancer IP across multiple services from Kubernetes v1.20+.
* Behavioral Change
  * The AKS default storage class behavior now will be to delay the creation of a Persistent Volume until a pod is created. Allowing the Persistent Volume to be created in the same zone as the pod. Read more [here](https://docs.microsoft.com/azure/aks/azure-disk-csi#create-a-custom-storage-class).
* Component Updates
  * Update default Windows Azure CNI to v1.2.2.
  * Calico updated to v3.8.9.2.
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1697.210127](vhd-notes/AKSWindows/2019/17763.1697.210127.txt).
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2021.02.03](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2021.02.03.txt).
  * AKS Ubuntu 18.04 image updated to [AKSUbuntu-1804-2021.02.03](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2021.02.03.txt).

## Release 2021-02-01

This release is rolling out to all regions - ETA for conclusion 2021-02-12 for public cloud.

### Announcements
* Kubernetes 1.16 is officially deprecated in AKS
* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st, 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.
* Starting on the week of 15 February 2021 (Azure China Cloud and Azure Government Cloud users will get this update in the following weeks), we will upgrade AKS clusters Calico network policy from Calico version v3.8.9 to v3.17.1. This upgrade will cause a breaking change to the default behavior of all-interfaces Host Endpoints. For customers that use Host Endpoints, and only these, this version brings a change. Please follow our [guidance](https://github.com/Azure/AKS/issues/2089) to apply the appropriate label and Global Network Policy if you want to keep the v3.8.9 default behavior of all-interfaces Host Endpoints.

### Release Notes

* Features
  * Generation 2 Virtual Machines are now [GA on AKS](https://docs.microsoft.com/en-us/azure/aks/cluster-configuration#generation-2-virtual-machines-preview).
  * New Kubernetes patch version available, 1.19.7
* Preview Features
  * Kubernetes 1.20.2 is now in preview
* Bug Fixes
  * Fixed ContainerD + Kubenet - Pod IP SNAT/Masquerade Behavior [GitHubIssue](https://github.com/Azure/AKS/issues/2031).
* Component Updates
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1697.210127](vhd-notes/AKSWindows/2019/17763.1697.210127.txt).
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2021.01.28](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2021.01.28.txt).
  * AKS Ubuntu 18.04 image updated to [AKSUbuntu-1804-2021.01.28](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2021.01.28.txt).

## Release 2021-01-25

This release is rolling out to all regions - ETA for conclusion 2021-02-03 for public cloud.

### Announcements

* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st, 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.
* As previously announced, with the Holiday Season ending AKS will deprecate Kubernetes v1.16, completing the extension given after the GA of v1.19 for the holiday season and returning to the regular 3 supported versions window. After the week of January 31st, 2021 you will no longer be able to create v1.16.x based clusters or node pools.

### Release Notes

* Features
  * AKS now supports NCasT4_v3 SKUs.
  * New Kubernetes patch versions available, v1.17.16, 1.18.14, v1.19.6.
  * AKS Managed AAD now supports Azure AD Conditional Access. See more: <https://docs.microsoft.com/azure/aks/managed-aad#use-conditional-access-with-azure-ad-and-aks>
* Preview Features
  * AKS now supports WinDSR in AKS Windows nodes in preview by registering the `Microsoft.ContainerService/EnableAKSWindowsDSR` feature flag.
  * New options for Custom node Configuration: `ContainerLogMaxSizeMB`, `ContainerLogMaxFiles`, `PodMaxPids`.
  * AKS now supports Auto-Upgrade channels. <https://aka.ms/aks/autoupgrade>
* Bug Fixes
  * When clusters that are using bring your own subnet and route table with kubenet are deleted, they will now clean up any routes set by Kubernetes/AKS.
  * Added new IP availability validation for cluster upgrade of kubenet clusters.
  * Fixed bug where `Standard_DC2s_v2`, `Standard_DC4s_v2`, `Standard_DC8_v2` were incorrectly listed as supporting Accelerated Networking resulting in creation failures.
* Behavioral Change
  * The [Reset Service Principal](https://docs.microsoft.com/azure/aks/update-credentials) operation will now perform a node image upgrade in-order to update the configuration of each agent node.
* Component Updates
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1697.210113](vhd-notes/AKSWindows/2019/17763.1697.210113.txt).
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2021.01.13](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2021.01.13.txt).
  * AKS Ubuntu 18.04 image updated to [AKSUbuntu-1804-2021.01.13](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2021.01.13.txt).
  * Virtual Node updated to Virtual Kubelet 1.3.2.

## Release 2021-01-04

This release is rolling out to all regions - ETA for conclusion 2021-01-13 for public cloud.

### Announcements

* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st, 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.
* AKS has defaulted Azure CNI to transparent mode (from its previous default of bridge mode). This should bring no impact and carries several benefits, read more about it [here](https://aka.ms/aks/transparent-mode)
* As previously announced, with the Holiday Season ending AKS will deprecate Kubernetes v1.16, completing the extension given after the GA of v1.19 for the holiday season and returning to the regular 3 supported versions window. After the week of January 31st, 2021 you will no longer be able to create v1.16.x based clusters or nodepools.

### Release Notes

* Features
  * AKS now supports every CPU-based SKU dynamically. This means that every new CPU-based SKU is automatically supported by AKS so long they're not on the [restrictions list](https://docs.microsoft.com/azure/aks/quotas-skus-regions#restricted-vm-sizes). GPU-based SKUs and other specialty SKUs still require additional validation before being enabled
  * AKS Cluster Autoscaler now exposes the `max-node-provision-time` and `priority` properties as part of the [Cluster Autoscaler profile](https://docs.microsoft.com/azure/aks/cluster-autoscaler#using-the-autoscaler-profile).
* Bug Fixes
  * Fixed edge case on Bring your own subnet + kubenet network plugin scenarios where the route table was not correctly associated before the nodes started being created.
  * Better handling of race condition with liveness probes of the `aks-link` component.
  * Cluster autoscaler bug fix for incorrectly reading the value of `new-pod-scale-up` and improvements to CA liveness probe.
  * Case insensitivity fix for `networkPlugin``, networkPolicy` and `loadbalancerSku`.
  * Bug fixed on BYO Route Table kubenet scenarios where the cluster deletion didn't correctly clean up the route table rules created by kubernetes.
* Preview Features
  * Cluster Start/Stop now works in clusters with Cluster Autoscaler enabled and Private clusters.
* Component Updates
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1579.201208](vhd-notes/AKSWindows/2019/17763.1637.201215.txt).
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.12.15](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.12.15.txt).
  * AKS Ubuntu 18.04 image updated to [AKSUbuntu-1804-2020.12.15](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.12.15.txt).
  * Updated Azure CNI plugin version for Linux and Windows to 1.2 - <https://github.com/Azure/azure-container-networking/releases>.

## Release 2020-11-30

This release is rolling out to all regions - ETA for conclusion 2020-12-09 for public cloud.

### Announcements

* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st, 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.
* AKS will be defaulting Azure CNI to transparent mode (from its current default of bridge mode) on the next release. This should bring no impact and carries several benefits, read more about it [here](https://aka.ms/aks/transparent-mode)

### Release Notes

* Features
  * Bring your Own (BYO) Control Plane Managed Identity is Now Generally Available.
  * You may now update your Uptime SLA clusters to Free.
* Behavioral Changes
  * AKS Clusters will from now on choose to fail the upgrade if the drain/evict operation doesn't succeed instead of timing out. This means that users must ensure their PodDisruptionBudgets (PDBs) allow their pods to be successfully moved. To see if you have any incorrect PDB check [AKS Diagnostics](https://docs.microsoft.com/azure/aks/concepts-diagnostics) and search for PDBs and Node Drain Failures to see if you have any problematic PDBs in your cluster.
* Preview Features
  * AKS now supports [Custom Node Configuration](https://aka.ms/aks/custom-node-config) in Public Preview.
  * AKS now supports Private Clusters created with no Private DNS zone, deferring all DNS to an enterprise-managed DNS server.
    * You can create a cluster like this by using `--private-dns-zone none`, and making sure your custom DNS server is on the cluster subnet and contains all necessary entries including the API server endpoint IP (you can add after the cluster is created).
  * [Azure AD Pod Identity Add-on](https://aka.ms/aks/pod-identity) is now in public preview.

## Release 2020-11-16

This release is rolling out to all regions - ETA for conclusion 2020-11-25 for public cloud.

### Announcements

* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st, 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.

### Release Notes

* Features
  * Ephemeral OS is now Generally Available (GA). From now on ephemeral OS will be the default OS disk type for all SKUs and disk sizes that support it. See more [here](https://aka.ms/aks/ephemeral-os).
  * Kubernetes v1.19 is now Generally Available (GA).
  * ContainerD is now Generally Available (GA) and the default container runtime for cluster created or upgraded to kubernetes v1.19+. See more [here](https://aka.ms/aks/containerd).
  * Max Surge upgrades are now generally available. See more [here](https://aka.ms/aks/maxsurge).
* Behavioral changes
  * The command `az aks browse` will now open the [Azure Portal Kubernetes resource view](https://docs.microsoft.com/azure/aks/kubernetes-portal) after the Azure CLI v2.15.0.
  * A new property `subnetCIDR` was added for the Application Gateway Ingress Controller (AGIC) addon. This property will eventually replace `subnetPrefix`, and is used by AGIC to create a new subnet for Application Gateway. Application Gateway is deployed in this subnet and is then configured by AGIC to provide ingress capability to AKS.
  * Added additional username and password validations for windows. The minimal password lenght in AKS is 14 characters. See more [here](https://docs.microsoft.com/rest/api/compute/virtualmachinescalesets/createorupdate#virtualmachinescalesetosprofile).
  * AKS Base images now come from [Shared Image Gallery](https://docs.microsoft.com/azure/virtual-machines/windows/shared-image-galleries) and no longer from the Azure Marketplace.
* Bug Fixes
  * Fixed issued caused by Chrony on recent AKSUbuntu-1604-2020.10.28 images.
* Component Updates
  * Azure Monitor for Containers updated to [version 11092020](https://github.com/microsoft/Docker-Provider/blob/ci_prod/ReleaseNotes.md#11092020--).
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1577.201111](vhd-notes/AKSWindows/2019/17763.1577.201111.txt).
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.11.11](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.11.11.txt).
  * AKS Ubuntu 18.04 image updated to [AKSUbuntu-1804-2020.11.11](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.11.11.txt).

## Release 2020-11-09

This release is rolling out to all regions - ETA for conclusion 2020-11-19 for public cloud

### Announcements

* AKS will default to containerd as the default runtime on kubernetes v1.19+ after this feature GAs. During preview we encourage to create nodepools with the new container runtime to validate workloads still work as expected. And do check the [containerd differences and limitations](https://docs.microsoft.com/azure/aks/cluster-configuration#containerd-limitationsdifferences). After GA of kubernetes v1.19, containerd will be served by default for all new clusters or cluster that upgrade to v1.19. If you are doing container builds in cluster please use the recommended [docker buildx](https://github.com/docker/buildx).
* After the GA of Ephemeral OS and release of the 2020-11-01 AKS API version. Clusters and nodepools will be created by default with Ephemeral OS. You can still select managed disks explicitly if you prefer that option. See more at <https://aka.ms/aks/ephemeral-os>.
* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st, 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.

### Release Notes

* Features
  * Migration from Service Principal-based clusters to Managed Identity Managed clusters is now supported. See how [here](https://docs.microsoft.com/azure/aks/use-managed-identity#update-an-existing-service-principal-based-aks-cluster-to-managed-identities).
  * Added Standard_Dxds_v4 VM SKUs.
  * Added Standard_exds_v4.
* Behavioral changes
  * From kubernetes clusters v1.19+ `az aks browse` CLI command will open the Azure Portal resource view instead of the kubernetes dashboard that no longer is supported on these clusters.
* Bug Fixes
  * The AKS control plane will always send RST for idle connections after 4min. Closes #1052, #1755, #1877.
  * Fixed issue with etcd replica management.
* Component updates
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.10.28](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.10.28.txt).
  * AKS Ubuntu 18.04 image updated to [AKSUbuntu-1804-2020.10.28](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.10.28.txt).
  * Azure Monitor for Containers updated to [version 10272020](https://github.com/microsoft/Docker-Provider/blob/ci_prod/ReleaseNotes.md#10272020--)
  * Updated CNI network monitor addon to version v1.1.18.
  * The new AKS API version 2020-11-11 [has been published](https://github.com/Azure/azure-rest-api-specs/tree/master/specification/containerservice/resource-manager/Microsoft.ContainerService/stable/2020-11-01).

## Release 2020-10-26

This release is rolling out to all regions - ETA for conclusion 2020-11-11

### Announcements

* AKS and Holiday Season: To ease the burden of upgrade and change during the holiday season, AKS is extending a limited scope of support for all clusters and nodepools on 1.16 as a courtesy. Customers with clusters and nodepools on 1.16 after the [announced deprecation date of 2020-11-30](https://docs.microsoft.com/azure/aks/supported-kubernetes-versions#aks-kubernetes-release-calendar) will be granted an extension of capabilities outside the [usual scope of support for deprecated versions](https://docs.microsoft.com/azure/aks/supported-kubernetes-versions#kubernetes-version-support-policy).
 The scope of this limited extension is effective from '2020-11-30 to 2021-01-31' and is limited to the following:
  * Creation of new clusters and nodepools on 1.16.
  * CRUD operations on 1.16 clusters.
  * Azure Support of non-Kubernetes related, platform issues. Platform issues include trouble with networking, storage, or compute running on Azure. Any support requests for K8s patching and troubleshooting will be requested to upgrade into a supported version.
* AKS will default to containerd as the default runtime on kubernetes v1.19+ after this feature GAs. During preview we encourage to create nodepools with the new container runtime to validate workloads still work as expected. And do check the [containerd differences and limitations](https://docs.microsoft.com/azure/aks/cluster-configuration#containerd-limitationsdifferences). After GA of kubernetes v1.19, containerd will be served by default for all new clusters or cluster that upgrade to v1.19. If you are doing container builds in cluster please use the recommended [docker buildx](https://github.com/docker/buildx).
* After the GA of Ephemeral OS and release of the 2020-11-01 AKS API version. Clusters and nodepools will be created by default with Ephemeral OS. You can still select managed disks explicitly if you prefer that option. See more at <https://aka.ms/aks/ephemeral-os>.
* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st, 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.

### Release Notes

* Features
  * Outbound type UDR now allows for dynamic route exchange over BGP for Private Clusters.
  * Proximity Placement Group support is now Generally Available. Releases for #1351
  * Spot Node pools are now Generally Available. Releases for #982
  * Support for `CriticalAddonsOnly` taint as an exception for system pools. Releases for #1833
  * Support for soft Taints. Resolves #1484
  * New Kubernetes patch versions available, v1.17.13, 1.18.10.
* Preview Features
  * New Preview Kubernetes patch versions available, 1.19.3.
* Bug Fixes
  * Fixed mis-alignment of taint validations with upstream kubernetes validations. Fixes #1412
* Component updates
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.10.21](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.10.21.txt).
  * AKS Ubuntu 18.04 image updated to [AKSUbuntu-1804-2020.10.21](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.10.21.txt).

## Release 2020-10-19

This release is rolling out to all regions - ETA for conclusion 2020-10-28.

### Announcements

* AKS and Holiday Season: To ease the burden of upgrade and change during the holiday season, AKS is extending a limited scope of support for all clusters and nodepools on 1.16 as a courtesy. Customers with clusters and nodepools on 1.16 after the [announced deprecation date of 2020-11-30](https://docs.microsoft.com/azure/aks/supported-kubernetes-versions#aks-kubernetes-release-calendar) will be granted an extension of capabilities outside the [usual scope of support for deprecated versions](https://docs.microsoft.com/azure/aks/supported-kubernetes-versions#kubernetes-version-support-policy).
 The scope of this limited extension is effective from '2020-11-30 to 2021-01-31' and is limited to the following:
  * Creation of new clusters and nodepools on 1.16.
  * CRUD operations on 1.16 clusters.
  * Azure Support of non-Kubernetes related, platform issues. Platform issues include trouble with networking, storage, or compute running on Azure. Any support requests for K8s patching and troubleshooting will be requested to upgrade into a supported version.
* AKS will default to containerd as the default runtime on kubernetes v1.19+ after this feature GAs. During preview we encourage to create nodepools with the new container runtime to validate workloads still work as expected. And do check the [containerd differences and limitations](https://docs.microsoft.com/azure/aks/cluster-configuration#containerd-limitationsdifferences). After GA of kubernetes v1.19, containerd will be served by default for all new clusters or cluster that upgrade to v1.19. If you are doing container builds in cluster please use the recommended [docker buildx](https://github.com/docker/buildx).
* After the GA of Ephemeral OS and release of the 2020-11-01 AKS API version. Clusters and nodepools will be created by default with Ephemeral OS. You can still select managed disks explicitly if you prefer that option. See more at <https://aka.ms/aks/ephemeral-os>.
* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.

### Release Notes

* Features
  * New cluster autoscaler parameters available for the [cluster autoscaler profile](https://docs.microsoft.com/azure/aks/cluster-autoscaler#using-the-autoscaler-profile). New parameters supported: `skip-nodes-with-local-storage`, `skip-nodes-with-system-pods`, `max-empty-bulk-delete`, `expander`, `new-pod-scale-up-delay`, `max-total-unready-percentage`, `ok-total-unready-count`
  * New Admission controllers supported from kubernetes v1.19: `PodNodeSelector`, `PodTolerationRestriction`, `ExtendedResourceToleration`. See how to use them [here](https://kubernetes.io/docs/reference/access-authn-authz/admission-controllers/#extendedresourcetoleration) Releases for #1143, #1719 and #1449.
* Bug fixes
  * Fixed a few CPU throttling and health probe issues on the AKS control plane.
  * Updated signed PowerShell package to v0.0.3. Fixes #1772
  * Fixed issue with Azure policy addon and kubernetes v1.19 preview. Fixes #1869
* Component updates
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1397.201014](vhd-notes/AKSWindows/2019/17763.1397.201014.txt).
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.10.15](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.10.15.txt).
  * AKS Ubuntu 18.04 image updated to [AKSUbuntu-1804-2020.10.15](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.10.15.txt).

## Release 2020-10-12
**This release is rolling out to all regions - ETA for conclusion 2020-10-22**

### Announcements

* AKS and Holiday Season: To ease the burden of upgrade and change during the holiday season, AKS is extending a limited scope of support for all clusters and nodepools on 1.16 as a courtesy. Customers with clusters and nodepools on 1.16 after the [announced deprecation date of 2020-11-30](https://docs.microsoft.com/azure/aks/supported-kubernetes-versions#aks-kubernetes-release-calendar) will be granted an extension of capabilities outside the [usual scope of support for deprecated versions](https://docs.microsoft.com/azure/aks/supported-kubernetes-versions#kubernetes-version-support-policy).
 The scope of this limited extension is effective from '2020-11-30 to 2021-01-31' and is limited to the following:
  * Creation of new clusters and nodepools on 1.16.
  * CRUD operations on 1.16 clusters.
  * Azure Support of non-Kubernetes related, platform issues. Platform issues include trouble with networking, storage, or compute running on Azure. Any support requests for K8s patching and troubleshooting will be requested to upgrade into a supported version.
* AKS will default to containerd as the default runtime on kubernetes v1.19+ after this feature GAs. During preview we encourage to create nodepools with the new container runtime to validate workloads still work as expected. And do check the [containerd differences and limitations](https://docs.microsoft.com/azure/aks/cluster-configuration#containerd-limitationsdifferences). After GA of kubernetes v1.19, containerd will be served by default for all new clusters or cluster that upgrade to v1.19. If you are doing container builds in cluster please use the recommended [docker buildx](https://github.com/docker/buildx).
* After the GA of Ephemeral OS and release of the 2020-11-01 AKS API version. Clusters and nodepools will be created by default with Ephemeral OS. You can still select managed disks explicitly if you prefer that option. See more at <https://aka.ms/aks/ephemeral-os>.
* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.

### Release Notes

* Features
  * You can now mutate the AKS default storage class. See how here <https://docs.microsoft.com/en-us/azure/aks/azure-disks-dynamic-pv>
  * AKS now supports Dv4 and DSv4 VM SKU.
* Bug Fixes
  * Fixed bug that allow setting unsupported labels. Unsupported labels are now blocked as per: <https://github.com/kubernetes/enhancements/blob/master/keps/sig-auth/0000-20170814-bounding-self-labeling-kubelets.md#proposal>
  * Fixed an issue with Managed-AAD and kubernetes v1.19 preview. Closes #1891
  * Fixed an issue where topology labels where not correctly preserved after upgrade.
* Behavior change
  * The `calico-typha` deployment is now called `calico-typha-deployment`.
  * The revisionHistoryLimit is now set to 2 for managed components and addon deployments. Closes #1502
* Component Updates
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.10.08](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.10.08.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.10.08](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.10.08.txt).

## Release 2020-09-21
**This release is rolling out to all regions - ETA for conclusion 2020-09-30**

* AKS will default to containerd as the default runtime in kubernetes v1.19. During preview we encourage to create nodepools with the new container runtime to validate workloads still work as expected. And do check the [containerd differences and limitations](https://docs.microsoft.com/azure/aks/cluster-configuration#containerd-limitationsdifferences). After GA of kubernetes v1.19, containerd will be served by default for all new clusters or cluster that upgrade to v1.19. If you are doing container builds in cluster please use the recommended [docker buildx](https://github.com/docker/buildx).
* [New Date] We heard your feedback and as such, the Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.

### Release Notes

* Features
  * Azure Policy Addon is now Generally Available, see <https://azure.microsoft.com/updates/ga-policy-addon-for-azure-kubernetes-service>
  * New Kubernetes patches available. v1.16.15 and v1.17.11
  * New detectors for [AKS Diagnostics](https://docs.microsoft.com/azure/aks/concepts-diagnostics):
    * Node drain failure detector that calls out node drain failures that might impact the cluster workloads.
    * Managed-AAD integration detector that looks for common issues with AADv2 integration like the kubectl minimum version.
* Preview features
  * AKS now supports the ability to completely stop and start clusters on demand. A great option for times your cluster might be idle. Start here: <https://aka.ms/aks/stop-cluster>
  * Ephemeral OS is now part of the 2020-09-01 AKS API and can be enabled through ARM. This will also allow you to in the future keep using managed network-attached disk if you want. <https://github.com/Azure/azure-rest-api-specs/blob/master/specification/containerservice/resource-manager/Microsoft.ContainerService/stable/2020-09-01/examples/AgentPoolsCreate_Ephemeral.json>
  * Azure RBAC for Kubernetes Authorization is now in Public Preview and open to anyone to test (no form required): <https://docs.microsoft.com/azure/aks/manage-azure-rbac>
  * Kubernetes v1.19 is now in public preview
  * Azure Confidential Compute addon for AKS is not in public preview providing you with confidential nodes: <https://docs.microsoft.com/azure/confidential-computing/confidential-nodes-aks-get-started>
  * AKS now integrates with Azure Files NFS shares on its CSI storage drivers. See more here: <https://docs.microsoft.com/azure/aks/azure-files-csi#nfs-file-shares>
* Bug fix
  * Issue where addon names where not accepted with any casing fixed.
* Component updates
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1397.200904](vhd-notes/AKSWindows/2019/17763.1397.200904.txt)
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.09.17](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.09.17.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.09.17](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.09.17.txt).
* Behavior Change
  * AKS is now validating/blocking labels that are [disallowed upstream](https://github.com/kubernetes/enhancements/blob/master/keps/sig-auth/0000-20170814-bounding-self-labeling-kubelets.md#proposal).

## Release 2020-08-31

**This release is rolling out to all regions - ETA for conclusion 2020-09-18**

* AKS will default to containerd as the default runtime in kubernetes v1.19. During preview we encourage to create nodepools with the new container runtime to validate workloads still work as expected. And do check the [containerd differences and limitations](https://docs.microsoft.com/azure/aks/cluster-configuration#containerd-limitationsdifferences). After GA of kubernetes v1.19, containerd will be served by default for all new clusters or cluster that upgrade to v1.19. If you are doing container builds in cluster please use the recommended [docker buildx](https://github.com/docker/buildx).
* [New Date] We heard your feedback and as such, the Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st 2021.
* Once GA AKS will default to its new [GPU specialized image](https://aka.ms/aks/specialized-gpu-image) as the supported option for GPU-capable agent nodes.

### Release Notes

* Features
  * Kubernetes version 1.18 is now Generally Available (GA) on AKS. (1.15 is being retired as this release progressively reaches all regions, as previously communicated). Check the [release calendar](https://docs.microsoft.com/azure/aks/supported-kubernetes-versions#aks-kubernetes-release-calendar) for future version release and GA date.
  * New Kubernetes patch versions available, v1.18.8.
  * The AKS Kubernetes Audit logs are now split in 2 categories to allow you granularly subscribe and save costs.
    * `kube-audit-admin`: This category contains only audit events that include write verbs (`create`,`update`,`delete`,`patch`,`post`)
    * `kube-audit`: This category contains all remaining audit events.
  * AKS Ubuntu 18.04 is now Generally Available and will be the default agent node base image on k8s v1.18 and onward. 
* Preview Features
  * AKS now supports [Azure disk and Azure files CSI storage drivers](https://docs.microsoft.com/en-us/azure/aks/csi-storage-drivers) in Public preview.
* Bug Fix
  * Fixed an issue where non-AKS managed identities (eg. from Pod Identity) would be lost after an AKS upgrade.
  * Fixed bug where the VMSS backend pool was removed after a Service Principal reset operation.
* Behavior Changes
  * Ensure all components use only strong ciphers (matching the AKS API server). Metrics server now only allows the following cipher suites:
    * TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
    * TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256
    * TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
    * TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384
* Component Updates
  * Azure Policy Addon updated to Gatekeeper beta12 and Policy 0804 versions.
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1397.200820](https://github.com/Azure/aks-engine/blob/master/vhd/release-notes/aks-windows/2019-datacenter-core-smalldisk-17763.1397.200820.txt)
  * Azure Monitor for Containers versions updated: <https://github.com/microsoft/Docker-Provider/blob/ci_prod/ReleaseNotes.md#08072020-->
    * Linux version mcr.microsoft.com/azuremonitor/containerinsights/ciprod:ciprod08072020
    * Windows version mcr.microsoft.com/azuremonitor/containerinsights/ciprod:win-ciprod08072020
  * Add LivenessProbe and ReadinessProbe for Metrics Server.
  * Updated AKS Moby version to 19.03.12 (from now on AKS Moby versions will follow docker versioning to assist scanning tools false positives).
  * Updated NVIDIA GPU drivers to v450.51.06.
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.08.28](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.08.28.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.08.28](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.08.28.txt).

## Release 2020-08-17

**This release is rolling out to all regions - ETA for conclusion 2020-08-26**

### Important Service Updates

* AKS will default to AKS ubuntu 18.04 in upcoming GA of kubernetes v1.18 which marks the GA of AKS Ubuntu 18.04 as well. We recommend testing existing workloads on AKS Ubuntu 18.04 nodepools prior to GA. See how here: <https://aka.ms/aks/Ubuntu1804>
* AKS will default to containerd as the default runtime in kubernetes v1.19. During preview we encourage to create nodepools with the new container runtime to validate workloads still work as expected. And do check the [containerd differences and limitations](https://docs.microsoft.com/azure/aks/cluster-configuration#containerd-limitationsdifferences). After GA of kubernetes v1.19, containerd will be served by default for all new clusters or cluster that upgrade to v1.19. If you are doing container builds in cluster please use the recommended [docker buildx](https://github.com/docker/buildx).
* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st 2020.
* Kubernetes version 1.18 will GA on the week of August 31st and you will no longer be able to create 1.15.x based clusters or nodepools.
* Once GA AKS will default to the GPU specialized image as the supported option for GPU-capable agent nodes.

### Release Notes

* Features
  * You can now see the [AKS Authentication Webhook Server](https://docs.microsoft.com/azure/aks/concepts-identity#webhook-and-api-server) logs for the Azure AD Integrated clusters, as part of the [AKS Control Plane logs](https://docs.microsoft.com/azure/aks/view-master-logs).
* Preview Features
  * AKS now has a specialized GPU Node Image that already includes not only the docker drivers but also the NVIDIA device plugin, so ready to use. See more at: <https://aka.ms/aks/specialized-gpu-image>
* Component Updates
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.08.13](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.08.13.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.08.13](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.08.13.txt).

## Release 2020-08-10

**This release is rolling out to all regions - ETA for conclusion 2020-08-21**

### Important Service Updates

* AKS will default to AKS ubuntu 18.04 in upcoming GA of kubernetes v1.18 which marks the GA of AKS Ubuntu 18.04 as well. We recommend testing existing workloads on AKS Ubuntu 18.04 nodepools prior to GA. See how here: <https://aka.ms/aks/Ubuntu1804>
* AKS will default to containerd as the default runtime in kubernetes v1.19. During preview we encourage to create nodepools with the new container runtime to validate workloads still work as expected. And do check the [containerd differences and limitations](https://docs.microsoft.com/azure/aks/cluster-configuration#containerd-limitationsdifferences). After GA of kubernetes v1.19, containerd will be served by default for all new clusters or cluster that upgrade to v1.19.
* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st 2020.
* Kubernetes version 1.18 will GA on the week of August 31st and you will no longer be able to create 1.15.x based clusters or nodepools.

### Release Notes

* Features
  * AKS now supports autoscaling to 0. (latest CLI extension and following core CLI version)
* Bug fixes
  * Fixed a bug when scaling windows node pools and the windows profile parameters were missing.
* Component Updates
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.08.06](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.08.06.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.08.06](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.08.06.txt).

## Release 2020-08-03

**This release is rolling out to all regions - ETA for conclusion 2020-08-14**

### Important Service Updates

* AKS will default to AKS ubuntu 18.04 in upcoming GA of kubernetes v1.18 which marks the GA of AKS Ubuntu 18.04 as well. We recommend testing existing workloads on AKS Ubuntu 18.04 nodepools prior to GA. See how here: <https://aka.ms/aks/Ubuntu1804>
* AKS will default to containerd as the default runtime in kubernetes v1.19. During preview we encourage to create nodepools with the new container runtime to validate workloads still work as expected. And do check the [containerd differences and limitations](https://docs.microsoft.com/azure/aks/cluster-configuration#containerd-limitationsdifferences). After GA of kubernetes v1.19, containerd will be served by default for all new clusters or cluster that upgrade to v1.19.
* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st 2020.
* Kubernetes version 1.18 will GA on the week of August 31st and you will no longer be able to create 1.15.x based clusters or nodepools.

### Release Notes

* Preview Features
  * AKS now supports Ephemeral OS disks in Public Preview. Read more here: <https://aka.ms/aks/ephemeral-os>
  * AKS has announced the AKS Portal Resource view: <https://azure.microsoft.com/updates/kubernetes-resource-view-is-in-public-preview>
* Bug fixes
  * Fixed but where VNET CIDR was not set correctly on Windows nodes which could result in incorrect NATing behavior.

## Release 2020-07-27

**This release is rolling out to all regions - ETA for conclusion 2020-08-07**

### Important Service Updates

* AKS will default to AKS ubuntu 18.04 in upcoming GA of kubernetes v1.18 which marks the GA of AKS Ubuntu 18.04 as well. We recommend testing existing workloads on AKS Ubuntu 18.04 nodepools prior to GA. See how here: <https://aka.ms/aks/Ubuntu1804>
* AKS will default to containerd as the default runtime in kubernetes v1.19. During preview we encourage to create nodepools with the new container runtime to validate workloads still work as expected. And do check the [containerd differences and limitations](https://docs.microsoft.com/azure/aks/cluster-configuration#containerd-limitationsdifferences). After GA of kubernetes v1.19, containerd will be served by default for all new clusters or cluster that upgrade to v1.19.
* AKS has removed the custom "high-priority" and "addon-priority" Priority Classes which are no longer used by the service.
* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/azure/aks/use-pod-security-policies) feature will be retired on May 31st 2020.
* Kubernetes version 1.18 will GA on the week of August 31st and you will no longer be able to create 1.15.x based clusters or nodepools.

### Release Notes

* Features
  * AKS-managed Azure AD integration (v2) is now generally available: <https://docs.microsoft.com/en-us/azure/aks/managed-aad>
    * You can now upgrade non-AzureAD clusters to AD-integrated clusters.
    * You can now upgrade clusters with the previous iteration of the AzureAD integration (v1) into AKS-managed AzureAD clusters (v2)
    * Closes: <https://github.com/Azure/AKS/issues/1489>
  * AKS is now supported on the following regions:
    * UAE Central - Closes <https://github.com/Azure/AKS/issues/1693>
    * West Central US - Closes <https://github.com/Azure/AKS/issues/998>
  * New Kubernetes patch versions available v1.16.13, v1.17.9
    * This patch versions respond the following CVEs:
      * https://github.com/Azure/AKS/issues/1724
      * https://github.com/Azure/AKS/issues/1731
      * https://github.com/Azure/AKS/issues/1732
    * We've heard your feedback and we will not be removing all the previous versions due to the vulnerabilities. Instead we've patched all the latest GA ones (v1.15.11, v1.15.12, v1.16.10, v1.17.7) and you can still mitigate the vulnerabilities in any GA version by leveraging <https://aka.ms/aks/node-image-upgrade>.
* Bug fixes
  * AKS has added the ready and health plugins to coredns. Closes <https://github.com/Azure/AKS/issues/1676>
  * We've added additional validations to prevent the creation of multiple node pool clusters with Basic Load Balancer which isn't supported.
* Preview features
  * AKS now supports Bring Your Own (BYO) control plane managed identity: <https://aka.ms/aks/byo-mi>
  * New Kubernetes patch versions are available for preview, v1.18.6.
* Behavior changes
  * After API version 2020-07-01 the node image upgrade operation will only allow POST and not PUT. CLI versions won't be affected.
  * A default load balancer is not longer created in UDR OutboundType clusters. The LB can be automatically created later if a public service of type LoadBalancer is created.
* Component Updates
  * Calico updated to v3.8.0
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1339.200716](https://github.com/Azure/aks-engine/blob/master/vhd/release-notes/aks-windows/2019-datacenter-core-smalldisk-17763.1339.200716.txt)
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.07.16](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.07.16.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.07.16](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.07.16.txt).

## Release 2020-07-06

**This release is rolling out to all regions**

### Important Service Updates

* AKS will default to AKS ubuntu 18.04 in upcoming GA of kubernetes 1.18 and after AKS Ubuntu 18.04 is GA as well. We recommend testing existing workloads on AKS Ubuntu 18.04 nodepools prior to GA. See how here: <https://aka.ms/aks/Ubuntu1804>
* AKS will default to containerd as the default runtime in the upcoming months. During preview we encourage to create nodepools with the new container runtime to validate workloads still work as expected. And do check the [containerd differences and limitations](https://docs.microsoft.com/en-us/azure/aks/cluster-configuration#containerd-limitationsdifferences). After GA containerd will be served for all new clusters on the latest kubernetes version clusters that upgrade to it.
* On the *next* release, AKS will be removing the custom "high-priority" and "addon-priority" Priority Classes which are no longer used by the service.
* The Azure Kubernetes Service [pod security policy (preview)](https://docs.microsoft.com/en-us/azure/aks/use-pod-security-policies) feature will be retired on May 31st 2020.

### Release Notes

* Features
  * Users can now reuse inbound and outbound IPs on the Load Balancer. After this change, users can assign an outbound IP that is same as an inbound IP in the AKS SLB.
* Preview Features
  * AKS is announcing the release of Azure RBAC integration for Kubernetes Authorization in Preview. Which allows you to control the RBAC of your cluster directly from the Azure Portal. See more at: <https://aka.ms/aks/azure-rbac>
  * AKS integration with Azure Policy and Gatekeeper now supports securing your pods with Azure Policy (with the equivalent controls that were made available previously in Pod Security Policies). Read more at <https://aka.ms/aks/azpodpolicy>
  * AKS now supports Azure Ultra disks in preview.
  * AKS now supports confidential workloads through DCSv2 SKUs (private preview). Read more [here](https://azure.microsoft.com/en-in/updates/azure-kubernetes-service-aks-now-supports-confidential-workloads-through-dcsv2-skus-preview/).
* Component Updates
  * New AKS base images - Upgrade to these using <https://aka.ms/aks/node-image-upgrade>
    * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.06.30](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.06.30.txt).
    * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.06.30](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.06.30.txt).

## Release 2020-06-29

**This release is rolling out to all regions**

### Important Service Updates

* AKS is preparing to GA the AKS Ubuntu 18.04 node image and recommends testing existing workloads on AKS Ubuntu 18.04 nodepools prior to GA. **After AKS Ubuntu 18.04 is GA**, at the time of upgrading to a pre-announced kubernetes version, clusters running AKS Ubuntu 16.04 will receive this new image. See how here: <https://aka.ms/aks/Ubuntu1804>
* AKS will default to containerd as the default runtime in the upcoming months. During preview we encourage to create nodepools with the new container runtime to validate workloads still work as expected. And do check the [containerd differences and limitations](https://docs.microsoft.com/en-us/azure/aks/cluster-configuration#containerd-limitationsdifferences). After GA containerd will be served for all new clusters on the latest kubernetes version clusters that upgrade to it.

### Release Notes

* Features
  * Kubernetes version 1.17 is now Generally Available (GA) on AKS. (1.14 is being retired as this release progressively reaches all regions, as previously communicated).
  * New Kubernetes patch versions available, v1.15.12, v1.16.10, v1.17.7. Note that as per [policy](https://docs.microsoft.com/en-us/azure/aks/supported-kubernetes-versions#supported-versions-policy-exceptions), versions <1.16.10 and <1.17.7 were removed due to severe bugs and security issues flagged upstream.
* Preview Features
  * New Kubernetes patch versions are available for preview, v1.18.4.
  * AKS now supports `containerd` as container runtime in preview. This runtime will be the default on AKS on the upcoming months. Read about it at https://aka.ms/aks/containerd and try it out!
  * AKS now supports Proximity Placement Groups in preview to provide collocation capabilities for low latency workloads. Read more about it at https://aka.ms/aks/ppg and try it out!
* Bug fixes
  * Fix issues on clusters using managed identities, where a cluster upgrade or scale operation would remove unknown identities.
  * Fixed bug where users where being shown more than the minor version above as available versions to upgrade to.
* Behavior changes
  * Kubernetes API server Log Level changed from 4 to 2. This will be reduce the log volume while keeping pair with k8s Prod recommendations.
  * Azure Policy for AKS is removing the built-in policies offered for the private preview version 1.0 of the add-on. The built-in policies with category name of "Kubernetes Service" will no longer function starting July 21st, 2020. To continue service, update the add-on to version 2.0 by following [these steps](https://docs.microsoft.com/en-us/azure/governance/policy/concepts/policy-for-kubernetes#install-azure-policy-add-on-for-aks) and use policies of category name "Kubernetes".
* Component Updates
  * Metrics Server has been updated to v0.3.6.
  * New AKS base images - Upgrade to these using <https://aka.ms/aks/node-image-upgrade>
    * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1282.200625](https://github.com/Azure/aks-engine/blob/master/vhd/release-notes/aks-windows/2019-datacenter-core-smalldisk-17763.1282.200625.txt)
    * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.06.25](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.06.25.txt).
    * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.06.25](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.06.25.txt).

## Release 2020-06-15

**This release is rolling out to all regions**

### Important Service Updates

* AKS is preparing to GA the AKS Ubuntu 18.04 node image and recommends testing existing workloads on AKS Ubuntu 18.04 nodepools prior to GA. **After AKS Ubuntu 18.04 is GA**, at the time of upgrading to a pre-announced kubernetes version, clusters running AKS Ubuntu 16.04 will receive this new image. See how here: <https://aka.ms/aks/Ubuntu1804>
* Kubernetes version 1.17 will GA on the week of July 1st and you will no longer be able to create 1.14.x based clusters or nodepools.
  * Kubernetes 1.17 introduces API deprecations, please make sure your manifests are up to date before upgrading, and check Azure Advisor to confirm you are not using deprecated APIs. More information on 1.17 API deprecations here: <https://v1-17.docs.kubernetes.io/docs/setup/release/#deprecations-and-removals>

### Release Notes

* Behavior changes
  * In advance of the GA of kubernetes v1.17 AKS is now defaulting to kubernetes v1.16 as the default version. If you have a dependency on the AKS default version, make sure your kubernetes APIs are up to date: https://github.com/Azure/AKS/issues/1205
* Component updates
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.06.10](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.06.10.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.06.10](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.06.10.txt).
  * Azure Monitor for Containers monitoring addon image was updated to ciprod05222020 and win-ciprod05222020-2 (for Windows). Notable changes:
    * Windows Logs - Starting from this release, users will see the agent automatically start collecting windows container STDOUT/STDERR logs and sending them to same log analytics workspace.
    * Metrics available for Alerting - Users will see the below metrics on the AKS 'Metrics' blade in the Azure portal, under the "Container Insights" Namespace.
      * Metrics:
        * diskUsagePercentage
        * completedJobsCount
        * oomKilledContainerCount
        * podReadyPercentage
        * restartingContainerCount
        * cpuExceededPercentage
        * memoryRssExceededPercentage
        * memoryWorkingSetExceededPercentage

## Release 2020-06-08

**This release is rolling out to all regions**

### Important Service Updates

* AKS is preparing to GA the AKS Ubuntu 18.04 node image and recommends testing existing workloads on AKS Ubuntu 18.04 nodepools prior to GA. **After AKS Ubuntu 18.04 is GA**, at the time of upgrading to a pre-announced kubernetes version, clusters running AKS Ubuntu 16.04 will receive this new image. See how here: <https://aka.ms/aks/Ubuntu1804>
* Kubernetes version 1.17 will GA on the week of July 1st and you will no longer be able to create 1.14.x based clusters or nodepools.
  * Kubernetes 1.17 introduces API deprecations, please make sure your manifests are up to date before upgrading, and check Azure Advisor to confirm you are not using deprecated APIs. More information on 1.17 API deprecations here: <https://v1-17.docs.kubernetes.io/docs/setup/release/#deprecations-and-removals>

### Release Notes

* Features
  * It is now supported to upgrade clusters from Free to Paid on all regions that support Uptime SLA. This can be done after this weeks release finishes via ARM and on the next CLI version.
  * Windows Server container support is now Generally Available on Azure China regions.
* Preview Features
  * AKS has released [Node Image Upgrade](http://aka.ms/aks/nodeimageupgrade), to allow users to upgrade the node image of all their cluster nodes, or a specific nodepool, without requiring a full kubernetes upgrade. See more at: <http://aka.ms/aks/nodeimageupgrade>
  * AKS has released the Application Ingress Controller (AGIC) Addon in public preview. With it you can now easily install and leverage AGIC as a fully managed addon on AKS. More here: <https://aka.ms/aks/agic>
  * AKS now supports NDr_v2 with the gen2 preview.
* Bug fixes
  * Fixed issue where upgrading older clusters would fail due to incompatibility with the podpriority kubelet feature gate.
  * Fixed issue in Upgrade and Update operations where there was a mismatch between the Cluster Autoscaler node count and current node count.
  * AKS has cherry picked the following bug fixes into v1.15.11:
    * https://github.com/kubernetes/kubernetes/pull/89337
    * https://github.com/kubernetes/kubernetes/pull/90749
    * https://github.com/kubernetes/kubernetes/pull/89794
* Behavior changes
  * You are now allowed deploy AKS into dual-stack subnets on dual-stack vnets. The AKS cluster will only leverage the IPv4 stack currently.
* Component Updates
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.05.31](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.05.31.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.05.31](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.05.31.txt).

## Release 2020-06-01

**This release is rolling out to all regions**

### Important Service Updates

* AKS has introduced AKS Ubuntu 18.04 in preview. During this time we will provide both OS versions side by side. **After AKS Ubuntu 18.04 is GA**, on the next cluster upgrade, clusters running AKS Ubuntu 16.04 will receive this new image.
* For any cluster created on K8s 1.18 or above, AKS will default the kube-dashboard add-on to disabled moving forward.
* Kubernetes version 1.17 will GA on the week of July 1st and you will no longer be able to create 1.14.x based clusters or nodepools.
  * Kubernetes 1.17 introduces API deprecations, please make sure your manifests are up to date before upgrading, and check Azure Advisor to confirm you are not using deprecated APIs. More information on 1.17 API deprecations here: <https://v1-17.docs.kubernetes.io/docs/setup/release/#deprecations-and-removals>

### Release Notes

* Features
  * Outbound Type is now Generally Available and supports Kubenet based clusters. Read more at <https://aka.ms/aks/outboundtype>
  * AKS now supports custom Route Tables for Kubenet-based clusters, by enabling use of existing Route Tables so Kubernetes can add required routes for node communication. Read more at <https://aka.ms/aks/customrt>
* Preview Features
  * Support for Confidential Workloads on AKS and [DC-series](https://docs.microsoft.com/en-us/azure/virtual-machines/dcv2-series) nodepools are now in Private Preview. Read more at <https://aka.ms/accakspreview>.
  * AKS now supports Max Surge Upgrades in preview. Read more at <https://aka.ms/aks/maxsurge>
* Behavior changes
  * AKS default OS disk size is now 128GB, a [P10](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/disks-types#premium-ssd).
  * Set calico `IptablesFilterAllowAction` to return from its default value, so that requests not dropped by the policy can be compared against system chains. In this way, the requests to services without endpoints can be rejected following the intention of kube-proxy.
  * AKS has released [API version 2020-04-01](https://github.com/Azure/azure-rest-api-specs/tree/master/specification/containerservice/resource-manager/Microsoft.ContainerService/stable/2020-04-01) which as previously announced defaults to VMSS (Virtual Machine Scale Sets), SLB (Standard Load Balancer) and RBAC enabled.
* Component Updates
  * Updated Kube-Dashboard images for 1.16, 1.17 and 1.18
    * 1.16 clusters will use dashboard:v2.0.0-rc3, 1.17 will use dashboard:v2.0.0-rc7, 1.18 will use dashboard:v2.0.1
    * Read more about the User Experience here: <https://docs.microsoft.com/en-us/azure/aks/kubernetes-dashboard>
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.05.27](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.05.27.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.05.27](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.05.27.txt).
  
## Release 2020-05-25

**This release is rolling out to all regions**

### Important Service Updates

* AKS API version 2020-04-01 defaults to VMSS (Virtual Machine Scale Sets), SLB (Standard Load Balancer) and RBAC enabled.
* AKS has introduced AKS Ubuntu 18.04 in preview. During this time we will provide both OS versions side by side. **After AKS Ubuntu 18.04 is GA**, on the next cluster upgrade, clusters running AKS Ubuntu 16.04 will receive this new image.
* Kubernetes 1.17 introduces API deprecations, please make sure your manifests are up to date before upgrading, and check Azure Advisor to confirm you are not using deprecated APIs. More information on 1.17 API deprecations here: <https://v1-17.docs.kubernetes.io/docs/setup/release/#deprecations-and-removals>
* For any cluster created on K8s 1.18 or above, AKS will default the kube-dashboard add-on to disabled moving forward.

### Release Notes

* Features
  * Uptime SLA is now available in all Public Cloud regions.
* Bug Fixes
  * Fixed bug with Windows nodes and Managed Identity, where nodes were unable to pull images from ACR.
* Component Updates
  * Azure Policy image updated to version `prod_20200519.1`
  * Azure Network policy image updated to v1.1.2, <https://github.com/Azure/azure-container-networking/releases/tag/v1.1.2>
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1217.200513](https://github.com/Azure/aks-engine/blob/master/vhd/release-notes/aks-windows/2019-datacenter-core-smalldisk-17763.1217.200513.txt)

## Release 2020-05-18

**This release is rolling out to all regions**

### Important Service Updates

* AKS API version 2020-04-01 (to be published) will default to VMSS (Virtual Machine Scale Sets), SLB (Standard Load Balancer) and RBAC enabled.
* AKS has introduced AKS Ubuntu 18.04 in preview. During this time we will provide both OS versions side by side. **After AKS Ubuntu 18.04 is GA**, on the next cluster upgrade, clusters running AKS Ubuntu 16.04 will receive this new image.
* Kubernetes 1.17 introduces API deprecations, please make sure your manifests are up to date before upgrading, and check Azure Advisor to confirm you are not using deprecated APIs. More information on 1.17 API deprecations here: <https://v1-17.docs.kubernetes.io/docs/setup/release/#deprecations-and-removals>
* Only Spot and Regular will be accepted as parameters for nodepool scaleSetPriority, low priority (now Spot) will no longer be accepted.
* For any cluster created on K8s 1.18 or above, AKS will default the kube-dashboard add-on to disabled moving forward.

### Release Notes

* Features
  * Windows Server container support is now Generally Available on Azure Government Cloud.
  * AKS has introduced new kubernetes patch versions v1.15.11, v1.16.8, v1.16.9.
* Preview Features
  * AKS has introduced new public preview patch version v1.17.4, v1.17.5.
  * AKS now supports Gen2 VMs in Public Preview.

    ```bash
    az feature register --name "Gen2VMPreview" --namespace "Microsoft.ContainerService"
    # wait for the feature to register
    az feature show --name Gen2VMPreview --namespace "Microsoft.ContainerService"
    # Re-register the AKS namespace by performing the below
    az provider register --namespace 'Microsoft.ContainerService'
    # Finally create the cluster
    az aks create -n aks -g aks -s Standard_D2s_v3 --aks-custom-headers usegen2vm=true
    ```

* Bug Fixes
  * Fixed an issue where if a nodepool operation was performed in a locked resource group it would return error 500 instead of correctly returning a ResourceGroupLocked error.
* Component Updates
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.05.13](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.05.13.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.05.13](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.05.13.txt).

## Release 2020-05-11

**This release is rolling out to all regions**

### Important Service Updates

* AKS API version 2020-04-01 (to be published) will default to VMSS (Virtual Machine Scale Sets), SLB (Standard Load Balancer) and RBAC enabled.
* AKS has introduced AKS Ubuntu 18.04 in preview. During this time we will provide both OS versions side by side. **After AKS Ubuntu 18.04 is GA**, on the next cluster upgrade, clusters running AKS Ubuntu 16.04 will receive this new image.
* Kubernetes 1.17 introduces API deprecations, please make sure your manifests are up to date before upgrading, and check Azure Advisor to confirm you are not using deprecated APIs. More information on 1.17 API deprecations here: <https://v1-17.docs.kubernetes.io/docs/setup/release/#deprecations-and-removals>
* Only Spot and Regular will be accepted as parameters for nodepool scaleSetPriority, low priority (now Spot) will no longer be accepted.

### Release Notes

* Features
  * AKS now offers an optional Paid Uptime SLA. Read more about it: <https://techcommunity.microsoft.com/t5/azure-kubernetes-service/aks-introduces-uptime-sla/ba-p/1350832>
* Preview Features
  * AKS now supports in preview kubernetes versions 1.18.1 and 1.18.2
  * AKS now supports creating nodepools leveraging AKS Ubuntu 18.04 images in any existing cluster
  eg. `az aks nodepool add -n ubuntu1804 --cluster-name aks -g aks --aks-custom-headers CustomizedUbuntu=aks-ubuntu-1804`
  * The Azure Policy Add-on for AKS has released a new version to integrate with OPA Gatekeeper v3. Read more here <https://github.com/Azure/AKS/issues/1606>
* Bug Fixes
  * Fixed bug where newly added agent pool did not inherit VnetCidrs from existing agent pools resulting in wrong nonMasqueradeCIDRs
* Component Updates
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.05.06](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.05.06.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.05.06](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.05.06.txt).

## Release 2020-05-04

**This release is rolling out to all regions**

### Important Service Updates

* AKS API version 2020-04-01 (to be published) will default to VMSS (Virtual Machine Scale Sets), SLB (Standard Load Balancer) and RBAC enabled.
* AKS has introduced AKS Ubuntu 18.04 in preview. During this time we will provide both OS versions side by side. **After AKS Ubuntu 18.04 is GA**, on the next cluster upgrade, clusters running AKS Ubuntu 16.04 will receive this new image.
* Kubernetes 1.17 introduces API deprecations, please make sure your manifests are up to date before upgrading, and check Azure Advisor to confirm you are not using deprecated APIs. More information on 1.17 API deprecations here: <https://v1-17.docs.kubernetes.io/docs/setup/release/#deprecations-and-removals>
* Only Spot and Regular will be accepted as parameters for nodepool scaleSetPriority, low priority (now Spot) will no longer be accepted.

### Release Notes

* Features
  * AKS has released an Admissions Enforcer to protect the system from Admission Controller Webhooks that might impact the kube-system components. Ready more about it [here](https://docs.microsoft.com/en-us/azure/aks/faq#can-admission-controller-webhooks-impact-kube-system-and-internal-aks-namespaces)
  * AKS now allows users to create windows nodepools with the latest windows image without requiring a cluster upgrade.
  * AKS now supports [HB series](https://docs.microsoft.com/en-us/azure/virtual-machines/hb-series) and [HBv2 series](https://docs.microsoft.com/en-us/azure/virtual-machines/hbv2-series) SKU families.

## Release 2020-04-27

**This release is rolling out to all regions**

### Important Service Updates

* AKS API version 2020-04-01 (to be published) will default to VMSS (Virtual Machine Scale Sets), SLB (Standard Load Balancer) and RBAC enabled.
* AKS has introduced AKS Ubuntu 18.04 in preview. During this time we will provide both OS versions side by side. **After AKS Ubuntu 18.04 is GA**, on the next cluster upgrade, clusters running AKS Ubuntu 16.04 will receive this new image.
* Kubernetes 1.17 introduces API deprecations, please make sure your manifests are up to date before upgrading, and check Azure Advisor to confirm you are not using deprecated APIs. More information on 1.17 API deprecations here: <https://v1-17.docs.kubernetes.io/docs/setup/release/#deprecations-and-removals>
* Only Spot and Regular will be accepted as parameters for nodepool scaleSetPriority, low priority (now Spot) will no longer be accepted.

### Release Notes

* Features
  * Windows Server container support is now Generally Available on AKS.
* Preview Features
  * [The Public IP Per Node Feature](https://aka.ms/aks/pip-per-node) can now be used with Standard Load Balancer SKU.
* Bug Fixes
  * Added validation to prevent a subnetID update which would result on a failed nodepool.
  * Fixed issue when multiple delete operations where attempted simultaneously.
  * Fixed issue when performing cluster updates with APIs older than 2020-03-01 failed in clusters created using API 2020-03-01.
  * Fixed issue with agent count mismatch on upgrade.
  * Fixed an issue with a dependency on github:443 on Windows provisioning.
* Behavior Changes
  * Metrics-server now enforces burstable QoS class.
* Component Updates
  * Azure Network Policy (NPM) was updated from v1.0.33 to v1.1.0 - <https://github.com/Azure/azure-container-networking/releases/tag/v1.1.0>
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1158.200421](https://github.com/Azure/aks-engine/blob/master/vhd/release-notes/aks-windows/2019-datacenter-core-smalldisk-17763.1158.200421.txt).
  * Azure CNI was updated to 1.0.33 on Windows
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.04.16](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.04.16.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.04.16](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.04.16.txt).

## Release 2020-04-13

**This release is rolling out to all regions**

### Important Service Updates

* AKS API version 2020-04-01 (to be published) will default to VMSS (Virtual Machine Scale Sets), SLB (Standard Load Balancer) and RBAC enabled.
* AKS has introduced AKS Ubuntu 18.04 in preview. During this time we will provide both OS versions side by side. **After AKS Ubuntu 18.04 is GA**, on the next cluster upgrade, clusters running AKS Ubuntu 16.04 will receive this new image.

### Release Notes

* Bug Fixes
  * Added CriticalAddonsOnly toleration for calico-typha-horizontal-autoscaler
  * Fixed a bug where the ILB backend bool would be removed after a manual VMSS update-instances command was issued.
* Features
  * AKS has now introduced a new **Mode** property for nodepools. This will allow you to set nodepools as *System* or *User* nodepools. System nodepools will have additional validations and will be preferred by system pods, while User pool will have more lax validations and can perform additional operations like scale to 0 nodes or be removed from the cluster. Each cluster needs at least one system pool. All details here: <https://aka.ms/aks/nodepool/mode>
    * System/User nodepools are available from core CLI version 2.3.1 or greater (or latest preview extension 0.4.43)
    * Nodepool mode requires API 2020-03-01 or greater
  * AKS now allows User nodepools to scale to 0.
  * AKS Diagnostics - Added networking and connectivity checks through our new Cluster Network Configuration detector. This allows you to check DNS and subnet related issues that may have impacted your cluster. It also highlights your network configuration to give you all this information at your fingertips.
* Component Updates
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.04.06](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.04.06.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.04.06](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.04.06.txt).

## Release 2020-03-30

**This release is rolling out to all regions**

### Important Service Updates

* AKS API version 2020-04-01 will default to VMSS (Virtual Machine Scale Sets), SLB (Standard Load Balancer) and RBAC enabled.
* AKS has introduced AKS Ubuntu 18.04 in preview. During this time we will provide both OS versions side by side. **After AKS Ubuntu 18.04 is GA**, on the next cluster upgrade, clusters running AKS Ubuntu 16.04 will receive this new image.

### Release Notes

* Features
  * New VM GPU SKUs are now supported: Standard_NV12_Promo; Standard_NV12s_v3; Standard_NV24_Promo; Standard_NV24s_v3; Standard_NV48s_v3.
* Bug fixes
  * Added validation to block cluster creation if user specifies a subnet that is delegated
  * Fixed bug caused by apmz package being installed from https://upstreamartifacts.blob.core.windows.net, which is not in the AKS required endpoint egress list.
  * CoreDNS memory *limit* increased to 170Mb and assigned *Guaranteed* QoS class.
  * Fixed a bug with Cluster Proportional Autoscaler (CPA) version on 1.16. This bug is solved on version 1.7.1 which is now the version being used in AKS.
  * Fixed bug passing the correct nodepool at validation time on UDR OutboundType preview feature.
  * Patched bug where nodepool was not correctly added to internal SLB backend address pool: https://github.com/kubernetes/kubernetes/issues/89336
* Component Updates
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.03.24](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.03.24.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.03.24](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.03.24.txt).


## Release 2020-03-23

**This release is rolling out to all regions**

### Important Service Updates

* AKS API version 2020-04-01 will default to VMSS (Virtual Machine Scale Sets), SLB (Standard Load Balancer) and RBAC enabled.
* AKS has introduced AKS Ubuntu 18.04 in preview. During this time we will provide both OS versions side by side. **After AKS Ubuntu 18.04 is GA**, on the next cluster upgrade, clusters running AKS Ubuntu 16.04 will receive this new image.
* **Two security issues were discovered in Kubernetes that could lead to a recoverable denial of service.**
  * CVE-2020-8551 affects the kubelet, and has been rated Medium ([CVSS:3.0/AV:A/AC:L/PR:N/UI:N/S:U/C:N/I:N/A:L](https://www.first.org/cvss/calculator/3.0#CVSS:3.0/AV:A/AC:L/PR:N/UI:N/S:U/C:N/I:N/A:L)).
  * CVE-2020-8552 affects the API server, and has also been rated Medium ([CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:N/A:L](https://www.first.org/cvss/calculator/3.0#CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:N/A:L)).
  * **Am I vulnerable?** 
    * Only in cases where the attacker can make authorized resource requests to un-patched API server or kubelets.
    * Also AKS auto restarts apiserver and kubelet in the event of an OOM error which further limits exposure.
  * **How can I get the latest patched API and kubelet and fix this vulnerability?**
    * Upgrade to kubernetes versions v1.16.7 or v1.15.10. Or AKS preview versions v1.17.3

### Release Notes

* Bug fixes
  * Fixed bug that caused an error while updating existing AAD cluster with the new 2020-03-01 API
* Preview Features
  * Updated Azure Policy addon preview to use Gatekeeper v3 on new and updated addons.
    See more at <https://docs.microsoft.com/en-us/azure/governance/policy/concepts/rego-for-aks>
* Behavioral changes
  * All AKS Standard LBs will now have TCP Reset flag set to true.
* Component Updates
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu-1604-2020.03.11](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.03.11.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu-1804-2020.03.11](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.03.11.txt).

## Release 2020-03-16

**This release is rolling out to all regions**

### Important Service Updates

* As previously announced we have retired support for Kubernetes 1.13 releases.
* AKS API version 2020-04-01 will default to VMSS (Virtual Machine Scale Sets), SLB (Standard Load Balancer) and RBAC enabled.
* AKS has introduced AKS Ubuntu 18.04 in preview. During this time we will provide both OS versions side by side. **After AKS Ubuntu 18.04 is GA**, on the next cluster upgrade, clusters running AKS Ubuntu 16.04 will receive this new image.

### Release Notes

* Features
  * An update to AAD integration (AADv2) is in public preview. Code has been rolled out; documents and cli extension to be published in the week of 23rd March.
  * AKS now exposes the balance-similar-node-groups setting on cluster autoscaler, which enables evenly balanced numbers of auto-scaled nodes across nodepools.
  * AKS has added 2 new built-in storage classes for Azure Files Standard (azurefile) and Azure Files Premium (azurefile-premium).
  * AKS Clusters using Managed Identity are now Generally Available (GA) and will no longer need a service principal.
* Behavioral Changes
  * The default azure disk storage class configuration has been changed from `Standard_LRS` to `StandardSSD_LRS`, and `allowVolumeExpansion` has been set to true.
  * Event deletion from the cluster will be audited to increase threat detection.
* Bug Fixes
  * A change in how swap nodes (used during upgrade of VMSS) are deleted from the cluster to increase reliability.
* Component Updates
  * AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.1075.200227](https://github.com/Azure/aks-engine/blob/master/vhd/release-notes/aks-windows/2019-datacenter-core-smalldisk-17763.1075.200227.txt).

## Release 2020-03-09

**This release is rolling out to all regions**

### Important Service Updates

* K8s 1.16 introduces API deprecations which will impact user workloads as described in this [AKS issue](https://github.com/Azure/AKS/issues/1205). If you plan to upgrade to this version user action is required to remove dependencies on the deprecated APIs to avoid disruption to workloads. Ensure you have taken this action prior to upgrading to K8s 1.16.
* AKS API version 2020-04-01 will default to VMSS (Virtual Machine Scale Sets), SLB (Standard Load Balancer) and RBAC enabled.
* AKS has introduced AKS Ubuntu 18.04 in preview. During this time we will provide both OS versions side by side. **After AKS Ubuntu 18.04 is GA**, on the next cluster upgrade, clusters running AKS Ubuntu 16.04 will receive this new image.
* [Egress Breaking Change] Azure MCR has Updated its CDN endpoints - Read about it here: #1476

### Release Notes

* Features
  * Kubernetes version 1.16 is now Generally Available (GA) on AKS. (1.13 is being retired as previously communicated).
  * New Kubernetes patch versions available, v1.15.10, v1.16.7.
* Preview features
  * New Kubernetes patch versions (v1.17.3) are available for v1.17 preview.
  * AKS will now generate a default Windows username and password when creating a cluster (similarly as with ssh keys for Linux nodes). Customers can then add Windows pools to any newly created cluster without the need to have explicitly specified this parameters at create time. Customers can also reset this username and password at any time if they need it.
    * Note that, as before, You can only add Windows nodepools to clusters using VMSS and AzureCNI.
  * AKS now supports a new AKS base image based of Ubuntu 18.04 LTS.
    * You can test it by following:
    
        ```bash
        # Install or update the extension
        az extension add --name aks-preview
        # Register the preview feature flag
        az feature register --name UseCustomizedUbuntuPreview --namespace Microsoft.ContainerService
        # Create 18.04 based cluster
        az aks create -g <CLUSTER RG> -n <CLUSTER NAME> --aks-custom-headers CustomizedUbuntu=aks-ubuntu-1804
        ```
        
    * If you want to continue to create 16.04 GA clusters, just omit the -aks-custom-headers.
* Behavioral Changes
  * To ensure user is correctly configuring OutboundType: UDR feature AKS now validates not only if a Route Table is present but also if it contains a default route from 0.0.0.0/0 to allow egress through an appliance, FW, on-prem GW, etc. More details how to correctly configure this feature can be found here: <https://docs.microsoft.com/en-us/azure/aks/egress-outboundtype>.
  * AKS enforces password expiration as part of CIS compliance but excludes the linux admin account that is using public key auth only. All accounts created using password will be subject to this enforcement.
    * As usual, with the GA of 1.16 the AKS default version follows n-1 and is now 1.15
    * As per https://github.com/Azure/AKS/issues/1304 AKS will now upgrade the rest of the fleet to CoreDNS 1.6.6 after upgrading only non-Proxy users on [Release 2020-01-27](#release-2020-01-27).
* Component Updates
  * AKS Ubuntu 16.04 image updated to [AKSUbuntu:1604:2020.03.05](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.03.05.txt).
  * AKS Ubuntu 18.04 image release notes: [AKSUbuntu:1804:2020.03.05](vhd-notes/aks-ubuntu/AKSUbuntu-1804/2020.03.05.txt).
  * Updated to Moby 3.0.10 - <https://github.com/Azure/moby/releases/tag/3.0.10>.
  * Updated Azure CNI plugin version for Linux to 1.0.33 and Azure CNI plugin version for Windows 1.0.30 - <https://github.com/Azure/azure-container-networking/releases>.
  * External DNS image was updated to v0.6.0.
  * (Added 03/16/2020) AKS Windows image has been updated to [2019-datacenter-core-smalldisk-17763.973.200213](https://github.com/Azure/aks-engine/blob/master/vhd/release-notes/aks-windows/2019-datacenter-core-smalldisk-17763.973.200213.txt)

## Release 2020-03-02

**This release is rolling out to all regions**

### Important Service Updates

* K8s 1.16 introduces API deprecations which will impact user workloads as described in this [AKS issue](https://github.com/Azure/AKS/issues/1205). When AKS supports this version user action is required to remove dependencies on the deprecated APIs to avoid disruption to workloads. Ensure you have taken this action prior to upgrading to K8s 1.16 when it is available in AKS.
* 1.16 will GA on the week of March 9th and you will no longer be able to create 1.13.x based clusters or nodepools.

### Release Notes

* Features
  * Added balance-similar-node-groups as an additional parameter users can configure for AKS Managed Cluster Autoscaler (CA)
* Behavioral Changes
  * For enhanced security AKS has removed CHACHA from API server accepted tls cipher suites.

## Release 2020-02-24

**This release is rolling out to all regions**

### Important Service Updates

* K8s 1.16 introduces API deprecations which will impact user workloads as described in this [AKS issue](https://github.com/Azure/AKS/issues/1205). When AKS supports this version user action is required to remove dependencies on the deprecated APIs to avoid disruption to workloads. Ensure you have taken this action prior to upgrading to K8s 1.16 when it is available in AKS.
* With the introduction of Kubernetes v1.16 on the last release that marked the start of the deprecation for v1.13 in AKS. 1.13 is scheduled to be retired on February 28th.

### Release Notes

* Features
  * AKS now supports [Service Account Token Volume Projection](https://github.com/Azure/AKS/issues/1208)
* Preview Features
  * AKS now supports [Azure Spot NodePools](https://docs.microsoft.com/en-us/azure/aks/spot-node-pool)
* Bug Fixes
  * Fixed bug on Windows Nodepools preview where vnetCidrs were sometimes not set correctly on Windows nodepools resulting in wrong NAT exceptions on Windows nodes.

## Release 2020-02-17

**This release is rolling out to all regions**

### Important Service Updates

* K8s 1.16 introduces API deprecations which will impact user workloads as described in this [AKS issue](https://github.com/Azure/AKS/issues/1205). When AKS supports this version user action is required to remove dependencies on the deprecated APIs to avoid disruption to workloads. Ensure you have taken this action prior to upgrading to K8s 1.16 when it is available in AKS.
* With the introduction of Kubernetes v1.16 on the last release that marked the start of the deprecation for v1.13 in AKS. 1.13 is scheduled to be retired on February 28th.

### Release Notes

* New Features
  * AKS Cluster AutoScaler now supports configuring the autoscaler profile parameters. <https://docs.microsoft.com/en-us/azure/aks/cluster-autoscaler#using-the-autoscaler-profile>
* Bug Fixes
  * Fixed bug when upgrading Virtual Machine Availability Set (VMAS) clusters that would trigger a PutNicOperation cancelled
  * Fixed bug causing throttling when using Internal Load Balancer
* Preview Features
  * AKS now supports adding tags and labels to nodepools
    * <https://github.com/Azure/AKS/issues/1088>
    * <https://github.com/Azure/AKS/issues/1344>
* Component Updates
  * AKS VHD image updated to [aks-ubuntu-1604-202002_202002.12](vhd-notes/aks-ubuntu/AKSUbuntu-1604/2020.02.12.txt)

## Release 2020-02-10

**This release is rolling out to all regions**

### Important Service Updates

* K8s 1.16 introduces API deprecations which will impact user workloads as described in this [AKS issue](https://github.com/Azure/AKS/issues/1205). When AKS supports this version user action is required to remove dependencies on the deprecated APIs to avoid disruption to workloads. Ensure you have taken this action prior to upgrading to K8s 1.16 when it is available in AKS.
* With the introduction of Kubernetes v1.16 on the last release that marked the start of the deprecation for v1.13 in AKS. 1.13 is scheduled to be retired on February 28th.

### Release Notes

* New Features
  * Virtual Nodes are now supported in Canada Central
  * AKS now supports [Service Account Token Volume Projection](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/#service-account-token-volume-projection)
* Preview Features
  * Windows nodepools will change to use a vhd image provided by aks-engine. This release updates the Windows base image to version: 17763.864.191211 --> Rel Notes: <https://github.com/Azure/aks-engine/blob/master/vhd/release-notes/aks-windows/2019-datacenter-core-smalldisk-17763.864.191211.txt>
    * **Important** With this change, the Image  Publisher to "microsoft-aks" also changes, as such existing node pools cannot upgrade to this new image. To get the newest OS image, you'll have to create a new node pool.
* Bug Fixes
  * Improved error message when attempting to skip minor versions when performing an upgrade operation.
  * Fixed a bug where the dashboard would not work when RBAC was set to false for kubernetes v1.16/v1.17
* Behavioral Changes
  * AKS has released a new API [version](https://github.com/Azure/azure-rest-api-specs/tree/master/specification/containerservice/resource-manager/Microsoft.ContainerService/stable/2020-02-01)


## Release 2020-02-03

**This release is rolling out to all regions**

### Important Service Updates

* K8s 1.16 introduces API deprecations which will impact user workloads as described in this [AKS issue](https://github.com/Azure/AKS/issues/1205). When AKS supports this version user action is required to remove dependencies on the deprecated APIs to avoid disruption to workloads. Ensure you have taken this action prior to upgrading to K8s 1.16 when it is available in AKS.
* CoreDNS has been updated to v1.6.6. This change can affect users using the deprecated Proxy plugin which is no longer supported. Users should replace that with the Forward Plugin.
<https://github.com/Azure/AKS/issues/1304>
* With the introduction of Kubernetes v1.16 on the last release that marked the start of the deprecation for v1.13 in AKS. 1.13 is scheduled to be retired on February 28th.

### Release Notes

* New Features
  * AKS now supports specifying the Outbound Port and Idle Timeout properties on the Azure SLB. https://aka.ms/aks/slb-ports
* Bug Fixes
  * Fixed a bug that caused a billing extension error.
* Preview features
  * AKS now supports specifying Outbound type to define if the cluster should egress through the Standard Load Balancer (SLB) or a custom UDR (that sends egress traffic through a custom FW, on-prem gateway, etc.) Egress requirements are still the same, wherever the traffic egresses from. <https://aka.ms/aks/egress>
* Behavioral Changes
  * The private cluster FQDN format has changed from *guid.<region>.azmk8s.io to *guid.privatelink.<region>.azmk8s.io
    

## Release 2020-01-27

**This release is rolling out to all regions**

### Important Service Updates

* AKS has updated supported versions as announced in this [service update](https://azure.microsoft.com/updates/azure-kubernetes-service-will-be-retiring-support-for-kubernetes-versions-1-11-and-1-12/) and [AKS issue](https://github.com/Azure/AKS/issues/1235) to move from the "N-3" to "N-2" window. Starting December 9th, 2019 AKS has removed support for anything older than K8s 1.13 and scoped the active support window to K8s 1.13, 1.14, and 1.15.
* K8s 1.16 introduces API deprecations which will impact user workloads as described in this [AKS issue](https://github.com/Azure/AKS/issues/1205). When AKS supports this version user action is required to remove dependencies on the deprecated APIs to avoid disruption to workloads. Ensure you have taken this action prior to upgrading to K8s 1.16 when it is available in AKS.
* CoreDNS will be updated to v1.6.6. This change can affect users using the deprecated Proxy plugin which is no longer supported. Users should replace that with the Forward Plugin.
<https://github.com/Azure/AKS/issues/1304>
* With the introduction of Kubernetes v1.16 this marks the start of the deprecation for v1.13 in AKS. 1.13 is scheduled to be retired on February 28th.

### Release Notes

* New Features
  * AKS now supports Customer-Managed keys (BYOK) to be used for encryption of both OS and Data Disks of AKS clusters.
  <https://docs.microsoft.com/en-us/azure/aks/azure-disk-customer-managed-keys>
  * New Supported SKUs: Standard_ND40s_v3, Standard_ND40rs_v2, Standard_D_v4, Standard_E_v4 and Standard_NP families
  * New supported patch version for kubernetes v1.15 (v1.15.7)
  * AKS now supports up to 10 nodepools.
  * Virtual Nodes is now supported in Korea Central
  * AKS now supports setting tags per nodepool. Which will propagate automatically to all nodes in the nodepool.
* Preview Features
  * AKS now supports Kubernetes versions 1.16 (1.16.1, 1.16.2) and 1.17 (1.17.0) in preview.
* Bug Fixes
  * Fixed bug with calico-typha health check in cases where localhost doesn't resolve 127.0.0.1
  * Fixed validation bug where users could not deploy AKS at the same time of their SLB Public IP resource
  * For clusters using Managed Identities and addons a bug was fixed where the addons' identity information was not displayed correctly.
  * Fixed bug where Accelerated Networking would be disabled after an upgrade.
  * Fixed issue while retrying to create the SLB default egress IP.
  * Fixed bug where DS3_v2 would be Network Accelerated despite supporting it.
  * Fixed several issues where under specific conditions users could see Azure API throttling on their subscriptions. - <https://github.com/Azure/AKS/issues/1413>
  * Fixed bug with `az aks reset-credentials --reset-aad` that would require manual intervention to complete.
* Component Updates
  * Updated to Moby 3.0.8 - <https://github.com/Azure/moby/releases/tag/3.0.8>
  * Updated AKS-Engine to 0.45.0 - <https://github.com/Azure/aks-engine/releases/tag/v0.45.0>
  * Azure Monitor for Containers Agent updated to [01072020 release](https://github.com/microsoft/Docker-Provider/releases/tag/v8.0.0.2)
    * **Important** Node cpu, node memory, container cpu and container memory metrics were obtained earlier by querying kubelet readonly port(http://$NODE_IP:10255). Agent now supports getting these metrics from kubelet port(https://$NODE_IP:10250) as well. During the agent startup, it checks for connectivity to kubelet port(https://$NODE_IP:10250), and if it fails the metrics source is defaulted to readonly port(http://$NODE_IP:10255).
  * AKS VHD image updated to [aks-ubuntu-1604-202001_2020.01.10](https://github.com/jackfrancis/aks-engine/blob/1de1ad55f86e863952081f0a6fbf85910d02e9d7/releases/vhd-notes/aks-ubuntu-1604/aks-ubuntu-1604-202001_2020.01.10.txt)


## Release 2019-12-02

**This release is rolling out to all regions**

### Important Service Updates

* AKS is updating supported versions as announced in this [service update](https://azure.microsoft.com/updates/azure-kubernetes-service-will-be-retiring-support-for-kubernetes-versions-1-11-and-1-12/) and [AKS issue](https://github.com/Azure/AKS/issues/1235) to move from the "N-3" to "N-2" window. Starting December 9th, 2019 AKS will remove support for anything older than K8s 1.13 and scope the active support window to K8s 1.13, 1.14, and 1.15.
* K8s 1.16 introduces API deprecations which will impact user workloads as described in this [AKS issue](https://github.com/Azure/AKS/issues/1205). When AKS supports this version user action is required to remove dependencies on the deprecated APIs to avoid disruption to workloads. Ensure you have taken this action prior to upgrading to K8s 1.16 when it is available in AKS.

### Release Notes

* Bug Fixes
  * Fixed cases of failed cluster creations due to an "Unregistering" or "NotRegistered" state for a subscription's access to NRP or CRP.
  * Added AKS validation that service principal secrets may not exceed 190 bytes.
* Behavior Changes
  * Fixed a bug where outbound IP creation for Standard Load Balancer did not retry when receiving internal server error from Network Resource Provider.
  * Improved validation of agent pool operations to only validate agent pool count when cluster autoscaler is turned off. When cluster autoscaler is turned on the minCount and maxCount set are used for count validations.

## Release 2019-11-18

**This release is rolling out to all regions**

### Release Notes

* New Features
  * Announcing AKS Diagnostics in Public Preview
    * Hopefully, most of the time your AKS clusters are running happily and healthily. However, when things go wrong, we want to make sure that our AKS customers are empowered to easily and quickly figure out what's wrong and the next steps for mitigation or deeper investigation.
    * AKS Diagnostics is a guided and interactive experience in the Azure Portal that helps you diagnose and solve potential issues with your AKS cluster, such as identity and security management, node issues, CRUD operations and more. Detectors in AKS Diagnostics intelligently find issues and observations as well as recommend next steps. This feature comes configured completely out-of-the-box and is free for all our AKS customers.
    * Get started and learn more here: https://aka.ms/aks/diagnostics
  * Support for new regions:
    * Norway East
    * Norway West
* Bug Fixes
  * Fixed enforcement that node pool versions can never be greater than the control plane `major.minor.patch` version.
  * Fixed error messages incorrectly stating a version was not supported to return proper errors detailing what validation was failed.
  * Added retries to retrieve a managed resource group. Errors can be returned with `ResourceGroupNotFound` due to slow Azure Resource Manager (ARM) data replication when AKS tries to place new managed resources into the managed resource group.
* Behavior Changes
  * Added a label `control-plane=true` to the `kube-system` namespace
* Component updates
  * AKS-Engine has been updated to [v0.43.0](https://github.com/Azure/aks-engine/releases/tag/v0.43.0)

## Release 2019-11-11

**This release is rolling out to all regions**

### Important Service Updates

* With the official 2019-11-04 Azure CLI release (v2.0.76), AKS has defaulted new cluster
  creates to VM Scale-Sets and Standard Load Balancers (VMSS/SLB) instead of VM
  Availability Sets and Basic Load Balancers (VMAS/BLB). Users can still explicitly
  choose VMAS and BLB.
* From 2019-10-14 AKS Portal has defaulted new cluster
  creates to VM Scale-Sets and Standard Load Balancers (VMSS/SLB) instead of VM
  Availability Sets and Basic Load Balancers (VMAS/BLB).
* From 2019-11-04 the CLI extension has a new parameter --zones to replace --node-zones, which specifies the zones to be used by the cluster nodes.

### Release Notes

* New Features
  * AKS has created a new default role clusterMonitoringUser to simplify the Azure Monitor Live metrics onboard experience so that moving forward users don't need to explicitly grant those permissions.
  This user will have 'GET' and 'LIST' permissions to  'POD/LOGS', 'EVENTS', 'DEPLOYMENTS', 'PODS', 'REPLICASETS' and 'NODES'.
  * Support for new regions:
    * Germany North
    * Germany West Central
    * UAE North
    * Switzerland North
    * Switzerland West
  * On-Demand Certificate Rotation is now Generally Available: <https://docs.microsoft.com/en-us/azure/aks/certificate-rotation>
* Bug Fixes
  * Fixed bug with MC_ infra resource group not being created/propagated quickly enough and triggering ResourceGroupNotFound errors.
  * Fixed missing cloud provider role binding: <https://github.com/Azure/AKS/issues/1104>
  * Fixed nodepool bug where a PUT would be accepted while the pool was being deleted.
  * Correctly assign the cluster-admin clusterrolebinding to the clusterAdmin user in all cases.
  * Fixed several upstream bugs with attach/detach in VMSS:
    * <https://github.com/kubernetes/kubernetes/pull/85158>
    * <https://github.com/kubernetes/kubernetes/pull/83685>
    * <https://github.com/kubernetes/kubernetes/pull/84917>
    * AKS is rolling this changes in automatically and users do not need to upgrade.
  * Fixed a bug upgrading Basic LB clusters that were using the preview of API Authorized Ranges feature, only supported in GA with Standard LB.
* Behavior Changes
  * Add priorityClass for calico-node and ensure calico-node tolerates all NoSchedule taints. This ensures calico-node will still be scheduled to all nodes even when users have added other node taints.
* Component updates
  * Metrics server has been updated to v0.3.5

## Release 2019-10-28

**This release is rolling out to all regions**

### Service Updates

* With the official 2019-11-04 Azure CLI release, AKS will default new cluster
  creates to VM Scale-Sets and Standard Load Balancers (VMSS/SLB) instead of VM
  Availability Sets and Basic Load Balancers (VMAS/BLB). Users can still explicitly
  choose VMAS and BLB.
* From 2019-10-14 AKS Portal will default new cluster
  creates to VM Scale-Sets and Standard Load Balancers (VMSS/SLB) instead of VM
  Availability Sets and Basic Load Balancers (VMAS/BLB).
* From 2019-11-04 the CLI extension will have a new parameter --zones to replace --node-zones, which specifies the zones to be used by the cluster nodes.

### Release Notes

* New Features
  * Multiple Nodepools backed AKS clusters are now Generally Available (GA)
    * https://docs.microsoft.com/en-us/azure/aks/use-multiple-node-pools
  * Cluster Autoscaler is now Generally Available (GA)
    * https://docs.microsoft.com/en-us/azure/aks/cluster-autoscaler
  * Availability Zones are now Generally Available (GA)
    * https://docs.microsoft.com/en-us/azure/aks/availability-zones
  * AKS API server Authorized IP Ranges is now Generally Available (GA)
    * https://docs.microsoft.com/en-us/azure/aks/api-server-authorized-ip-ranges
  * Kubernetes versions 1.15.5, 1.14.8 and 1.13.12 have been added.
    * These versions have new API call logic that helps users with many AKS clusters in the same subscription to incur is less throttling.
    * These versions have security fixes for [CVE-2019-11253](https://github.com/Azure/AKS/issues/1262)
  * The minimum `--max-pods` value has been altered from **30 per node to 30 per Nodepool**. Each node will have a hard **minimum of 10 pods** the user can specify, but this value can only be used if the total pods across all nodes on the nodepool accrue to 30+.
* Bug Fixes
  * Added additional validation to nodepool operations to check for enough address space. If there is no address space left for a scale/upgrade operation,
  the operation will not start and give a descriptive error message.
  * Fixed bug with Nodepool operations and `az aks update-credentials` to reflect on the agentpool state.
  * Fixed bug on Nodepool operations when using incorrect SKUs to have more descriptive error.
  * Added validation to block `az aks update-credentials` if nodepool is not ready to avoid conflicts.
  * Node count on the Nodepool is ignored when user has autoscaling enabled. (Manual scale with autoscaler enabled is not allowed)
  * Fixed bug where some clusters would still receive an older Moby version (3.0.6). Current version is 3.0.7
* Preview Features
  * Windows docker runtime updated to 19.03.2
* Component updates
  * Moby has been updated to v3.0.7
  * AKS-Engine has been updated to v0.41.5

## Release 2019-10-14

**This release is rolling out to all regions**

### Service Updates

* With the official 2019-11-04 Azure CLI release, AKS will default new cluster
  creates to VM Scale-Sets and Standard Load Balancers (VMSS/SLB) instead of VM
  Availability Sets and Basic Load Balancers (VMAS/BLB).
* From 2019-10-14 AKS Portal will default new cluster
  creates to VM Scale-Sets and Standard Load Balancers (VMSS/SLB) instead of VM
  Availability Sets and Basic Load Balancers (VMAS/BLB). Users can still explicitly
  choose VMAS and BLB.
* From 2019-11-04 the CLI extension will have a new parameter --zones to replace --node-zones, which specifies the zones to be used by the cluster nodes.

### Release Notes

* Bug Fixes
  * Fixed a bug where nodepool API would not accept and handle empty fields correctly, "", "{}", "{"properties":{}}".
  * Fixed a bug with http application routing addon where portal would lowercase all addon names and the input was not accepted.
  * Upgrade operation will not fail when manual changes have been applied to the SinglePlacementGroup property on underlying VMSS.
  * Fixed bug where customers trying to enable pod security policy without providing k8s version in the request would encounter failure (500 internal error).
  * Fixed bug where NPM pods would consume an excessive amount of memory.
* Preview Features
  * Updated windows image to the latest version.
* Component Updates
  * Updated Azure Network Policy (NPM) version to v1.0.28
  * Azure Monitor for Containers Agent updated to 2019-10-11 release: <https://github.com/microsoft/Docker-Provider/releases>

## Release 2019-10-07

**This release is rolling out to all regions**

### Service Updates

* With the official 2019-11-04 Azure CLI release, AKS will default new cluster
  creates to VM Scale-Sets and Standard Load Balancers (VMSS/SLB) instead of VM
  Availability Sets and Basic Load Balancers (VMAS/BLB).
* From 2019-10-14 AKS Portal will default new cluster
  creates to VM Scale-Sets and Standard Load Balancers (VMSS/SLB) instead of VM
  Availability Sets and Basic Load Balancers (VMAS/BLB). Users can still explicitly
  choose VMAS and BLB.

### Release Notes

* Behavioral Changes
  * Improved process and speed of upgrade to reduce impact to pods during the process
* Bug Fixes
  * Fixed a bug where kubelet reserved values where applied only to primary node pool. Now correctly applied to all nodepools if using multiple nodepools.
  * Added additional service principal validation on Upgrade.
  * Prevented multiple concurrent provisioning operations.
* New Features
  * Kubernetes versions 1.15.4, 1.14.7 and 1.13.11 have been added.
* Component Updates
  * AKS-Engine has been updated to v0.41.4

## Release 2019-09-30

**This release is rolling out to all regions**

### Service Updates

* With the official 2019-11-04 Azure CLI release, AKS will default new cluster
  creates to VM Scale-Sets and Standard Load Balancers (VMSS/SLB) instead of VM
  Availability Sets and Basic Load Balancers (VMAS/BLB).
* Support for node pool taints and public ip assignment per node with AKS will
  be available in Azure CLI extension v0.4.17
* AKS Availability Zone support has been expanded to the following regions:
  * Japan East
  * UK South
  * France Central
  * East US
  * Central US
  * Australia East

### Release Notes

* New Features
  * Customer may use NetworkPolicies with Azure CNI and Kubenet based clusters:
    * https://docs.microsoft.com/en-us/azure/aks/use-network-policies
  * Managed Identity (MSI) support is now in *public preview*.
    * https://docs.microsoft.com/en-us/azure/aks/use-managed-identity
* Bug Fixes
  * Fix a bug where the removal of an outbound rule from standard load balancer
    in the AKS node resource group could cause the failure of subsequent
    cluster operations.
  * Fixed the issue impacting GPU enabled clusters being unable to install the
    required NVidia drivers.
  * Fixed an issue where customers could encounter a CSE (custom script
    extension) error 99 during operations.
  * Fixed an issue with the Azure Portal cluster metrics multiplying the metric
    count based on the viewed window of time. Moving forward the default for
    these metrics will be correctly set to average() as opposed to sum().
    * For customers with metrics already enabled and in-use in portal, the sum()
      type will continue to be supported.
* Component Updates
  * AKS-Engine has been updated to v0.40.1
* Preview Features
  * Fixed an issue where nodes provisioned by cluster autoscaler would be
    de-provisioned when resetting or updating AAD credentials.

## Release 2019-09-23


### Service Updates

* Azure CLI 2.0.74 released with key AKS changes
  * https://github.com/Azure/azure-cli/releases/tag/azure-cli-2.0.74
  * Added `--load-balancer-sku` parameter to aks create command, which allows for
    creating AKS cluster with SLB
  * Added `--load-balancer-managed-outbound-ip-count`,
    `--load-balancer-outbound-ips` and `--load-balancer-outbound-ip-prefixes`
    parameters to aks `[create|update]` commands, which allow for updating load
    balancer profile of an AKS cluster with SLB
  * Added `--vm-set-type` parameter to aks create command, which allows to
    specify vm types of an AKS Cluster (vmas or vmss)

### Release Notes
* Bug Fixes
  * Fixed an issue where the node pool count rendered in the portal would be incorrect when not using the multiple node pools feature.
  * Fixed an issue to ensure a cluster upgrade will upgrade both the control plane and agent pools for clusters using VMSS, but not multiple agent pools.
  * Resolved an issue with cluster upgrades that could remove existing
    diagnostics settings and data erroneously.
  * Fixed an issue where AKS was not validating user defined taint formats per agent pool resulting in
    failures at cluster creation time.
* Behavioral Changes
  * Increased the reserved CPU cores for kubelets to scale proportionally to cores available on the kubelet's host node. Read more about [AKS resource reservation here](https://docs.microsoft.com/en-us/azure/aks/concepts-clusters-workloads#resource-reservations).
* Preview Features
  * Fixed an issue where AKS was not enforcing the minimum Kubernetes version
    required at additional agent pool creation time when using the multiple node pools feature.
  * Fixed an issue where creating new agent pools will overwrite the route
    table and customers would lose their route table rules. Fixes issue [#1212](https://github.com/Azure/AKS/issues/1212).

## Release 2019-09-16

**This release is rolling out to all regions**

### Service Updates

* The announced updates to default new clusters to VMSS/SLB configurations is
  under way, if you are using the `aks-preview` Azure CLI extension,
  all clusters created are now defaulted to VMSS & SLB.
* AKS Kubernetes 1.10 support will end-of-lifed on Oct 25, 2019
* AKS Kubernetes 1.11 & 1.12 support will end-of-lifed on Dec 9, 2019
* New Documentation additions:
  * [Authenticate with Azure Container Registry from AKS](https://docs.microsoft.com/en-us/azure/aks/cluster-container-registry-integration)
  * [Security hardening in AKS virtual machine hosts](https://docs.microsoft.com/en-us/azure/aks/security-hardened-vm-host-image)
* The AKS team is pleased to announce the new `aks-periscope` tool.
  * AKS Periscope will allow AKS customers to run initial diagnostics and
    collect logs into an Azure Blob storage account to help them analyze and
    identify potential problems.
  * For more information please see: https://aka.ms/AKSPeriscope

### Release Notes

* New Features
  * AKS now GA in the Azure US Gov Virginia region.
    * https://azure.microsoft.com/en-us/updates/azure-kubernetes-service-is-now-available-in-azure-government/
  * Control of egress traffic for cluster nodes in AKS is now GA
    * This feature allows you to restrict outbound network communication for
      you cluster as required for compliance or other secure use-cases.
    * https://docs.microsoft.com/en-us/azure/aks/limit-egress-traffic
* Known Issues:
  * Clusters that do not have PSPs enabled upgrading to Kubernetes 1.15 will fail
    * https://github.com/Azure/AKS/issues/1220
* Bug Fixes
  * An issue where excessively logs (eg node/status patch events) were being
    emitted to the audit logs stream and stored. Customer should now see
    greatly reduced audit log volume
* Preview Features
  * The `--control-plane-only` flag has been added to the `aks-preview` extension - this command
    will force the upgrade of the customers control plane without simultaneously
    upgrading the other nodepools. This functionality is only supported for
    multi-pool clusters.
    * See: https://github.com/Azure/azure-cli-extensions/blob/master/src/aks-preview/HISTORY.md

## Release 2019-09-09

**Service Updates**

* AKS Kubernetes 1.10 support will end-of-lifed on Oct 25, 2019
  * Please see: https://azure.microsoft.com/en-us/updates/kubernetes-1-10-x-end-of-life-upgrade-by-oct-25-2019/
* AKS Kubernetes 1.11 & 1.12 support will end-of-lifed on Dec 9, 2019
  * Note that AKS Kuberrnetes 1.15 support is in public preview, on Dec 9, 2019
    the supported *minor* Kubernetes versions will be 1.13, 1.14, 1.15
  * Azure Updates blog post with additional details will be published this week

* New Features
  * VMSS backed AKS clusters are now GA
    * VMSS is the underlying compute resource type which enables features such
      as cluster autoscaler, but is a separate feature.
    * See https://docs.microsoft.com/azure/virtual-machine-scale-sets/overview
      and https://docs.microsoft.com/azure/aks/cluster-autoscaler
      for more information.
    * **NOTE**: Official support in the Azure CLI for AKS+VMSS will be released
      on 2019-09-24 (version 2.0.74 https://github.com/Azure/azure-cli/milestone/73)
  * Standard Load Balancer support (SLB) is now GA
    * See https://docs.microsoft.com/azure/aks/load-balancer-standard
      for documentation.
    * **NOTE**: Official support in the Azure CLI for AKS+SLB will be released
      on 2019-09-24 (version 2.0.74 https://github.com/Azure/azure-cli/milestone/73)
  * Support for the following VM SKUs is now released: Standard_D48_v3,
    Standard_D48s_v3, Standard_E48_v3, Standard_E48s_v3, Standard_F48s_v2,
    Standard_L48s_v2, Standard_M208ms_v2, Standard_M208s_v2
* Bug Fixes
  * CCP Fall back is not working as expected. This is because we updated CCP
    to turn on useCCPPool flag based on the toggle. But we did not refresh the useCCPPool flag after the change. So the flag is still false even though toggle changed it to true.
  * Fixed an issue where cluster upgrade could be blocked when the "managedBy"
    property is missing from the node resource group.
  * Fixed an issue where ingress controller network policy would block all
    egress traffic when assigned to pods (using label selectors).
* Behavioral Changes
  * Review the planned changes for new cluster creation defaults referenced in
    [Release 2019-08-26](https://github.com/Azure/AKS/releases/tag/2019-08-26)
* Preview Features
  * Fixed an issue where multiple nodepool clusters would use the incorrect
    version(s) and block upgrades.
  * Fixed an issue where AKS would incorrectly allow customers to specify
    different versions for multiple nodepools.
  * Fixed an issue where the incorrect node count would be returned or fail to
    update when using multiple node pools


## Release 2019-09-02

* Preview Features
  * Kubernetes 1.15 is now in Preview (1.15.3)

* Bug Fixes
  * A bug where kube-svc-redirect would crash due to an invalid bash line has been fixed.
  * A recent Kubernetes dashboard change to enable self-signed certs has been reverted due to browser issues.
  * A bug where the OMSAgent pod would fail scheduling on a user tainted node has been fixed with proper toleration on the OMSAgent pod.
  * A preview bug allowing more than 8 node pools to be created has been fixed to enforce a max of 8 node pools per cluster.
  * A preview bug that would change the primary node pool when adding a new node pool has been fixed.

* Behavioral Changes
  * Review the planned changes for new cluster creation defaults referenced in [Release 2019-08-26](https://github.com/Azure/AKS/releases/tag/2019-08-26)

* Component Updates
  * aks-engine has been updated to v0.40.0
    * https://github.com/Azure/aks-engine/releases/tag/v0.40.0

## Release 2019-08-26

**This release is rolling out to all regions**

* Features
  * Added prometheus annotation to coredns to facilitate metric port discovery
    * For more info please check: <https://docs.microsoft.com/en-us/azure/azure-monitor/insights/container-insights-agent-config#overview-of-configurable-prometheus-scraping-settings>
* Bug Fixes
  * Fixed bug with older 1.8 clusters that was preventing clusters from upgrading.
    * **Important: this was a best effort fix since these cluster versions are out of support. Please upgrade to a currently supported version**
    * For information on how AKS handles Kubernetes version support see:
      [Supported Kubernetes versions in Azure](https://docs.microsoft.com/en-us/azure/aks/supported-kubernetes-versions)
  * Removed the default restricted Pod Security Policy to solve race condition with containers not seeing the user in their config. This policy can be applied by customers.
  * Fixed a bug with kube-proxy, ip-masq-agent and kube-svc-redirect where in certain scenarios they could try to access iptables at the same time.
* Preview Features
  * CLI extension updated for new Standard Load Balancer (SLB) and VM Scale Set (VMSS) Parameters:
    * `--vm-set-type` Agent pool vm set type. VirtualMachineScaleSets or AvailabilitySet.
    * `--load-balancer-sku` - Azure Load Balancer SKU selection for your cluster. Basic or Standard.
    * `--load-balancer-outbound-ip-prefixes` - Comma-separated public IP prefix resource IDs for load balancer outbound connection. Valid for Standard SKU load balancer cluster only.
    * `--load-balancer-outbound-ips` - Comma-separated public IP resource IDs for load balancer outbound connection. Valid for Standard SKU load balancer cluster only.
    * `--load-balancer-managed-outbound-ip-count` - Desired number of automatically created and managed outbound IPs for load balancer outbound connection. Valid for Standard SKU load balancer cluster only.
* Behavioral Changes
  * Starting from 2019-09-10, the **preview CLI extension** will default new cluster creates to VM Scale-Sets and Standard Load Balancers (VMSS/SLB) instead of VM Availability Sets and Basic Load Balancers (VMAS/BLB).
  * Starting from 2019-10-22 the official CLI and Azure Portal will default new cluster creates to VMSS/SLB instead of VMAS/BLB.
  * These client defaults changes are important to be aware of due to:
    * SLB will automatically assign a public IP to enable egress. This is a requirement placed by Azure Standard Load Balancers, to learn more about Standard vs. Basic, read [here](https://docs.microsoft.com/en-us/azure/load-balancer/load-balancer-standard-overview).
    * SLB enables bringing your own IP address to be used, you will be able to define these with new parameters.
    * The capability to use an SLB without any public IP assigned is on the roadmap plan.
    * You may still provision a basic load balancer by specifying "basic" for the "loadbalancersku" property at cluster create time.
    * Read more at <https://aka.ms/aks/slb>
* Component Updates
  * aks-engine has been updated to v0.39.2
    * <https://github.com/Azure/aks-engine/releases/tag/v0.39.2>
  * Azure Monitor for Containers Agent updated to 2019-08-22 release: <https://github.com/microsoft/Docker-Provider/releases>

## Release 2019-08-19 (Hotfix)

**This release is rolling out to all regions**

**Please Note**: This release includes new Kubernetes versions 1.13.10 &
1.14.6 these include the fixes for CVEs CVE-2019-9512 and
CVE-2019-9514. Please see our [customer guidance](https://github.com/Azure/AKS/issues/1159)

* Bug Fixes
  * New kubernetes versions released to fix CVE-2019-9512 and CVE-2019-9514
    * Kubernetes 1.14.6
    * Kubernetes 1.13.10
  * Fixed Azure Network Policy bug with multiple labels under a matchLabels selector.
  * Fix for CNI lock timeout issue caused due to race condition in starting telemetry process.
  * Fixed issue creating AKS clusters using supported Promo SKUs
* Component Updates
  * aks-engine has been updated to v0.38.8
    * https://github.com/Azure/aks-engine/releases/tag/v0.38.8
  * Azure CNI has been updated to v1.0.25


## Release 2019-08-12

**This release is rolling out to all regions**

* Bug Fixes
  * Several bug fixes for AKS NodePool creation and other CRUD operations.
  * Fixed audit log bug on older < 1.9.0 clusters.
    * **Important: this was a best effort fix since these cluster versions are out of support. Please upgrade to a currently supported version**
    * For information on how AKS handles Kubernetes version support see:
      [Supported Kubernetes versions in Azure](https://docs.microsoft.com/en-us/azure/aks/supported-kubernetes-versions)
  * Improved error messaging for VM size errors, including actions to take.
  * Fixed for PUT request bug that caused an unexpected API restart.

* Behavioral Changes
  * AKS has released an API update, documentation available here: [https://docs.microsoft.com/en-us/rest/api/aks/managedclusters](https://docs.microsoft.com/en-us/rest/api/aks/managedclusters)
    * **Important:** With this API update there are changes to the API whitelisting API. This is now under [ManagedClusterAPIServerAccessProfile](https://docs.microsoft.com/en-us/rest/api/aks/managedclusters/createorupdate#managedclusterapiserveraccessprofile), where previously it was a top level property.

## Release 2019-08-05

**This release is rolling out to all regions**

**Please Note**: This release includes new Kubernetes versions 1.13.9 &
1.14.5 (GA today) these include the fixes for CVEs CVE-2019-11247 and
CVE-2019-11249. Please see our [customer guidance](https://github.com/Azure/AKS/issues/1145)

* New Features
  * Kubernetes 1.14 is now GA (1.14.5)
    * As of Monday August 12th (2019-08-12) customers running Kubernetes 1.10.x
      have 60 days (2019-10-14) to upgrade to a supported release. Please see
      [AKS supported versions document][1] for more information.
  * [Kubernetes Audit log](https://docs.microsoft.com/en-us/azure/aks/view-master-logs)
    support is now GA.
* Bug Fixes
  * Fixed an issue where creating a cluster with a custom subnet would return an
    HTTP error 500 vs 400 when the subnet could not be found.
* Behavioral Changes
* Preview Features
  * Fixed an issue where customers could not create a new node pool with AZs
    even if they were already using SLBs.
  * Fixed an issue where VMSS cluster commands could return the incorrect node
    count.
* Component Updates
  * aks-engine has been updated to v0.38.7
    * https://github.com/Azure/aks-engine/releases/tag/v0.38.7


## Release 2019-07-29

* New Features
  * Customers may now create multiple AKS clusters using ARM templates
    regardless of what region the clusters are located in.
* Bug Fixes
  * AKS has resolved the issue(s) with missing metrics in the default
    metrics blade.
  * An issue where the `--pod-max-pids` was set to 100 (maximum) for clusters
    and re-applied during upgrade causing `pthread_create() failed (11: Resource
    temporarily unavailable)` pod start failures was fixed.
    * See https://github.com/Azure/aks-engine/pull/1623 for more information

* Preview Features
  * AKS is now in **Public Preview** in the Azure Government (Fairfax, VA)
    region. Please note the following:
    * Azure Portal support for AKS is in progress, for now customers must use the
      Azure CLI for all cluster operations currently.
    * AKS preview features are not supported in Azure Government currently and will
      be supported when those features are GA.
  * Fixed an issue where a delete request for a locked VMSS node would get an
    incorrect and unclear `InternalError` failure - the error message and error
    code have both been fixed.
  * Fixed an issue with egress filtering where managed AKS pods
    would incorrectly use the IP address to connect instead of the FQDN.
  * Fixed an issue with the SLB preview where AKS allowed the customer to
    provide an IP address already in use by another SLB.
  * An issue that prevented customers from using normal cluster operations
    on multiple node pool clusters with a single VMSS pool has been fixed.

* Component Updates
  * AKS-Engine has been updated to v0.38.4
    * https://github.com/Azure/aks-engine/releases/tag/v0.38.4

## Release 2019-07-22

* Preview Features
  * An issue where New Windows node pools in existing cluster would not get
    updated Windows versions has been fixed.
  * TCP reset has been set for all new clusters using the SLB preview.
  * An issue where AKS would trigger a scale operation requested on a previously
    deleted VMSS cluster has been fixed.
* Component Updates
  * AKS-Engine has been updated to v0.38.3

## Release 2019-07-15

**Important behavioral change**: All AKS clusters are being updated to pull all
needed container images for cluster operations from Azure Container Registry,
this means if you have custom allow/deny lists, port filtering, etc you will
need to update your network configuration to allow ACR.

[Please see the documentation](https://docs.microsoft.com/en-us/azure/aks/limit-egress-traffic#required-ports-and-addresses-for-aks-clusters) for more
information including all required AKS cluster ports and URLs


* New Features
  * Support for the M, NC_promo and DS_v3 Azure Compute VM SKUs has been added.
* Bug Fixes
  * Fixed an issue with clusters created in Canada and Australia regions between
    2019-07-09 and 2019-07-10 as well as US region clusters created on 2019-07-10
    where customers would receive `error: Changing property
    'platformFaultDomainCount' is not allowed` errors.

* Behavioral Changes
  * The error message returned to users when attempting to create clusters with
    an unsupported Kubernetes version in that region has been fixed.
  * Noted above, AKS has moved all container images required by AKS clusters for
    cluster CRUD operations have been moved to Azure Container Registry. This
    means that customers must update allow/deny rules and ports. See:
    [Required ports and addresses for AKS clusters](https://docs.microsoft.com/en-us/azure/aks/limit-egress-traffic#required-ports-and-addresses-for-aks-clusters)
* Preview Features
  * Fixed a VMSS cluster upgrade failure that would return: `Changing property
    'type' is not allowed.`
  * An issue where `az aks nodepool list` would return the incorrect node count
    has been resolved.
* Component Updates
  * The Azure Monitor for Container agent has been updated to the 2019-07-09 release
    * Please see the [release notes](https://github.com/Microsoft/docker-provider/tree/ci_feature_prod#07092019--).

## Release 2019-07-08

* New Features
  * Kubernetes versions 1.11.10 and 1.13.7 have been added. Customers
    are encouraged to upgrade.
    * For information on how AKS handles Kubernetes version support see:
      [Supported Kubernetes versions in Azure](https://docs.microsoft.com/en-us/azure/aks/supported-kubernetes-versions))
  * The `az aks update-credentials` command now supports Azure tenant migration of your
AKS cluster. Follow the instructions in [Choose to update or create a service principal][8] and then execute the `Update AKS cluster with new credentials` command passing in the `--tenant-id` argument.
* Behavioral Changes
  * All new clusters now have --protect-kernel-defaults enabled.
    * See: https://kubernetes.io/docs/reference/command-line-tools-reference/kubelet/
* Preview Features
  * Kubernetes 1.14.3 is now available for preview users.
  * Azure availability zone support is now in public preview.
    * This feature enables customers to distribute their AKS clusters across
      availability zones providing a higher level of availability.
    * Please see [AKS previews][previews] for additional information.
  * For all previews, please see the [previews][previews] document for opt-in
    instructions and documentation links.
* Component Updates
  * aks-engine has been updated to version 0.37.5
    * https://github.com/Azure/aks-engine/releases/tag/v0.37.5
  * Azure CNI has been updated to version 1.0.22
  * Moby has been updated to 3.0.5 from 3.0.4
    * Note that this version number is Azure specific, the Moby project does not
      have official releases / release numbers.

## Release 2019-07-01

* Bug Fixes
  * Fixed an issue with `az aks update-credentials` where the command would
    not take special characters and nodes would get incorrect values.
    Note that double quote `"` , backslash `\`, ampersand `&`, and angle quotations `<>`
    are still NOT allowed to be used as password characters.
  * Fixed an issue with update-credentials where the command would not work for VMSS clusters
    with more than 10 instances.
  * AKS now has validation to check for Resource Locks when performing Scale and Upgrade operations.
  * Fixed an issue where GPU nodes could fail to install the GPU driver due to ongoing
    background apt operations.
  * Adjusted the timeout value for Service Principal update based on the number of nodes in the
    cluster, to accommodate larger clusters.
* New Features
  * AKS now supports OS disk sizes of up to 2048GiB.
  * Persistent Tags
    * Custom tags can now be passed to AKS and will persisted onto the MC infrastructure Resource Group.
      Note: They will NOT be applied to all child resources in that RG, aka VMs, VNets, disks, etc.
* Preview Features
  * Windows Node Pools
    * AKS updated Windows default image to latest windows patch release.
  * API server authorized IP ranges
    * The max number of API server authorized IP ranges has now increased to 100.
* Component Updates
  * [AKS-Engine has been updated to v0.35.6](https://github.com/Azure/aks-engine/releases/tag/v0.35.6)
    * This change includes a new AKS VHD with the Linux Kernel CVE fixes. See more:
      https://github.com/Azure/AKS/issues/
    * This new VHD also fixes broken IPv6 support for the host.


## Release 2019-06-24

* Bug Fixes
  * Fixed an issue that could result in a failed service principal update and
    AKS cluster creation.
  * Fixed an issue where deploying AKS clusters using ARM templates without a
    defined Service Principal would incorrectly pass validation.
* Preview Features
  * Azure Standard load balancer support is now in public preview.
    * This has been a long awaited feature which enables selection of the SKU
      type offered by Azure Load Balancer to be used with your AKS cluster. Please see
      [AKS previews][previews] for additional information.
  * For all previews, please see the [previews][previews] document for opt-in
    instructions and documentation links.
* Component Updates
  * The Azure Monitor for Container agent has been updated to the 2019-06-14 release
    * Please see the [release notes](https://github.com/Microsoft/docker-provider/tree/ci_feature_prod#06142019--).

## Release 2019-06-18

* Behavioral Changes
  * **Important: Change in UDR and subnet behavior**
    * When using Kubenet with a custom subnet, AKS now checks if there is an
      existing associated route table.
    * If that is the case AKS will NOT attach the kubenet RT/Routes automatically
      and they should be added manually to the existing RT.
    * If no Route Table exists AKS will automatically attach the kubenet RT/Routes.

* Preview Features
  * A bug where users could not scale VMSS based clusters after disabling the
   cluster autoscaler has been fixed.
  * A missing CRD for calico-enabled clusters (#1042) has been fixed.


## Release 2019-06-10

* Bug Fixes
  * Kubernetes taints and tolerations are now supported in all AKS regions.
    * Taints & Tolerations are preserved for current cluster nodes and
      through upgrades, however they are _not_ preserved through scale (up,
      down) operations.

* Preview Features
  * A bug that prevented cluster agent pool deletions due to VMSS creation
    failures has been fixed.
  * A bug preventing the cluster autoscaler from working with nodepool enabled
    clusters (one or more nodepools) has been fixed.
  * A bug where the NSG would not be reset as needed during a nodepool create
    request has been fixed.

* Behavioral Changes
  * AKS removed all weak CBC suite ciphers for API server. More info: https://blog.qualys.com/technology/2019/04/22/zombie-poodle-and-goldendoodle-vulnerabilities

* Component Updates
  * AKS-Engine has been updated to v0.35.4

## Release 2019-05-28

* New Features
  * AKS is now available in both China East 2 / China North 2 Azure Regions.
  * AKS is now available in South Africa North
  * The L and M series Virtual Machines are now supported

* Component Updates
  * AKS-Engine has been updated to version 0.35.3
  * CoreDNS has been upgraded from 1.2.2 to version 1.2.6

* Preview Features
  * A bug where users could not deleted an agent pool containing VMSS nodes if
    the VMSS node creation fails has been fixed.

## Release 2019-05-20

* Behavioral Changes
  * The 192.0.2.0/24 IP block is now reserved for AKS use. Clusters created in
    a VNet that overlaps with this block will fail pre-flight validation.
* Bug Fixes
  * An issue where users running old AKS clusters attempting to upgrade would
    get a failed upgrade with an Internal Server Error has been fixed.
  * An issue where Kubernetes 1.14.0 would not show in the Azure Portal or AKS
    Preview CLI with the 'Preview' or 'isPreview' tag has been resolved.
  * An issue where customers would get excessive log entries due to missing
    Heapster rbac permissions has been fixed.
    * https://github.com/Azure/AKS/issues/520
  * An issue where AKS clusters could end up with missing DNS entries resulting
    in DNS resolution errors or crashes within CoreDNS has been resolved.

* Preview Features
  * A bug where the AKS node count could be out of sync with the VMSS node count
    has been resolved.
  * There is a known issue with the cluster autoscaler preview and multiple
    agent pools. The current autoscaler in preview is not compatible with
    multiple agent pools, and could not be disabled. We have fixed the issue
    that blocked disabling the autoscaler. A fix for multiple agent pools and
    the cluster autoscaler is in development.


## Release 2019-05-17 (Announcement)

* Window node support for AKS is now in Public Preview
  * Blog post: https://aka.ms/aks/windows
  * Support and documentation:
    * Documentation: https://aka.ms/aks/windowsdocs
    * Issues may be filed on this Github repository (https://github.com/Azure/AKS)
      or raised as a Sev C support request. Support requests and issues for
      preview features do not have an SLA / SLO and are best-effort only.
  * **Do not enable preview featured on production subscriptions or clusters.**
  * For all previews, please see the [previews][previews] document for opt-in
    instructions and documentation links.

* Bug fixes
  * An issue impacting Java workloads where pods running Java workloads would
    consume all available node resources instead of the defined pod resource
    limits defined by the user has been resolved.
    * https://bugs.openjdk.java.net/browse/JDK-8217766
    * AKS-Engine PR for fix: https://github.com/Azure/aks-engine/pull/1095

* Component Updates
  * AKS-Engine has been updates to v0.35.1

## Release 2019-05-13

* New Features
  * Shared Subnets are now supported with Azure CNI.
    * Users may bring / provide their own subnets to AKS clusters
    * Subnets are no longer restricted to a single subnet per AKS cluster, users
      may now have multiple AKS clusters on a subnet.
    * If the subnet provided to AKS has NSGs, those NSGs will be preserved and
      used.
      * **Warning**: NSGs must respect: https://aka.ms/aksegress or the
      cluster might not come up or work properly.
    * Note: Shared subnet support is not supported with VMSS (in preview)
* Bug Fixes
  * A bug that blocked Azure CNI users from setting maxPods above 110 (maximum
    of 250) and that blocked existing clusters from scaling up when the value
    was over 110 for CNI has been fixed.
  * A validation bug blocking long DNS names used by customers has been fixed.
    For restrictions on DNS/Cluster names, please see
    https://aka.ms/aks-naming-rules

## Release 2019-05-06

* New Features
  * Kubernetes Network Policies are GA
    * See https://docs.microsoft.com/en-us/azure/aks/use-network-policies
      for documentation.

* Bug Fixes
  * An issues customers reported with CoreDNS entering CrashLoopBackoff has
    been fixed. This was related to the upstream move to `klog`
    * https://github.com/coredns/coredns/pull/2529
  * An issue where AKS managed pods (within kube-system) did not have the correct
    tolerations preventing them from being scheduled when customers use
    taints/tolerations has been fixed.
  * An issue with kube-dns crashing on specific config map override scenarios
    as seen in https://github.com/Azure/acs-engine/issues/3534 has been
    resolved by updating to the latest upstream kube-dns release.
  * An issue where customers could experience longer than normal create times
    for clusters tied to a blocking wait on heapster pods has been resolved.
* Preview Features
  * New features in public preview:
    * Secure access to the API server using authorized IP address ranges
    * Locked down egress traffic
      * This feature allows users to limit / whitelist the hosts used by AKS
        clusters.
    * Multiple Node Pools
    * For all previews, please see the [previews][previews] document for opt-in
      instructions and documentation links.

## Release 2019-04-22

* Kubernetes 1.14 is now in Preview
  * Do not use this for production clusters. This version is for early adopters
    and advanced users to test and validate.
  * Accessing the Kubernetes 1.14 release requires the `aks-preview` CLI
    extension to be installed.

* New Features
  * Users are no longer forced to create / pre-provision subnets when using
    Advanced networking. Instead, if you choose advanced networking and do not
    supply a subnet, AKS will create one on your behalf.

* Bug fixes
  * An issue where AKS / the Azure CLI would ignore the `--network-plugin=azure`
    option silently and create clusters with Kubenet has been resolved.
    * Specifically, there was a bug in the cluster creation workflow where users
      would specific `--network-plugin=azure` with Azure CNI / Advanced Networking
      but miss passing in the additional options (eg '--pod-cidr, --service-cidr,
      etc). If this occured, the service would fall-back and create the cluster
      with Kubenet instead.

* Preview Features
  * Kubernetes 1.14 is now in Preview
  * An issue with Network Policy and Calico where cluster creation could
    fail/time out and pods would enter a crashloop has been fixed.
    * https://github.com/Azure/AKS/issues/905
    * Note, in order to get the fix properly applied, you should create a new
      cluster based on this release, or upgrade your existing cluster and then
      run the following clean up command after the upgrade is complete:

```
kubectl delete -f https://github.com/Azure/aks-engine/raw/master/docs/topics/calico-3.3.1-cleanup-after-upgrade.yaml
```

* Component Updates
  * Azure Monitoring for Containers has been updated to the 2019-04-23 release
    * For more information, please see: https://github.com/Microsoft/docker-provider/tree/ci_feature_prod#04232019--

## Release 2019-04-15

* Kubernetes 1.13 is GA
* **The Kubernetes 1.9.x releases are now deprecated.** All clusters
  on version 1.9 must be upgraded to a later release (1.10, 1.11, 1.12, 1.13)
  within **30 days**. Clusters still on 1.9.x after 30 days (2019-05-25)
  will no longer be supported.
  * During the deprecation period, 1.9.x will continue to appear in the available
    versions list. Once deprecation is completed 1.9 will be removed.

* (Region) North Central US is now available
* (Region) Japan West is now available

* New Features
  * Customers may now provide custom Resource Group names.
    * This means that users are no longer locked into the MC_* resource name
      group. On cluster creation you may pass in a custom RG and AKS will
      inherit that RG, permissions and attach AKS resources to the customer
      provided resource group.
    * Currently, you must pass in a new RG (resource group) must be new, and
      can not be a pre-existing RG. We are working on support for pre-existing
      RGs.
    * This change requires newly provisioned clusters, existing clusters can
      not be migrated to support this new capability. Cluster migration across
      subscriptions and RGs is not currently supported.
  *  AKS now properly associates existing route tables created by AKS when
      passing in custom VNET for Kubenet/Basic Networking. *This does not
      support User Defined / Custom routes (UDRs)*.

* Bug fixes
  * An issue where two delete operations could be issued against a cluster
    simultaneously resulting in an unknown and unrecoverable state has been
    resolved.
  * An issue where users could create a new AKS cluster and set the `maxPods`
    value too low has been resolved.
    * Users have reported cluster crashes, unavailability and other issues
      when changing this setting. As AKS is a managed service, we provide
      sidecars and pods we deploy and manage as part of the cluster. However
      users could define a maxPods value lower than the value required for the
      managed pods to run (eg 30), AKS now calculates the minimum number of
      pods via: `maxPods or maxPods * vm_count > managed add-on pods`

* Behavioral Changes
  * AKS cluster creation now properly pre-checks the assigned service CIDR
    range to block against possible conflicts with the dns-service CIDR.
    * As an example, a user could use 10.2.0.1/24 instead of 10.2.0.0/24 which
      would lead to IP conflicts. This is now validated/checked and if there is
      a conflict, a clear error is returned.
  * AKS now correctly blocks/validates users who accidentally attempt an
    upgrade to a previous release (eg downgrade).
  * AKS now validate all CRUD operations to confirm the requested action will
    not fail due to IP Address/subnet exhaustion. If a call is made that would
    exceed available addresses, the service correctly returns an error.
  * The amount of memory allocated to the Kubernetes Dashboard has been
    increased to 500Mi for customers with large numbers of nodes/jobs/objects.
  * Small VM SKUs (such as Standard F1, and A2) that do not have enough RAM to
    support the Kubernetes control plane components have been removed from the
    list of available VMs users can use when creating AKS clusters.

* Preview Features
  * A bug where Calico pods would not start after a 1.11 to 1.12 upgrade has
    been resolved.
  * When using network policies and Calico, AKS now properly uses Azure CNI for
    all routing vs defaulting to using Calico the routing plugin.
  * Calico has been updated to v3.5.0

* Component Updates
  * AKS-Engine has been updates to v0.33.4

## Release 2019-04-01

* Bug Fixes
  * Resolved an issue preventing some users from leveraging the Live Container
    Logs feature (due to a 401 unauthorized).
  * Resolved an issue where users could get "Failed to get list of supported
    orchestrators" during upgrade calls.
  * Resolved an issue where users using custom subnets/routes/networking with
    AKS where IP ranges match the cluster/service or node IPs could result in
    an inability to `exec`, get cluster logs (`kubectl get logs`) or otherwise
    pass required health checks.
  * An issue where a user running `az aks get-credentials` while a cluster is
    in creation resulting in an unclear error ('Could not find role name') has
    been resolved.


## Release 2019-04-08 (Hotfix)

This release fixes one AKS product regression and an issue identified with the
Azure Jenkins plugin.

* A regression when using ARM templates to issue AKS cluster update(s) (such as
  configuration changes) that also impacted the Azure Portal has been fixed.
  * Users do not need to perform any actions / upgrades for this fix.
* An issue when using the Azure Container Jenkins plugin with AKS has been
  mitigated.
  * This issue caused errors and failures when using the Jenkins plugin - the
    bug triggered by a new AKS API version but was related to a latent issue in
    the plugin's API detection behavior.
  * An updated Jenkins plugin has been published:
    https://github.com/jenkinsci/azure-acs-plugin/issues/16
  * https://github.com/jenkinsci/azure-acs-plugin/releases/tag/azure-acs-0.2.4

## Release 2019-04-04 - Hotfix (CVE mitigation)

* Bug fixes
  * New kubernetes versions released with multiple CVE mitigations
    * Kubernetes 1.12.7
      * https://github.com/kubernetes/kubernetes/blob/master/CHANGELOG-1.12.md#changelog-since-v1126
    * Kubernetes 1.11.9
      * https://github.com/kubernetes/kubernetes/blob/master/CHANGELOG-1.11.md#changelog-since-v1118
    * Customers should upgrade to the latest 1.11 and 1.12 releases.
      * Kubernetes versions prior to 1.11 must upgrade to 1.11/1.12 for the fix.

* Component updates
  * Updated included AKS-Engine version to 0.33.2
    * See: https://github.com/Azure/aks-engine/releases/tag/v0.33.4 for details

## Release 2019-03-29 (Hotfix)

* The following regions are now GA: South Central US, Korea Central and Korea
  South

* Bug fixes
  * Fixed an issue which prevented Kubernetes addons from being disabled.

* Behavioral Changes
  * AKS will now block subsequent PUT requests (with a status code 409 -
    Conflict) while an ongoing operation is being performed.

## Release 2019-03-21

* The Central India region is now GA

* Bug fixes
  * AKS will now begin preserving node labels & annotations users apply to
    clusters during upgrades.
    * Note: labels & annotations will not be applied to new nodes added during
      a scale up operation.
  * AKS now properly validates the Service Principal / Azure Active Directory
    (AAD) credentials
    * This prevents invalid, expired or otherwise broken credentials being
      inserted and causing cluster issues.
  * Clusters that enter a failed state due to upgrade issues will now allow
    users to re-attempt to upgrade or will throw an error message with
    instructions to the user.
  * Fixed an issue with cloud-init and the walinuxagent resulting in
    `failed state` VMs/worker nodes
  * The `tenant-id` is now correctly defaulted if not passed in for AAD enabled
    clusters.

* Behavioral Changes
  * AKS is now pre-validating MC_* resource group locks before any CRUD
    operation, avoiding the cluster enter Failed state.
  * Scale up/down calls now return a correct error ('Bad Request') when users
    delete underlying virtual machines during the scale operation.
  * Performance Improvement: caching is now set to read only for data disks
  * The Nvidia driver has been updated to 410.79 for N series cluster
    configurations
  * The default worker node disk size has been increased to 100GB
    * This resolves customer reported issues with large numbers (and large
      sizes) of Docker images triggering out of disk issues and possible
      workload eviction.
  * The Kubernetes controller manager `terminated-pod-gc-threshold` has been
    lowered to 6000 (previously 12500)
    * This will help system performance for customers running large number of
      Jobs (finished pods)
  * The Azure Monitor for Container agent has been updated to the 2019-03
    release
  * The "View Kubernetes Dashboard" has been removed from the Azure Portal
    * Note that this button did not expose/add functionality, it only linked to
      the existing instructions for using the Kubernetes dashboard found here:
      https://docs.microsoft.com/en-us/azure/aks/kubernetes-dashboard

## Release 2019-03-07

* The Azure Monitor for containers Agent has been updated to 3.0.0-4 for newly
  built or upgraded clusters
* The Azure CLI now properly defaults to N-1 for Kubernetes versions, for
  example N is the current latest (1.12) release - the CLI will correctly pick
  1.11.x. When 1.13 is released, the default will move to 1.12.

* Bug Fixes:
  * If a user exceeds quota during a scale operation, the Azure CLI will now
    correctly display a "Quota exceeded" vs "deployment not found"
  * All AKS CRUD (put) operations now validate and confirm user subscriptions
    have the needed quota to perform the operation. If a user does not, an
    error is correctly shown and the operation will not take effect.
  * All AKS issued Kubernetes SSL certificates have had weak cipher support
    removed, all certificates should now pass security audits for BEAST and
    other vulnerabilities.
    * If you are using older clients that do not support TLS 1.2 you will need
      to upgrade those clients and associated SSL libraries to securely connect.
      * Note that only Kubernetes 1.10 and above support the new certificates,
        additionally existing certificates will not be updated as this would
        revoke all user access. To get the updated certificates you will need
        to create a new AKS cluster.
  * Clusters that are in the process of upgrading or in failed upgrade state
    will attempt to re-execute the upgrade or throw an obvious error message.
* The preview feature for Calico/Network Security Policies has been updated to
  repair a bug where ip-forwarding was not enabled by default.
* The `cachingmode: ReadOnly` flag was not always being correctly applied to
  the managed premium storage class, this has been resolved.


## Release 2019-03-01

* New kubernetes versions released for CVE-2019-1002100 mitigation
  * Kubernetes 1.12.6
  * Kubernetes 1.11.8
  * Customers should upgrade to the latest 1.11 and 1.12 releases.
  * Kubernetes versions prior to 1.11 must upgrade to 1.11/1.12 for the fix.
    * Announcement here: https://groups.google.com/forum/#!msg/kubernetes-announce/vmUUNkYfG9g/B9rHFrqLCAAJ
* A security bug with the Kubernetes dashboard and overly permissive service
  account access has been fixed
* The France Central region is now GA for all customers
* Bug fixes and performance improvements

## Release 2019-02-19

* Fixed a bug in cluster location/region validation has been resolved.
  * Previously, if you passed in a location/region with a trailing unicode
    non-breaking space (U+00A0) would cause failures on CRUD operations or
    cause other non-parseable characters to be displayed.
* Fixed a bug where if the dnsService IP conflicts with the apiServer IP
  address(es) creates or updates would fail after the fact.
  * Addresses are now checked to ensure no overlap or conflict at CRUD operation
    time.
* The Australia Southeast region is now GA
* Fixed a bug when using the new Service Principal rotation/update command on
  cluster nodes using the Azure CLI would fail
  * Specifically, there was a missing dependency (e.g. `jq is missing`) on the
    nodes, all new nodes should now contain the `jq` utility.

## Release 2019-02-12 - Hotfix Release (UPDATE)

At this time, all regions now have the CVE hotfix release. The simplest way to
consume it is to perform a Kubernetes version upgrade, which will cordon, drain,
and replace all nodes with a new base image that includes the patched version of
Moby. In conjunction with this release, we have enabled new patch versions for
Kubernetes 1.11 and 1.12. However, as there are no new patch versions available
for Kubernetes versions 1.9 and 1.10, customers are recommended to move forward
to a later minor release.

If that is not possible and you must remain on 1.9.x/1.10.x, you can perform
the following steps to get the patched runtime:

1. Scale *up* your existing 1.9/1.10 cluster - add an equal number of nodes to
  your existing worker count.
1. After scale-up completes, pick a single node and using the kubectl command,
  cordon the old node, drain all traffic from it, and then delete it.
1. Repeat step 2 for each worker in your cluster, until only the new nodes
  remain.

Once this is complete, all nodes should reflect the new Moby runtime version.

We apologize for the confusion, and we recognize that this process is not ideal
and we have future plans to enable an upgrade strategy that decouples system
components like the container runtime from the Kubernetes version.

Note: All newly created 1.9, 1.10, 1.11 and 1.12 clusters will have the new
Moby runtime and will not need to be upgraded to get the patch.

### Release 2019-02-12 - Hotfix Release

**Hotfix releases follow an accelerated rollout schedule - this release should
be in all regions by 12am PST 2019-02-13**

* Kubernetes 1.12.5, 1.11.7
* This release mitigates CVE-2019-5736 for Azure Kubernetes Service (see below).
  * Please note that GPU-based nodes do not support the new container runtime
    yet. We will provide another service update once a fix is available for
    those nodes.

**CVE-2019-5736 notes and mitigation**
Microsoft has built a new version of the Moby container runtime that includes
the OCI update to address this vulnerability. In order to consume the updated
container runtime release, you will need to **upgrade your Kubernetes cluster**.

Any upgrade will suffice as it will ensure that all existing nodes are removed
and replaced with new nodes that include the patched runtime. You can see the
upgrade paths/versions available to you by running the following command with
the Azure CLI:

```
az aks get-upgrades -n myClusterName -g myResourceGroup
```

To upgrade to a given version, run the following command:

```
az aks upgrade -n myClusterName -g myResourceGroup -k <new Kubernetes version>
```

You can also upgrade from the Azure portal.

When the upgrade is complete, you can verify that you are patched by running
the following command:

```
kubectl get nodes -o wide
```

If all of the nodes list **docker://3.0.4** in the Container Runtime column,
you have successfully upgraded to the new release.

## Release 2019-02-07 - Hotfix Release

This hotfix release fixes the root-cause of several bugs / regressions
introduced in the 2019-01-31 release. This release does not add new features,
functionality or other improvements.

**Hotfix releases follow an accelerated rollout schedule - this release should
be in all regions within 24-48 hours barring unforeseen issues**

* Fix for the API regression introduced by removing the Get Access Profile API
  call.
  * Note: This call is planned to be deprecated, however we will issue advance
    communications and provide the required logging/warnings on the API call to
    reflect it's deprecating status.
  * Resolves [Issue 809](https://github.com/Azure/AKS/issues/809)
* Fix for CoreDNS / kube-dns autoscaler conflict(s) leading to both running in
  the same cluster post-upgrade
  * Resolves [Issue 812](https://github.com/Azure/AKS/issues/812)
* Fix to enable the CoreDNS customization / compatibility with kube-dns config
  maps
  * Resolves [Issue 811](https://github.com/Azure/AKS/issues/811)
  * Note: customization of Kube-dns via the config map method was technically
    unsupported, however the AKS team understands the need and has created a
    compatible work around (formatting of the customizations has changed
    however). Please see the example/notes below for usage.

### Using the new CoreDNS configuration for DNS configuration.

With kube-dns, there was an undocumented feature where it supported two config
maps allowing users to perform DNS overrides/stub domains, and other
customizations. With the conversion to CoreDNS, this functionality was lost -
CoreDNS only supports a single config map. With the hotfix above, AKS now has a
work around to meet the same level of customization.

You can see the pre-CoreDNS conversion customization instructions [here][7]

Here is the equivalent ConfigMap for CoreDNS:

```
apiVersion: v1
kind: ConfigMap
metadata:
  name: coredns-custom
  namespace: kube-system
data:
  azurestack.server: |
    azurestack.local:53 {
        errors
        cache 30
        proxy . 172.16.0.4
    }
```

After create the config map, you will need to delete the CoreDNS deployment to
force-load the new config.

```
kubectl -n kube-system delete po -l k8s-app=kube-dns
```


## Release 2019-01-31

* [Kubernetes 1.12.4 GA Release][1]
  * With the release of 1.12.4 *Kubernetes 1.8 support has been removed*, you
    will need to upgrade to at least 1.9.x
* CoreDNS support GA release
  * Conversion from kube-dns to CoreDNS completed, CoreDNS is the default for
    all new 1.12.4+ AKS clusters.
  * If you are using configmaps or other tools for kube-dns modifications, you
    will need to be adjust them to be CoreDNS compatible.
    * The CoreDNS add-on is set to `reconcile` which means modifications to the
      deployments will be discarded.
    * We have identified two issues with this release that will be resolved in
      a hot fix beginning rollout this week:
      * https://github.com/Azure/AKS/issues/811 (kube-dns config map not
        compatible with CoreDNS)
      * https://github.com/Azure/AKS/issues/812 (kube-dns/coreDNS autoscaler
        conflicts)
* Kube-dns (pre 1.12) / CoreDNS (1.12+) autoscaler(s) are enabled by default,
  this should resolve the DNS timeout and other issues related to DNS queries
  overloading kube-dns.
  * In order to get the dns-autoscaler, you must perform an **AKS cluster
    upgrade** to a later supported release (clusters prior to 1.12 will
    continue to get kube-dns, with kube-dns autoscale)
* Users may now self update/rotate Security Principal credentials using the
  [Azure CLI][6]
* Additional non-user facing stability and reliability service enhancements
* **New Features in Preview**
  * **Note**: Features in preview are considered beta/non-production ready and
    unsupported. Please do not enable these features on production AKS clusters.
  * [Cluster Autoscaler / Virtual machine Scale Sets][2]
  * [Kubernetes Audit Log][3]
  * Network Policies/Network Security Policies
    * This means you can now use `calico` as a valid entry in addition to
      `azure` when creating clusters using Advanced Networking
    * There is a known issue when using Network Policies/calico that prevents
      `exec` into the cluster containers which will be fixed in the next release
  * For all product / feature previews including related projects, see
    [this document][5].

[1]: https://docs.microsoft.com/azure/aks/supported-kubernetes-versions
[2]: https://docs.microsoft.com/azure/aks/cluster-autoscaler#create-an-aks-cluster-and-enable-the-cluster-autoscaler
[3]: https://github.com/Azure/AKS/blob/master/previews.md#kubernetes-audit-log
[5]: https://github.com/Azure/AKS/blob/master/previews.md
[6]: https://docs.microsoft.com/azure/aks/update-credentials
[7]: https://www.danielstechblog.io/using-custom-dns-server-for-domain-specific-name-resolution-with-azure-kubernetes-service/
[8]: https://docs.microsoft.com/en-us/azure/aks/update-credentials

[previews]: https://github.com/Azure/AKS/blob/master/previews.md
