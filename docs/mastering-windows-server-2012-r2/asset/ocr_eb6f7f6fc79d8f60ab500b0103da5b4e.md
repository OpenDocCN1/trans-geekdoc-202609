# ENABING HYPERV-REPLICA

Now that you have an understanding of what HVR is, in this section we will walk through configuring a replication of VM between two non-clustered Hyper-V hosts running Windows Server 2012 R2. We will use VMHOST1-SRV as our source server and VMHOST2-SRV as the destination server. Both hosts in this example are part of the same Active Directory forest and can resolve each other's names across the WAN. By default, HVR is disabled, and you will need to enable it on the destination server.

+   1. On the destination server, open Hyper-V Manager with an account that has administrative permissions, right-click the host, and select Hyper-V Settings from the context menu.

+   2. Click Replication Configuration from the Server column; then select the "Enable computer as a Replica server" check box, as shown in Figure 28.19.

Notice the two different authentication options for Kerberos and certificate-based authentication: because we are using Active Directory to authenticate, Kerberos is fine in this case.

# FIGURE 28.19
enabling HVR on the destination host

![](bbox=[0.318, 0.442, 0.903, 0.876])