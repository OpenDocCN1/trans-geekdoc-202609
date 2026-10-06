
# XXX CONTENTS

- Creating an Active Directory Snapshot ................................................................... 1573
- Mounting an Active Directory Snapshot ........................................................................ 1574
- Working with Mounted Active Directory Snapshots ................................................ 1574
- Backing Up and Restoring Active Directory ................................................................ 1576
- Introducing the Active Directory Recycle Bin ................................................................... 1577
- Creating an Active Directory Backup ........................................................................ 1579
- Restoring an Active Directory Backup ....................................................................... 1580
- Performing an Authoritative Restore ........................................................................ 1582
- The Bottom Line ............................................................................................................ 1583

# Appendix • The Bottom Line ................................................................................... 1585

- Chapter 2: Installing and Upgrading to Windows Server 2012 ........................ 1585
- Chapter 3: Introduction to Server Core ..................................................................... 1586
- Chapter 4: Windows Server 2012 R2 Networking Enhancements ................................ 1587
- Chapter 5: IP Address Management and DHCP Failover ................................................... 1589
- Chapter 6: DNS and Name Resolution in Windows Server 2012 R2 ................................. 1591
- Chapter 7: Active Directory in Windows Server 2012 ................................................ 1592
- Chapter 8: Creating and Managing User Accounts ....................................................... 1593
- Chapter 9: Group Policy: AD Gauntlet and Active Directory Delegation .......................... 1597
- Chapter 10: Active Directory Federation Services ................................................... 1599
- Chapter 11: Shared Storage and Clustering Introduction ............................................ 1600
- Chapter 12: Windows 2012 R2 Storage: Storage Spaces, Snapabilities, and Better Tools ................................................................................................ 1600
- Chapter 13: Files, Folders, and Basic Shares ...................................................... 1602
- Chapter 14: Creating and Managing Shared Folders ................................................ 1603
- Chapter 15: Dynamic Access Control: File Shares, Reimagined ................. 1605
- Chapter 16: Sharing Printers on Windows Server 2012 R2 Networks ........................ 1606
- Chapter 17: Remote Server Administration ................................................... 1607
- Chapter 18: Connecting Windows and Mac Clients ....................................................... 1608
- Chapter 19: Web Server Management with IIS ...................................................... 1611
- Chapter 20: Advanced IP: Routing with Windows ....................................................... 1612
- Chapter 21: Getting from the Office to the Road: VPNs ................................................ 1614
- Chapter 22: Adding Locations: Sites in Active Directory ...................................... 1614
- Chapter 23: The Third DC: Understanding Read-Only Controllers .............. 1616
- Chapter 24: Creating Large Active Directory Environments: Beyond One Domain 1617
- Chapter 25: Migrating, Merging, and Modifying Your Active Directory ................... 1619
- Chapter 26: Advanced User Account Management and User Support .......................... 1620
- Chapter 27: Server Virtualization with Hyper-V ................................................. 1621
- Chapter 28: Managing Virtual Machines ................................................... 1623
- Chapter 29: Installing, Using, and Administering Remote Desktop Services .... 1624
- Chapter 30: Monitoring Windows Server 2012 R2 ............................................ 1625
- Chapter 31: Patch Management ................................................................................... 1627
- Chapter 32: Windows Server 2012 R2 and Active Directory Backup and Maintenance ........................................................................................................ 1628

Index ............................................................................................................................ 1631

# Introduction

Welcome to this book on Windows Server 2012 R2. All of the enhancements and new features that this latest release of Microsoft's flagship enterprise operating system have definitely raised the bar for future versions of Windows Server. To give you an insight into how extra you get with 2012 R2, you only have to look at the original Windows Server 2012 release that reached general availability in September 2012. Shortly after that hit the shelves, Sybox got this group of authors together to write a book on it, but just as we were coming to the final edits of our chapters, Microsoft announced that Windows Server 2012 R2 to be released in October 2013—that's just 12 months after the original version of Windows Server 2012. In short period of time, the amount of new functionality that was packed into Server 2012 R2 that we literally had to rewrite nearly half of the original Server 2012 book it!

The team of authors who have worked on this book have an abundance of experience designing, deploying, and troubleshooting Windows Server in large-scale enterprise environments, and we're really excited to tell you all about this version of the product.

If you're new to Windows Server, then this book will strive to give you the knowledge to go out and start working with it straight away. If you're an experienced administrator or consultant you are already familiar with it, don't worry; we definitely have loads of new information in here for you to learn to help you get ahead of the pack.

# Who Should Read This Book?

Like every other book in the Mastering Windows Server series, we've aimed this book at people who know how to install, configure, maintain, and troubleshoot a Windows Server environment. We assume that you already have a basic understanding of TCP/IP networking and that basic working level of comfort with previous versions of the Windows GUI and Microsoft Management Console (MMC) in particular.

As complex software products are becoming, no one can be an expert on all of them. If you have time to manage it effectively, there is probably a lot more that you could be doing with any one product. This book will get you up to speed quickly and then help you through some of the more arcane topics.

Not every administrator will have the same type of infrastructure to work with. What works well in a large corporation does not always work for small companies. What works for small companies may not scale well for large organizations. Microsoft has attempted to address the differences among companies and deliver a product that can be implemented quickly for a small company yet still scale well for large organizations. No matter what scenario hits you, you will want to learn how this product will work for you.

# What's Inside?

Chapter 1 starts out with an overview of what's new in Windows 2012 R2, and Chapter 2 shows you how to install it. Chapter 3 introduces you to Server Core, and Chapter 4 looks at networking enhancements in Windows 2012 R2, and Chapter 5 introduces you to new functionality around DHCP. Chapter 6 shows you how to build DNS, and Chapter 7 is the first chapter to address Active Directory: one that contains just domain. Speaking of AD, Chapter 8 shows you to create and manage user accounts. Once you have a working AD in place, then its time to get payback from all your design, and the tool for that is Group Policy. Chapter 10 covers Active Directory Federation Services, which is a way to provide single sign-on to your resources.

Chapter 11 and Chapter 12 introduce you to shared storage and clustering, which are the pillar components of delivering highly available infrastructure, along with an introduction to the new capabilities of 2012 R2 using Storage Spaces. Chapter 13 introduce you to a three-part series on sharing folders and files using Windows' security to control who can get to particular files. You will then be walked through Dynamic Access Control, which is a new way of controlling and auditing your file share access. Many servers will not only share files but printers, and Chapter 16 shows you how to accomplish this.

Following that, Chapter 17 shows you how to maintain and control your servers remotely using a number of built-in technologies, including Remote Desktop. Now, you have working servers (which is nice) but clients to use those services (which makes the whole thing sort of), so Chapter 18 shows you how to hook up the various varieties of Windows created in the past to a Windows Server 2012 R2 network. That's say? You've got a Mac? No problem, you'll learn to connect to that.

Chapter 19 gets you up and running with one of Windows' most complex server add-ons, Microsoft's Internet Information Services (IIS), better known as the web server. You will learn how to get IIS running, how to set up a simple website, and how to find your way around the IIS management tools built into Server 2012 R2.

Chapter 20 discusses how a Server 2012 system can facilitate IP routing, which sound like an odd topic until you need to understand a bit of IP routing on a Windows Server before you can tackle Chapter 21, which shows you how to use your Server.
