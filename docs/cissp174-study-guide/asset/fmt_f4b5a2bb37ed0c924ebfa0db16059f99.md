
![Fig. 4.12 Linux “ls -la” command.](images/B9780443187346000076/f04-12-9780443187346.jpg)

[Fig. 4.12](#Ch004_107-223_B9780443187346000076_1.xhtml#B-f0065) Linux “ls -la” command.

The output in [Fig. 4.12](#Ch004_107-223_B9780443187346000076_1.xhtml#f0065) shows permissions, owner, group, size, date, and filename. Permissions beginning with “d” (such as “acpi”) are directories. Permissions beginning with “-” (such as “at.deny”) describe files. [Fig. 4.13](#Ch004_107-223_B9780443187346000076_1.xhtml#f0070) zooms in on files in `/etc`, highlighting the owner, group, and world permissions.

![Fig. 4.13 Linux /etc permissions, highlighting owner, group, and world.](images/B9780443187346000076/f04-13-9780443187346.jpg)

[Fig. 4.13](#Ch004_107-223_B9780443187346000076_1.xhtml#B-f0070) Linux /etc permissions, highlighting owner, group, and world.

The `adduser.conf` file in [Fig. 4.13](#Ch004_107-223_B9780443187346000076_1.xhtml#f0070) is owned by root and has “-rw-r--r--” permissions. This means `adduser.conf` is a file (permissions begin with “-”), has read and write (rw-) permissions for the owner (root), read (r--) for the group (also root), and read permissions (r--) for the world.

#### Microsoft NTFS Permissions

Microsoft NTFS (New Technology File System) has the following basic file permissions:

*   Read
*   Write
*   Read and execute
*   Modify
*   Full control (read, write, execute, modify, and in addition the ability to change the permissions)

NTFS has more types of permissions than most UNIX or Linux file systems. The NTFS file is controlled by the owner, who may grant permissions to other users. [Fig. 4.14](#Ch004_107-223_B9780443187346000076_1.xhtml#f0075) shows the permissions of a sample photo at `C:\Users\Public\Pictures\Sample Pictures\Penguins.jpg`.

![Fig. 4.14 NTFS permissions.](images/B9780443187346000076/f04-14-9780443187346.jpg)

[Fig. 4.14](#Ch004_107-223_B9780443187346000076_1.xhtml#B-f0075) NTFS permissions.

To see these permissions, right-click an NTFS file, choose “properties,” and then “security.”

#### Privileged Programs

On UNIX and Linux systems, a regular user cannot edit the password file (`/etc/passwd`) and shadow file (`/etc/shadow`), which store account information and encrypted passwords, respectively. But users need to be able to change their passwords (and thus those files). How can they change their passwords if they cannot (directly) change those files?

The answer is `setuid` (set user ID) programs. `Setuid` is a Linux and UNIX file permission that makes an executable run with the permissions of the file’s owner, and not as the running user. `Setgid` (set group ID) programs run with the permissions of the file’s group.

[Fig. 4.15](#Ch004_107-223_B9780443187346000076_1.xhtml#f0080) shows the permissions of the Linux command `/usr/bin/passwd` used to set and change passwords. It is `setuid` root (the file is owned by the root user, and the owner’s execute bit is set to “s,” for `setuid`), meaning it runs with root (super user) permissions, regardless of the running user.

![Fig. 4.15 Linux setuid root program /usr/bin/passwd.](images/B9780443187346000076/f04-15-9780443187346.jpg)

[Fig. 4.15](#Ch004_107-223_B9780443187346000076_1.xhtml#B-f0080) Linux `setuid` root program `/usr/bin/passwd`.

The “passwd” program runs as root, allowing any user to change their password, and thus the contents of `/etc/passwd` and `/etc/shadow`. `Setuid` programs must be scrutinized for security holes: attackers may attempt to trick the `passwd` command to alter other files. The integrity of all `setuid` and `setgid` programs on a system should be closely monitored.

## Virtualization, Cloud, and Distributed Computing

Virtualization and distributed computing have revolutionized the computing world, bringing wholesale changes to applications, services, systems data, and data centers. Yesterday’s best practices may no longer apply. Where is the DMZ when your data is in the cloud? Can your NIDS monitor data sent from one guest to another in a single host? Does your physical firewall matter?

### Virtualization

*Virtualization* adds a software layer between an operating system and the underlying computer hardware. This allows multiple “guest” operating systems to run simultaneously on one physical “host” computer. Popular transparent virtualization products include VMware, QEMU, and Xen.

There are two basic virtualization types: transparent virtualization (sometimes called full virtualization) and paravirtualization. Transparent virtualization runs stock operating systems, such as Windows 11 or Ubuntu Linux 22.04, as virtual guests. No changes to the guest OS are required. Paravirtualization runs specially modified operating systems, with modified kernel system calls. Paravirtualization can be more efficient but requires changing the guest operating systems. This may not be possible for closed operating systems such as the Microsoft Windows family.

#### Hypervisor

The key to virtualization security is the *hypervisor*, which controls access between virtual guests and host hardware. A Type 1 hypervisor (also called bare metal) is part of an operating system that runs directly on host hardware. A Type 2 hypervisor runs as an application on a normal operating system, such as Windows 10. For example: VMware ESX is a Type 1 hypervisor and VMware Workstation is Type 2.

Many virtualization exploits target the hypervisor, including hypervisor-controlled resources shared between host and guests, or guest and guest. These include cut-and-paste, shared drives, and shared network connections.

#### Virtualization Benefits

Virtualization offers many benefits, including lower overall hardware costs, hardware consolidation, and lower power and cooling needs. Snapshots allow administrators to create operating system images that can be restored with a click of a mouse, making backup and recovery simple and fast. Testing new operating systems, applications, and patches can be quite simple. Clustering virtual guests can be far simpler than clustering operating systems that run directly in hardware.

#### Virtualization Security Issues

Virtualization software is complex and relatively new. As discussed previously, complexity is the enemy of security: the sheer complexity of virtualization software may cause security problems.

Combining multiple guests onto one host may also raise security issues. Virtualization is no replacement for a firewall: never combine guests with different security requirements (such as DMZ and internal) onto one host. The risk of virtualization escape (called VMEscape, where an attacker exploits the host OS or a guest from another guest) is a topic of recent research. Network World reports: “Multiple vulnerabilities have been discovered in Cisco’s Enterprise NFV Infrastructure Software (NFVIS). The worst of the vulnerabilities could let an attacker escape from the guest virtual machine (VM) to the host machine, Cisco disclosed. The other two problems involve letting a bad actor inject commands that execute at the root level and allowing a remote attacker to leak system data from the host to the VM” [\[15\]](#Ch004_107-223_B9780443187346000076_2.xhtml#bb0080). Known virtualization escape bugs have been patched, but new issues may arise.

Many network-based security tools, such as network intrusion detection systems, can be blinded by virtualization. A traditional NIDS connected to a physical SPAN port or tap cannot see traffic passing from one guest to another on the same host. NIDS vendors are beginning to offer virtual IDS products, running in software on the host, and capable of inspecting host-guest and guest-guest traffic. A similar physical to virtual shift is occurring with firewalls.

### Cloud Computing
