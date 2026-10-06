# 4. Finally, from Server Manager, under File and Storage Services, click Volumes ➤ Disks.

As shown in Figure 12.62, we have two new disks with Bus Type listed as iSCSI. They are now available to format and create standard volumes out of.

# FIGURE 12.62
Displaying added iSCSI disks

![](bbox=[0.318, 0.215, 0.905, 0.403])

# NFS Shares

Network File System (NFS) allows you to share files between a Windows server and a Unix/Linux platform using the NFS Protocol. In Windows Server 2012 the following improvements were introduced:

**NFS Version 4.1 Support** This includes easier accessibility through firewalls, RPCSEC_GSS protocol for enhanced security, client and server security negotiation, Windows and Unix semantics, better support for clustered servers, and WAN-friendly compound procedures.

**Improved Performance** No more tuning is necessary because using the new RPC-XDR protocol, you should achieve optimal performance out of the box.

**Easier Management** You can manage via PowerShell and a unified GUI in Server Manager. RPC port 2049 makes it easier to configure firewalls. Another improvement is better identity mapping, and there is a new WMIV2 provider.

**NFSv3 HA Improvements** These are now improved features with the new per-physical disk and tensor fault paths. This makes failover fast for NFS clients.

# Where to use an NFS Share

NFS is used in environments where you have a requirement for file shares in a mixed operating system environment (such as Windows and Unix/Linux). With the improvements in Windows Server 2012, you can now present a share with NFS and SMB at the same time.

A common use for this has been found in some third-party hypervisors using Windows Server 2012 NFS shares as data stores for templates and ISOs.