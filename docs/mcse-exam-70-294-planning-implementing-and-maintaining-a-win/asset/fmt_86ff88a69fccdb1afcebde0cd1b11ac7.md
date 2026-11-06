
The other reason why two types of groups are used is for performance. When security groups are used, the `SID` of that group is added to the access token of its members when they log on. The more security groups a user belongs to, the longer it will take to log on. Each security group that’s added to the access token increases the token’s size, making the logon and subsequent resource access slower and more resource intensive. When distribution groups are used, there is no `SID` for the group, so the number of distribution groups a user is a member of has no effect on the token’s size. Because of these issues, it is always better to use distribution groups for e-mail needs, and security groups for collections of people who need access.

## Group Scopes in Active Directory

Scope is the range that a group will extend over a domain, tree, and forest. The scope is used to determine the level of security that will apply to a group, which users can be added to its membership, and the resources that they will have permission to access. As we’ll discuss in the sections that follow, Active Directory provides three different scopes for groups:

■ Universal
■ Global
■ Domain Local

### Universal

Universal groups have the widest scope of any of the different group scopes. Members of this group are able to contain accounts and groups from any domain in the forest, and can be assigned permissions to resources in any domain in the forest. In other words, it is all encompassing within any part of the forest.

Whether a universal security group can be used depends on the functional level that the domain has been set to. Domains that have the functional level set to Windows 2000 mixed won’t allow universal security groups to be created. However, if the domain functional level is Windows 2000 native or Windows Server 2003, then universal security groups can be created. In this situation, the group can contain user accounts, global groups, and universal groups from any domain in the forest, and be assigned permissions to resources in any domain. Universal distribution groups can be used at any functional level, including Windows 2000 mixed.

Universal groups can be converted to groups with a lesser scope. Providing the group doesn’t contain any universal groups as members, a universal group can be converted to a global group or a domain local group. If universal groups are members of the universal group that’s being converted, you won’t be able to perform the conversion until these members are removed.

![note](images/note.jpg)Note

Universal groups are stored in the `GC`, along with their membership lists, Because of this, any change in membership triggers forestwide replication. To limit the impact of this type of replication, Microsoft recommends using relatively static members (such as global groups) in these groups.

### Global

Global groups have a narrower scope than universal groups. A global group can contain accounts and groups from the domain in which it is created, and be assigned permissions to resources in any domain in a tree or forest. Because it only applies to the domain in which it’s created, this type of group is commonly used to organize accounts that have similar access requirements.

As we saw with universal groups, however, the members that can be part of a global group depend on the domain functional level. If the functional level of the domain is set to Windows 2000 mixed, then the membership of a global group can only consist of user accounts from the same domain. If the functional level of the domain is set to Windows 2000 native or Windows Server 2003, then the global group can have user accounts and other global groups from the same domain as members. User accounts and global groups from other domains cannot become members of a global group.

Global groups can also be converted into a universal group, provided that the global group isn’t a member of any other global groups. If other global groups are members of the global group, then these must be removed before the conversion can take place. The domain functional level must be Windows 2000 native or Windows Server 2003 to convert to a universal security group.

### Domain Local

Domain local groups also have a scope that extends to the local domain, and are used to assign permissions to local resources. The difference between domain local and global groups is that user accounts, global groups, and universal groups from any domain can be added to a domain local group. Because of its limited scope, however, members can only be assigned permissions within the domain in which this group is created.

As you might expect from the two previous scopes, the abilities of a domain local group depends on the domain functional level. If the functional level is set to Windows 2000 mixed, then the domain local group can only contain user accounts and global groups from any domain. It cannot contain universal groups when Windows Server 2003 is using this level of functionality. If the functional level is set to Windows 2000 native or Windows Server 2003, then the domain local group can contain user accounts and global groups from any domain, as well as universal groups. In addition, it can contain other domain local groups from the same domain. These abilities, however, have no impact on permissions. In all cases, permissions can only be assigned to resources in the local domain.

Domain local groups can be converted to a universal group, provided that there are no other domain local groups in its membership. If the domain local group does have other domain local groups as members, then these must be removed from the membership before a conversion is made.

## Built-In Group Accounts

As we saw when we discussed user objects, a number of built-in accounts are automatically created when you install Active Directory. This not only applies to user accounts, but group accounts as well. Many of these groups have preconfigured rights, which allow members to perform specific tasks. When users are added to these groups, they are given these rights in addition to any assigned permissions to access resources.

The groups that are created when Active Directory is installed can be accessed through `Active Directory Users and Computers`, and are located in two containers: `Builtin` and `Users`. Although they are stored in these containers, they can be moved to other `OU`s within the domain. Those in the Built-in container have a domain local scope, while those in the `Users` container have either a domain local, global, or universal scope. In the paragraphs that follow, we will look at the individual groups located in each of these containers, and see what rights they have to perform network-related tasks.

### Default Groups in Builtin Container

Up to 14 different built-in groups that might be located by default in the `Builtin` container, including:

■ Account Operators, which allows members to manage accounts
■ Administrators, which gives members full control
■ Backup Operators, which allows members to back up and restore files
■ Guests, which gives members minimal access
■ Incoming Forest Trust Builders, which is only available in forest root domains, and gives members permission to Create Inbound Forest Trusts
■ Network Configuration Operators, which allows members to manage network settings
■ Performance Monitor Users, which allows users to manage performance counters and use System Monitor
■ Performance Log Users, which allows users to manage performance counters and use Performance Logs and Alerts
■ Pre-Windows 2000 Compatible Access, which is used for backward compatibility.
■ Print Operators, which allows members to manage printers
■ Remote Desktop Users, which allows members to connect to servers using Remote Desktop
■ Replicator, which is used for replication purposes
■ Server Operators, which allows members to manage servers
■ Users, which contains every user account created in the domain
