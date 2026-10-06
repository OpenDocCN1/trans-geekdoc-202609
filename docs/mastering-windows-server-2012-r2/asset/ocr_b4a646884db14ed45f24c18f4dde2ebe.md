# SHARED STORAGE BASICS 55

As you can see, the Storage Services component of this role is installed by default and cannot be uninstalled. The other components can be installed and removed as needed.

The File and iSCSI Services component of this role provides multiple components that will help you manage your files, disk size, replication, and branch offices. The following list provides an overview of each of these components and what they will offer to your file and storage capabilities with Windows Server 2012 R2:

File Server This component allows you to manage shares and enable users to access files on this specific server in your organization's network.

BranchCache for Network Files This component allows your BranchCache servers to have network service files.

Data Deduplication This service helps you manage and save disk space by looking through your volume and making sure that only a single version of a file exists. Continuing with the earlier example of Sarah and her HR files, let's say Matthew, an HR coworker of Sarah, saved a copy of a file somewhere else thinking it wasn't available. Data Deduplication makes sure that only a single version of the specific files exists that are available so that Matthew can find his file.

DFS Namespaces Distributed File System (DFS) allows you to set up a group of shared folders that could be hosted on other servers in your organization but appear under one name. Here's an example:

+   * Server 1—Has a share location \\Server\Files.
* Server 2—Has a share location \\Server2\Stuff.

Using DFS Namespaces, you could locate both of them \\Bigfarm\Shared.

DFS Replication This feature enables you to synchronize shared folders across a WAN. It does not require DFS Namespaces but can be used with it.

File Server Resource Manager File Resource Manager (FSRM) is a performance and monitoring tool that will give you more detailed reports on what's happening with your storage. You can build files, quotas, and classifications using FSRM as needed.

File VSS Agent Service You can use this service to copy files and the data that are stored on the specific server the role is on is using Volume Shadow Copy Service (VSS). For more information on VSS you can use http://tinyurl.com/c1l1ivss

is Target Target This provides the tools and services to manage your iSCSI servers.

Server for NFS You can enable Network File System (NFS), which is used by Unix/Linux-based computers, so that shares on this installation of Windows Server 2012 R2 are visible to those clients.

Work Folders This new feature of Windows Server 2012 R2 provides a simple way to manage files that exist on a bunch of different workstations and personal devices. The work folder will act as a host and synchronize the users' files to this location so they can access their files from