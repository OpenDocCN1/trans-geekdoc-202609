# 25.5.2 Windows NT/2000, XP, Vista, Win7, and Win8.

From a security perspective, Windows 2000 Millennium Edition (ME) is not significantly stronger than Windows 9x. Network administrators should periodically scan the network’s public shares to ensure that they are appropriate. Windows NT Server, NT Workstation, and 2000 Server editions are built for security, and network services and have the software architecture to support these services. However, a security vulnerability announcement related to these operating systems seems to come out almost weekly. Many of the hacking tools available for Win9x also are available for Windows NT and 2000; Back Orifice 2000 (BO2K), for example, is an NT/2000 version of BO and NetBus also can take control of an NT/2000 host.

Scripting holes in Internet Explorer (IE) and Office 2000 make all Windows systems susceptible to a variety of new virus and worm attacks. Although the early viruses, such as Melissa and I LOVE YOU, required users to open e-mail attachments, that is no longer so. Microsoft Outlook and Outlook Express will execute Hypertext Markup Language (HTML) and script code in the body of an e-mail by default. Several ActiveX components also will execute from an e-mail containing HTML and script code; examples of such controls include Scriptlet.typelib (ships with IE 4.x and 5.x) and the UA control (Office 2000). The best protection against these types of vulnerabilities is to define Outlook and Outlook Express to read e-mail in the “Restricted Sites Zone” and disable all Active Scripting and ActiveX related settings in that zone. This vulnerability affects all Windows systems with Office 2000 or Internet Explorer 4.x/5.x installed, even if IE is not used.

Securing Windows NT/2000 systems is well beyond the scope of this chapter, but some of the precautions, in addition to those listed already, follow.

+   - Format the drive using NTFS rather than FAT.
+   - Use long file names and disable the DOS 8.3 naming format.
+   - Disable the Everyone group.
+   - Rename the administrator account.
+   - Turn auditing on. (It is off by default.)

All NT-based systems have been given the C2 security rating by the National Computer Security Center, which includes Windows NT 3.5 and 4.0 and Windows 2000 SQL Server version 8.0. This means that when these versions of Windows are installed correctly, they meet evaluation criteria set forth in the National Computer Security Center (NCSC) Orange Book of security specifications. C2 certification is not applied to the operating system itself; rather, it is applied to a particular installation. Microsoft provides tools to audit a site so administrator(s) can deploy the correct hardware and software configurations to achieve this level of security in a network.

Windows 2000 introduced a new feature that administrators might want to employ. Windows NT introduced the ability to compress and decompress files on the fly. Windows 2000 introduces the capability to encrypt and decrypt files on the fly. The Encrypting File System (EFS) uses public key cryptography and the Data Encryption Standard (DES) to encrypt files on the hard drive. EFS includes an optional capability for a recovery mechanism in case of key loss. Organizations using EFS on critical systems should consider employing this mechanism to protect against loss or destruction of the private key.

Windows XP, which has sold well over 400 million copies and still enjoys the second largest installed base of any Microsoft OS next to Win7, introduced a number of