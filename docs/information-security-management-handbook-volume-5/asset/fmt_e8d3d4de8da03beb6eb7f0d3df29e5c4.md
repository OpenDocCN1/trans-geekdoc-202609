
# Other Security and Operational Considerations

The official vSphere Hardening Guide is a great place to start to harden the initial configuration of the virtual realm. However, there are several areas that are simply beyond the scope of the vSphere Hardening Guide:

- Security of the software running inside the virtual machine, such as operating system and applications, or of the traffic traveling through the virtual machine networks.
- Security of any other add-on products, such as SRM.
- Detailed operational procedures related to maintaining security, such as event monitoring, auditing, and privilege management. Guidance is provided on general areas in which to perform these important tasks, but details on exactly how to perform them are beyond the scope of the guide.

Additional valuable guidance for security in the typical SANS hands-on format can be found in the SANS course `SEC577 Virtualization Security Fundamentals`. Additional information can be found at [http://www.sans.org/security-training/virtualization-security-fundamentals-3807-tid](http://www.sans.org/security-training/virtualization-security-fundamentals-3807-tid).

While the `SEC577 Virtualization Security Fundamentals` course covers many of the vSphere Hardening Guide recommendations, it also provides insight into many areas not covered in the official vSphere Hardening Guide. In the author’s opinion it is a valuable and highly recommended resource.

## SANS SEC577 Virtualization Security Fundamentals

- Virtualization basics and introduction
- Virtual networking
- Virtual switch security policies
- Command-line virtual network configuration and administration
- Virtual network architecture design
- vCenter security and administration
- Virtual infrastructure client security
- ESX and ESXi security
- ESX file system security
- VM guest security
- Storage considerations
- Backup and recovery
- Virtualization risk assessment
- Virtualization threats
- Virtualization vulnerabilities

## Password Policy Recommendations

### COP03: Establish a password policy for password history

Use and enforcement of a password policy can go a long way in reducing the risk of passwords being guessed or otherwise cracked.

The repeated reuse of old passwords increases the likelihood that the password will be guessed or cracked. The password policy should address the issue of password reuse through tracking password history.

### COP04: Establish a maximum password aging policy

Using a control to establish how long a password can be used before it is changed can go a long way in reducing the risk of passwords being guessed or otherwise cracked.

### COP05: Establish a password policy for minimum days before a password is changed

One trick users often use is to quickly change their new password multiple times so they can override the typical password reuse constraints. This often occurs right after a mandatory password change is required where the user then quickly changes the password multiple times and returns back to a password they are familiar with. Setting a minimum period of time before a password can be changed can mitigate this issue.

### COP06: Ensure that purser auto password change in vCenter meets policy

The `vpxuser` password is automatically changed every 30 days by default. Be sure this policy in fact meets with the requirements of your password policy.

## Logging Configuration

### COL01: Configure syslog logging

Using remote syslog logging can reduce administrative burden as well as reducing the risk that an attacker that compromised a given machine can easily cover their tracks by deleting or modifying the logs on the local compromised machine.

### COL02: Configure NTP time synchronization

Time synchronization across all systems within the virtual environment in the author’s opinion is a necessity and makes troubleshooting issues and responding to incidents significantly easier and more accurate. Not utilizing time synchronization could in fact cause you to miss the fact that an incident occurred in the first place. Lastly, several VMware operations, such as `vMotion`, require that time be accurately synchronized across the respective hosts/guests in order for the operation to be completed successfully.

## File System Integrity

### COH01: Partition the disk to prevent the root file system from filling up

Like most Linux derivatives, if the root file system fills on ESX it can degrade the ability to manage it and, worst case, can make it unresponsive, creating a DoS.

### COH03: Establish and maintain file system integrity

Monitoring the integrity of the configuration files could be your first indication of a security incident.

### COH04: Ensure permissions of important files and utility commands have not been changed from default

File permissions should be checked by a thorough file integrity system as part of the overall file integrity check. Altering a files permissions can impact its ability to function and could result in a DoS.

## Access Control

### COA01: Prevent tampering at boot time

The service console in ESX, like most other Linux derivatives, can allow a user to enter kernel options such as booting in to single user mode during boot. A grub password is recommended to reduce the risk of an unauthorized person from passing options to the kernel during boot.

### COA02: Require authentication for single user mode

An additional layer of security can be provided to COA01 by also requiring a password to enter single user mode.

### COA03: Ensure root access via SSH is disabled

You simply cannot audit specifically who is issuing commands or performing tasks when a user logs in as root via SSH. Disabling root from logging in to SSH forces the user to first log in with their own account, creating an audit trail, and then use `su` or `sudo` to elevate their level of privilege.

### COA04: Disallow console root login

As with SSH in COA03, you simply cannot audit specifically who is issuing commands or performing tasks when a user logs in as root via the local console when using a connected screen and keyboard. Disabling root from logging in to the console locally forces the user to first log in with their own account, creating an audit trail, and then use `su` or `sudo` to elevate their level of privilege.

### COA05: Limit access to the su command

Use of the `su` command dramatically increases the level of privilege for a given logged-in user and should be carefully controlled.

### COA06: Configure and use sudo to control administrative access

Use of the `sudo` utility can dramatically increase the level of privilege for a given logged-in user and should be carefully controlled. The configuration files for sudo users can be configured to granularly and explicitly specify which privileged commands the user can execute when using `sudo`.
