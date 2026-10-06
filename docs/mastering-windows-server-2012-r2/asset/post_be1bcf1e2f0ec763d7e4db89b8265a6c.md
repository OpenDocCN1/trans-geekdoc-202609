
A DNS application partition that can be accessed by all domain controllers in the forest. They must enlist in the replication of the partition before supporting it.

**Manage and troubleshoot DNS resolution for both internal and external names.** Internal and external name resolution relies on the connectivity between DNS servers. Forwarding and root hints are the primary methods to allow DNS servers to send queries between them. Several tools are available to assist troubleshooting and monitoring DNS configurations and performance; %nslookup, PowerShell, and Dcdig.

**Master It** The SRV record registration for domain controllers is performed by the logon service. It is a very complex and demanding task to perform this many. What tests can be performed to verify whether SRV records are correctly registered within a domain?

**Solution** The Dcdig utility tests to verify whether SRV records are available within the specified domain. Dcdig /registry validates the domain controller can perform updates to the domain using DDNS updates.

## Chapter 7: Active Directory in Windows Server 2012

**Create a single-domain forest.** Any Windows Server 2012 server can be promoted to a domain controller to create a single-domain forest. A DC hosts an Active Directory Domain Services.

**Master It** You want to promote a server to a DC and create a single-domain forest. Should you do?

**Solution** Install the Active Directory Domain Services role and then run the Active Directory Domain Services Configuration Wizard. Follow the wizard to create a new forest.

**Add a second DC to the domain.** A single DC represents a potential single point of failure. If it goes down, the domain goes down. Often, administrators will add a second DC to the domain.

**Master It** You want to add a second DC to your domain. What would you do?

**Solution** Install the Active Directory Domain Services role and then run the Active Directory Domain Services Configuration Wizard. Follow the wizard to an existing domain.

**Decide whether to add a global catalog.** A global catalog server hosts a copy of the global catalog. Any domain controller can become a GC, but only the first domain controller is a GC by default.

**Master It** You are promoting a second server to a domain controller in your single-domain forest. Should you make it a GC?

**Solution** Yes. In a single-domain forest, all domain controllers should be global catalog servers. This provides redundancy in the domain without any additional overhead.

**Create accounts.** Any domain needs to host user and computer accounts representing users and computers that access the domain. There are several ways to create user and computer accounts.

**Master It** What are four methods that can be used to create a user account? Two have GUI and the other two command-line tools.

**Solution** The four methods are Active Directory Users and Computers, Active Directory Administrative Center, the DSAdd command-line tool, and PowerShell using the New-ADUser cmdlet.

**Create fine-grained password policies.** Windows Server 2012 introduced the ability to create multiple password policies within a domain by using fine-grained password policies. You can use a fine-grained password policy to assign a different password policy to a user or group within the domain.

**Master It** You want to create a fine-grained password policy for a group of administrators in your network. What should you create and what tool should you use?

**Solution** Create a password-settings object with the Active Directory Administrative Center GUI. You can also apply the PSO to users or groups using Active Directory Users and Computers.

**Understand the Windows Server 2012 functional level.** Each forest functional level has traditionally offered new functionality to Active Directory. For example, the Windows Server 2008 R2 functional level brought support for the Recycle Bin feature.

**Master It** What new feature is offered in the Windows Server 2012 forest functional level?

**Solution** There are no new features in the Windows Server 2012 forest functional level.

**Upgrade your domain to Windows Server 2012.** You currently have a Windows Server 2008 single-forest domain, and you are figuring out how to upgrade this forest. You want to have a Windows Server 2012 forest.

**Master It** What methods for upgrading or migrating your forest make the most sense?

**Solution** You probably want to perform in-place upgrades or a swing migration depending on your flavor. A migration using ADMT probably does not make sense.

## Chapter 8: Creating and Managing User Accounts

**Manage local users and groups.** Local users and groups are stored on a computer and cannot be used to log into or access resources on other computers.

**Master It** You have 25 PCs with 25 users on a workgroup network, in other words, a network with no Active Directory or Windows domain. You are installing two file servers. You want to provide authorized-only access to shared resources on the file servers. How will you do this?

**Solution** You will need to create a user account for each of the 25 users. However, because there is no domain, you will need to create the user account on the users' PCs and on each of the two servers. The username and password will be identical to their PCs and each of the two servers. You can speed the process up by using a scripted option, such as using the `net` command in script.

**Manage users and groups in Active Directory.** Users and groups can be stored in Active Directory. That means administrators can create a single copy of each user and group that is stored in a replicated database and can be used by member computers across the entire Directory forest. You can use Active Directory Users and Computers, the command prompt, PowerShell, and Active Directory Administrative Center to manage users and groups in Windows Server 2012.

**Master It** List the different types of Active Directory group types and scopes. Why would you use each of them?

**Solution** There are two Active Directory group types:

- The *distribution* group type is used to collectively communicate with the group members via a single mail address that is associated with the group.
- The primary purpose of the *security* group type is to manage assigned permissions for a collection of members.

The members of an Active Directory group may be users or other group objects. There are three group scopes:

- A *domain local* group can only be used within the domain that it was created. It can contain user/computer accounts, global groups, and universal groups from any domain in the forest and domain local groups from the same domain.
- The *default* scope when you create a group in Active Directory is the *global* group. A global group can be used by computers within the domain that it is a member of and by other members in the Active Directory forest. It can contain user/computer accounts from the domain that the group is created in.
- The *universal* group is the third and final scope. A universal group is stored on domain controllers that are configured as global catalogs. The universal group is replicated to domains across the entire forest. This allows it to be used by all computers in the forest.

**Manage users and computers in Windows Server 2012.** Local users and groups are stored on a computer and cannot be used to log into or access resources on other computers. The Active Directory module for Windows PowerShell offers a command-line interface and to script repetitive tasks that would consume too much time using an administrative console.

**Master It** You are a domain administrator in a large organization. Your network contains several server files. These files are secured using domain-based security groups.
