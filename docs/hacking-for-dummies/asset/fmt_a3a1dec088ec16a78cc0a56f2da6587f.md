
Edit your `/etc/inittab` file, and comment out (place a `#` sign in front of) the line that reads `ca::ctrlaltdel:/sbin/shutdown -t3 -r now`, shown in the last line of [Figure 13-9](#c13.xhtml#c13-fig-0009). These changes prevent someone from rebooting the system by pressing Ctrl+Alt+Delete. Be forewarned that this change also prevents you from legitimately pressing Ctrl+Alt+Delete.

![ FIGURE 13-9:  /etc/inittab showing the line that allows a Ctrl+Alt+Delete shutdown.](images/9781119485476-fg1309.png)

 [FIGURE 13-9:](#c13.xhtml#rc13-fig-0009)  /etc/inittab showing the line that allows a Ctrl+Alt+Delete shutdown.

For Linux-based laptops, use disk-encryption software from WinMagic ([`https://www.winmagic.com`](https://www.winmagic.com)) or Symantec EndPoint Encryption ([`https://www.symantec.com/products/endpoint-encryption`](https://www.symantec.com/products/endpoint-encryption)). If you don't, when a laptop is lost or stolen, you could very well have a data breach on your hands, not to mention the state and federal compliance, and disclosure-law requirements that go along with it. Not good!

![tip](images/tip.png)If you believe that someone recently gained access to your system, physically or by exploiting a vulnerability such as a weak password or buffer overflow, you can use a program called last to view the last few logins into the system to check for strange login IDs or login times. This program peruses the `/var/log/wtmp` file and displays the users who logged in last. You can enter **last | head** to view the first part of the file (the first ten lines) if you want to see the most recent logins.

## Performing General Security Tests

Assess critical and often-overlooked security issues on your Linux and macOS systems, such as the following:

*   Misconfigurations or unauthorized entries in the shadow password files, which could provide covert system access.

*   Password complexity requirements.

*   Users equivalent to root.

*   Suspicious automated tasks configured in cron, the script scheduler program.

*   Signature checks on system binary files.

*   Checks for rootkits.

*   Network configuration, including measures to prevent packet spoofing and other DoS attacks.

*   Permissions on system log files.

You can perform all these assessments manually or use an automated tool. [Figure 13-10](#c13.xhtml#c13-fig-0010) shows the initiation of the Tiger security-auditing tool ([`www.nongnu.org/tiger`](http://www.nongnu.org/tiger)), and [Figure 13-11](#c13.xhtml#c13-fig-0011) shows a portion of the audit results. Talk about some great bang for no buck!

![ FIGURE 13-10:  Running the Tiger security-auditing tool.](images/9781119485476-fg1310.png)

 [FIGURE 13-10:](#c13.xhtml#rc13-fig-0010)  Running the Tiger security-auditing tool.

![ FIGURE 13-11:  Partial output of the Tiger tool.](images/9781119485476-fg1311.png)

 [FIGURE 13-11:](#c13.xhtml#rc13-fig-0011)  Partial output of the Tiger tool.

Alternatives to Tiger include Linux Security Auditing Tool ([`http://usat.sourceforge.net`](http://usat.sourceforge.net)) and Bastille Unix ([`http://bastille-linux.sourceforge.net`](http://bastille-linux.sourceforge.net)).

## Patching

Ongoing patching is perhaps the best thing you can do to enhance and maintain the security of your Linux and macOS systems. Regardless of the Linux distribution you use, using a tool to assist in your patching efforts makes your job a lot easier.

![warning](images/warning.png)I often find that Linux and macOS are out of the patch-management loop. With the focus on patching Windows, many network administrators forget about these other systems on their network. Don’t fall into this trap, especially given the growing use of macOS.

![remember](images/remember.png)Patching is critical, even on OSes that have long been assumed to be secure. macOS High Sierra, for example, had two recent vulnerabilities that affected a lot of Mac computers. The first vulnerability provided full root user access to the system without a password, and the second provided App Store Settings access if you entered any admin username combined with a random password. This fact underscores the importance of being alert to these flaws, responding fast, and patching the systems quickly. Even when users bring in their own Macs, they need to know that timely patching is of the essence, and you need to be able to enforce patching wherever possible. Your business network is on the line!

### Distribution updates

For Linux, the process is different in every distribution. You can use the following tools, based on your specific distribution:

*   **Red Hat:** The following tools update Red Hat Linux systems: 

    *   RPM Packet Manager, which is the graphical user interface (GUI) application that runs in the Red Hat GUI desktop. It manages files with an `.rpm` extension that Red Hat and other freeware and open-source developers use to package their programs. RPM Packet Manager was originally a Red Hatsystem but is now available for many versions of Linux.

    *   up2date, a command-line, text-based tool that's included in Red Hat, Fedora, and CentOS.

*   **Debian:** You can use the Debian package management system (dpkg) included with the OS to update Debian Linux systems.

*   **Slackware:** You can use the Slackware Package Tool (pkgtool) included with the OS to update Slackware Linux systems.

*   **SUSE:** SUSE Linux includes YaST2 software management.

 ![tip](images/tip.png)In addition to Linux kernel and general operating system updates, make sure to pay attention to Apache, OpenSSL, OpenSSH, MySQL, PHP, and other software programs on your systems. They may have weaknesses that you don’t want to overlook.

For macOS, the updates are pushed to the computer locally, and unfortunately, it’s up to the user to install the updates by default.

### Multiplatform update managers

Commercial patch-management tools have additional features, such as correlating patches with vulnerabilities and automatically deploying appropriate patches. Commercial tools that can help with Linux and macOS patch management include ManageEngine ([`https://www.manageengine.com/products/desktop-central/mac-management.html`](https://www.manageengine.com/products/desktop-central/mac-management.html)), GFI LanGuard ([`https://www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard/specifications/patch-management-for-operating-systems`](https://www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard/specifications/patch-management-for-operating-systems)), and KACE Systems Management Appliance ([`https://www.quest.com/products/kace-systems-management-appliance`](https://www.quest.com/products/kace-systems-management-appliance)).

Part 5

# Hacking Applications

IN THIS PART …

Discover how email and Voice over Internet Protocol (VoIP) impacts your security posture.

See how common application flaws create bit and unnecessary business risks.

Understand how database and storage systems can create some of the biggest security challenges of all.

Chapter 14

# Communication and Messaging Systems

IN THIS CHAPTER

![check](images/check.png)**Attacking email systems**

![check](images/check.png)**Assailing instant messaging**

![check](images/check.png)**Assaulting Voice over IP applications**

Communication systems and protocols such as email and Voice over Internet Protocol (VoIP) often create vulnerabilities that people overlook. Why? Well, in my experience, communications software — at both the server and client levels — is vulnerable because network administrators often believe that firewalls and antimalware software are all they need to keep trouble away, or they simply forget about securing these systems.

In this chapter, I show you how to test for common email and VoIP issues. I also outline key countermeasures to help prevent these hacks against your systems.

## Introducing Messaging System Vulnerabilities
