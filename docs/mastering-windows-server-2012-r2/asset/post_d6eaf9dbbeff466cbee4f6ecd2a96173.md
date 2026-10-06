
Just as the different domain functional levels adds features to your domain, the different forest functional levels also provide various features.

**Windows Server 2003** Windows Server 2003 provides the following features:

- Ability to create forest trusts
- Ability to rename a domain
- Ability to deploy a read-only domain controller (RODC)
- Improved Knowledge Consistency Checker (KCC)
- Improved linked-value replication so that only the differences of the group memberships replicated
- Access-based enumeration in the DFS namespace

**Windows Server 2008** The Windows Server 2008 functional level does not provide any additional features.

**Windows Server 2008 R2** The Active Directory Recycle Bin lets you restore deleted objects without starting the domain controller in Active Directory Restore Mode. You need to enable the Active Directory Recycle Bin using PowerShell commands. Active Directory Recycle Bin is a great feature that was improved in Windows Server 2012. It is now much easier to set up and manage, as you will see later in this book.

**Windows Server 2012** The Windows Server 2012 functional level offers no new features.

## WHAT'S DIFFERENT IN WINDOWS SERVER 2012 R2 FUNCTION LEVELS

As we are writing this book, we are testing with a preview version of Windows Server 2012 R2. Although little in Active Directory has changed, there are some changes in functional levels from predecessor.

You can add a Windows Server 2012 R2 controller into an existing 2003 functional level environment. But be aware that the Windows Server 2012 R2 functional level is deprecated. When you deploy a Windows Server 2012 R2 into an existing Windows Server 2003 environment, you will be prompted to move to a higher functional level.

The lowest functional level you can select in Windows Server 2012 R2 is the Windows Server 2008 domain and forest functional.

You can find a full-featured overview of the new functional level on TechNet. Hopefully, will be updated by the time this book is published. Go to:

```
http://technet.microsoft.com/en-us/library/understanding-active-directory-functional-levels.aspx
```

## LOCATIONS FOR FILES AND SYSVOL

The Active Directory Domain Services Configuration Wizard prompts you for the location of various Active Directory files and the location of the SYSVOL shared folder.

## AN INTRODUCTION AND ACTIVE DIRECTORY BASICS

The SYSVOL shared folder is used to share information, such as scripts and elements of Group Policy objects between domain controllers. SYSVOL, and the Active Directory database and log files must be placed on an NTFS formatted drive. The database and log files can be located on different drives, but those must be formatted as NTFS (see Figure 7.6).

## FIGURE 7.6
File paths

![](img/41a83208e6906a3732620203b836cea7_306_0.png)

Windows Server 2012 introduces the new Resilient File System. ReFS offers higher integrity and scalability, and it has proactive error identification built in. You might think that it would be a perfect place for an Active Directory component, but as discussed earlier, this is not supported. Nor can you place the Active Directory database, Directory log file, or SYSVOL directory on ReFS.

At its core, Active Directory is a large database, and databases have a primary data file and a transaction log file. Changes to the database are first written to the transaction log file, and periodically the transaction log file is check-pointed—just like a way of saying that changes in the transaction log are committed to the database.

The transaction log provides significant fault tolerance and recovery capabilities to the Active Directory database. If the server loses power in the middle of any change, Active Directory can use the log to ensure that the database is in a consistent state when the server is rebooted. Any changes recorded in the log are committed to the database, and any unfinished changes recorded in the log are ignored.

From a performance perspective, it is possible to increase the performance of your DC by moving the database and transaction log files to different drives. For optimal disk performance of Active Directory, you may use a configuration similar to this:

- C:\drive: Operating system
- D:\drive: Active Directory database file and SYSVOL
- E:\drive: Transaction log file

In this configuration, each of the drives needs to be a separate spindle (a separate physical disk). Using three partitions wouldn't provide any performance gain. Additionally, if your drives have different speeds, you should put the operating system on the fastest disk, the transaction log on the next fastest, and the Active Directory database file and SYSVOL on the slowest disk. The operating system and the transaction log file will receive the heaviest usage.

To optimize your domain controller just a bit more, you distinguish between heavy read and write operations. If you have heavy read operations, you could add sufficient memory to the domain controller so that it can cache the database in memory. For heavy write operations, you can improve performance by adding the following:

- Hardware RAID controllers
- High RPM disks
- Battery backend write-caching (BBWC) on the RAID controller

This sounds good and makes sense, but what will happen if you virtualize your domain controller? In this case it's a good idea to add sufficient memory for your domain controller so that it can cache the database. If SYSVOL on different virtual disks, the performance improvement will probably be minimal. The problem is that all virtual disks are on the same LUN, and the LUN is spread over an array of disks. This means that all virtual disks share the same physical disks in the storage. From a theoretical standpoint, it would be best to place each file on a separate array or LUN. In any case, you should use the fastest storage you have.

For a good starting point to figure out if you have a disk performance problem, you can use these performance counters. Each of these counters should have a low value:

- Avg. Disk Queue Length
- Avg. Disk Read Queue Length
- Avg. Disk Write Queue Length

Let's look at an example. If your domain includes 100 users, you can store the database and log files on the C drive with the operating system and not notice any performance problems. On the other hand, if you are supporting 50,000 users, you may want to squeeze every ounce of performance out of the server, so you will locate the database and log files on different drives. If you are building a test system, there is nothing wrong with leaving everything on C.

## AN INTRODUCTION AND ACTIVE DIRECTORY BASICS

## MOVING THE DATABASE AND LOG FILES

Windows Server 2012 introduces restartable Active Directory Domain Services (AD DS), which you can use to perform database management tasks without restarting the domain controller in Directory Services Restore Mode (DSRM). If you need to relocate the AD database onto another drive, you can use the command-line utility NTutil. Because of the AD DS, you don't have to restart the domain controller in DSRM; you just need to stop the Windows AD DS service and perform your task.

## DIRECTORY SERVICES RESTORE MODE PASSWORD

If you ever need to perform maintenance or restoration of Active Directory, you would use Directory Services Restore Mode. You can access DSRM by pressing F8 to the Advanced Options menu. You can also access the Safe Mode from this menu.
After selecting Directory Services Restore Mode, you will be prompted to log on. However, Active Directory will not be running, you can't use an Active Directory account. Instead, you will use a special administrator account with a different password. The Active Directory Domain Services Configuration Wizard prompts you to set the password for the DSRM account, as shown in Figure 7.7.

## FIGURE 7.7
Setting the Directory Services Restore Mode password

![](img/41a83208e6906a3732620203b836cea7_308_0.png)
