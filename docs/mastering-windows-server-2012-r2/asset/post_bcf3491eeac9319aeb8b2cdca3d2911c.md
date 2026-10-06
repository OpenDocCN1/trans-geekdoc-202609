
# VERSION INCOMPATIBILITY

At the time of this writing, ADMT 3.2 is the latest version for this tool. However, it is only compatible with Windows Server 2008 R2. When you try to install the Active Directory Migration Tool (ADMT) 3.2 on a Windows Server 2012 server, you receive the following error: "Active Directory Migration Tool v3.1 must be installed on Windows Server 2008." ADMT 3.2 and PES 3.1 are not supported for installation on Windows Server 2012. The installers intentionally block unsupported operating systems. There is a Knowledge Base article about this problem:

> http://microsoft.com/kb/275368/en-us

What would be the recommended solution? Install ADMT 3.2 onto a Windows Server 2008 R2 in the target domain. To have a supported scenario you also need to install a Windows Server 2008 R2 as target controller in the new domain.

But what happens if you already promoted a Windows Server 2012 forest functional level? Well, luckily you can lower the forest and domain functional levels to Windows Server 2008 R2 using PowerShell commands.

First, you need to lower the forest functional level by executing:

```
Set-ADForestMode -identity bigfirm.com -forestmodeWindows2008R2Forest
```

Next, you need to confirm your input and wait a few seconds for the command to successfully finish.

```
Set-ADDomainMode -identity bigfirm.com -domainmodeWindows2008R2Domain
```

If you're already using Dynamic Access Control, you will not be able to use this feature because Windows Server forest functional level 2012 is required.

# An Example Migration Setup

To provide a basic run-through of this, we'll use this example: Bigfirm. OtherDomain is a Windows Server 2003 Active Directory domain. Bigfirm has purchased a clean-and-pristine Bigfirm.com for consolidating its domains into one. Microsoft has not published any ADMT for Windows Server 2012, therefore for compatibility Bigfirm also has a Windows 2008 R2 domain controller installed just for targeting with ADMT. After the migration, OtherDomain will decommission this domain controller. The forest functional level is set to Windows Server 2008 R2. The ADMT will also be installed onto a Windows 2008 R2 server named ADMT01.

The administration department needs to be migrated from OtherDomain's Windows Server 2003 administration. The administration department shares a workstation (they don't get a lot of work done), and their user folders are located on the domain controller named DC2003. During the migration, the department members will need to access their home folders and log onto their workstation until these are migrated to the new domain too. In this example, we'll cover

- How to migrate user accounts and groups across two forests.
- How SID allowed the migrated user to access resources on the old domain whose ACLs have not been changed.

# USING MICROSOFT'S FREE MIGRATION TOOL: ADMT 3.4

- How ADMT can re-ACL the workstation in the old resource domain. This will also sign the local profiles of the users to their new accounts.
- How ADMT can migrate member servers from the old domain to the new AD domain.

To make this work, we'll set up five systems—two in OtherDomain.local and three in Bigfirm.com. The two in OtherDomain.local are as follows. We'll set up a DC for OtherDomain.local named DC2003. On DC2003, we'll create the following:

- A shared folder named Users with Everyone assigned Full Control permissions. The Active Directory Users and Computers snap-in will configure the NTFS permissions for specific user accounts.
- An organizational unit named Administration.
- Domain user accounts for those dependable Administration people.
- A home folder mapped to the Z: drive with the UNC path of \DC2003\users\username%.
- A global group named Administration Group and its members.
- A shared folder named Administration with the Administration Group assigned Full Control permissions.
- A Windows 7 client Win7 that needs to be migrated to the Bigfirm.domain.

The Bigfirm.domain will contain three systems:
- A clean Windows Server 2008 R2 domain controller, which is being used for ADMT as a target.
- A temporary Windows Server 2008 R2 domain controller, Its name is W2K8DC.
- A Windows Server 2008 R2 member server of the domain where ADMT is installed, server is called ADMT01.

To visualize the scenario see Figure 7.51:

# FIGURE 7.51
Migration scenario

![](img/41a83208e6906a3732620203b836cea7_384_0.png)

# Establishing the Trust

Next, we'll establish the trust between the two domains. The quickest method for this example is using the Active Directory Domains and Trusts console (domain.msc). Use the New Trust Wizard for the following:

- 1. Specify the type of trust. An external trust is simple and effective for this procedure.
- 2. Specify a two-way trust. Accounts from each domain will need to access the other's resources.
- 3. Create the trusts on the other domain. This will require admin credentials for that domain.
- 4. Validate the trust to make sure things are working fine—is the trust working, and are the permissions correct on DC2003? Since users and global groups from any domain can be members of local groups and server local groups, we attempt to add a user from the opposite domain to a built-in group on the domain controller. This is a required step down the road. So, search and add the Bigfirm\Administrator to Administrators group of OtherDomain in Active Directory Users and Computers.

But adding users to is not what we really want. We want the migrated accounts to be able to access resources in the opposite domain. This is where SID history comes into play. As stated, the SID history is treated as another group on the security token that will be passed to the resource domain for access to the migrated accounts'. If you weren't paying attention to the New Trust Wizard and clicking every Next and OK like a mind-numbing automaton, you might have missed the window shown in Figure 7.52.

SID filtering warning

![](img/41a83208e6906a3732620203b836cea7_385_0.png)

What is SID filtering? SID history can be exploited by an evil hacker in an elevated privilege attack. He could construct a security token with an SID of a domain administrator within the trusting resource domain. Since the SID is recognized as a domain administrator, his account would have the same level of access. SID filtering strips any SIDs that do not originate from the trusted user domain. Our users' security tokens wouldn't buy a gumball in the source domain with SID filtering enabled because the SID history value would be stripped off. So, following the useful hyperlink "Securing external trusts" in the window, we can learn the net command to disable and enable SID filtering for migrations as these.

# USING MICROSOFT'S FREE MIGRATION TOOL: ADMT 3.5

The netdom.command comes installed with Windows Server 2012, but earlier versions had it available in the Support Tools. Microsoft released a later version of Support Tools after Windows Server 2003 Service Pack 2, so be sure to search its site for the latest version.

The following commands are run to deduce SID filtering. The /quarantine:no parameter does the trick. You should be able to deduce how SID filtering will be enabled:

```
Rem performed on dc01.bigfirm.com
netdom trust otherdomain /quarantine:no
user:administrator /password:Pssword
```

```
Rem performed on DC2003.OtherDomain.local
netdom trust bigfirm /quarantine:no
user:administrator /password:Pssword
```

# Getting Both Sides ADMT-friendly

ADMT can be an absolutely frustrating nightmare of a program because of its needs. A program that takes information is fairly private and internal to a domain—user accounts and passwords—and reveals it to a different domain. Before ADMT can do that, you'll have to open a number of locked doors. The following is what you have to do.

# PUTTING A DOMAIN IN EACH'S ADMINISTRATORS GROUPS

The ADMT utility needs an account that is both a member of the Domain Admins group in the target domain, Bigfirm.com, and a member of local Administrators groups of servers and workstations in the source domain, OtherDomain.local. This will allow ADMT utility to perform changes to permissions, user rights, and other nifty stuff that powerful administrators have the privileges to do. In this example, we created an account with the name of ADMT in Bigfirm.com and assigned it to the Domain Admins group. Using the trust relation between the two domains, it was also assigned to the built-in Administrators group in OtherDomain.local and the local Administrators group on Win7-bigfirm.com.

On the source domain, OtherDomain.local, a similar requirement is needed for the Password Encryption Service (PES). This is an additional service that will read the password of migrating account, and store it with its properties. It needs to be a member of the Domain Admins group in the source domain, OtherDomain.local, and a member of the built-in Administrators group in the target domain, Bigfirm.com. Over at Bigfirm.com, we created an account with an equally imaginative name, PES, in OtherDomain.local.

# TURNING ON AUDITING

ADMT has some tricky auditing, preferably so that it can monitor how it's doing. The source domain—the one that are being copied from, OtherDomain.local—needs both success and failure audits for user and group management.

On the target and source machines (W2K8DC.Bigfirm.com and DC2003.OtherDomain.local), we enable auditing by modifying a group policy called Default Domain Controller Policies. In a
