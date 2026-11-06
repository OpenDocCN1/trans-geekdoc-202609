
# Windows Forest Functional Levels

## Windows 2000 Forest Functional Level

The Windows 2000 forest functional level is primarily designed to support mixed environments during the course of an upgrade. Typically, this applies to a transition from Windows 2000 to Windows Server 2003. It is also the default mode for a newly created Windows Server 2003 domain. It is characterized by relatively lower security features and reduced efficiency, but maintains the highest compatibility level possible for Active Directory. The Windows 2003 interim forest functional level handles upgrades from Windows NT to Windows Server 2003.

- All Windows DCs are supported.
- Active Directory forest features not supported in this mode:
- Efficient group member replication using linked value replication
- Improved KCC inter-site replication topology generator algorithms
- ISTG aliveness no longer replicated
- Attributes added to the GC, such as `ms-DS-Entry-Time-To-Die`, `Message Queuing-Secured-Source`, `Message Queuing-Multicast-Address`, `Print-Memory`, `PrintRate`, and `Print-Rate-Unit`
- Defunct schema objects
- Cross-forest trust
- Domain rename
- Dynamic auxiliary classes
- `InetOrgPerson` objectClass change
- Application groups
- 15-second intra-site replication frequency for Windows Server 2003 DCs upgraded from Windows 2000
- Reduced `NTDS.DIT` size
- Unlimited site management
- Can only be raised to the Windows 2003 native forest level.
- Can never be lowered back to the Windows 2000 level.

In the Windows 2000 functional level, which is the default level, Windows 2000 and greater DCs can exist, as well as Windows NT BDCs. Newly created Windows Server 2003 forests always start at this level. Windows NT PDCs do not exist in any version of Active Directory. Features available in the Windows 2000 forest functional level of Windows Server 2003 carry over the old features and add many new ones.

## Windows Server 2003 Interim Forest Functional Level

The Windows Server 2003 interim forest functional level is the preferred method of supporting Windows NT environments during the course of an upgrade. This level only applies to a transition from Windows NT to Windows Server 2003 because it does not allow for the presence of Windows 2000 DCs anywhere in the forest. It is characterized by lowered security features and defaults, but provides many efficiency improvements over the Windows 2000 forest functional level.

- Microsoft Windows 2000 DCs are not supported.
- New Active Directory forest features not supported in this level:
- Defunct schema objects
- Cross-forest trust
- Domain rename
- Dynamic auxiliary classes
- `InetOrgPerson` objectClass change
- Application groups
- 15-second intrasite replication frequency for Windows Server 2003 DCs upgraded from Windows 2000
- Reduced `NTDS.DIT` size
- Unlimited site management
- Can only be raised to the Windows Server 2003 forest functional level.
- Can never be lowered to the Windows 2000 level, since the Windows 2003 interim domain level only exists during an upgrade directly from Windows NT 4.0 to Windows Server 2003.
- Reasons to use the Windows 2003 interim forest functional level:
- Upgrading a root Windows NT 4.0 domain directly to Windows 2003.
- Windows NT 4.0 BDCs will not upgrade immediately.
- Your Windows NT 4.0 domain contains groups with more than 5000 members, not including the Domain Users group.
- You have no plans to implement Windows 2000 DCs at any time.
- Since the Windows 2003 interim domain level greatly improves group replication efficiency, it is better to use the Windows 2003 interim forest functional level instead of upgrading to Windows 2000, and then to Windows 2003.
- You are upgrading a Windows NT 4.0 PDC as the first DC of a new root domain in an existing Windows Server 2003 forest.
- Simultaneously upgrading and joining a Windows NT 4.0 domain as a child domain in an existing Windows Server 2003 forest.

In the Windows Server 2003 interim forest functional level, unlike the Windows Server 2003 interim domain functional level, many new features are activated while still allowing Windows NT 4.0 BDC replication. This mode is only used during the upgrade of a Windows NT 4.0 domain to a Windows Server 2003 forest. If a Windows 2000 Active Directory forest already exists, then the Windows Server 2003 interim forest level cannot be achieved.

To revert your Windows Server 2003 forest back to the interim level for an upgrade, you must manually configure the forest level with LDAP tools such as `Ldp.exe` or `Adsiedit.msc`. Remember that any domain joined to an existing forest inherits its domain functional level from the child, top-level, or root-level domain that it connects to during the joining process. The default forest level of Windows 2000 only applies when you create a new forest.

## Windows Server 2003 Forest Functional Level

The Windows Server 2003 forest functional level is the ideal level. This level does not allow for the presence of Windows NT or Windows 2000 DCs anywhere in the forest. It starts out with the best security defaults and capabilities, and the least compatibility with earlier versions of Windows. All new 2003 Active Directory forest features are enabled at this level, providing the most efficient and productive environment.

- DCs not supported at this level:
- Windows NT 4.0 DCs
- Windows 2000 DCs
- All new Active Directory forest features are supported at this level.
- Cannot be raised to any other level, since no higher level exists in Windows Server 2003.
- Can never be lowered back to the Windows 2000 level, but can be temporarily lowered to the Windows Server 2003 interim level for the purpose of joining a Windows NT 4.0 domain as a new domain in an existing forest during an upgrade of the NT 4.0 domain to the Windows Server 2003 level.

In the Windows Server 2003 forest functional level, only Windows Server 2003 DCs can exist.

![u04-01-9781931836944](images/B9781931836944500106/u04-01-9781931836944.jpg)

## Raising the Functional Level of a Domain and Forest

Before increasing a functional level, you should prepare for it by performing the following tasks. First, inventory your entire forest for earlier versions of DCs. The Active Directory Domains and Trusts MMC snap-in can generate a detailed report should you need it. You can also perform a custom LDAP query from the Active Directory Users and Computers MMC snap-in that will discover Windows NT DC objects within the forest. Use the following search string:

```
(&(objectCategory=computer) (operatingSystem Version=4*)
(userAccountControl:1.2.840.113556.1.4.803:=8192))
```

There should be no spaces in the query, and type it in all on one line. The search string is shown on two lines for readability.

Second, you need to physically locate all down-level DCs for the new functional level in the domain or forest as needed, and either upgrade or remove them.

Third, verify that end-to-end replication is working in the forest using the Windows Server 2003 versions of `Repadmin.exe` and `Replmon.exe`.

Finally, verify the compatibility of your applications and services with the version of Windows that your DCs will be running, and specifically their compatibility with the target functional level. Use a lab environment to test for compatibility issues, and contact the appropriate vendors for compatibility information.

### Domain Functional Level
