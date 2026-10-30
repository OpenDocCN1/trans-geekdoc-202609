
12. One of your SANs is reaching capacity. During your investigation, you notice a very large number of transaction logs and backups from the customer service database. When you ask why there are so many logs, you’re told that no one knows how long they’re supposed to keep those logs and when it’s okay to delete them. What should your organization develop to help prevent runaway accumulation of log files?

A. Data encryption policy
B. HSM policy
C. Data retention policy
D. Customer service policy

13. Which of the following technologies is used to help secure access to “big data”?

A. HSM encryption
B. Kerberos-based authentication
C. Account whitelisting
D. Secure protocol methodology

14. Your manager is extremely worried about attacks occurring inside your network between systems. He’s convinced that someone from Engineering is attacking his system just to “mess with him.” You don’t currently have any good way to monitor the traffic between your manager’s system and the rest of the network. Which of the following capabilities could you recommend to help your manager see if his system is really under attack?

A. Host-based vulnerability scanner
B. Host-based intrusion detection system
C. Host-based pop-up blocker
D. Host-based anti-spyware

15. A developer wants you to set up a system she can run multiple tests on with the ability to return the system to its starting configuration over and over again as she tests out different versions of code. She thinks virtualization might be the way to go. What virtualization capability will help satisfy her testing and rollback requirement?

A. Sandboxing
B. Snapshots
C. Host elasticity
D. Baselining

## Answers

1. B. Cable locks are a good way to secure laptops to a desk or table. They allow access to the laptop keyboard, USB ports, and optical drive and secure the laptop to whatever the cable is mounted to.

2. C. If you are looking for protection from things that “infect” your computer, you should install a good antivirus program, ensure it receives regular updates, and configure it to perform regular scans, including on removable media.

3. A. A good way to ensure that only programs you want to run are allowed to run is to use application whitelisting. An application whitelist is a list of programs that the administrator has granted permission to run on that system.

4. B. If a system is directly connected to the Internet and you need to protect it from Internet-based probes, scans, and attacks, you will definitely need a host-based firewall. A host-based firewall performs the same functions as a network-based firewall—it blocks traffic you don’t want coming in and allows traffic going out that you want to go out. But a host-based firewall only works at the host level—it only protects the system it is running on.

5. C. A patch management system allows you to control and track the patch status of any system it is managing. With a patch management system, you can schedule updates, determine which updates are applied, and verify the patch status of any connected system.

6. A. Host software baselining is the establishment of all essential requirements of both the operating system and applications installed on a host system.

7. C. Trusted operating system is used to refer to an operating system that provides support for multilevel security and meets the specifications for use as a trusted operating system.

8. D. Your colleague is describing the process of sandboxing. A “sandbox” is a means for separating untrusted code and applications from trusted code and applications. When sandboxing is done correctly, anything that happens in the sandbox is controlled and is prevented from harming the host system.

9. A. Your boss wants a laptop with a Trusted Platform Module (TPM). A TPM is a specialized chip that stores encryption keys specific to the host system for hardware authentication. When BitLocker encrypts an entire drive, it stores the encryption keys within the TPM.

10. B. Data that is stored on a drive but is not currently being accessed is referred to as “data at rest.”

11. A. Your colleague is performing operating system hardening—he’s securing the system by reducing vulnerabilities and minimizing the potential attack surface. Removing unnecessary software and services, patching, and restricting the traffic that can go into or out of the system are all steps to help secure, or “harden,” the system against potential attacks.

12. C. In this situation your organization could really use a good data retention policy. A data retention policy balances the legal, business, or operational need to keep records against the risk and cost of keeping those records. The policy should also clarify how long records should be kept and under what circumstances it’s permissible to destroy those records.

13. B. Kerberos-based authentication is one of the methods used to help secure access to “big data.” Kerberos is a network authentication protocol that uses “tickets” to allow systems to identify and authenticate each other even if the network they are operating on is insecure.

14. B. A host-based intrusion detection system (or HIDS) would help your manager determine whether or not his system is under attack. An HIDS works in the same fashion as a network-based IDS, but it operates at the host level. It examines traffic coming into and leaving the host for attack signatures and patterns. An HIDS can only really protect the system it is installed on.

15. B. The ability to work with snapshots inside a virtualization environment will satisfy the developer’s requirements. Snapshots are copies of the state of a virtual machine at a specific point in time—the file system, memory contents, power state, and so forth are all captured and stored as part of the snapshot. Users have the ability to roll back or revert to snapshots that restore the virtual machine to the state captured by that snapshot, regardless of any changes that were made to the virtual machine.

## Securing Alternative Environments

In this chapter, you will

- Learn how to compare and contrast alternative methods to mitigate security risks in static environments
- Understand the role of security in alternative environments
- Examine risk associated with alternative environments

Traditionally, the term computing has been associated with mainframes, servers, workstations, and network components. Today, computing also plays a role in many other environments, from ATM machines and SCADA control systems to embedded systems, smartphones, and gaming consoles.

There are a wide variety of methods that can be employed to assist in securing of non-traditional systems. Some of these are direct copies of methods employed in traditional IT systems, while others are unique to these alternative environments.

## Alternative Environments

Alternative environments are those that are not traditional computer systems in a common IT environment. This is not to say that these environments are rare; in fact, there are millions of systems, composed of hundreds of millions of devices, all across society. Computers exist in many systems where they perform critical functions specifically tied to a particular system. These alternative systems are frequently static in nature; that is, their software is unchanging over the course of its function. Updates and revisions are few and far between. While this may seem to be counter to current security practices, it isn't: because these alternative systems are constrained to a limited, defined set of functionality, the risk from vulnerabilities is limited. Examples of these alternative environments include embedded systems, SCADA systems, mobile devices, mainframes, game consoles, and in-vehicle computers.

## SCADA

SCADA is an acronym for *supervisory control and data acquisition*, a system designed to control automated systems in cyber-physical environments. SCADA systems control manufacturing plants, traffic lights, refineries, energy networks, water plants, building automation and environmental controls, and a host of other systems. SCADA is also known by names such as distributed control systems (DCS) and industrial control systems (ICS), the variations depending on the industry and the configuration. Where computers control a physical process directly, a SCADA system likely is involved.

Most SCADA systems involve multiple components networked together to achieve a set of functional objectives. These systems frequently include a human machine interface (HMI), where an operator can exert a form of directive control over the operation of the system under control. SCADA systems historically have been isolated from other systems, but the isolation is decreasing as these systems are being connected across traditional networks to improve business functionality. Many older SCADA systems were air gapped from the corporate network; that is, they shared no direct network connections. This meant that data flows in and out were handled manually and took time to accomplish. Modern systems wished to remove this constraint and added direct network connections between the SCADA networks and the enterprise IT network. These connections increase the attack surface and the risk to the system, and the more they resemble an IT networked system, the greater the need for security functions.

SCADA systems have been drawn into the security spotlight with the Stuxnet attack on Iranian nuclear facilities, initially reported in 2010. Stuxnet is malware designed to specifically attack a specific SCADA system and cause failures resulting in plant equipment damage. This attack was complex and well designed, crippling nuclear fuel processing in Iran for a significant period of time. This attack raised awareness of the risks associated with SCADA systems, whether connected to the Internet or not (Stuxnet crossed an air gap to hit its target).

## Embedded Systems

*Embedded system* is the name given to a computer that is included as an integral part of a larger system. From computer peripherals like printers, to household devices like smart TVs and thermostats, to the car you drive, embedded systems are everywhere. Embedded systems can be as simple as a microcontroller with fully integrated interfaces (a system on a chip) or as complex as the tens of interconnected embedded systems in a modern automobile. Embedded systems are designed with a single control purpose in mind and have virtually no additional functionality, but this does not mean that they are free of risk or security concerns. The vast majority of security exploits involve getting a device or system to do something it is capable of doing, and technically designed to do, even if the resulting functionality was never an intended use of the device or system.

The designers of embedded systems typically are focused on minimizing costs, with security seldom seriously considered as part of either the design or the implementation. Because most embedded systems operate as isolated systems, the risks have not been significant. However, as capabilities have increased, and these devices have become networked together, the risks have increased significantly. For example, smart printers
