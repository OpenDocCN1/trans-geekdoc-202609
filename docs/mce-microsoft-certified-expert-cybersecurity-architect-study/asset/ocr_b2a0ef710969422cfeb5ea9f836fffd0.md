In addition to its many advantages, Kubernetes also brings several security challenges that must be addressed. Therefore, understanding the various security risks in containerized environments is crucial.

Azure Kubernetes Service clusters and Azure Arc-enabled Kubernetes clusters (Preview) are protected by default when you enable Microsoft Defender for Containers. The security recommendations appear in the Defender for Cloud dashboard when you enable Microsoft Defender for Containers, as depicted in Figure 7.7.

# FIGURE 7.7 Microsoft Defender for Containers

![](bbox=[0.235, 0.285, 0.75, 0.555])

Defender for Cloud provides runtime protections and collects node signals for Azure Kubernetes Service clusters without the need for agent software. Defender profiles are deployed on each node, providing runtime protections and collecting node signals. Azure Policy's Kubernetes add-on includes clusters and workload configurations for admission control policies. Figure 7.8 depicts Azure kubernetes service cluster.

+   - The Defender profile incorporates a DaemonSet, a set of containers focused on collecting inventory and security events.
+   - The open Policy Agent (OPA)'s Gatekeeper is the admission controller webhook, which implements at-scale enforcement and safeguarding at scale on clusters.