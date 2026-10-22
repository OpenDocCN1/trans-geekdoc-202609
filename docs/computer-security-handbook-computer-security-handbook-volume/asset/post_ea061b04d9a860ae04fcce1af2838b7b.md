
- If using the Simple Network Management Protocol (SNMP) for network administration, carefully choose community names and block external access to the SNMP service. Make management information bases (MIBs) read-only, where possible.
- Avoid use of the DNS HINFO (host info) resource record to identify the central processing unit type and the installed operating system.

Specific operating system vulnerabilities are beyond the scope of this chapter; entire books and Websites are devoted to securing some of these individual operating systems. At a minimum, network managers must monitor their operating system vendor’s Website and all other sites that cover the NOS’s security. The sections that follow provide some general observations and comments about the various network operating systems.

## 25.5.1 Windows 9x.

All of the Windows operating systems (including NT and 2000) support peer-to-peer resource sharing and are vulnerable to exploitation of NetBIOS file and print sharing. In particular, when file and print sharing is enabled, the service is, by default, bound to TCP/IP. Although this does not cause an additional exposure to systems on the local network (since shares can be seen by other nodes on the LAN anyway), it does provide a potential vulnerability for hosts connected to the Internet. File and print sharing can be unbound from TCP/IP using Start, Control Panel, and Network.

Windows 9x (including Windows 95, Windows 98, and Windows ME) systems also have a vulnerability in the way authentication is performed when a user wishes to access a remote share. Windows uses the challenge-handshake authentication protocol (CHAP) for all passwords that need to be sent over the network, so passwords never appear in plaintext on the LAN. However, because Windows 9x uses the same challenge during a given 15-minute period, an intruder with a physical access to the LAN and to a sniffer could effect a replay attack by resending a duplicate authentication request and remapping a share on the Windows 9x system. This example illustrates the critical role of physical security in preventing compromise of LANs.

One of the classic Trojan horse programs for Windows 9x is Back Orifice (BO). Advertised as a remote Win9x administrator tool, it can be used by a nefarious user to take total control of someone else’s system, including the capability to modify the registry, reboot the system, transfer files, view cached passwords, spawn processes, and create shares. SubSeven and NetBus are other tools that can be used to take control of a remote Windows system. Some commercial virus scanners can detect these programs on individual systems, and several workstation firewalls exclude communications characteristic of these Trojans.

Windows 9x has no particular logon security mechanism. Although every user might be forced to log on to a system, any user can log in with any username and any password to get at least basic access. Several password-cracking programs are available through the Internet to break Windows’ .PWL password files, which are accessible once a user has access to the network. If a password-protected screen saver is preventing an attacker from logging in, there is an easy way around this as well: Simply reboot the computer. However, third-party security programs include nonbreakable secure logins and secure screen savers; many include bootlock functions that prevent any access whatever unless a valid password is entered. Current examples of such software can be located easily using buyers’ guides such as the annual listing from the Computer Security Institute.⁶

## 25.5.2 Windows NT/2000, XP, Vista, Win7, and Win8.

From a security perspective, Windows Millennium Edition (ME) is not significantly stronger than Windows 9x. Network administrators should periodically scan the network’s public shares to ensure that they are appropriate. Windows NT Server, NT Workstation, and 2000 Server editions are built for security, and network services and have the software architecture to support these services. However, a security vulnerability announcement related to these operating systems seems to come out almost weekly. Many of the hacking tools available for Win9x also are available for Windows NT and 2000; Back Orifice 2000 (BO2K), for example, is an NT/2000 version of BO and NetBus also can take control of an NT/2000 host.

Scripting holes in Internet Explorer (IE) and Office 2000 make all Windows systems susceptible to a variety of new virus and worm attacks. Although the early viruses, such as Melissa and I LOVE YOU, required users to open e-mail attachments, that is no longer so. Microsoft Outlook and Outlook Express will execute Hypertext Markup Language (HTML) and script code in the body of an e-mail by default. Several ActiveX components also will execute from an e-mail containing HTML and script code; examples of such controls include Scriptlet.typelib (ships with IE 4.x and 5.x) and the UA control (Office 2000). The best protection against these types of vulnerabilities is to define Outlook and Outlook Express to read e-mail in the “Restricted Sites Zone” and disable all Active Scripting and ActiveX related settings in that zone. This vulnerability affects all Windows systems with Office 2000 or Internet Explorer 4.x/5.x installed, even if IE is not used.

Securing Windows NT/2000 systems is well beyond the scope of this chapter, but some of the precautions, in addition to those listed already, follow.

- Format the drive using NTFS rather than FAT.
- Use long file names and disable the DOS 8.3 naming format.
- Disable the Everyone group.
- Rename the administrator account.
- Turn auditing on. (It is off by default.)

All NT-based systems have been given the C2 security rating by the National Computer Security Center, which includes Windows NT 3.5 and 4.0 and Windows 2000 SQL Server version 8.0. This means that when these versions of Windows are installed correctly, they meet evaluation criteria set forth in the National Computer Security Center (NCSC) Orange Book of security specifications. C2 certification is not applied to the operating system itself; rather, it is applied to a particular installation. Microsoft provides tools to audit a site so administrator(s) can deploy the correct hardware and software configurations to achieve this level of security in a network.

Windows 2000 introduced a new feature that administrators might want to employ. Windows NT introduced the ability to compress and decompress files on the fly. Windows 2000 introduces the capability to encrypt and decrypt files on the fly. The Encrypting File System (EFS) uses public key cryptography and the Data Encryption Standard (DES) to encrypt files on the hard drive. EFS includes an optional capability for a recovery mechanism in case of key loss. Organizations using EFS on critical systems should consider employing this mechanism to protect against loss or destruction of the private key.

Windows XP, which has sold well over 400 million copies and still enjoys the second largest installed base of any Microsoft OS next to Win7, introduced a number of security-oriented features. The major improvement was the inclusion of a firewall capability in both the Home Edition and Professional versions. Professional goes a couple of steps further by offering EFS file encryption, Kerberos,⁷ smart card support, and a new software restriction feature allowing administrators to mitigate the impact of viruses and Trojan horses. XP also supports raw sockets, which in itself is not unusual—UNIX and Linux do as well. This feature is intended to increase the functionality of Internet services, but in Microsoft’s implementation, it is available to any user, no matter what privilege level. Thus hackers can possibly gain control of a computer running XP and use it to initiate DoS attacks by commanding the OS to generate a flood of traffic.

Although Microsoft’s Windows Vista was released with much fanfare—and after a number of delays—it has not been as widely implemented as might have been due to concerns about security and stability of the platform, not to mention a perception that many of the security features create a great deal of inconvenience in the user experience (e.g., User Account Control, to be described, and the Digital Rights Management implementation). Regardless, a prime mover of Vista development was Microsoft’s Trustworthy Computing initiative, and as such, a number of new security capabilities were added.

Features include User Account Control (UAC), Bitlocker Drive Encryption, Windows Defender, Data Execution Prevention, Application isolation, Windows Service Hardening, Network Access Protection, and a variety of others. UAC is the most visible from the user perspective, requiring user intervention before allowing any action that requires administrative-level privileges. These include⁸:

- Right-clicking an application’s icon and clicking “Run as administrator”
- Changes to files or folders in %SystemRoot% or %ProgramFiles%
- Installing and uninstalling applications
- Installing device drivers
- Installing ActiveX controls
- Changing settings for Windows Firewall
- Changing UAC settings
- Configuring Windows Update
- Adding or removing user accounts
- Changing a user’s account type
- Configuring Parental Controls
- Running Task Scheduler
- Restoring backed-up system files
- Viewing or changing another user’s folders and files

As an interesting historical aside, the National Security Agency assisted Microsoft in the development of Vista. As reported in the Washington Post in January 2007:

> For the first time, the giant software maker is acknowledging the help of the secretive agency, better known for eavesdropping on foreign officials and, more recently, U.S. citizens as part of the Bush administration’s effort to combat terrorism. The agency said it has helped in the development of the security of Microsoft’s new operating system—the brains of a computer—to protect it from worms, Trojan horses and other insidious computer attackers. ...
> 
> The NSA declined to comment on its security work with other software firms, but Sager said Microsoft is the only one “with this kind of relationship at this point where there’s an acknowledgment publicly.”
