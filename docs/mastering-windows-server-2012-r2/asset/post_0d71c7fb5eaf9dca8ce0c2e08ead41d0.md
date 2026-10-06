
Open the Active Directory Domain and Trusts console and make the changes to your FSMO roles in this order:

- 1. Move the RID Master role to your new Windows Server 2012 DC.
- 2. Move the PDC Emulator role.
- 3. Move the Active Infrastructure Master role.

The tabs are in consecutive order on your server, so hopefully this isn't a big surprise. Once you've done this, you should consider doing a manual replication of your domain. It's always a good practice to give each of your domain-wide changes a couple minutes to settle and then manually synchronize them. Depending on how many domain controllers you have, this process can take some time when you take speed and into consideration.

After you have changed and synchronized your domain, you can use the Active Domains and Trusts console to change your current domain controller to the Windows Server 2012 domain controller; this might just be verification because it may already be utilizing that, but you want to make sure. Now you will want to switch the Domain Naming Master role to the Windows Server 2012 domain controller.

## CHANGING THE SCHEMA MASTER ROLE

The Schema Master role is held by one of the domain controllers and will do all updates and modifications to the Active Directory schema. The schema is the part of Active Directory that defines all objects and associated attributes for all items in the domain and controls the processing of the directory and all its objects. Since there is only one schema per directory, it is not moved in the typical fashion.

To move the Schema Master role you will need to open an elevated command prompt and follow these steps:

- 1. At the command prompt type regsv32 schmmmgmt.dll. A pop-up will tell you if you succeeded or not.
- 2. If it succeeded, click OK and close the command prompt.
- 3. Open the MMC (which can be done from the Windows Server 2012 Start screen).
- 4. Choose Add/Remove Snap-In.
- 5. Choose and add the Active Directory Schema snap-in.
- 6. Click OK.

> This should open your new MMC with the Active Directory schema loaded and ready to go.

## A WORD OF CAUTION

Modifications to the schema should always be done with care. Even though you are not deleting any records in this procedure, you always want to be careful.

## UPGRADE AND MIGRATION STRATEGIES

Now within the Active Directory Schema tool you need to verify that you are connected to the appropriate domain controller. You want to be connected to your new Windows Server 2012 Active Directory DC for this. Once you have validated that you are, follow these steps:

- 1. Right-click Active Directory Schema and choose Operations Manager.
- 2. Select Schema Master.
- 3. Select Yes when it prompts you to validate if this is what you want to do.
- 4. Close the Schema Master section.

Now you need to replicate your domain controllers and give them a few minutes to update the AD database. You can move on to the next two tasks, which are removing your Windows Server 2003 server as a global catalog (GC) server and then removing the Windows Server 2003 server as a domain controller.

The process of removing the server as a GC is simple. Open the Active Directory Sites and Services on the new Windows Server 2012 domain controller, go to the appropriate site, and select Servers. In this folder you will see your Windows Server 2003 DC. Select that and do the following:

- 1. Right-click NTDS Settings and select Properties.
- 2. On the tab that you open, uncheck the box that says Global Catalog.
- 3. Click Apply and then OK for this to take effect.

After a replication refresh you can use DCPromo to refresh your Windows Server 2003 domain controller. Before jumping the gun, make sure you have run a tool like Netdom and queried your FSMO roles, and make sure you have no errors showing up in your Event log, specifically under Directory Services.

## SWING MIGRATION: PROS AND CONS

To summarize, these are the benefits of swing migrations:

- They are gradual in implementation. Once the first Windows Server 2012 domain controller is introduced, the rest of the domain controllers can be upgraded or replaced as necessary.
- Your users keep their old SIDs and the domain keeps its old trust relationships, so any servers in other domains—resource domains containing perhaps file and print servers or email servers—will recognize those users.
- The users keep their old passwords.
- The swing migration offers the opportunity to redeploy Windows Server 2012 on the original server.

There are few disadvantages of this method. These are the most common pain points:

- More preparation and planning are required to ensure a smooth delivery.
- Any leftover junk remains in your Active Directory database.

## Active Directory Domain Migration

The third approach is characterized as clean and pristine. In this approach, you leave your existing domains (2003-based AD domains or 2008 R2-based AD domains) alone and create a new, empty AD domain. You use a program called a migration tool to copy user and machine accounts from the old (or domains) into the new AD domain.

The advantage of this method is that it is gradual. The migration can span a period of time where you continue testing and resolving issues. During this period, users still need access to their data. You can maintain access by reassigning permissions or relying on the capability of security identifier (SID) history.

## Domain Migration Is Gradual

In specific cases, we prefer the domain migration approach. For one thing, it's gradual. With an in-place, you walk your domain through a one-way door. If you find later that Windows Server 2012-based ADs aren't just for you, then you're stuck. But if you have a new domain and copy some subset of your users over to that domain, then you tell those users to log in to this new domain. If you start the new domain and wait a week or that the AD is not the tool for you, then you can always tell those users to go back to their old domain accounts.

Although the using migration approach is gradual, the process still leaves the artifacts that may have contributed to the poor performance and issues that initiated the migration in the first place. Over time, unwelcome administrators can configure Active Directory in some manner that confuses the folks who read this book. These problems will still be there to work through after the domain is migrated to a later version.

The domain migration approach also provides an intermediate phase that is not available with the other two. During this phase, you have the opportunity to test the process, proving that users will be able to access their resources and uncovering common issues that may arise with later production runs of the migration. This reduces the headaches that could arise upon crossing the threshold of the one-way door.

## INTRAFOREST MIGRATIONS

Keep in mind that these processes are applicable to intraforest migrations too. In Chapter 23, "The Third DC: Understanding Read-only Domain Controllers," you learned that the forest is a group of domains built in relation to each other.

Users, computers and groups may need to be transferred to another domain within the forest. You migrate these objects from one domain to another domain in the forest using these processes. The primary difference is that, like users and groups, must be moved rather than copied. The source user account is deleted after the target account is created. The Active Directory Migration Tool (ADMT) is used to migrate the accounts back to the source domain in a rollback. New computer accounts are created in the new domain, but the old computer account is disabled for rollback purposes.

There are two combinations of objects that need to be migrated together. These are referred to as closed sets.

## UPGRADE AND MIGRATION STRATEGIES 1259

**Users and Global Groups** Global groups allow only users and other global groups from the same domain as members. When a user changes domains, it can't be a member of its original group. When a global group is moved, the members from the original domain are dropped as well. These need to be merged together to maintain access within the limits of global group.

**Resource Computers and Domain Local Groups** Resources cannot assign permissions to local groups from other domains. If the computer is migrated without the assigned local groups, the computer will not be able to see the group's SID on its security token. As an alternative, you can opt to change the scope of local group to universal, which will impact the global status.

## HANDLING PERMISSIONS WITH THE NEW DOMAIN

Suppose you decide to go that domain migration route. Since there will be you expect the users of the organization will be members of domain or the new one. This will require users in the new domain to be able to access files and other resources in old one. Straddling the two domains, the organization will be heavily dependent on the trusts between the domain controllers all servers that have the resources on the same side. Business continuity is big-ticket item for management; they need to ensure their people will be able to get their data. A seamless migration will minimize any outages. There are two approaches to maintain access to the resources:

- re-ACLING ACL stands for access control list, a tech for the security of a resource like a shared folder.
- SID Histories The SID is the security identifier, which is the unique number assigned to accounts to identify it within the permission structure.

If you don't blink after opening the security tab of a file, you may see the SID listed on the ACL before the computer resolves SID to a friendly name.

![](img/41a83208e6906a3732620203b836cea7_1294_0.png)

## THE DOMAIN MIGRATION FOR COMPANY CONSOLIDATIONS

A firm of our authors owned 11 smaller companies that ran and managed their own Active Directory infrastructure. In some places this may make the most sense or provide the people ability to do things within their boundaries. One of the major problems this firm had IT turnover. If one of the IT administrators leave the company, that would often create a huge knowledge and support gap. They decided that along with moving towards an upgrade to Windows Server 2012 Active Directory, they would look to consolidate these domains into one. The management of the newly formed forest and domain wanted to merge the firms’ Active Directory forests into one to provide a unified message system based on Exchange Server and reduce the administrative overhead and risks.

# Real World Scenario
