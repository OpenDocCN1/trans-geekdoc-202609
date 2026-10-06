
# Checking for Corrupt Volumes

The last thing in relyup that we will talk about in this chapter is volume corruption checks. As you can imagine, the more commonly found in the files, the more the chunk will grow, and the more reparse points that will exist on disk.

Imagine if a disk section where a chunk became corrupted. You risk losing potentially hundreds or thousands of files. Although this is a rare occurrence, especially if you combine it with resiliency checks, it is a potential for it to happen. Dedup has some special checks that will prevent this from happening.

For example, relyup has redundancy for critical metadata; it also provides redundancy for the most accessed chunks (if a chunk is accessed more than 100 times, it becomes a hot spot). It provides a log to record the details of any corruption, and later through the use of scrubbing it will analyze the log and make repairs.

Repairs can be made from the backup of the working copy when referring to the critical metadata or the hot spots. If you have dedup a mirrored storage space, dedup can use the mirrored data to repair the chunk.

With optimization of dedup and garbage-collection jobs, scrubbing jobs on a scheduled basis and can be triggered to happen more than the default of one week. You can trigger a job with PowerShell using the following syntax:

```
Start-DedupJob -Type Scrubbing -Volume E:
```

This will involve a verification job against the E: drive but will only check the entries in the corruption log file.

To check the integrity of the entire deduplicated volume, use the following command:

```
Start-DedUpJob -Type Scrubbing -Volume E: -full
```

To review the output of the scrubbing, check Event Viewer. All output for a scrubbing job is stored in Event Viewer > Applications and Services Logs > Microsoft > Windows > Dedplication > Scrubbing. See Figure 12.87.

![](img/41a83208e6906a3732620203b836cea7_681_0.png)

# The Bottom Line

Create a storage pool on a virtual disk. Storage is an ever-growing business requirement. If you were constantly buying SAN solutions to meet this need, it would prove very costly. Also, it is hard to predict what you may need in a year's time. How would you manage your storage to get the most out of it and meet your future storage needs?

Master It: In your lab create a storage pool using the GUI with three disks. Create a virtual disk three times the size of the total usable capacity of the disk. Format it and get it ready to use.

Create additional storage on a virtual disk. A common occurrence in enterprises today is last-minute requests for provisioning of applications that require large amounts of storage. Often the storage available locally in the server is not large enough to meet the need. How can you get additional storage onto the server without adding local storage?

Master It: In your lab deploy an iSCSI target, create a virtual disk, and connect your server to use the newly created storage.

Use deduplication techniques to reduce file size. Part of the reason behind data growth in today's environments is the availability of storage, but storage will become a problem sooner rather than later. A high percentage of these files contain a large degree of identical data patterns, but using deduplication techniques can dramatically reduce the disk space required and make better overall use of the storage in place.

Master It: In your lab copy an ISO multiple times into different shares, and repeat for office documents that are not located on your System volume. Enable Deduplication on the data drive, and exclude a share of importance in your environment.

# Chapter 13

# Files, Folders, and Basic Shares

One of the core functions of any server is to serve resources such as files and folders. In Windows Server 2012 R2, the File Services and Storage Services roles have been combined into one role called File and Storage Services. This role is installed by default; however, any additional roles that serve File and Storage Services will need to be added via the wizard in Server Manager. The File Services role includes roles such as the File Resource Manager (FSRM), services for Network File System (to support Unix clients), the Windows search service, and BranchCache for remote offices. Now that Storage Services is available in conjunction with File Services, Windows Server 2012 R2 has unleashed some new and improved roles and features like Deduplication, Storage Spaces, and Storage Pools that have made this version of Windows Server 2012 the best.

When you plan on sharing folders and files, it's important that you understand not only how to share the data but how to protect it with permissions including both Technology File System (NTFS) and share permissions. Both sets of permissions are applied independently, to provide multiple levels of enhanced security options. You should be able to quickly determine what the ultimate permissions are for a user who accesses a share over the network. And, if you want to protect hard drives, you can still use BitLocker Drive Encryption to encrypt them using Windows Server 2008 R2. One of the most notable new features in Windows Server 2012 R2 is BitLocker Drive Encryption options. You can now use the "Encrypted disk space only" option—no waiting hours for the entire volume to finish encryption when you are only using a small portion of the total disk space. We will take a deep dive into BitLocker's new features towards the end of the chapter.

The underlying protocol that handles file transfers is Server Message Block (SMB), which has been upgraded to 3.0 in Server 2012. SMB 3.0 comes with many new features that have redefined files as a foundation for enterprise storage solutions for small and medium-sized companies. This protocol stack provides significant benefits for file transfers over the network—as you are connecting to the right kinds of clients. Both SMB 1.0 and SMB 2.0, with all their inherent challenges, will still be used when connecting to legacy machines. Currently only Windows 8 and the Windows Server 2012 family can take full advantage of the new SMB 3.0 features that will be discussed in this chapter.

In this chapter, you will learn to:

- Install additional File and Storage roles on a server
- Combine share and NTFS permissions
- Implement BitLocker Drive Encryption

# Understanding the File and Storage Services Role

The File and Storage Services role combines multiple file and storage technologies that assist administrators with setting up file servers for their organization. The default installation would allow basic administration of storage functionality using Server Manager or PowerShell, but to build a proper file server you would need to install the File Server role alongside important roles like File Resource Manager and DFS Replication. If DFS is needed all the time—it can easily be a great addition when you need replication for availability or geographically dispersed locations. The important thing is to have a plan and an end goal in place for your server roles. To get the most out of the wizard the first time by planning accordingly.

The core component of any service is its ability to share file. In fact, the service in the entire Windows Server family (including Windows Server 2012 R2) handles the server’s file- and print-sharing capabilities. What exactly does that mean, and why is it important? Just because you have a server running does not mean it has anything available for your users. Before they can actually get access to resources, you must share your resources. Let’s say how you share a folder on your local F drive with three subscribers, as shown in Figure 13.1.

FIGURE 13.1
Subfolders in the F: \Apps folder

![](img/41a83208e6906a3732620203b836cea7_685_0.png)

When you share this folder on the network under the name Apps, you allow your clients to map a new drive letter on their machines to your F:\\Apps folder. By mapping a drive, you are placing a virtual pointer directly on the remote drive. If you map your client’s M drive to the Apps share of the server, the M drive will look identical to the server’s F:\\Apps folder, as shown in Figure 13.2.
