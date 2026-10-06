# EXPLORING THE DISTRIBUTED FILE SYSTEM

DFS Replication is an efficient, multiple-master replication engine that can keep folders synchronized between servers across limited-bandwidth network connections. DFS Replication can occur across multiple sites and servers that live within the same forest. DFS Replication uses differential compression (RDC) to locate and replicate only the changed data blocks of a file. This works hand in hand with the new Data Deduplication features provided by Windows Server 2012 R2. Integrated with the new block-level storage technology, DFS Replication supports replicating folders and files that are hosted on volumes that have Dedupe enabled. Using Dedupe to reduce storage requirements on an NTFS file system has no effect on DFS Replication.

Before you use these features, you must first add these roles to your server. The DFS Namespaces and DFS Replication roles you will need to add the Roles and Features Wizard in Server Manager to add them, as seen in Figure 14.26.

There are a few additional requirements to take note of before running DFS. Your servers will need to be configured using the following steps before you can properly deploy DFS in your environment:

+   * All the servers you wish to be members of the replication group must have the DFS Replication installed.
* You must make sure your antivirus software is compatible with DFS Replication.
* All member servers must reside within the same forest. DFS Replication works great between domains, but it is not currently possible to replicate between forests.
* Verify that your AD schema is up to date with all relevant server element additions. Windows Server 2012 R2 comes already to date.
* Understand that DFS Replication does not support the FAT or NTFS File System (ReFS), nor does DFS support replicated data that is stored on cluster shared volumes. The data must be present on an NTFS file system to support replication between servers.

# FIGURE 14.26
Adding the DFS Namespaces and DFS Replication roles

![](bbox=[0.315, 0.603, 0.885, 0.917])