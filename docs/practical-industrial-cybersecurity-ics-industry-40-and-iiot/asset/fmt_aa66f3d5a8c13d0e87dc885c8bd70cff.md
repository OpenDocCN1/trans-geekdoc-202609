
## Chapter 4: ICS Modules and Element Hardening

### Review Question Answers

1.  You can think of protecting individual IT or ICS devices in terms of three layers of security:

    1.  The outer perimeter is the space around the outside of the physical device and its housing.

    2.  The inner perimeter should be viewed as the device's operating system and application programs.

    3.  The interior of the device consists of the intangible data assets—the information created, obtained, and stored electronically in the device.

    For more information, see the section “User Workstation Hardening.”

2.  Autonomous or semi-autonomous ICS control devices, such as `PLCs` or stand-alone microcontrollers, can normally be placed in secure, lockable enclosures where access is limited to only those people possessing the key. For more information, see the section “User Workstation Hardening.”

3.  Just as joining the ICS network to the enterprise network opens new avenues for outsiders to exploit the previously more secure ICS, bringing `BYOD` devices into the network opens even more vulnerabilities. Network administrators and security personnel must determine whether such a `BYOD` environment creates security gaps for their networks. For more information, see the section “Mobile Device Protection.”

4.  While not trivial, these systems are vulnerable to being exploited by those who possess some specialized hardware and a few skills. By getting close to a user with an `RFID` badge, a hacker can read the target's badge information using their own reader. Once they have captured the badge data, they can make their own badge to circumvent access controls. This could occur while the user is in the cafeteria, at a local coffee shop, or even through a small `IoT` device hidden in the office or production facility. For more information, see the section “Near Field Communications.”

5.  The principle of least privilege access. This principle should be implemented when providing users with access to objects through rights and permissions assignments. Under the least privilege rule, each user is only granted the levels of access required to perform their job role. Applying this principle consistently limits the damage that can be inflicted by a security breech to the initial task, process, or user. For more information, see the section “Logical Server Access Control.”

6.  Isolation, segmentation, firewalling, and least privilege usage configuration: Virtual networks are by default isolated from each other. And, because communications within the virtual network never leave the virtual environment, there is no need for network segmentation to be configured and maintained with the physical network or firewall. For more information, see the section “Virtualization.”

7.  Applying software updates and patches. Security patches are updates issued for the specific purpose of correcting an observed weakness to prevent exploitation of the vulnerability. For more information, see the section “Applying Software Updates and Patches.”

8.  In almost every environment, organizational policy will call for all servers to have a real-time scanning antivirus application installed, along with a real-time antispyware program. In particular, these applications are required if the server is a file server or has nonadministrative users who have remote access capabilities. For more information, see the section “Implementation.”

9.  Antivirus and other anti-malware programs have traditionally been inappropriate for use with `OT` computing and control devices. These types of scanning applications are performance hogs when they are running. Due to the real-time computing requirements of `ICS` controllers, the presence of these types of security applications would introduce communication and computing delays that would be unacceptable and potentially dangerous to equipment and personnel. However, growing numbers of organizations are opting to run anti-malware applications in their `OT` environments, under strictly controlled implementation and management. For more information, see the section “Implementation.”

10.  Poorly written programming code for public-facing forms, such as login forms. For more information, see the section “SQL Injection.”

11.  As with servers in enterprise networks, the most important question concerning database security is, where should the database be located in the network? The most common method of securing the data historian is to place it in a secure network structure, such as a `DMZ`, between the enterprise and `ICS` networks. For more information, see the section “Database Hardening.”

12.  Public key encryption (`PKE`). This technique employs two keys to ensure the security of the encrypted data: a public key and a private key. For more information, see the section “File System Security.”
