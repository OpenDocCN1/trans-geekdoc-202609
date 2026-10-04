
use the ip default-gateway ip-address global configuration command. Use the IPv4 address of the local router interface that is connected to the switch.

## Video—Network Device Differences: Part 1 (10.4.1)

## Video—Network Device Differences: Part 2 (10.4.2)

## Packet Tracer—Basic Device Configuration (10.4.3)

Your network manager is impressed with your performance in your job as a LAN technician. She would like you to now demonstrate your ability to configure a router connecting two LANs. Your tasks include configuring basic settings on a router and a switch using Cisco IOS. You will then verify your configurations as well as the configurations on existing devices by testing end-to-end connectivity.

## Lab—Build a Switch and Router Network (10.4.4)

In this lab, you will complete the following objectives:

- Part 1: Set Up the Topology and Initialize Devices
- Part 2: Configure Devices and Verify Connectivity
- Part 3: Display Device Information

## Practice

The following activities provide practice with the topics introduced in this chapter. The lab is available in the companion *Introduction to Networks Labs & Study Guide (CCNAv7)* (ISBN 9780136634454). The Packet Tracer activity instructions are also provided in the *Labs & Study Guide*. The PKA files are available in the online course.

## Lab

Lab 10.4.4: Build a Switch and Router Network

![](img/e71dc48d3ae3db3394e5857ab2acae75_373_0.png)

## Packet Tracer Activities

- Packet Tracer 10.1.4: Configure Initial Router Settings
- Packet Tracer 10.3.4: Connect a Router to a LAN
- Packet Tracer 10.3.5: Troubleshoot Default Gateway Issues
- Packet Tracer 10.4.3: Basic Device Configuration

## Check Your Understanding Questions

Complete all the review questions listed here to test your understanding of the topics and concepts in this chapter. The appendix “Answers to ‘Check Your Understanding’ Questions” lists the answers.

1. A router boots without any preconfigured commands. What is the reason for this?

+   a. The IOS image is corrupt.
b. Cisco IOS is missing from flash memory.
c. The configuration file is missing from NVRAM.
d. The POST process has detected hardware failure.

2. Which command is used to encrypt all passwords in a router configuration file?

+   a. Router_A(config)# enable secret <password>
b. Router_A(config)# service password-encryption
c. Router_A(config)# enable password <password>
d. Router_A(config)# encrypt password

3. Company policy requires you to use the most secure method to safeguard access to the privileged EXEC and configuration mode on the routers. The privileged EXEC password is trustknow1. Which of the following router commands achieves the goal of providing the highest level of security?

+   a. secret password trustknow1
b. enable password trustknow1
c. service password-encryption
d. enable secret trustknow1

4. What will be the command prompt from the router after the command router(config)# hostname portsmouth is entered?

+   - a. portsmouth#
- b. portsmouth(config)#
- c. invalid input detected
- d. hostname portsmouth#
- e. ? command not recognized
  Router(config)#

5. An administrator is configuring a new router to permit out-of-band management access. Which set of commands will allow the required login using the password cisco?

+   - a. Router(config)# line vty 0 4
  Router(config-line) password manage
  Router(config-line) exit
  Router(config)# enable password cisco
- b. Router(config)# line vty 0 4
  Router(config-line) password cisco
  Router(config-line) login
- c. Router(config)# line console 0
  Router(config-line) password cisco
  Router(config-line) login
- d. Router(config)# line console 0
  Router(config-line) password cisco
  Router(config-line) exit
  Router(config)# service password-encryption

6. Which command can be used on a Cisco router to display all interfaces, the IPv4 address assigned, and the current status?

+   - a. show ip interface brief
- b. ping
- c. show ip route
- d. show interface fa0/1

7. Which CLI mode allows users to access all device commands, such as those used for configuration, management, and troubleshooting?

+   - a. user EXEC mode
- b. privileged EXEC mode
- c. global configuration mode
- d. interface configuration mode

8. What is the purpose of the startup configuration file on a Cisco router?

+   - a. It facilitates the basic operation of the hardware components of a device.
- b. It contains the commands that are used to initially configure a router on startup.
- c. It contains the configuration commands that the router IOS is currently using.
- d. It provides a limited backup version of IOS, in case the router cannot load the full-featured IOS.

9. Which characteristic describes the default gateway of a host computer?

+   - a. the logical address of the router interface on the same network as the host computer
- b. the physical address of the switch interface connected to the host computer
- c. the physical address of the router interface on the same network as the host computer
- d. the logical address assigned to the switch interface connected to the router

10. What is the purpose of the banner motd command?

+   - a. It configures a message that identifies printed documents to LAN users.
- b. Routers use it to communicate the status of their links with one another.
- c. It provides an easy way of communicating with any user attached to a router's LAN.
- d. It provides a way to make announcements to those who log in to a router.

11. A technician is configuring a router to allow for all forms of management access. As part of each different type of access, the technician is trying to type the command login. Which configuration mode should be used to do this task?

+   - a. user EXEC mode
- b. global configuration mode
- c. console line and vty line configuration modes
- d. privileged EXEC mode

12. What is stored in the NVRAM of a Cisco router?

+   - a. Cisco IOS
- b. the running configuration
- c. the bootup instructions
- d. the startup configuration

13. Which statement regarding the service password-encryption command is true?

+   - a. It is configured in privileged EXEC mode.
- b. It encrypts only line mode passwords.
- c. When the service password-encryption command is entered, all plaintext passwords are encrypted.
- d. To see the passwords encrypted by the service password-encryption command in plaintext, issue the no service password-encryption command.

## Objectives

Upon completion of this chapter, you will be able to answer the following questions:

- What is the structure of an IPv4 address, including the network portion, the host portion, and the subnet mask?
- What are the characteristics and uses of unicast, broadcast, and multicast IPv4 addresses?
- What are public, private, and reserved IPv4 addresses?
- How does subnetting a network enable better communication?
- How do you calculate IPv4 subnets for a /24 prefix?
- How do you calculate IPv4 subnets for /16 and /8 prefixes?
- Given a set of requirements for subnetting, how do you implement an IPv4 addressing scheme?
- How do you create a flexible addressing scheme using variable-length subnet masking (VLSM)?
- How do you implement a VLSM addressing scheme?

## Key Terms

This chapter uses the following key terms. You can find the definitions in the glossary at the end of the book.

*octet boundary*  *page 364*
*intranet*  *page 375*
*DMZ*  *page 375*
*variable-length subnet masking (VLSM)*  *page 381*

## Introduction (11.0)

Plenty of networks are still using IPv4 addressing today, while organizations are making the transition to IPv6. So it is still very important for network administrators to know everything they can about IPv4 addressing. This chapter covers the fundamental aspects of IPv4 addressing in detail. It covers how to segment a network into subnets and how to use variable-length subnet masking (VLSM) as part of an overall IPv4 addressing scheme. Subnetting is like cutting a pie into smaller and smaller pieces. Subnetting may seem overwhelming at first, but we show you some tricks to help you along the way. This chapter includes several videos, activities to help you practice subnetting, Packet Tracer activities, and labs. Once you get the hang of IPv4 addressing, you'll be on your way to network administration!

## IPv4 Address Structure (11.1)

This section presents the IPv4 address structure.

### Network and Host Portions (11.1.1)

An IPv4 address is a 32-bit hierarchical address that is made up of a network portion and a host portion. When determining the network portion versus the host portion, you must look at the 32-bit stream, as shown in Figure 11-1.

![](img/e71dc48d3ae3db3394e5857ab2acae75_378_0.png)

Figure 11-1 Network and Host Portions of an IPv4 Address

The bits in the network portion of the address must be identical for all devices that reside in the same network. The bits in the host portion of the address must be unique to identify a specific host within a network. If two hosts have the same bit pattern in the specified network portion of the 32-bit stream, those two hosts reside in the same network.

But how do hosts know which portion of the 32 bits identifies the network and which identifies the host? That is the role of the subnet mask.
