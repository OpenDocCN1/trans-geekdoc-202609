# 588 CHAPTER 11 SHARED STORAGE AND CLUSTERING INTRODUCTION

+   1. Build out a minimum of two virtual machines.

+   2. Create two virtual network switches based on your requirements.

If you need access to additional resources, you will need to create additional networks that are externally external virtual switches.

+   3. Connect the associated storage solution to your VMs, such as your virtual Fiber, iSCSI, or SMB storage.

+   4. Install Windows Server 2012 R2 on your virtual machine.

+   5. Install the Failover Clustering feature on each of the VMs in cluster.

+   6. Connect your network and storage to the VMs.

+   7. Run the Validate Cluster Configuration Wizard and make sure you get a positive result.

Configuring your guest-based clusters is essentially the same as configuring your host cluster; you want to connect and configure all the settings with the exception of the Hyper-V role, because all Hyper-V guests. If you are feeling more knowledgeable now that you have gone through this introduction on shared storage and clustering, we highly recommend looking at the Clustering and High-Availability blog on TechNet at http://blogs/msdn.com/b/clustering/.

# The Bottom Line

Use the available storage options for clustering. With the release of Windows Server 2012 R2, many more storage options are available for your clustering and high-availability solutions.

**Master It** You want to build out a JBOD solution and need the most effective type of disk capacity. The failover doesn't matter as much as space and speed. What technology should you consider?

**Use quor to help in clustering.** A quorum is the minimum number of members required to be present at an assembly or meeting before it can validly proceed to transact business. This definition holds true for the use of a quorum in clustering.

**Master It** You have chosen to deploy an odd-numbered cluster with five nodes, and once the cluster is up and running, you host an application. After the installation the application has a major memory leak and starts seizing the servers and shutting them down. How many nodes will you lose before the cluster is completely offline?

**Build out host and guest clusters.** Clustering is a mix of software and hardware and can be hosted on physical servers or virtual machines. Windows Server 2012 R2 has the components and tools built in it to help you deploy your clusters, including a handy prerequisites wizard to validate that you have all the components and configurations in to successfully set up a cluster.

**Master It** When planning your host- and guest-based clusters, excluding the Hyper-V role, what is the difference between the two in setting up a cluster?