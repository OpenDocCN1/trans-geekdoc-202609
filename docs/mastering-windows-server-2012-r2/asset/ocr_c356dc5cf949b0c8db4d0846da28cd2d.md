# Chapter 25

# # Migrating, Merging, and Modifying Your Active Directory

Active Directory has become the default and most common authentication and directory service in most major organizations. Active Directory controls access to servers, computers, file and printer resources, email, databases, and applications throughout organizations.

Microsoft first released Active Directory with Windows 2000. It has had over a decade of Active Directory to become an essential part of business operations, information technology and infrastructure. Windows Server 2012 is the fifth major release of Active Directory's design doesn't support mergers, acquisitions, or spin-offs. In other words, you cannot add a domain or take away an existing domain from a forest. Separating or adding business operations will impact the Active Directory environment, forcing you to manually merge users, computers, and data while maintaining business continuity. It's important to intelligently understand these operations to make decisions within management.

Since Windows 2008, the upgrade path has provided solid updates to the Active Directory functions. Microsoft spent the majority of the development cycles for Windows Server 2012 Active Directory advancing existing product features. For example, the Active Directory Recycle Bin has been a GUI. While it was available only through PowerShell. Also, group Managed Service Accounts (gMSA) expands the Windows 2008 R2 feature to include support of Managed Service Accounts in things like clustering and load balancers.

Simple changes to the interface and performance tuning are always welcome, and I think you will like the refresh of basic items. Once you have upgraded your domain controller (DC), you can clone it with Hyper-V for safe restore.

In this chapter, you will learn to:

+   * Introduce new versions of Active Directory into a network
* Migrate accounts from one domain to another

# ## Upgrade and Migration Strategies

So far we've been talking like you were creating a new network where none existed before, but that's not likely these days. Instead, it's more likely that you already have an Active Directory domain and you want to move to a Windows Server 2012-based Active Directory domain. Either way, that kind of work falls under the topic of *migration.*