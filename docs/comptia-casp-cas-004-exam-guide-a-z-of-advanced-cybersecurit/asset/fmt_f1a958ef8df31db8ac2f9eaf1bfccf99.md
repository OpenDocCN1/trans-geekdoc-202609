
## Privileged Access Management Benefits

*   Eliminates the need to share privileged administrative credentials (like the root user password on Linux) that are required for some `software-defined storage` (`SDS`) products.
*   Provides time-bound privilege storage admin sessions and remote termination of storage admin sessions.
*   Supports multi-factor authentication for the users accessing storage admin sessions.
*   Can capture keystrokes, process activity, and programs that are running (useful in some `SDS` offerings).
*   Manages and audits privileged storage accounts and authentication secrets, such as passwords and `SSH` keys.

## Secure Remote Support

Secure remote support is managed by the customer, and it has the following benefits:

*   Provides time-bound audited access to the service, maintenance, or support teams.
*   Supports a custom approval workflow (multi-level approval) for each access session.
*   Records and audits all activity that is performed in support or service sessions.

## Use Case Examples

This chapter demonstrates the integration of the IBM Spectrum Scale with Verify Privilege Vault. The concept can be extended and applied to other IBM Storage Systems. IBM® Security™ Verify Privilege Vault On-Premises (Verify Privilege Vault), formerly known as IBM Security™ Secret Server, is the next-generation privileged account management that integrates with IBM Storage to ensure that access to IBM Storage administration sessions is secure and monitored in real-time with required recording for audit and compliance. Privilege access to storage administration sessions is centrally managed, and each session can be time-bound with remote monitoring.

## IBM Spectrum Scale

IBM Spectrum Scale is a scalable, high-performance file system that is suitable for various use cases (Figure 8.2). It provides world-class storage management with scalability, flash-accelerated performance, and automatic storage tier capabilities. IBM Spectrum Scale reduces storage costs while improving security and management efficiency in the cloud, big data, and analytics environments. In a nutshell, IBM Spectrum Scale provides the following benefits:

*   Virtually limitless scaling to nine quintillion files and yottabytes of data.
*   High performance and simultaneous access to a common set of shared data.
*   Integrated `information lifecycle management` (`ILM`) functions to automatically move data between storage tiers, including flash, disk, tape, and object storage (public and private cloud). `ILM` can reduce operational costs because fewer administrators can manage larger storage infrastructures.

With `SDS`, you can build your infrastructure solution with the following characteristics:

*   Easy to scale with relatively inexpensive commodity hardware while maintaining world-class storage management capabilities.
*   Deployable on `Amazon Web Services` (`AWS`) and IBM Cloud. A cross-platform solution that is available on IBM AIX®, Linux, and Windows server nodes, or a mix of all three. IBM Spectrum Scale is also available for IBM Z.
*   Available as the prepackaged storage solution that is named IBM ESS with de-clustered RAID included.
*   Global data access across geographic distances and unreliable WAN connections.
*   Multi-site support to connect a local IBM Spectrum Scale cluster to remote clusters, which provides greater administrative flexibility and control.
*   Proven reliability across multiple sites, and support for concurrent hardware and software upgrades.
*   State-of-the-art protocol access methods for managing files and objects under the same global namespace, which make more efficient use of storage space and avoid data islands. The supported protocols include `NFS`, `SMB`, `POSIX`, `OpenStack Swift`, and `S3`.
*   Seamless integration for Hadoop applications through the `Hadoop Distributed File System` (`HDFS`) transparency feature.
*   Proven security features to ensure data privacy, authenticity, and auditability.
*   File-level encryption for data at rest and secure erase.
*   Policy-driven compression to reduce the size of data at rest and increase storage efficiency.
*   Can be used as persistent storage for containers.
*   Includes a GUI to simplify storage administration tasks and monitor many aspects of the system.

Figure 8.2 illustrates the IBM Spectrum Scale:

![](images/Image25860.jpg)

**Figure 8.2:** IBM Spectrum Scale

IBM Spectrum Scale is often used in high-performance and computationally demanding environments across different areas, such as banking, financial, healthcare, oil and gas, and automotive industries. Its most common use cases are in `artificial intelligence` (`AI`) and deep learning, big data analytics, content repository, private cloud, and compute clusters. It is also commonly used for data optimization and resiliency for archive, high-speed backup, and disaster recovery, and `ILM`.

IBM Spectrum Scale supports various deployment models, and one of them is IBM ESS, which is a modern hardware-based implementation. IBM ESS is available as IBM ESS 3000 (high-density storage) and IBM ESS 5000 (high-capacity and high-performance storage).

## Verify Privilege Vault

IBM Security Verify Privilege provides on-premises and cloud offerings. Verify Privilege Vault (Figure 8.3) is a cloud-based solution, for which organizations do not need to worry about any hardware or software requirements. However, IBM Security Verify Privilege On-Premises requires a dedicated server for installation and an `SQL` database to store details. Based on the requirements, features, and architecture, your organization can decide which offering to select. In this chapter, we refer to Verify Privilege Vault On-Premises, although the information in this paper can be extended to the cloud offering with relevant and required changes. Privileged access is the route to an organization’s most valuable information. As a result, implementing PAM has become a top priority. Verify Privilege Vault is a full-featured PAM solution that is available both on-premises and in the cloud, and it is ready to empower your security and IT ops team to secure and manage all types of privileged accounts quickly and easily. With Verify Privilege Vault, you can do the following:

*   Establish a secure vault.
*   Discover privileges.
*   Protect passwords.
*   Meet compliance requirements.
*   Control sessions.

Verify Privilege Vault is fast to deploy, easy to use, and scalable for the enterprise. It integrates with the larger IBM Security portfolio for key use cases, such as identity governance and multi-factor authentication. Figure 8.3 illustrates the IBM Privilege Vault:

![](images/Image25867.jpg)

**Figure 8.3:** IBM Privilege Vault

The following list describes the architecture that is shown in the preceding figure:

*   The left side of the architecture represents different mediums through which Verify Privilege Vault can be accessed. The right side represents the high-level internal working.
*   Verify Privilege Vault requires an `SQL` server for its configuration and data management. You can configure the setup for high availability as needed.
*   Verify Privilege Vault provides session launchers that are tailored to start specific applications based on triggers in a secret template. For example, for the Windows platform, the remote desktop connection application is invoked when trying to access a Windows account secret. Similarly, for the UNIX or Linux platforms, the `PuTTY` application is triggered when using a UNIX or Linux account secret.
*   A distributed engine is used for remote password changing and the discovery of new accounts.

## Security Implications/Privacy Concerns
