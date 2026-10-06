# VM MAINTENANCE

+   12. Click Next.

+   13. Select the option “Back up to a hard disk that is dedicated for backups (recommended).”

To use this option, you must have at least one disk attached to the server computer that has no existing volume. The disk should be raw, with no partition or file system.

+   14. Click Next.

+   15. Select the disk to use for the backup volume and click Next.

You will be warned that finishing this wizard will cause the selected disks to be formatted, losing any existing data on the disks.

+   16. If you are certain want to use the selected disks, click Yes to proceed.

+   17. Review your selected options; click Finish to format the disks and schedule the backup.

It may have occurred to you to use the Export feature as a backup. Still, an exported VM is not equivalent to a normal backup because there is no VSS integration. When you import a VM, it doesn’t know it has been “restored.” The downsides of exporting are that you typically do them by one and importing them may require you to update the current VM first (if it exists). If you know what you are doing, an export/import will do you in a pinch. Otherwise, it’s not a backup solution and doing at scale isn’t an option either.

# Malware Protection and Patching

It goes a good idea. Having some type of malware protection on your servers is what you need continuous scanning, or can you get away with daily or weekly scans? As long as you are in a position to counter threats, you are probably OK.

A possible complication with virtualization may have occurred to you. Not only do you have the host to consider, but I/O is a resource on a virtualization platform. If you have a host with 10 VMs, all of them performing continuous scanning, the I/O system of host gets 10 times more load than a single server would have. This practice is not a limiting factor. Modern antivirus software, certainly the server-class kind, knows how to be careful with I/O bandwidth. For VMs, the advice is clear: install malware scanners in all of them. Treat each VM as a physical server, and ensure that you have implemented the documented exclusions deasant to the workload.

But what about Hyper-V? If it has no services except, what is the need for malware scanning? Especially on Server Core, there is little for malware to attack. Although that’s true, that’s not the point. Any operating system connecting to a network is vulnerable to attacks. Each flaw in the TCP/IP stack could lead to a compromise of the system. If you want full protection, you need to scan the host as well. Consider that by far the most disk activity will be performed by the VMs, and you see that the performance impact of a malware scanner on the host will be low. Clearly, you will need to exclude the virtual disks and the Hyper-V processes from scanning. To be, exclude the default VM Configuration folder, the VHD folder, the Snapshot folder, VMMS.exe, and VMWP.exe. Without excluding these from an online access scanner, you might well find that some of the VMs don’t start or even disappear from Hyper-V Manager!