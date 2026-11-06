
Where this becomes important is where, for example, you make an error in the definition of an attribute. In Windows 2000, the best you can do is deactivate the attribute with the incorrect syntax and create a new one with a different name. If you have an application that requires a certain attribute name, there’s little you can do but operate with the incorrect definition, get by without it altogether, or find a different application. Restoring the schema from a state backup is possible, but risky. Now, with the new functionality of Windows Server 2003, you can deactivate the incorrect attribute and safely create a new one that uses the same object identifier (`OID`) and Lightweight Directory Access Protocol (`LDAP`) display name as the old one, but with the correct syntax.

Another case is when an object identifier collision occurs. This is where a needed `OID` conflicts with an existing one, a situation usually created by mistyping a number. By deactivating the first `OID`, the second can be created. There are several situations in which classes and attributes cannot be deactivated, and it is an operation that should always be performed with great care and planning.

## Domain Rename
This is a complex and sweeping modification to the namespace of a domain. `DNS` names, and `NetBIOS` names of any child, parent, or forest-root domain can now be changed. As far as Windows Server 2003 Active Directory is concerned, the identity of a domain rests in its domain Globally Unique Identifier (`GUID`), and its domain `SID`. Creating new `DNS` or `NetBIOS` names will leave those attributes unchanged. The domain rename function is not able to promote a domain to the forest root role. Even if you rename the forest root domain, its role will remain unchanged.

The renaming process will temporarily interrupt the functionality of the domain and its interaction with the forest, until the `DC`s are rebooted. Client workstations will not function properly until they are each rebooted twice. Due to the complexity of the operation, the risks of such a sweeping change, and the unavoidable domain and workstation service interruptions, domain renaming should not be considered a routine operation.

## Forest Restructuring
Existing domains can now be moved to other locations within the namespace. During this restructuring, you will manually break and reestablish the appropriate trust relationships among the domains. A requirement for namespace changes, or a need to decrease administrative overhead, typically drives forest restructuring. This reduction in overhead is accomplished by reducing replication traffic, reducing the amount of user and group administration required, and simplifying the administration of Group Policy. The smallest possible number of domains will provide the most efficient design. Minimizing the number of domains reduces administrative costs and increases the efficiency of your organization. Reasons to restructure include:
■ Decommissioning a domain that is no longer needed
■ Changing the internal namespace
■ Upgrading your network infrastructure to increase your bandwidth and replication capacity, which enables you to combine domains

Before you begin restructuring Windows Server 2003 domains within your forest, make sure that the forest is operating at the Windows Server 2003 functional level.

## Universal Group Caching
Before Windows Server 2003, some sites had to make a decision to deploy a Global Catalog (`GC`) at each remote site regardless of the number of users at that location, because each `DC` contacts a `GC` server during a Windows 2000 native mode logon. The problem was that a `GC` generated a lot of replication traffic and required a lot of disk space, memory, and WAN bandwidth. The solution in Windows Server 2003 is Universal Group caching.

Universal Group caching is a new feature of the Windows Server 2003 `DC`, which caches a user’s complete Universal Group membership. The cache is populated at first logon, and subsequent logons use the cache, which is refreshed periodically.

Some of the benefits of Universal Group caching include faster logon times. Authenticating `DC`s no longer have to consult a `GC` to get Universal Group membership information. In addition, you can save the cost of upgrading a server to handle the extra load for hosting the `GC`. Finally, network bandwidth is minimized because a `DC` no longer has to handle replication for all of the objects located in the forest.

## Application Partitions
Another `DC` enhancement allows for the creation of application-specific Active Directory partitions, also known as naming contexts. Active Directory stores the information in a hierarchy that can be populated with any type of object except for security principles such as users, groups, and computers. This dynamic body of data can be configured with a replication strategy involving `DC`s across the entire forest, not just a single domain. With application partitions, you can define as many or as few replicas as you want. Site topologies and replication schedules are observed, and the application objects are not replicated to the `GC`. Conveniently, application partitions can leverage `DNS` for location and naming. The Windows Server 2003 Web Edition cannot host application partitions because they do not support the `DC` role.

### New & Noteworthy…
#### Active Directory Application Partitions Can Exist on a Non-DC
Another new type of application partition is the Active Directory in Application Mode (`ADAM`) stand-alone product that allows Windows Server 2003 web edition and other member servers and workstations to participate in a form of application partitions without being `DC`s. It is maintained and replicated independent of the central Active Directory, although it interfaces with directory-enabled Kerberos and `NTLM` for authentication services. One advantage with this configuration is that schema changes made to support Web-based applications do not have to clutter up the core operating system’s (`OS`’s) schema. it gives you local control and naming flexibility in addition to the autonomous schema, and can be run on Windows XP or Windows Server 2003. `ADAM` is sometimes referred to as Active Directory “Light.”

`ADAM` runs as a non-`OS` service. This means that multiple instances can run concurrently on a single server, with each instance being independently configurable. It is an extended capability that allows you to deploy Active Directory as a lightweight directory service for the rapid and flexible implementation of directory- enabled applications.

`ADAM` can be particularly helpful in the following areas:
■ Application-specific directories, where you can store “private” directory data relevant only to the application,
■ Application developer activities, where `ADAM` uses the same programming model and administration as Active Directory. This enables the developer to work with a local instance on the developer workstation and then later move the application to Active Directory.
■ Extranet Access Management (`EAM`) solutions, such as hosting user objects that are not Active Directory security principals. This allows you to use `LDAP` to authenticate non-Windows or external users.
■ Migration scenarios, where an organization has an established `X.500` directory that must be maintained to serve legacy applications.

## Install from Backups
The Install from backups feature provides the capability to install a `DC` using backup media rather than populating the Active Directory through a lengthy replication period. This is especially useful for domains that cross-site boundaries using limited WAN connectivity. To do this, back up your directory store using `Windows Backup`, restore the files at the remote site’s candidate `DC`, and run `dcpromo` using the `source replication from files` option. This also works for `GC` servers.

## Active Directory Quotas
