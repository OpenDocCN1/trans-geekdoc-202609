
# Clustering Inside Virtual Machines

When you develop your clustering strategy for files, shares, or Hyper-V, you are giving the infrastructure a highly available solution, one that can grow and you can move your critical systems into. To the support of Windows Server 2012 R2 and guest-based clustering, you are adding the next level of HA and increasing the speed of recovery from a system failure. It's not always the hardware that requires high availability; in many cases the software is causing a problem, resulting from memory leaks, software updates, or configuration changes. When you run cluster applications as virtual workloads, the failover time and integration with many of the new controls become more enticing because consumers experience no interruption.

To understand the workloads that are capable of this type, you need to remember the golden rule: If a workload is made for clustering or recommended to cluster for HA or disaster recovery (DR) purposes, it can work in a guest cluster. Microsoft has made the Windows Server 2012 and Windows Server 2012 R2 workloads aware of this virtual guest cluster, in such areas as these:

- Continuously available file shares
- DHCP server
- SQL Server 2012—always on
- Exchange Server
- SharePoint
- File shares (standard file sharing)
- Print services

To use this technology you utilize a model enabled in Windows Server 2012 R2: a shared VHDX. Windows Server 2012 introduced the VHDX format, which addressed the storage, data protection, and performance on large disks. When you create virtual guest clusters, you are attaching a VHDX to a SCSI controller for your VM, enabling sharing to create a connection, and presenting the VHDX as an SAS drive. So you are getting the option of building an infrastructure that doesn't necessarily require iSCSI, Fibre Channel SAN, or block-level storage, but you are getting to use SMB 3.0.

Now that you understand some of the basic blocks, you can take your knowledge of the shared storage and clustering capabilities of Windows Server 2012 R2 into the next section and dive into setup.

# Setting Up a Cluster

In this section we will walk through the basic steps of setting up a host-based cluster. For the purpose of this example we will be creating a two-node cluster and configuring it for file shares. Clustering file shares is a great starting place to introduce you to managing a cluster. The requirements are very simple. We'll take a basic need in any enterprise and provide immediate high availability.

To successfully set this up, you need to work through each of the following sections.

# Cluster Configuration

The lab we are going to use for this example is very simple. We have two running Windows Server 2012 R2. The servers are named as follows:

## Server 1 = Cluster1

- Local storage = C:\ drive 30 GB
- NIC #1 (primary) IP address: 192.168.1.17
- NIC #2 (secondary) IP address: 192.168.1.18

## Server 2 = Cluster2

- Local storage = C:\ drive 30 GB
- NIC #1 (primary) IP address: 192.168.1.19
- NIC #2 (secondary) IP address: 192.168.1.20

The cluster for this example is named DemoCluster, and its IP address is 192.168.1.21.
To examine the basic options of clustering we are going to focus on clustering file services, but we'll spend more time going over how to set the cluster service on two nodes, step by step.

When preparing to build a similar example cluster, the steps should be fairly straightforward, and hopefully you will see the value in getting your organization set up and using cluster services. In regard to the quorum we discussed previously, I have created a share on a separate server; you can utilize a file share as the quorum, as we discussed. The share will be located on the Active Directory domain controller for this example, BF1. The share BF1#Cluster will be utilized for the witness.

The two servers have two physical NICs. Ideally you would have a minimum of three NICs for needs. If you have five or more NICs available, then you can learn to separate the three types of network needs: one NIC for the primary cluster services. Remember, for every NIC you use, you should always use a static IP address. DHCP is supported with clustering, but it's not ideal or advised in many scenarios. The following list is a typical configuration for NICs:

NIC rule 1: cluster management and storage—Do not set traffic (for VMs or apps)

- Needs the default gateway
- Needs DNS

Once you have set up the NICs and are ready to move on, the next step is taking the host names (rename the servers to something descriptive of your clusters) and joining them to Active Directory. As previously shown, the servers we are using in this example are Cluster1 and Cluster2.

# SETTING UP CLUSTER

After you have joined these devices to an Active Directory domain, you need to make sure each cluster node has Remote Desktop and Remote Management installed, and you are going to be creating a file server cluster, setting up the File Server role is required.

# Storage

Before we set up the cluster itself, let's do a quick review of the storage options of clusters. You have several choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:

- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

Wait, the quorum we discussed previously, I have created a share on a separate server; you can utilize a file share as the quorum, as we discussed. The share will be located on the Active Directory domain controller for this example, BF1. The share BF1#Cluster will be utilized for the witness.

The two servers have two physical NICs. Ideally you would have a minimum of three NICs for needs. If you have five or more NICs available, then you can learn to separate the three types of network needs: one NIC for the primary cluster services. Remember, for every NIC you use, you should always use a static IP address. DHCP is supported with clustering, but it's not ideal or advised in many scenarios. The following list is a typical configuration for NICs:

NIC rule 1: cluster management and storage—Do not set traffic (for VMs or apps)

- Needs the default gateway
- Needs DNS

Once you have set up the NICs and are ready to move on, the next step is taking the host names (rename the servers to something descriptive of your clusters) and joining them to Active Directory. As previously shown, the servers we are using in this example are Cluster1 and Cluster2.

# SETTING UP CLUSTER

After you have joined these devices to an Active Directory domain, you need to make sure each cluster node has Remote Desktop and Remote Management installed, and you are going to be creating a file server cluster, setting up the File Server role is required.

# Storage

Before we set up the cluster itself, let's do a quick review of the storage options of clusters. You have several choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:

- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage are:
- iSCSI SAN
- SAS enclosures
- SMB 3.0

You have choices, and since it's a requirement, you need to figure out what type of storage solution you want to use. Typical options for shared storage
