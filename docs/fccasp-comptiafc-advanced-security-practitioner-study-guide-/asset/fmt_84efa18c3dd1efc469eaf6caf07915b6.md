
### 3. HVAC Controllers
Systems designed to control a home or business HVAC system over the Internet. One example is Nest, which was purchased by Google in 2014.

### 4. Sensors
A variety of components that can be used to activate light switches, open gates and doors, and provide other home automation over the Internet. Medical equipment, pacemakers, implantable devices, and auto/truck computers/sensors/locks are just some of the devices with sensors.

### 5. Physical Access Control Systems
Items used for the control of access such as Bluetooth and RFID locks.

### 6. A/V Systems
Technology designed for the automation of audiovisual (AV) systems. These systems can include in-home TVs, home AV networks (PC controlled), and also corporate AV with projectors and videoconferencing.

### 7. Scientific/Industrial Equipment
This includes power generation equipment, SCADA, industrial motors, and even power generation.

## Summary

Host security can be divided into two broad categories:

*   Reducing the attack surface
*   Implementing controls to detect and respond to a problem

Host hardening, restricting command-line ability, removing unwanted applications and programs, deploying a standard operating system, and using Group Policy to implement strong security are all techniques used to reduce the attack surface. Each removes or restricts the ability of an attacker or malicious individual.

Some of the controls discussed in this chapter have the ability to detect or remove a problem. These include anti-malware, anti-spyware, spam filters, firewalls, HIDSs, NIDSs, HIPSs, and NIPSs. These tools and techniques can help limit the damage done by malicious code and can even prevent an attack from occurring. Devices such as IDSs may be placed at the network boundary; others such as antivirus may reside on the host. Each of these controls adds to the concept of defense in depth. This layering tactic seeks to defend any system against any attack using multiple methods that vary.

## Exam Essentials

1.  **Be able to describe host-based firewalls.** Host-based firewalls usually have predefined rules to protect the host against basic attack patterns. Some host-based firewalls can also prevent malicious software from attacking other devices on the network.

2.  **Be able to describe a trusted OS.** A trusted operating system (TOS) can be defined as one that has implemented sufficient controls to support multilevel security. Trusted OSs must be tested to demonstrate evidence of correctness to meet specific standards. These standards require the TOS to have undergone testing and validation.

3.  **Know the importance of endpoint security solutions.** Endpoint security consists of the controls placed on client systems such as control of USB and CD/DVD, antivirus, anti-malware, and anti-spyware.

4.  **Be able to describe antivirus.** Antivirus typically uses one of several techniques to identify and eradicate viruses. These methods include signature-based detection, which uses a signature file to identify viruses and other malware, and heuristic-based detection, which looks for deviation from normal behavior of an application or service. This detection method is useful against unknown and polymorphic viruses.

5.  **Be able to describe anti-spyware.** Spyware is a term that has come to describe a variety of undesirable software programs, whose bad behavior ranges from annoying you with pop-up ads to surreptitiously sending your private information to other people.

6.  **Be able to describe spam filters.** The classic approach to filtering spam is defense in depth. This edge–hub technique uses several layers of defense to deal with spam. The idea is to start filtering email at the moment it reaches the edge of the network.

7.  **Be able to describe host hardening.** Host hardening can be described as a series of steps that are carried out to remove unwanted services and features for the purpose of making it harder for an attacker to successfully attack a computer.

8.  **Be able to describe a standard operating environment.** A standard operating system is a standardized build of a host system to be used throughout the organization. This reduces the TCO and provides a standard build. This aids in configuration management and makes patching and upgrading easier.

9.  **Know the characteristics of command shell restrictions.** Restricting the users' access to the command prompt is another way to tighten security. There are many commands a user can run from the command prompt that can weaken security or allow an attacker to escalate their privilege on a host system. Not only should the security administrator block access to the command line, but they should also disable unneeded programs such as FTP, Telnet, and TFTP.

10. **Be able to explain warning banners.** Warning banners are brief messages used to inform users of specific policies and procedures regarding the use of applications and services. A warning banner can be a splash screen, pop-up, or message box that informs the user of specific rules.

11. **Know what a restricted interface is.** A restricted interface is a profile that dictates what programs, menus, applications, commands, or functions are available within an environment. This technique allows a security administrator to control the users' environment and dictate what objects they have access to. This technique is considered a restricted interface because the user can only use the provided environment to interface with the operating system, installed applications, and resources.

12. **Be able to describe data exfiltration.** Data exfiltration is the unauthorized transfer of data from a computer. With so many possible ways for an attacker to extract data out of a network, data exfiltration is a big problem. Private data can be compromised, resulting in loss of revenues, organizational fines, and loss of trust.

13. **Be able to describe IDSs and IPSs.** An intrusion detection system (IDS) gathers and analyzes information from a computer or a network it is monitoring. There are three basic ways in which intrusions are detected: signature recognition, anomaly detection, and protocol decoding. NIDSs are designed to capture and analyze network traffic. HIDSs are designed to monitor a computer system and not the network. A network IPS system can react automatically and actually prevent a security occurrence from happening, preferably without user intervention. Host-based intrusion prevention is generally considered capable of recognizing and halting anomalies.

## Review Questions

1.  By default, what is at the end of every ACL?
    **A.** A stateful inspection checkpoint
    **B.** An implicit allow statement
    **C.** A command that checks for ICMP
    **D.** An implicit `deny all` statement

2.  Which of the following can extended ACLs not check for?
    **A.** Protocol
    **B.** Port number
    **C.** Response value
    **D.** Precedence value

3.  Extended ACLs can process all of the following except which one?
    **A.** SSL
    **B.** ICMP
    **C.** TCP
    **D.** UDP

4.  An NIDS can do which of the following with encrypted email network traffic?
    **A.** Nothing
    **B.** Scan for viruses
    **C.** Alert if malicious
    **D.** Full content inspection

5.  One item of importance to the CASP is trusted operating systems. Several standards have been developed to measure trust in an operating system. One such standard is TCSEC. TCSEC mandatory protection can be defined as?
    **A.** Category A
    **B.** Category B
    **C.** Category C
    **D.** Category D

6.  ITSEC has how many assurance levels?
    **A.** 5
    **B.** 7
    **C.** 9
    **D.** 11

7.  EAL 3 is equal to which of the following?
    **A.** Semi-formally designed and tested
    **B.** Methodically checked and tested
    **C.** Functionally tested
    **D.** Methodically designed, tested, and reviewed
