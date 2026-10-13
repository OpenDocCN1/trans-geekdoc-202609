
# Modern Linux Distributions

Modern Linux distributions are based on one of two basic designs—`SystemV` and `Systemd`. `SystemV` is an older platform that traces back to the original Linux, while `Systemd` is a newer platform that many Linux distributions have moved to. The Systemd design offers much faster booting and better dependency management.

Systemd employs a modern system service manager that is responsible for the `daemons` that run in the background and provide functionality for other programs. Some of these daemons are used to monitor security events and provide alerts. They also provide security features for isolating services and applications from the underlying operating system, as well as from each other.

Organizations such as Red Hat, CentOS, Fedora, Amazon, Debian, Ubuntu, and Mint have built their Linux Distributions on the Systemd platform. Distributions based on SystemV architecture include Alpine, Slackware, and Linux from Scratch.

## TABLE 4.2 Operating System Security Comparisons

| Name | Resource Access Control | Subsystem Isolation Mechanisms | Integrated Firewall | Encrypted File Systems | No Execute (NX) |
| --- | --- | --- | --- | --- | --- |
| Linux | POSIX, ACLs, MAC | Chroot, capability-based security, secomp, SELinux, AppArmor | Netfilter, varied by distribution | Yes | Hardware/emulation |
| macOS | POSIX, ACLs | Chroot, BSD file flags set using chflags | Ipfw | Yes | Hardware/emulation |
| Windows Server | ACLs, privileges, RBAC | Win32 WindowsStation, desktop, job objects | Windows Firewall | Yes | Hardware/emulation |
| Windows Client OS | ACLs, privileges, RBAC | Win32 WindowsStation, desktop, job objects | Windows Firewall | Yes | Hardware/emulation |

## Hardening Operating Systems

As noted earlier, the second level of hardening local computer systems against attacks is to secure their operating systems. This involves updating vulnerable code segments of the OS as they become known to the developers. OS hardening occurs through the application of new programming in the form of service packs, patches, and updates.

### Service packs

After an operating system has been in the field for some time, vendors may combine several product improvements and distribute a numbered `service pack` for the specific operating system being upgraded. Critical files should always be backed up in the event that the service pack or OS fails to work after installing the service pack.

### Patches

`Patches` (also referred to as `hotfixes` by Microsoft) are general improvements to a given operating system that has been released for distribution. Many patches and updates are purely cosmetic and convenient add-on features, while others are critical security upgrades designed to respond to a particular virus, discovered threat, or weakness found in the operating system.

### Updates

An `update` is a service pack or patch that improves the reliability, security, or attractiveness of an operating system. Some updates may make the OS more convenient but not necessarily more secure. Therefore, they should be tested before implementing. Consider backing up critical files in the event that the patch or OS fails to work after installation.

## Common Operating System Security Tools

After the system has reached bootup, there are a few steps that can be taken to prevent unauthorized personnel from accessing the operating system and its applications. In particular, if the operating system does not take control over the system, it becomes difficult to access the information stored in the system (this is the real target of most malicious computer endeavors). These steps include the following:

### Implementing local login requirements

*   Establishing user and group accounts
*   Setting up password policies
*   Establishing lockout policies

### Implementing additional authentication options

*   Using biometric authentication devices
*   Using physical authentication devices
*   Using multifactor authentication devices

### Using local administrative tools

*   Enabling system auditing and event logging
*   Installing Microsoft sysmon
*   Implementing data encryption tools
*   Overseeing application software security

### Providing remote access protection

*   Establishing firewall settings
*   Configuring browser security options
*   Establishing and implementing malicious software protection
*   Applying security updates and patches

Figure 4.11 shows the Local Security Policy/Security Settings options available in the Microsoft Windows Control Panel. The first set of options includes password and account lockout policy choices to locally control access to the system. You can also implement local admin policies for system auditing, users' rights, and security policies.

![FIGURE 4.11 Local Security Policy/Security Settings](images/c04f011.png)

**FIGURE 4.11** Local Security Policy/Security Settings

The Windows Firewall and Advanced Security tools enable the local administrator (or owner) to establish and configure a local firewall. The remaining tools in the figure are security tools that enable local policies to be established to control the local computer's interactions with an external network. In the following sections, we will examine these tools to determine how to implement them for best local host security practices.

**Bastille Linux** is a suite of Linux hardening tools used to lock down the OS and configure the system for optimum security. It is shipped as part of the distribution by the vendors of SuSE, Debian, Gentoo, and HP-UX Linux and UNIX products.

## Implementing Local Login Requirements

The main user authentication tool used with personal computing devices is the `username` and `password` login. In general, there are three types of user-related login to contend with: a logon to the local machine, a logon to a specific software application, and a network logon.

At the local computer level, the local logon is typically required. This level of login validates the user for using the local computer's resources, files, and devices. However, in a shared computer environment where multiple users may be enabled to use the same computer, `local user and group credentials` are created and configured through a `user accounts database` that is stored on the local computer.

These credentials are used to gain initial access to the computer, control access to its local resources, and control access to network resources. In a Windows environment, these accounts are created and managed through the Local Users and Groups utility under Computer Management, as depicted in Figure 4.12.

![FIGURE 4.12 Microsoft Local User and Groups accounts](images/c04f012.png)

**FIGURE 4.12** Microsoft Local User and Groups accounts

The first time a stand-alone system is started, an `administrator's account` is automatically created in the operating system's local accounts database. The administrator has rights and permissions to all the system's hardware and software resources. The administrator, in turn, creates other users and then grants them rights and permissions to system resources as necessary.

The administrator can deal with `users` on an individual basis or may gather users into `groups` that can be administered uniformly. In doing so, the administrator can assign permissions or restrictions on an individual or an entire group. The value of using groups is that it saves time to apply common rights to several users instead of applying them one by one.
