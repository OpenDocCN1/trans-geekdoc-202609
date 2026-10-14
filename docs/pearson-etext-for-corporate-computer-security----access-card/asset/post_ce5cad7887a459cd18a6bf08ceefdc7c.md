
## Chapter 7
## Host Hardening
### Learning Objectives
After studying this chapter, you should be able to:
- 7.1 Define the elements of host hardening, security baselines and images, and systems administration.
- 7.2 Know important server operating systems.
- 7.3 Describe vulnerabilities and patches.
- 7.4 Explain how to manage users and groups.
- 7.5 Explain how to manage permissions.
- 7.6 Explain how to create strong passwords.
- 7.7 Describe how to test for vulnerabilities.

### Chapter Outline
- 7.1 Introduction
- 7.2 Important Server Operating Systems
- 7.3 Vulnerabilities and Patches
- 7.4 Managing Users and Groups
- 7.5 Managing Permissions
- 7.6 Creating Strong Passwords
- 7.7 Testing for Vulnerabilities
- 7.8 Conclusion

### 7.1 Introduction
**7.1 Define the elements of host hardening, security baselines and images, and systems administration.**

Although firewalls stop most Internet-based attacks, they will never stop them all. Consequently, protecting individual servers and other hosts is critical. In fact, if you install a server "out of the box," that is, use the operating system’s installation media and installation defaults and then connect the server to the Internet, a hacker is likely to "own" it within minutes or even seconds.

### What Is a Host?
In networking, any device with an IP address is a **host**. That simple definition works in security as well because any device with an IP address can be over a network. Consequently, the term *host* includes servers, clients, routers, firewalls, smartphones, and a variety of IoT devices. Although we do not usually think of firewalls and routers as hosts, think of the damage a hacker could do if he or she took over a firewall or router.

> Any device with an IP address is a host.

### The Elements of Host Hardening
The process of protecting a host against attacks is called **host hardening**. Hardening is not a single protection but rather a number of protections that often have little in common with each other. Among these protections are the following:
- *Back up* the host regularly. Without this, nothing else matters.
- Restrict *physical access* to the host.
- Install the operating system with *secure configuration* options. In particular, be sure that all default passwords are replaced by strong passwords. Adversaries know every default password. If you fail to change even one, they can use it to get into your system immediately.
- Minimize the number of *applications* and operating system *services* that run on the host to reduce the ability of hackers to take over the host by compromising an application or service. Minimizing the number of running programs reduces the “attack surface” of hosts.
- Harden all remaining *applications* on the host
- Download and install patches for known operating system vulnerabilities
- Manage *users* and *groups* (additions, changes, deletions, etc.)
- Manage access *permissions* for users and groups securely
- *Encrypt* data if appropriate
- Add a host *firewall*
- Read operating system *logs* regularly to look for suspicious activities
- Run *vulnerability tests* against the system regularly to identify security weaknesses that were not caught in the normal course of installation or operation

### Security Baselines and Images
In a long and complex set of actions, it is easy to overlook something. Consequently, firms adopt standard **security baselines**—set of specific actions to be taken to harden all hosts of a particular type (Windows, macOS, Linux, etc.) and of particular versions within each type (Windows 7, Windows 10, Windows Server 2019, etc.).

You also need baselines for servers with different functions, such as webservers (nginx, Apache, IIS, etc.) and e-mail servers (Sendmail, Microsoft Exchange, Exim, etc.). Security baselines are like pilot checklists for aircraft. Even experienced pilots make mistakes if they do not follow the checklist before takeoff.

Some companies go beyond baselines by creating a few secure software installations and testing them extensively. These companies then save disk **images** (full copies) of these installations. Future installations will be based on these disk images.

![](img/073342643701cc54eb7875c41ab92ef2_348_0.png)

**Figure 7-1** Threats to Hosts (Study Figure)

- 1. Backup
- 2. Backup
- 3. Backup
- 4. Restrict physical access to hosts (see Chapter 5)
- 5. Install the operating system with secure configuration options
- 6. Minimize the applications that run on the host
- 7. Harden all remaining applications on the host (see Chapter 8)
- 8. Download and install patches for vulnerabilities
- 9. Manage users and groups securely
- 10. Manage access permissions for users and groups securely
- 11. Encrypt data if appropriate
- 12. Add a host firewall
- 13. Read operating system log files regularly for suspicious activity
- 14. Run vulnerability tests frequently

Figure 7-2 The Elements of Host Hardening (Study Figure)

Figure 7-4 shows Windows Deployment Services with multiple groups of disk images that can be deployed depending on the needed host configuration.

When a new computer of that type must be installed, the company downloads the operating system image directly into the new computer. This saves money on each installation. It also ensures that each server is properly configured according to the firm’s security baselines and general security policies.

- **Security Baselines Guide the Hardening Effort**
- Security baselines are specifications for how hardening should be done
- Needed because it is easy to forget a step
- It is like a pilot's checklist
- Different baselines for different operating systems and versions
- Different baselines for servers with different functions (webservers, mail servers, etc.)
- Disk images
- Can also create a well-tested secure implementation for each operating system version and server function
- Save as a disk image
- Load the new disk image on new servers
- **Server Administrators Are Called Systems Administrators**
- Administer one or more servers
- Implement security baseline actions
- Larger firms have many systems administrators
- Security baselines help ensure uniformity in hardening
- Systems administrators are usually not responsible for network administration

Figure 7-3 Security Baselines and Systems Administrators (Study Figure)

### Virtualization
In larger enterprise environments companies manage hundreds of virtual disk images. They can be independently deployed across a variety of hardware platforms using virtualization. **Virtualization** allows multiple operating systems, with their associated applications and data, to run independently on a single physical machine. These **virtual machines** run their own operating system and share local system resources.

Virtualization can seem counterintuitive at first. Most users are accustomed to one operating system (OS) being installed on one physical computer (e.g., Microsoft Windows 10 installed on a Dell laptop). However, it is possible to have *multiple* operating systems running on a *single* physical computer, or running dynamically across multiple physical computers.

### VIRTUALIZATION ANALOGY
An analogy that helps understand how virtualization works compares (1) physical computers to buildings and (2) operating systems to people. A person is like an operating system (e.g., Windows 10, macOS, or Linux) in that they both interact with hardware and consume resources (memory, processing power, etc.). A building is like a physical computer (e.g., a laptop, desktop, or server) in that they both allow operating systems to reside in them and provide needed resources.

**Bachelor Pad**  Most end users have the equivalent of a “bachelor pad” on their personal computers. One person is living in one physical structure. The computing equivalent is one operating system running on one physical computer. The native OS has full access to all of the computer’s memory and processing power.

**Single-Family Home**  If you live in a house with a family, then it’s likely you have multiple people sharing a single physical structure. The computing equivalent is multiple operating systems running on a single physical computer. For example, you could run both Windows 10 and macOS concurrently on a single MacBook Pro®. Figure 7-5 shows a Linux virtual machine running in a Microsoft Windows 10 host.

Having two operating systems allows you to run applications that may be proprietary to each operating system. However, RAM, CPU, and hard disk space are all shared. Additional resources may be needed to run both operating systems at the same time.

**Hotel**  A hotel allows multiple people to stay in multiple physical structures. The computing equivalent is a stack of physical servers hosting tens, or hundreds, of

### Figure 7-4 Windows Deployment Services
![](img/073342643701cc54eb7875c41ab92ef2_350_0.png)
