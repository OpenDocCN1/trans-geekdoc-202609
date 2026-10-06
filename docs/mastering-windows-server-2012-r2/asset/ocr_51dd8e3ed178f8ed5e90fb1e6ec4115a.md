# Chapter 11: Shared Storage and Clustering Introduction

Use the available storage options for clustering. With the release of the Windows Server 2012 R2, many more storage options are available for your clustering and high-availability solutions.

**Master** You want to build a JBOD solution and need the most effective type of disk capacity. The failover doesn't matter as much as space and speed. What technology you consider?

**Solution** You must build a Storage Places solution utilizing simple volumes; your volume type is designed for throughput and size. Maximize the disks and access to the disks to make the storage fast and effective.

**Use quums in clustering.** A quorum is the "minimum number of members required to be present at an assembly or meeting before it can validly proceed to transact business." This definition holds true for the use of a quorum in clustering.

**Master** It have chosen to deploy an odd-numbered cluster with five nodes, and you will use one node as a file share for quorum. Once the cluster is up and running, you host an application. But after the install the application has a major memory leak starts seizing up the servers and shutting them down. How many nodes will you before the cluster is completely offline?

**Solution** Since you have an even number of quorum nodes and a witness node, the cluster will remain online until the very last node is about to go down. With proper monitoring and alerting, you would never let anything this far, would you? Hopefully not, but the benefit of a witness node is that you can keep your application and while you get other servers either online or rolled back to a different version of the application.

**Build host and guest clusters.** Clustering is a mix of software and hardware and can be hosted on physical servers or virtual machines. Windows Server 2012 R2 has the components and tools built in it to deploy your clusters, including a handy सिक्योरिटी to validate that you have all the components and configurations in places to successfully set up a cluster.

**Master** When planning your host- and guest-based clusters, excluding the Hyper-V role, what is the difference between the two in setting up a cluster?

**Solution** There is no difference; once you start to plan your hardware and networks, the requirements on both the VM and host sides of the cluster process are exactly the same. The process is simple and easy to step through.

# Chapter 12: Windows 2012 R2 Storage: Storage Spaces, SANish Abilities, and Better Tools

**Create a storage pool on a virtual disk.** Storage is an ever-growing business requirement. If you were constantly buying SAN solutions to meet this need, it would prove very costly. Also,