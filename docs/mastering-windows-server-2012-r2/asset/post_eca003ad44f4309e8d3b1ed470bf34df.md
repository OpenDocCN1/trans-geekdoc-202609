
reboots if necessary. Once the first node comes back up, CA takes that particular server out of maintenance mode, fails back the original roles, and moves to the next node.

As an example, if you have a two-node cluster, all the roles or servers migrate to Node 2. Once Node 1 has been patched and rebooted, it will fail back its original roles, and then once it has completed, it takes the roles that are living on Node 2. Node 2 will send the job to put itself in maintenance and fails its servers to Node 1.

The Cluster-Aware Updates can be installed on both Windows Server 2012 R2 and Windows 8 clients. After the tools are installed, you configure the CA scenario you want; examples of these scenarios can be found at http://tinyurl.com/c31cluster.

As you will see from the Cluster-Aware update guides, the CA works in two basic modes:

- Self-Updating: This configuration runs on the cluster node you want to update, and you will build an update schedule and let CA update the cluster.

- Remote Updating: You run the CA from a stand-alone server or client that is not clustered; an example would be your Windows 8 desktop with the CA tools. You then utilize the tool to connect to the specific cluster you want and update the cluster on your schedule.

During your installation and management of Cluster-Aware Updates you will find a series of PowerShell cmdlets that you can check if a server is ready, launch the process, and check the overall status of the clusters. Once you have chosen how for you want to use CA and get your schedule, you can take advantage of Windows Server 2012 R2's advanced features and push your WSUS v6 role!

# ADDITIONAL PATCH MANAGEMENT TOOLS PROVIDED BY MICROSOFT

Although we're focusing on WSUS in this section, Microsoft has several tools that can assist you in managing updates in your organization:

**Microsoft Update** Microsoft Update is now included in your Control Panel, and from there you can view your current settings, when updates are applied, and the action that is taken when updates are found.

**Microsoft Catalog** All files available on Microsoft Update are available in the Microsoft Catalog, including drivers, security, and other updates to Microsoft products. One nifty having the Microsoft Update Catalog is the ability to add multiple files to your shopping basket and download them all at once. You can find the Microsoft Update Catalog at http://catalog.update.microsoft.com.

**Windows Server Update Cmdlets in PowerShell** Windows Server 2012 R2 offers an extensive library of PowerShell cmdlets that you can utilize to combine and repeatable tasks within WSUS infrastructure. TechNet (http://tinyurl.com/c31pscmdlets). Being able to manage components and patches from PowerShell gives you the ability to further automate the management of multiserver infrastructure and gives you the granularity you may need to do things like deny a specific patch for a particular deployment.

**Microsoft Security Tools** The MSA has been replaced with the Security Assessment Tools for Windows Server 2012 R2 and Windows 8 clients; it covers the support of Windows 7, Windows Server 2008, Windows XP, Windows Vista, and Server 2008 R2.

# DEPLOYING UPDATES AND MIGRATION FOR WINDOWS SERVER UPDATE SERVICES

Multiple tools are available: Microsoft Security Assessment Tool 4.0, Microsoft Baseline Security Analyzer 2.2, and Microsoft Compliance Manager. You can find all of these tools and more at http://tinyurl.com/c31mst.

Security Response Center Blog The Microsoft Security Response Center (MSRC) is in charge of issuing security updates for Microsoft. The site also advisories for problems that have been disclosed or that it's investigating. The MSRC blog is a good way to get current information. See http://blogs.technet.com/b/msrcrc/

Following the team on Twitter @MSFTSecResponse is a great option to keep you on updates.

# System Center Configuration Manager

System Center Configuration Manager (SCCM) is a centralized management tool built on Microsoft's System Center suite of software. The focus area SCCM includes (server and workstation) management, patching, endpoint protection, application deployment, and automated operating delivery. A breakdown of SCCM 2012 SP1, the most current version of the product, can be found at http://microsoft.com/en-us/server-cloud/system-configuration-manager-2012.

System Center Configuration Manager offers advanced reporting and compliance capabilities over WSUS. A typical recommendation is that any large organization utilize SCCM as their primary patching.

- Advanced reporting and compliance
- Server and workstation management
- Patching
- Endpoint protection
- Application deployment
- Automated operating delivery

# Chapter 32

# Windows Server 2012 R2 and Active Directory Backup and Maintenance

Backup and recovery are familiar tasks to most server administrators. Protecting data and applications is important, but recovering your Active Directory can be even more vital to continued operations.

In this chapter, we'll cover the various types of backup and recovery available in Windows Server 2012 R2 as how they apply to Active Directory. You will learn about the Active Directory Recycle Bin, Microsoft System Center 2012 R2 Data Protection Manager, and a new online backup option for Windows Server 2012 R2 that allows you to back up to the cloud with Microsoft Azure.

In addition, we will describe some Active Directory maintenance tasks, such as the ability to stop and restart Active Directory without having to restart the server. The ability to stop Active Directory lets you perform maintenance of the Active Directory database, such as defragmentation and integrity checks.

In this chapter, you will learn to:

- Use Windows Server Backup to back up and restore a Windows Server 2012 R2 computer
- Defragment AD DS offline
- Install the Active Directory Recycle Bin
- Create and recover a system state backup for Active Directory

# ## Introducing Windows Server Backup

Backup has long been part of Windows Server, and in Windows Server 2012 R2 the backup tasks are performed by Windows Server Backup. Although Windows Server Backup may not provide every feature you might want in an enterprise environment, it does a very good job of backing up and restoring Windows Server 2012 R2 can be a viable solution for small-to-medium-size environments. Windows Server Backup can be used to back up remote computers, but it's most suited to backing up the load server.

The Windows Server Backup includes with Windows Server 2012 R2 has some notable improvements over the previous version in Windows Server 2008 R2. Here's a list of them:

- Backing up and restoring individual virtual machines from a Hyper-V host server is now supported.
