# IN-PLACE UPGRADES: PRO AND CONS

The following factors are favor of in-place upgrades:

+   - They don't typically require new machines.
- Your users keep their SIDs, and the domain keeps its old trust relationships, so any servers in other domains—resource domain contains includes file and printer email servers, for example—will recognize those users without trouble.
- The users keep their old passwords.
- It's a relatively simple, quick upgrade.
- If you're going from 2008-based ADs to 2012-based ADs, then the upgrade is basically trouble-free.
- In-place upgrades from Windows 2008 R2 are seamless and simple.

Some of the limitations are as follows:
- The upgrade path is somewhat limited. The Windows Server supported versions are 64-bit only. Many organizations deployed 32-bit domain controllers when Windows Server 2003 became available, so an in-place upgrade may not be an option.
- It is all-or-nothing upgrade. You upgrade all, and it's a one-way trip—no AD rollback wizard. (However, you can, as we suggested, restore the system data.) We prefer proper accounts.
- Any leftover junk remains in your Active Directory database. I mention this because many people think an upgrade will clean out those old, stale objects. The some of newer tools in Windows Server 2012 from the AD PowerShell modules can help you clean up these entries.

# MIGRATING WITH A SWING MIGRATION

One general approach is the swing migration, known as an Active Directory migration. This would involve adding a Windows Server 2012 domain controller into an Active Directory domain. The environment would remain essentially the same, but the existing domain controllers can be upgraded or replaced at the convenience of the administrators. Historically the drawback is requirement for more hardware, but with today's virtualization such as Hyper-V, you can just create a virtual domain controller on Windows Server 2012.

You avoid the all-or-nothing nature of the server upgrade because the new domain controller doesn't threaten the integrity of the Active Directory database. The replica is just receiving a copy. This process still requires preparing the forest and schema, but these procedures are less intensive than the upgrade.

A domain controller redeployment involves complications that require some planning. The domain controller is an important part of the environment. It may have FSMO roles and the global catalog assigned to it. It may have other services such as DNS, DHCP, file shares, and printers that users depend on regularly. There may be groups and group policies that point to this domain controller. You need to find out what will happen when this server is removed from the network. You must determine resolutions to these gaps. New Windows Server 2012 can assume these roles and services.