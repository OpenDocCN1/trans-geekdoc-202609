# AUTHENTICATION PITFALL

Domain controllers running Windows 2008 and later including Windows Server 2012 have the "Allow cryptography algorithms compatible with Windows NT 4" setting disabled by default. The legacy cryptography algorithms used in Windows NT 4.0 can be cracked with today's technologies.

Therefore, Microsoft made their domain controller more secure by using a Group Policy setting to prevent logins from hardware and clients that use weak Windows NT 4.0 cryptographic algorithms. This could be a SAMBA Server Message Block (SMB) client that cannot establish a secure channel to a Windows 2008 or higher-based domain controller or an SMB storage device that can create a secure channel to the domain controller. The work-around is to enable this setting in the Default Domain Controller Policy. You can find more details on this page:

```
http://support.microsoft.com/kb/942564/
```

# OPERATING SYSTEM COMPATIBILITY

In Windows Server 2012 Microsoft introduces the Resilient File System (ReFS). This file system is, as its name suggests, more resilient than NTFS. It has higher integrity and stability, and it also has proactive error identification built in. You may be tempted to choose this file system for all your upoming projects because of its qualities, but sadly there are limitations you need to be aware of:

+   - ReFS is only available in Windows Server 2012.
- ReFS is only used for data volumes. There is no way to use ReFS as an operating system volume or boot volume.
- As an Active Directory administrator, you need to know these best practices:
- Use only NTFS to store your SYSVOL, Active Directory database, and the Active Directory log files.
- Do not install SYSVOL on an ReFS-formatted volume or disk.
- Do not install the Active Directory database on an ReFS-formatted volume or disk.

# DOMAIN NAME

Because this is the first domain controller, you will choose to add a new forest. Then, you will also need to install DNS and the global catalog. Both DNS and GC are required for the first domain controller in your new forest. It is not possible to install a read-only domain controller (RODC) as the first domain controller; you cannot select this option.

# NAMING YOUR ROOT DOMAIN

Giving a name to a new root domain is probably the most difficult part. If you are setting up a lab domain controller, you don't care about the name. But the situation is different if you have to build a domain or forest in a productive environment. Because the NetBIOS name of the