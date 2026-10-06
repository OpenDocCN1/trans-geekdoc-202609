# CHAPTER 14 CREATING AND MANAGING SHARED FOLDERS

FIGURE 14-34

The Browse for Shared Folders dialog box

![](bbox=[0.315, 0.1, 0.892, 0.435])

Understand, though, DFS isn't a kind of file server. In a sense, it's not a file server at all—it is instead, a way of putting a kind of “table of contents” on a bunch of existing file servers and pointing the clients to that store of information when they need to connect to a share that is referenced in that. DFS does not create file shares; you must create all the files on the various servers and then use DFS to impose some order. Emphasize that point, here's another fact about DFS: the file shares aren't NTFS, Server 2003, or Server 2008 file shares. If you use NFS, Banyan Vines, and NetWare client software on your computer, you could actually create a DFS “share” that points only to NFS, DFS, and NetWare wanted. We will cover NFS later, but let's finish with DFS.

But does that mean that if the DFS root “table of contents”—constitutes a single point of failure? If that server that houses the root—the place where all users go to find their resources—goes dead in the water, so do your users, right? Not necessarily. Combined with Active Directory, DFS roots can be made fault tolerant. In actual, the file root hosted on one server, can be stored in Active Directory, which is maintained across all domain controllers. If one of those servers fails the root—in Active Directory—your users are automatically directed to retrieve information without even a hiccup.

Again, we'll stress the function of DFS. Fault-tolerant DFS doesn't mean that you're backing up the data in the file shares. It only means that the “table of contents” that is a DFS root gets backed up so that if the computer hosting the DFS root goes down—and we're're sorry to be stressing this point, but again there's a good chance that the machine hosting the DFS root does not contain one single byte of shared files, just the pointers to the servers that contain those files—then there's another computer standing by to assume the role of “table of contents server,” or in Server 2012 the DFS root.