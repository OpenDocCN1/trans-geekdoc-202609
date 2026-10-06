Each host serving part in a clustering setup is a node. In Windows Server 2012 R2, the maximum number of nodes has been pushed to 64, a massive increase from the 16-node limitation in Windows Server 2008 R2. The main point of failover clustering is to provide high availability: if one host goes down, either planned or unexpectedly, the clustering services ensure the application is restarted on another node.

# HOW TO CHOOSE BETWEEN LIVE MIGRATION AND QUICK MIGRATION

Why would you ever want to use quick migration when you can have live migration? One reason is that live migration can sometimes fail. If you look at how it works, you can see its theoretical spot: it needs to transfer memory faster to the destination than the VM is changing. If you have an application that writes a lot of data to very quickly and keeps doing this, it could make live migration impossible. Clearly, a fast network is required to make live migration reliable.

But this shows the advantage of quick migration: it is deterministic because it saves and restores the VM state between migrations. So, if live migration ever fails for a particular VM, then by using quick migration.

# Cluster-free Live Migrations

As mentioned earlier, Windows Server 2012 has an enhancement whereby you can migrate VMs between hosts with no downtime and—crucially—no shared cluster configurations! This capability is known as Shared Nothing Migration. All you need is two hosts and a high-speed network cable, as shown in Figure 28.11.

Figure 28.11
Moving VMs with Shared Nothing Live Migration

![](bbox=[0.298, 0.576, 0.702, 0.765])

It's made possible using a process very similar to the online VM export functionality discussed previously and another new feature in Windows Server 2012 R2 called Live Storage Migration.

With Storage Migration, you can choose to move the storage (virtual disks) of your VM to another location, such as a new folder structure on the local host or onto storage located on a remote host. This feature alone is a very welcome addition to Hyper-V since it was not noticeably