# Chapter 14

# Creating and Managing Shared Folders

Maybe you still remember putting data on floppy disks that you wanted to share with peers. Sharing files and folders is one of the really reasons why server technologies were developed. Microsoft Windows Server 2012 has developed new and advanced ways to share files with services like Network File System (NFS), which provides a file-sharing solution for enterprises that may be running a mix of operating systems. With NFS, you can share files with not only other Windows servers but also Unix, Linux, and Mac OS if they exist in your organization. We will look at NFS in depth in this chapter and go over what is new and what has changed with this server edition.

Windows Server 2012 R2 has also revamped its Distributed File System (DFS) technologies by continuing to offer WAN-friendly replication to simplify access to geographically dispersed files and folders. You can share files and folders across the network based on your groupings of them. This fortune streamline a complex process that was both tedious and time-consuming in earlier Windows Server releases.

In this chapter, we will help you dig into DFS and NFS with step-by-step guides on how to use these exciting functions. You'll find out what they are, how they work, and how to make them for you.

In this chapter, you will learn to:

+   - Add a File and Storage Services role to your server
- Add a shared folder using NFS
- Add a DFS root

# Creating Shared Folders

Before you can create a shared folder, you must have the appropriate rights to do so. This requires that you be either an administrator or a power user. You can create shares in a couple of ways: you can use the Windows Explorer interface when sitting at the server, or you can use the Share window in Server Manager to create shares either at the server or remotely.