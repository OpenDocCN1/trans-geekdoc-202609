
Another new capability provided in Windows Server 2003 is that DCs can be created from backups. Backups are used to copy data to other media such as tapes, and can be used to restore lost data if problems arise. For example, if the hard disk on a server fails, you can use the backup to restore the data to another disk and have the server up and running again. This same process can be used to restore Active Directory to a new DC, avoiding the need to replicate the entire directory to the DC across the network. Allowing additional DCs to be added to an existing domain through the use of backups reduces the time it takes to set up new DCs on the network.

You can use encryption to protect information that is being transmitted across the network. As previously discussed, `LDAP` can be used over `SSL` to encrypt data and ensure that data isn’t tampered with. This protection prevents unauthorized users from accessing data over the network.

Active Directory allows you to select multiple user objects, so that you can change the attributes of more than one object at a time. After selecting two or more user objects in Active Directory Users and Computers, you can bring up the properties and modify the attributes that are common to each object. This capability makes it faster to manage users, because you don’t have to make changes to each account individually.

Active Directory also provides the capability to drag and drop objects into containers. By selecting an object with your mouse, you can then hold down your left mouse button to drag the object to another location (such as another OU). Releasing the left button drops the object into the container. This capability also makes it easy to add user and group objects to groups. Dragging and dropping a user or group into another group adds it to the group membership.

As we’ll see in the next chapter, a new object class has been added to Active Directory called `InetOrgPerson`. `InetOrgPerson` is a type of object that’s used to represent users in non-Microsoft directory services, and used just as a user object. The presence of this type of class is important when directory information is migrated to Active Directory from these directories.

To prevent users, computers, and groups from creating an unlimited number of objects in Active Directory, Windows Server 2003 has added quotas. Active Directory quotas are used to limit how many objects are owned in a particular directory partition. While quotas can be applied to almost every user, computer, and group, Domain Administrators and Enterprise Administrators are exempted from these limits.

The quotas that are used to limit the ability of a user, computer, or group from creating too many objects in Active Directory should not be confused with disk quotas, which are also available on Windows Server 2003 servers (regardless of the functionality level being used). Disk quotas can be used to limit the amount of hard disk space that can be used on a volume that’s formatted in `NTFS`. The `NTFS` file system is more advanced than other file systems such as `FAT` or `FAT32`, which can also be used to format volumes. By using disk quotas on an `NTFS` volume, administrators can prevent users from filling up the hard disk with an unlimited number of files.

Finally, searching for objects in Active Directory is easier and more efficient in Windows Server 2003. Active Directory uses object-orientated searches to minimize network traffic, and provides the capability to save queries so that they can be reused repeatedly. The capability to save commonly used queries in Active Directory Users and Computers is a topic we’ll look at in detail in [Chapter 2](#B9781931836944500088.xhtml).

## New Features Available Only with Windows Server 2003 Domain/Forest Functionality

When the domain or forest functional levels have been raised so that all DCs are running Windows Server 2003, a number of new features become enabled. These features allow you to modify elements of both your domain and forest, and provide advanced functions that aren’t available until functionality levels are raised. In the paragraphs that follow, we will look at the new features available in Active Directory when all DCs have been upgraded to Windows Server 2003, and the functionality has been raised to Windows 2003.

### Domain Controller Renaming Tool

The DC renaming tool allows you to rename a DC without having to demote it first. This can be useful when you need to restructure the network, or simply want to use a more meaningful name for a particular DC. When this tool is used, the DC name changes, and any Active Directory and DNS entries are automatically updated.

### Domain Rename Utility

Domains can also be renamed. Using the domain rename utility (`rendom.exe`), you can change the NetBIOS and DNS names of a domain, including any child, parent, domain-tree, or forest root domains (from which all others branch off in the hierarchy). By renaming domains in this manner, you can thereby move them in the hierarchy. For example, you can change the name of [dev.web.syngress.com](http://www.dev.web.syngress.com) to [dev.syngress.com](http://www.dev.syngress.com), making the [web.syngress.com](http://www.web.syngress.com) and [dev.syngress.com](http://www.dev.syngress.com) domains on the same level of the hierarchy. You could even rename the domain so that it becomes part of a completely different domain tree. The only domain that you can’t reposition in this manner is the forest root domain.

### Forest Trusts

As we saw earlier, forest trusts can also be created, so that a two-way transitive trust relationship exists between two different forests. In creating such a trust, the users and computers in each forest are able to access what’s in both forests. This expands the network, so users are able to use services and resources in both forests.

### Dynamically Links Auxiliary Classes

Additional features have also been added to the schema. Windows Server 2003 supports dynamically linked auxiliary classes, which allow additional attributes to be added to individual objects. For example, you can have an auxiliary class that has attributes that are used for the Accounting department, and others that are useful for the Sales department. By applying the auxiliary classes to the objects, only those objects are affected. Rather than adding attributes to an entire class of objects, dynamically linking auxiliary classes allows you to apply additional attributes to a selection of objects.

### Disabling Classes

Because certain objects in Active Directory might no longer be needed after a specific point, you can disable classes and attributes that are no longer needed in the schema. Classes and attributes can be disabled, but cannot be deleted. If schema objects are not longer required, you can deactivate them, and reactivate them later if the situation changes.

### Replication

Improvements have also been made in how Active Directory replicates directory data. Rather than having the entire group membership replicated as a single unit, individual members of groups can now be replicated to other DCs. In addition, changes have been made to GC replication. When there is an extension of a partial attribute set, only the attributes that have been added are replicated. These improvements decrease the amount of network traffic caused by replication because less data is transmitted across the network.

### Exercise 1.05

#### Raising Domain and Forest Functionality

This exercise should not be performed on a production network. It assumes that all DCs in the domain are running Windows Server 2003. After raising the functional levels, you will not be able to roll back to a previous level.

1. From the Windows Start menu, select Administrative Tools, and then click the Active Directory Domains and Trusts menu item.

2. When Active Directory Domains and Trusts opens, expand the Active Directory Domains and Trusts node, and select your domain.
