
| `Dsastat.exe`: Active Directory Diagnostic Tool || Compares and detects differences between naming contexts on DCs. |

## ![u06-09-9781931836944](images/B978193183694450012X/u06-09-9781931836944.jpg) Monitoring File Replication Service Replication

The File Replication Service (FRS) is used to synchronize the contents of the Sysvol folders, located by default in `< systemroot>\\sysvol\\sysvol`, across multiple Active Directory domain controllers (FRS is also used in keeping Dfs replicas synched, but in the context of this book, we will be discussing FRS synchronization of Sysvol).

FRS runs as a service. It is installed by default on domain controllers and startup mode is automatic. The executable, `ntfrs.exe`, is located in the `< systemroot>\\system32` directory. FRS replication differs from Active Directory replication of changes to user, group and computer accounts in that its intrasite replication is almost instantaneous (By default, regular AD replication occurs at five minute intervals). Intersite replication mirrors that of AD; it occurs at whatever interval the administrator has set for intersite AD replication. Because FRS uses a multi-master replication model, changes can be made to the SysVol on any domain controller and then propagated to the SysVols on other DCs in the domain. These other DCs are called replication partners, and can be either inbound or outbound. Inbound partners are those that provide data to the DC; outbound partners are those to which data is provided by the DC. Tables in the FRS database, called the inbound and outbound logs, hold the change orders that come from inbound replica partners and those to be sent to outbound replica partners, respectively. There are several ways to monitor FRS: log files, FRS node in Event Viewer, and Tools and Scripts.

### Examining the Log Files

FRS writes logs to the `< systemroot>\\Debug` folder. These are text files that can be used in troubleshooting problems with FRS. The default files are named `Ntfrs_0001` through `Ntfs_0005`.

By default there are five files saved; however, you can increase the number of log files. You can also save the files to a different location to archive them. Changing the configuration for the log files requires that you edit the registry entries in the following key:

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\NtFrs\Parameters.`

Edit the data value for the `Debug Log Files` entry to change the number of log files that will be created. (If you use the `QA_check.cmd` script, you’ll also need to edit its file and change the value from 5 to the new number, to correspond to the change in the registry). Edit the data value for the `Debug Log Severity` entry to specify how much detail you want recorded in the logs (0 is least amount of detail; 5 is most). Edit the value for the `Debug Maximum Log Messages` entry to control the number of lines (and thus the file size) of each log. The default is 10,000 lines, which results in a file of approximately 1 MB in size.

The log files record errors, warning messages and other events related to the service.

For more information on how to analyze the contents of the FRS logs, see [http://www.microsoft.com/technet/treeview/default.asp?url=/technet/prodtechnol/ad/windows2000/deploy/adguide/addeploy/addch09.asp](http://www.microsoft.com/technet/treeview/default.asp?url=/technet/prodtechnol/ad/windows2000/deploy/adguide/addeploy/addch09.asp). Although this TechNet article was written for Windows 2000, it is applicable to Server 2003 FRS log files as well.

### Using the FRS Node in Event Viewer

A much more user-friendly way to monitor FRS events is through the File Replication Service node of the event viewer. This node appears only on domain controllers, and contains the familiar Event Viewer Information, Warning and Error messages.

Information events record occurrences that are not problems, such as notification that the service is starting or stopping. Warnings record events that could potentially cause problems, such as the FRS service being unable to bind to a domain controller when polling for FRS replica set configuration information. Errors record events that present existing problems.

### Using Tools and Scripts

There are some tools and scripts provided by Microsoft that can be used to monitor FRS replication. We’ve already mentioned the `QA_check.cmd` script. You can also use the following utilities and scripts to monitor FRS:

■ The `Ntfrsutl.exe` tool This utility can be used to show the ID table and inbound and outbound logs for FRS computers, examine how much memory FRS uses, view the FRS configuration, get a list of active replica sets, find out the API and version number of FRS running on the computer, and poll for changes to FRS configuration. You must be an administrator to access all of the data provided by this utility.

■ `Connstat.cmd` This is a script that creates a summary of the domain controller’s FRS connections and shows the states of both the inbound and outbound connections.

■ `Frscheck.cmd` This is a script that uses `Ntfrsutl.exe` to collect information about the FRS version, sets, directory services, configtable, inlog and outlog, as well as registry parameters related to FRS. It also looks for error information in the Debug log files. Again, you need to be an administrator to access all of its information.

## Summary of Exam Objectives

This chapter explained the role of sites, and discussed the relationship of sites to other Active Directory components. We showed you how to create sites and site links, and explained site replication. This chapter enables you to become familiar with exam objectives covering such topics as the various roles and services offered by Active Directory Sites.

The chapter also offered the basics of how each role and services of Active Directory Sites works and how Active Directory Sites can be used efficiently in terms of data transmission as part of a large network. You should be familiar with the difference between interactive and network authentication and be aware that using Active Directory sites can help to ensure that users and computers will communicate with the appropriate DCs for authentication and authorization.

Sites and subnets are essential components that make up the physical structure of your Active Directory network. Understanding how to use them for enhanced performance and best bandwidth usage is necessary, not only in mastering the objectives for Exam 70-294, but in performing your daily duties as a Windows Server 2003 network administrator.

## Exam Objectives Fast Track

### Understanding the Role of Sites

☑ Sites are used for optimizing the authentication process, by reducing authentication traffic across slow, high-cost WAN links.

☑ Subnets provide rapid and reliable communication between locations.

☑ The primary role of sites is to increase the performance of a network, which is achieved by economic and rapid transmission of data.

☑ Replication enables transferring data from a data store present on a source computer to an identical data store present on a destination computer.

☑ The Knowledge Consistency Checker (`KCC`) is a process that runs on a DC.

☑ Authentication is a process by which a system validates users, using the logon information provided.

☑ Network authentication verifies the user’s identification to a network service.

### Relationship of Sites to Other Active Directory Components

☑ The distribution of services information in Active Directory enables the client and applications to get information from the directory.

☑ Domains are defined as units of replication that receive changes and replicate those changes among all DCs present in the domain of a network.

☑ A single site consists of one or more Internet Protocol (IP) subnets.

☑ Sites and subnets are represented in Active Directory by site and subnet objects, which we create through Active Directory Sites and Services.

### Creating Sites and Site Links
