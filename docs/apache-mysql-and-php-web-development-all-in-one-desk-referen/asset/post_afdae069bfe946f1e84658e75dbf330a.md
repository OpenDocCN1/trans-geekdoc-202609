
## Getting Windows behind a Firewall

Okay, you have Windows all patched with nonessential services disabled. Now are you safe? Unfortunately the answer is somewhere between “probably not” and “if so, probably not for long.” No operating system that provides a wide range of end user services should be directly connected to the Internet. This includes Windows, Linux, Unix and NetWare just to name a few. Along with patching, securing, and limiting operating services, you also should use a hardware firewall. A firewall is hardware or software that acts as a security agent for your network or server. A firewall sits physically between your protected system (such as your Web server) and any unsecured networks (such as the Internet). All data coming to your Web server first must come through your firewall. Though the features vary by manufacturer and model, firewalls can be configured to refuse certain kinds of connections, block traffic from a denial-of-service attack, and log suspicious activity.

Firewalls vary widely in cost and ease of use. If you are protecting a small network or a single host you don’t necessarily need to spend a fortune on a firewall. However, a few features should be considered essential. The list below outlines the minimum features your firewall needs to have. Other features such as DHCP and Virtual Private Network (VPN) hosting services could be useful depending on your network layout, but they are not essential.

- Stateful packet inspection
- Denial-of-service (DoS) prevention
- Configurable Port Forwarding
- Easy to configure management interface

Stateful packet inspection involves the examination of data traffic coming into the firewall from the Internet. It is designed to prevent a kind of attack known as spoofing, where an external user tries to fool the firewall into believing a local host is actually located on the Internet. A successful spoof allows the external user to bypass the security that the router provides. With a firewall, the inbound traffic is checked to see if it is in response to a request that an internal host made. If it is, then the traffic is forwarded along. If the traffic is not legitimate, it is discarded.

The denial-of-service protection provided by a firewall can come in several forms. A denial-of-service attack typically involves either sending large volumes of traffic or malformed data to a host. The idea is to cause the host (router or firewall) to become so overloaded it stops forwarding traffic. The attack thus denies the users (who depend on the router/firewall for network access) any use of their service. Hence the name Denial of Service.

The firewall's method of preventing the attack often involves blocking or ignoring traffic from a host or set of hosts. This is extremely effective. After the firewall ceases processing traffic from the attacking host there is very little chance that a prolonged service outage will occur.

Port forwarding is only essential if you intend to allow inbound (from the Internet) connections. An *inbound connection* occurs when an Internet-based user gains access to some resource on your network. A relevant example is your Web server. To allow users access to your internal Web server, the firewall must be configured to forward Web traffic (on TCP port 80) to the internal IP address of your Web server.

Make sure that when you purchase a firewall you research the device thoroughly. You will probably want functionality beyond just the basic items outlined above. Develop a list of features you deem essential. Read the product literature and select a device that best matches your needs. There are many great firewall producers out there. The list below outlines some of the most popular.

- Cisco Systems: www.cisco.com
- Netgear: www.netgear.com
- Sonic Wall: www.sonicwall.com
- Nokia: www.nokia.com
- 3Com: www.3com.com

## Chapter 3: Ten Third-Party Packages That Enhance Security

### In This Chapter

- Bastille Hardening System
- LIDS
- Guarddog
- Firestarter
- WinRoute
- ZoneAlarm
- SNORT
- ACID
- Pandora
- Nessus

In your quest to secure your server, you don't need to depend solely on the tools that came with your operating system. Many third-party vendors make security-enhancing products. In the Linux community, these tools not only are powerful but often have little or no retail costs associated with them. This chapter examines ten excellent products designed to help you keep your system secure.

### Locking Down with Bastille

The program known as the Bastille Hardening System is used to perform a systemic hardening of supported operating systems. This tool currently supports a variety of Linux distributions including Red Hat, Debian, Mandrake, SuSE, and Turbo Linux, as well as other operating systems such as HP-UX and Mac OS X. Essentially, Bastille is a collection of scripts that when executed removes a large number of known configuration weaknesses. These scripts are built by a collection of developers who are experts in their respective fields. The scripts are designed to reconfigure the system on which they're executed. Along with individual expert input, accepted industry guidelines, such as the SANS institute's recommendations for securing Linux, are used.

Go to www.bastille-linux.org to download the installer for your operating system, such as the RPM package for Red Hat and the perl-TK or perl-Curses package. To run the script, simply type bastille in a terminal window. The hardening script then executes and walks you through the process of hardening the system.

### Linux Intrusion Detection with LIDS

The Linux Intrusion Detection System (LIDS) is a collection of components that updates the Linux kernel's security options. Access rules are put in place that control the default abilities of the kernel. These access options expand the ability to control access to the level where even root can be restricted from accessing various system resources. In addition, LIDS extends the system capabilities allowing it to control the whole system as well as some network and file-system security features. The LIDS developers promote it as “A Protection, Detection, and Response in the Linux system.” You use rules along with LIDS to define which events are tracked, how LIDS should respond to network-intrusion attempts, and so forth. The following list outlines some of the key features of LIDS:

- It allows the configuration of file access in such a manner that not even root can make changes to the file.
- It can protect processes from being killed.
- It enables you to restrict RAW IO operations, protect your hard drive, and protect the Master Boot Record.
- When your LIDS-enabled system is the target of a port scan, LIDS can detect it and send an alert to the user in charge of maintaining the system. Any violation of the defined rules can also be logged and generate alerts.
- When someone violates the rules, LIDS can log the detail message about the violated action to the system log file or to your syslog server, either of which may be protected by LIDS.
- Also in response to rule violations, LIDS can notify an administrator or even kill the offending session/connection.

For more information about LIDS, including usage and configuration, check out www.lids.org/.

### Starting Easy with Guarddog

Guarddog is a KDE-based graphical firewall-configuration utility that helps simplify the process of configuring your Linux firewall. This product was designed to help beginners, as well as save more advanced users the trouble of dealing with complex scripts and ipchains configurations. Along with easy setup, Guarddog enables you to continually tweak and adjust your firewall. Like the initial setup, easy-to-navigate graphical tools are used. Here are some of the key features of Guarddog:

- Enables you to divide hosts/networks into zones. Different zones can have different security policies if needed. For example, one zone may contain computers used for public access with nonsensitive information (minimal security needs) and another zone could contain mission-critical servers (maximum security needs).
- Supports a huge number of networking protocols, including FTP, SSH, Telnet, SMTP, DNS, HTTP, HTTPS, and POP.
- Enables you to add at a later date any protocols not supported by the default configuration.
- Works with local router configurations (if your system is performing routing).
- Runs on KDE 2 or 3, and Linux 2.2 and 2.4 series kernels.
- Works with iptables features including connection tracking and rate-limited logging.
- Enables you to import/export firewall scripts.
- Uses a fail-safe default configuration that denies all activities that are not implicitly allowed.

For more information on Guarddog, check out www.simsonzone.com/software/guarddog/.

### Taking Control with Firestarter

Another graphical tool for configuring Linux firewalls is Firestarter. This tool uses GTK+/GNOME. The product developers tout Firestarter as a user-friendly means of configuring Linux firewalls using GNOME. When compared to Guarddog, Firestarter seems to be slightly more feature-rich. For many users, particularly beginners who are comfortable with a particular desktop environment, the best option is to select the GUI configuration tool that works with their configuration. The following list highlights some of the most interesting and useful features of Firestarter:

- Provides a configuration wizard that enables the program to work in a useful way for both beginners and experts.
- Provides multilanguage support.
- Comes with predefined rule sets, as well as tools for adding your own access and monitoring rules.
