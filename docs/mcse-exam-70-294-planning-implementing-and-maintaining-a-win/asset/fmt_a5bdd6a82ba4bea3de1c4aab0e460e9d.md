
# Active Directory Data Store Impact

The presence of Active Directory’s data store on a Windows Server 2003 server has a major impact on that server’s role in the network. As shown in [Figure 1.1](#B9781931836944500076.xhtml#f0010), the directory is stored on DCs, which are servers with writable copies of the data store. A DC is used to manage domains, which are groups of computers, users, and other objects that share (or are included in) the same directory. Domains that use different Active Directory data sources can still communicate with one another, but (as we’ll see later in this chapter) secure relationships between them must be configured.

![Figure 1.1 Relationship Between Active Directory, Domain Controllers, Member Servers, and Clients](images/B9781931836944500076/f01-01-9781931836944.jpg)

Figure 1.1 Relationship Between Active Directory, Domain Controllers, Member Servers, and Clients

Each DC retains its own copy of the directory, containing information on the domain in which it is located. If one DC becomes unavailable, users and computers can still access the Active Directory data store on another DC in that domain. This allows users to continue logging on to the network even though the DC that’s normally used is unavailable. It also allows computers and applications that require directory information to continue functioning while one of these servers is down.

Because a domain can have more than one DC, changes made to the directory on one DC must be updated on others. The process of copying these updates is called replication, and is used to synchronize information in the directory. Without replication, features in Active Directory would fail to function properly. For example, if you added a user on one DC, the new account would be added to the directory store on that server. This would allow the user to log on to that domain controller, but he or she still couldn’t log on to other DCs until these changes to the directory were replicated. When a change is made on one DC, the changes need to be replicated quickly so that each DC continues to have an accurate duplicate copy of Active Directory.

## Directory Partitions and Replication Efficiency

Because replication is so important to making the directory consistent across the network, the data source is organized in a way to make replication more efficient. Not every piece of data is saved in the same location of the data source. As shown in [Figure 1.2](#B9781931836944500076.xhtml#f0015), information resides in different areas of the directory, called directory partitions. Because Active Directory is a logical, hierarchical structure, it has a treelike structure similar to that of the Windows Registry or folders on a hard disk. Data is stored within subtrees of the directory, much like data on your hard disk is stored within folders that are nested within one another. Each contiguous subtree in the directory is a partition. Any data that changes within a directory partition is replicated as a single unit to other DCs.

![Figure 1.2 Active Directory Is a Hierarchical Structure](images/B9781931836944500076/f01-02-9781931836944.jpg)

Figure 1.2 Active Directory Is a Hierarchical Structure

In Active Directory, three partitions exist on any DC and must be replicated, as these contain data that the Microsoft network needs to function properly:

![Squareb](images/Squareb.png) Domain partition

![Squareb](images/Squareb.png) Configuration partition

![Squareb](images/Squareb.png) Schema partition

### Note

Directory partitions shouldn’t be confused with disk partitions. Disk partitions are used to logically separate the hard disk so that multiple operating systems can run from a single hard drive, or to make it appear that a single hard disk is actually more than one. For example, if you have a single hard disk on your computer, the `C:` drive, you might partition it into two logical drives, so that the system now has `C:` and `D:` drives. While this is useful for organizing files stored on the hard disk, it is unrelated to how Active Directory is partitioned.

A directory is physically a database where information is stored within a table, and logically, a naming hierarchy made up of containers and objects. Information is partitioned in this manner to allow data to be stored in different areas. As we’ll see in the paragraphs that follow, these partitions consist of containers storing domain, configuration, schema, and application information.

## Domain Partition

The domain partition contains information about the domain. This includes information about users, computers, resources, and attributes associated with each. Without this data being replicated, any changes would be limited to the server on which the changes were made, and other servers would use older settings. For example, if the domain data wasn’t replicated and you disabled a user’s account on one DC, the user would still be able to log on to other DCs. The domain partition is important because it contains information about objects and their attributes, which are fundamental elements of your network.

## Configuration Partition

Configuration data deals with the topology of Active Directory, and includes information about how the domains, domain trees, and forests within a network are configured. A domain tree is a structure of domains. If more than one domain is in a domain tree, trusts are set up between those domains so that they can share data and resources between them. A forest also consists of multiple domains that share directory data. It consists of one or more trees that are connected through trusts. The configuration partition also includes information about the locations of DCs and the GC, which is a subset of the data contained in Active Directory that is used to provide search and logon functionality across multiple domains. We discuss each of these topics in greater detail later in this chapter.

## Schema Partition

Because Active Directory is made up of different objects, and each object has specific attributes, certain rules must be created to control what objects can exist in the directory, and the attributes of each. For example, a user account has attributes that include a password, an account name, and the first and last of the person to whom the account belongs. The types of objects that exist in Active Directory, and which attributes each type has, is determined by the schema. The schema partition contains information that defines object classes and attributes used within the domain. It determines what objects can exist within Active Directory, and what attributes each can have.

## Application Partitions

Windows Server 2003 servers can also create one or more application partitions, which are used to store data that is specific to different applications running on the network. Programs can use this partition to store settings that are needed while the programs are running on a server. We discuss this in greater detail later in the chapter.

## Configuring & Implementing: Providing the Best Possible Protection for Your Directory

In addition to Windows 2000 servers, Active Directory can only be installed on Microsoft Windows Server 2003, Standard Edition; Windows Server 2003, Enterprise Edition; and Windows Server 2003, Datacenter Edition. When a server is configured to be a DC on any of these editions, a writable copy of the directory is stored on the server’s hard disk. Because any file can be damaged, destroyed, or compromised (such as in the case of a hacking attempt or virus), you should take steps to ensure that the directory is safe on your server(s).

If only one DC is used, then only one `NTDS.DIT` file will exist, meaning there is only one copy of the directory for that domain. Failure of this server or damage to the `NTDS.DIT` file will disable the network. Users will be unable to log on, computers will be unable to access needed information from the directory, and any configurations on your network could be lost. Rather than hoping that nothing ever happens to your one DC, it is wise to use multiple DCs on your network.
