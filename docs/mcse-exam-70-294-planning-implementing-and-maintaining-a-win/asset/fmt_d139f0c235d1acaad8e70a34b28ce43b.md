
15. You are upgrading your domain to use a mix of Windows 2000 and Windows Server 2003 DCs. After installing the first Windows Server 2003 DC on the domain, you want to raise the domain functional level to the highest level possible. Which of the following will you choose?

A. Windows 2000 mixed

B. Windows 2000 native

C. Windows 2003 interim

D. Windows 2003

☑ B. Windows 2000 native is used for domains with Windows 2000 and Windows Server 2003 DCs. Windows 2000 native removes support for replication to Windows NT BDCs, so these older servers are unable to function as DCs. In this level, only Windows 2000 and Windows Server 2003 DCs can be used in the domain.

![wrong](images/wrong.png) Answer A is incorrect, because Windows 2000 mixed allows domains to contain Windows NT BDCs and interact with Windows 2000 and Windows Server 2003 servers. Because it only provides basic Active Directory features, this isn’t the highest level you could choose. Answer C is incorrect, because Windows 2003 interim is used when your domain consists of Windows NT and Windows Server 2003 DCs. Answer D is incorrect, because the Windows 2003 level is used when there are only Windows Server 2003 DCs in the domain.

## Chapter 2 Working with User, Group, and Computer Accounts

### Understanding Active Directory Security Principal Accounts

1. You create a new user account and assign it permissions to resources. When this account is created, a `SID` is given to the account to uniquely identify it. When the user logs on and attempts to access one of these resources, which of the following will the `SID` be compared to when determining access?

A. Access token

B. `SACL`

C. `DACL`

D. `SID`

☑ C. The discretionary access control list (`DACL`) determines whether a security principal is granted or denied access to a resource. When a user tries to access an object, the user’s `SID` is compared to entries in the `DACL`. If the user’s `SID` or the `SID` of a group he or she belongs to matches an entry in the `DACL`, the user is permitted to use the resource.

![wrong](images/wrong.png) Answer A is incorrect, because an access token is created when the user logs on, and contains information about the user’s name, group affiliation, `SID`, and `SIDs` for the groups of which he or she is a member. The `SIDs` contained in the access token are compared to the `SIDs` listed in the `DACL`. Answer B is incorrect, because the system access control list (`SACL`) is used for auditing access to a resource. The `SACL` contains information on whether logging should be generated on attempts to access a resource. Answer D is incorrect, because `SID` is an acronym for security identifier.

2. A user attempts to access a resource, and entries in the `ACL` are analyzed to match the `SID`. The system examines the entire `ACL`, but no match is found. Which of the following will occur?

A. The user will be denied access.

B. The user will be granted access.

C. The account will be disabled.

D. Each `ACE` in the `ACL` will be read until a match is eventually found.

☑ A. Since no entry is found, the security principal is implicitly denied access. Each `ACE` in the `DACL` is analyzed in sequence to determine a security principal’s access. The `SID` of the user and any groups he or she belongs to is compared to the `ACEs` in the `DACL`. Windows Server 2003 will look at each `ACE` until an entry is found that explicitly denies access to the resource, one or more entries are found that explicitly grants access to the resource, or until the entire `DACL` is searched but no `ACE` is found that explicitly grants or denies access.

![wrong](images/wrong.png) Answer B is incorrect; if no entry is found in the `ACL`, the user is implicitly denied access. If the user was granted access when no entry was found, then anyone who hadn’t been given permission to the resource would have access. Answer C is incorrect, because accounts aren’t disabled when they are denied access to a resource. Answer D is incorrect, because if the `ACL` were reviewed until an `ACE` matching the `SID` was found, it would never stop looking if no match existed.

3. A RID server has temporarily gone offline. During this time, you seize the RID Master role on another DC. After the original RID server becomes available again, you are concerned that duplicate `SIDs` might now exist for objects in Active Directory. Which of the following tools would you use to find and delete duplicates?

A. `Active Directory Users and Computers`

B. `MOVETREE`

C. `WHOAMI`

D. `NTDSUTIL`

☑ D. `NTDSUTIL` is a tool that runs from the command line, and has the ability to manage `SIDs`. Using this tool, you can find security principals with duplicate `SIDs` and delete them.

![wrong](images/wrong.png) Answer A is incorrect, because although `Active Directory Users and Computers` can be used to create and manage security principals, it doesn’t have the functionality to find and remove duplicate `SIDs`. Answer B is incorrect, because `MOVETREE` is used to move objects to other locations in Active Directory. Answer C is incorrect, because `WHOAMI` is used to view information about the user who is currently logged on. While it can view `SIDs` associated with the user, it can’t be used to detect and delete duplicate `SIDs`.

### Working with Active Directory User Accounts

4. You want to use Remote Assistance to help users with problems by connecting to their machine and taking control of it remotely. When this action is performed, which of the following accounts is automatically created and used?

A. `HelpAssistant`

B. `Support_388945a0`

C. `Guest`

D. `InetOrgPerson`

☑ A. The `HelpAssistant` account is automatically created in Active Directory when a Remote Assistance session is established. Remote Assistance allows a user or administrator to connect to the desktop on other users’ machines and assist them by talking them through a problem or taking control of their computer remotely.

![wrong](images/wrong.png) Answer B is incorrect, because the `Support_388945a0` account is used to control access to scripts that use the account. The account allows users who don’t have administrator access on the computer to perform tasks that require this access through signed scripts in Help and Support Services. Answer C is incorrect, because the `Guest` account is used by users who don’t have an account of their own, or want to connect to the network without using their own account. Answer D is incorrect, because `InetOrgPerson` is a class that’s used to define a specific type of user account. It isn’t an actual account that’s used for authentication and accessing resources.

5. Your network consists of an Active Directory domain with DCs running Windows Server 2003 and another network running Novell NetWare. You are preparing to migrate the Novell NetWare network to Windows Server 2003, but want to use an account that will connect the directory services of these two networks together. Which of the following class of user account will you create?

A. `HelpAssistant`

B. `Support_388945a0`

C. `InetOrgPerson`

D. None. A regular user account should be created.

☑ C. `InetOrgPerson` is an object class used to create user accounts. This type of account is used to represent users in non-Microsoft directory services. The `InetOrgPerson` is used to allow applications written for other directories, or when migrating from these directory services to Active Directory.

![wrong](images/wrong.png) Answer A is incorrect, because the `HelpAssistant` is a user account that’s used for Remote Assistance sessions. Answer B is incorrect, because the `Support_388945a0` user account is used to control access to signed scripts. Answer D is incorrect, because regular user accounts aren’t used for this purpose.

6. You are configuring a user account to use Terminal Services. Which of the following tabs on the user’s account would you use to configure this user?

A. General, Address, Organization

B. Terminal Services Profile, Profile, Account

C. Environment, Sessions, Remote Control
