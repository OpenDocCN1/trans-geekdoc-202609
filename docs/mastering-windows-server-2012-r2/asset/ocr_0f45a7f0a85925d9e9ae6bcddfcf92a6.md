# UPGRADING YOUR ACTIVE DIRECTORY

Clean and Pristine Migration A "pure as the driven snow" Windows Server 2012 Active Directory is created. User accounts, groups, and computers are migrated into this new domain with the use of tools, such as the Active Directory Migration Tool (ADMT). The latest released version is 3.2.

These approaches are explained in detail in the following sections.

# MIGRATING WITH AN IN-PLACE UPGRADE

An in-place upgrade means installing a Windows Server 2012 installation over an existing domain controller. The upgrade process is more or less a Next, Next, Finish job. But as easy as may sound, there are some consequences to be aware of. Everything in the domain will stay or more less the same. That means users, computers, and groups are not touched, and all are happy that not much changed. But the downside might be that all the good things and the bad things are carried forward and stay the same. Or some applications that are installed on the system are not compatible. If something goes wrong, it could really get hard because the upgrade process. Even with a tested backup ensures that nothing should go wrong, Murphy might be in the corner waiting for you.

It is important to know that all the roles that you have, for example, DNS and DHCP roles installed on your system, these will also be upgraded to the Windows Server 2012 versions.

If you decide to do an in-place upgrade of your domain controller, you need to know which version of Windows Server you can actually upgrade.

Domain controllers that run 64-bit versions of Windows Server 2008 or Windows Server 2008 R2 can be upgraded to Windows Server 2012 (as shown in Table 7.2). There is no way to upgrade domain controllers that run Windows Server 2003 or 32-bit versions of Windows Server 2008. To replace them, you must install domain controllers that run Windows Server 2012 in the domain, and remove the domain controllers that run Windows Server 2003.

# TABLE 7.2: Upgrade Path

| IF YOU ARE RUNNING THESE EDITIONS... | YOU CAN UPGRADE TO THESE EDITIONS... |
| Windows Server 2008 Standard with SP2 | Windows Server 2012 Standard |
| or | or |
| Windows Server 2008 Enterprise with SP2 | Windows Server 2012 Datacenter |
| Windows Server 2008 Datacenter with SP2 | Windows Server 2012 Datacenter |
| Windows Web Server 2008 | Windows Server 2012 Standard |
| Windows Server 2008 R2 with SP1 | Windows Server 2012 Standard |
| or | or |
| Windows Server 2008 R2 Enterprise with SP1 | Windows Server 2012 Datacenter |
| Windows Server 2008 R2 Datacenter with SP1 | Windows Server 2012 Datacenter |
| Windows Web Server 2008 | Windows Server 2012 Standard |