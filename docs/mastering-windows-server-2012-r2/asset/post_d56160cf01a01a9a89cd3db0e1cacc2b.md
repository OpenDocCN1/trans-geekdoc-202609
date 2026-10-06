
# Installing a Sample Server Network for This Book’s Examples

You are going to need a laboratory or test network to practice what you learn in this book.
To follow along with the examples, build two servers using the clean installation or unattended installation method. Our recommendation is to use both methods for your first attempt to build this lab network. You can then use the unattended installation method for all future builds to speed things along.
Customize each of the two servers using the following settings:

## SERVER 1

| ITEM | CONFIGURATION |
| --- | --- |
| Full Computer Name | bf1.bigfirm.com |
| IPv4 Configuration | Address: 192.168.1.51 |
| Subnet mask: 255.255.255.0 |
| Default gateway: 192.168.1.1 |
| DNS1: <blank> |
| DNS2: <blank> |

## SERVER 2

| ITEM | CONFIGURATION |
| --- | --- |
| Full Computer Name | bf2.bigfirm.com |
| IPv4 Configuration | Address: 192.168.1.52 |
| Subnet mask: 255.255.255.0 |
| Default gateway: 192.168.1.1 |
| DNS1: <blank> |
| DNS2: <blank> |

At this point, you will be the proud owner of your very first Windows Server 2012 R2 server network.

# The Bottom Line

**Upgrade your old servers.** Microsoft has provided several upgrade options for Windows Server 2012 R2.

- **Master It** You have a Windows 2008 x86 file server. What will your upgrade path be to Windows Server 2012 R2?

**Configure your server.** Windows Server 2012 R2 allows you to use Server Manager and PowerShell to add or remove roles, role services, and features.

- **Master It** You have started to deploy Windows Server 2012 R2. You are planning on automating as much of the build process as possible. What tool will you use to add or remove roles, role services, and features?

**Build a small server farm.** Installing Windows Server normally requires that you sit in front of the machine and answer a number of questions. This is time-consuming and distracts administrators from other engineering or project tasks that they could be working on. A number of alternative techniques can be employed.

- **Master It** You have been instructed to build four new servers with Windows Server 2012 R2. This will be the first time your organization will deploy Windows Server 2012 R2. Your department is short-staffed because a number of colleagues are on vacation. You want to do this job quickly and efficiently. How will you do it?

# Chapter 3

# Introduction to Server Core

Microsoft designs and develops the next version of its products based on what the market demands. In this edition, it fends the competition by integrating the strengths and features the others have to offer. With Server Core, introduced in Windows Server 2008 and improved in Windows Server 2012 R2, Microsoft has enhanced its Windows operating systems to combat its competitors and meet the demands of system administrators who want to work from the command line. In this chapter, we'll explore what's new in the Windows Server 2012 R2 operating system and how to manage it using PowerShell.

- Use the new functionality in Server Core
- Install and configure Server Core
- Set up Server Core for a branch-office deployment
- Remotely manage the operating system

# What's New in Server Core

You're installing Windows Server 2012 R2 for the first time, and a couple of screens into the installation you set the installation options. Should you use the GUI or not? You like the benefits of Server Core has with regard to security and overhead savings, but you like the point-and-click UI that comes with the GUI version. We have good news for you: In Windows Server 2008 R2, once Server Core was set you couldn't switch back, but in Windows Server 2012 R2 you now switch back and forth between Server Core and the GUI. The default installation choice is Core, but if you choose to install the GUI, you will still have PowerShell available. Once you have the server set up and ready to run in production, you can simply switch over to Core.

Keep in mind as you read this chapter that even though you can switch to the GUI version to accomplish the tasks, we will be using Server Core to do those tasks. For example, we will be showing how to validate your copy of Windows using Server Core. You may find it easier to switch to the GUI version to accomplish this, and that's fine if you choose to do it way. Most of the samples in this chapter are also in Chapter 2, 'Installing and Upgrading to Windows Server 2012 R2'. PowerShell 3.0 offers you more cmdlets to administer your Server Core. The cmdlets' syntax is now simpler to understand. Many of the existing cmdlets have had parameters added to extend their functionality. We will provide the Survival Guide later in this chapter for a complete list of the new cmdlets added in Windows Server 2012 R2.

# What IS Server Core?

Server Core is Windows stripped to the minimum requirements to run an operating system. It runs without the GUI, Windows Explorer, Internet Explorer, and other dependent components. Removing the extras that we have to cope without many of the administration tools that we know and love, namely, snap-ins built on the Microsoft Management Console. This leaves the PowerShell command prompt as our primary interface to the operating system.

What does this all mean to you, the administrator?

**Reduced Maintenance** Less code means fewer updates to perform.

**Reduced Attack Surface** Without the fluff, there is less to attack. Roles and features can be installed as needed and the limited number of services will reduce the areas for attack.

**Reduced Performance Requirements** Server Core takes fewer CPU cycles and less disk space, the opportunity to repurpose hardware is with this.

# Installing Server Core

Before you install Server Core, keep in mind that you can switch between Server Core and the GUI, it does not matter which version you initially set up. This allows you to set up the server in the GUI, as we showed in Chapter 2, and switch it over Server Core.
The process for installing Windows Server 2012 R2 Server Core is as straightforward as other Windows Server 2012 R2 installations. You install the installation DVD and allow the server to boot from it. Then you "follow the bouncing ball." You can use an unattended installation, .xml file to configure the OS all the way down to the installed features. You can generate the file with the Windows Automated Installation Kit, which we won't cover in this chapter.
The Setup program selects the operating system to install, as shown in Figure 3.1.

![](img/41a83208e6906a3732620203b836cea7_141_0.png)

- 1. For Server Core, select the desired edition, Standard or Datacenter, and click Next.

- 2. Accept the license terms and click Next.

The next screen asks which type of installation you want.

- 3. Since you are doing a clean install, select Custom.

The next screen, “Where do you want to install Windows?” as shown in Figure 3.2.

# Figure 3.2
Choosing the installation partition

![](img/41a83208e6906a3732620203b836cea7_142_0.png)

We prefer dividing the drive into two partitions: 50 GB for the operating system and the remainder for data or applications. The tricky part of this is projecting the right size. Additional updates, service packs, security updates, and patches can drive the overall size to the capacity of the small partition. This can cause system instability and potentially require a rebuild.

- 4. Using the options on the bottom of the screen, click New to create the 50 GB partition.

Windows Setup also created the 350 MB system partition. This holds the recovery operating system. You can’t delete this partition. Don't worry about this unavailable space; thumb drives come in bigger sizes now.

- 5. After a successful installation, use the Administrator account to log on as with a full installation.

- 6. There is no assigned password, so enter a new one.

Once the installation finishes the administrator’s profile, the desktop appears, as shown in Figure 3.3, which looks very spartan. There’s no Server Manager, no taskbar, no system tray—no nuttin’. There’s just an open command prompt.
