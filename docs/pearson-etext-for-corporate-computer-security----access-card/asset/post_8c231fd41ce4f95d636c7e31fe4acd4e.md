
**Figure 7-7: Windows Server 2019 User Interface**

![](img/073342643701cc54eb7875c41ab92ef2_354_0.png)

The installation of vulnerability patches is very simple and usually automatic. They include server software firewalls, the ability to encrypt data, and many other security enhancements.

These protections are not perfect. Security vulnerabilities need to be patched each month. Other operating systems also have this problem as well.

### THE WINDOWS SERVER USER INTERFACE

All recent versions of Windows Server have user interfaces that look like the interfaces in client versions of Windows. This makes learning Windows Server relatively easy. As Figure 7-7 shows, Windows Server 2019 comes with many of the same applications found on the client version of Windows. It comes with Internet Explorer and File Explorer, and it has a *Start* menu with most choices being familiar to desktop users. You can even run standard client software on Windows Server.

### START → ADMINISTRATIVE TOOLS

As Figure 7-7 shows, Windows Server places most management tools on the **Administrative Tools** choice on the *Start* menu. This makes it easier for systems administrators to guess where to find the tools they will need.

### WINDOWS SERVER MANAGER

The day-to-day management of Windows Server can be done through the Windows Server Manager. New roles, features, and services can be added through the Server Manager. It also gives administrators notices about potential performance issues and unexpected events. Administrators can see all potential issues on a single window and fix them directly without having to open each application individually.

### MICROSOFT MANAGEMENT CONSOLES (MMC)

Most administrative tools in Windows Server come in the same general format, called the **Microsoft Management Console (MMC)**. Figure 7-8 shows the organization of an important MMC, *Computer Management*.

**Figure 7-8: Computer Management Microsoft Management Console (MMC)**

![](img/073342643701cc54eb7875c41ab92ef2_355_0.png)

- First, there is the icon bar. When a user selects an object in one of the two lower panes, the icons specify actions that the administrator can take on the selected object. One of the most important choices is *Action*, which is specific to the selected object.
- Second, there is a tree of administrative applications in the lower-left pane (the **tree pane**).
- Third, the individual applications on the tree pane are called **snap-ins** because they can be added or dropped from the tree list easily. This allows systems administrators to tailor MMCs easily to their particular needs. In the figure, the snap-in *Services* is selected.
- Fourth, there are sub-objects for the selected tool (Services) in the lower-right pane. In this case, the Windows Defender Firewall service is selected.

All MMCs have this same general organization, with an icon bar, a tree pane, and the sub-objects pane. The actions that the administrator can take on a selected object are displayed by clicking the Action icon. This consistent user interface makes it fairly easy to learn how to use new MMCs and new snap-ins.

## Test Your Understanding

- **3a.** What is the name of Microsoft’s server operating system?
- **3b.** What security protections do recent versions of this operating system offer?
- **3c.** Why is Microsoft Windows Server easy to learn?
- **3d.** Why would a server administrator like to use Windows Server Manager?
- **3e.** What are MMCs? (Do not just spell out the acronym.)
- **3f.** On what object does an icon bar icon operate?
- **3g.** What is in the tree pane?
- **3h.** To what things do items in the sub-object pane refer?
- **3i.** What is a snap-in?
- **3j.** Why are they called “snap-ins”?
- **3k.** Why is the standardized layout of MMCs beneficial?
- **3l.** How does the systems administrator get to most administrative tool MMCs?
- **3m.** What does selecting Action do?

## UNIX (Including Linux) Servers

UNIX is a popular operating system for the largest servers. It is also used on some individual PCs. UNIX was created many years ago. This long history has given it broad functionality and high reliability. In some cases, however, the fact that its basic architecture is very old shows itself in some limitations and archaic modes of interaction with users.

### MANY VERSIONS

It is difficult to talk about UNIX security broadly because UNIX is not a single operating system like Windows. Instead, many different versions of UNIX exist. The major vendors, including IBM, Sun, and Hewlett-Packard, all have their own commercial versions of UNIX. A company does not just purchase UNIX; it purchases a specific version of UNIX.

> A company does not just purchase UNIX; it purchases a specific version of UNIX.

These different versions of UNIX tend to be interoperable at the **kernel** level (the core part of the operating system). Kernel compatibility allows them to run most of the same applications. Figure 7-10 shows an example of a Unix terminal.

However, the kernel is only part of the operating system. Different versions of UNIX usually have different management tools, including security tools. This can make UNIX administration difficult if a company uses different types of UNIX.

![](img/073342643701cc54eb7875c41ab92ef2_356_0.png)

**Figure 7-9: UNIX Operating Systems (Study Figure)**

**Figure 7-10: Unix Terminal**

```text
boyler@DESKTOP-5514P26:/$ ls -l
total 112
drwxr-xr-x 1 root root 512 Aug 14 17:17 bin
drwxr-xr-x 1 root root 512 May 21 08:42 boot
drwxr-xr-x 1 root root 512 Aug 14 18:06 dev
drwxr-xr-x 1 root root 512 Aug 14 17:17 etc
drwxr-xr-x 1 root root 512 Aug 14 17:17 home
-rwxr-xr-x 1 root root 112600 Dec 31 1969 init
drwxr-xr-x 1 root root 512 May 21 08:41 lib
drwxr-xr-x 1 root root 512 May 21 08:39 lib64
drwxr-xr-x 1 root root 512 May 21 08:39 media
drwxr-xr-x 1 root root 512 Aug 14 17:17 mnt
drwxr-xr-x 1 root root 512 May 21 08:39 opt
dr-xr-xr-x 9 root root 0 Aug 14 18:06 proc
drwx------ 1 root root 512 May 21 08:42 root
drwxr-xr-x 1 root root 512 Aug 14 18:06 run
drwxr-xr-x 1 root root 512 May 21 08:42 sbin
drwxr-xr-x 1 root root 512 Mar 21 03:55 snap
drwxr-xr-x 1 root root 512 May 21 08:39 srv
dr-xr-xr-x 12 root root 0 Aug 14 18:06 sys
drwxrwxrwt 1 root root 512 Aug 14 17:24 tmp
drwxr-xr-x 1 root root 512 May 21 08:39 usr
drwxr-xr-x 1 root root 512 May 21 08:42 var
boyler@DESKTOP-5514P26:/$
```

SOURCE: © 1995–2019 The Open Group

### LINUX

For UNIX on PCs, the situation is even more chaotic. The most popular version of UNIX for PCs is **Linux**. However, Linux is only the operating system kernel. What Linux vendors actually offer are distributions that combine this kernel with other software. Much of the software is free from the open-source GNU project. For most functions, GNU offers several alternative programs. Consequently, Linux distributions tend to be rather different, especially in management and security.

> Linux is a version of UNIX that runs on ordinary PCs. Actually, Linux is only the kernel of the operating system. Actual Linux packages are distributions that contain the kernel and many other programs—mostly common programs from the GNU project.

Linux is popular because it is free, although “free” must be taken with several grains of salt. First, some Linux vendors charge fees to use their versions of Linux, whether they call this a sales price or not. Even so, Linux is much less expensive to purchase than commercial server operating systems, and a single copy of Linux may be installable on multiple servers without additional cost. This is certainly not the case with Microsoft Windows Server or versions of UNIX created by server vendors.

However, purchase price is only one factor in the total cost of ownership (TCO). Many firms find that Linux is rather expensive to administer, especially if they have many distributions in use from multiple Linux vendors.

The fact that many different distributions of Linux exist makes hardening a Linux system difficult. Some of the more popular Linux distributions include, but are not limited to, Mint, Ubuntu, Debian, Manjaro, and so on. It is important to have a good security baseline for the particular version of the UNIX distribution you are using.

Although Linux was created originally for personal computers, many large servers now run Linux. Server purchasing usually is centralized, so the variety of Linux distributions on corporate servers can be controlled.

### UNIX DESKTOP ENVIRONMENTS

Even within a specific version of UNIX, the operating system software may come with several alternative desktop environments. Some of these interfaces will be graphical user interfaces similar to the interface of Microsoft Windows. On Linux, there are several popular desktop environments
