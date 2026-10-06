# CHAPTER 14 CREATING AND MANAGING SHARED FOLDERS

As an alternative to using the Roles and Features Wizard, you can always add the roles and features to your server by utilizing Windows PowerShell. Following are a few examples of using PowerShell to add these roles to a server and to create a DFS namespace:

+   1. Open Windows PowerShell from the taskbar, running the program as an administrator.

+   2. Run the following commands to install the DFS role on a server:

```
PS C:\> Import-Module ServerManager
PS C:\> Add-Windows Feature FS-DFS
PS C:\> Import-Module DFS
```

+   3. Run the following command to create a standalone-DFS namespace:

```
PS C:\> New-Dfsnroot -TargetPath \Test-DFS\Software" -Type Standalone -EnablesSiteHosting -Path \Test\Software"
```

+   4. To see all the DFS cmdlets available in Windows Server 2012 R2, run the following command:

```
PS C:\> Get-Command -Module DFS
```

# Understanding DFS Terminology

Before we go much further, you need to understand the terminology of DFS. Just like learning to understand Active Directory, a new set of concepts and terms comes into play.

You start with a root. This translates into the share that will be visible to the network. In the example, AP is the root. You can have many pages on the root of your site, and save with Server 2012 one can have more than one root just like Server 2008. A root is shared to the network and operates like any other share. You can have additional files and folders within the shared folder.

Under a root, you add DFS links. The link is another somewhere on the network that it is under the root. The link is part of our never-ending terminology. In this case, it is shifting to meaning of an Internet nomenclature. Picture the DFS root as a web page with nothing on the name of the page and a bunch of links to other pages. The links within the DFS hierarchy are hyperlinks on a web page that automatically directs you to a new location. As long as you get the page you are looking for. Once you find your home page (the DFS root), you will be directed by those hyperlinks (DFS links) to any other website you will save (your shares).

A target replica refer to either a root or a link. If you have two identical shares on the network, on separate servers, you can group them within the same link, as DFS targets. You can also replicate an entire root—you know, the table of contents—as a root replica member. Once the targets are configured for replication, the File Replication Service keeps the contents of roots in sync.

![](bbox=[0.19, 0.803, 0.225, 0.833])

# Real World Scenario

# DFS AND YOU

We started this chapter with a suggestion that you should look into or start playing around DFS. Well, let us tell you short story about the day a server died. Now we know you are thinking about a song with a similar name; just read on and find out why DFS can save critical files and reduce the time required to restore files and folders.