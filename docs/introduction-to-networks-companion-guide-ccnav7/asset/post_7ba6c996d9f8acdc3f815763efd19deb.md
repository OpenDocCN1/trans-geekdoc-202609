
2. Which term refers to a network that provides secure access to the corporate offices for suppliers, customers, and collaborators?

- a. internet
- b. intranet
- c. extranet
- d. extended net

3. A large corporation has modified its network to allow users to access network resources from their personal laptops and smartphones. Which networking trend does this describe?

- a. cloud computing
- b. online collaboration
- c. bring your own device
- d. video conferencing

4. What is an ISP?

- a. It is a standards body that develops cabling and wiring standards for networking.
- b. It is a protocol that establishes how computers in a local network communicate.
- c. It is an organization that enables individuals and businesses to connect to the internet.
- d. It is a networking device that combines the functionality of several different networking devices in one.

5. For which of the following would the use of a WISP be recommended?

- a. an internet café in a city
- b. a farm in a rural area without wired broadband access
- c. any home with multiple wireless devices
- d. an apartment in a building with cable access to the internet

6. What characteristic of a network enables it to quickly grow to support new users and applications without impacting the performance of the service being delivered to existing users?

- a. reliability
- b. scalability
- c. quality of service
- d. accessibility

7. A college is building a new dormitory on its campus. Workers are digging in the ground to install a new water pipe for the dormitory. A worker accidentally damages a fiber-optic cable that connects two of the existing dormitories to the campus data center. Although the cable has been cut, students in the dormitories experience only a very short interruption of network services. What characteristic of the network is described here?

- a. quality of service
- b. scalability
- c. security
- d. fault tolerance
- e. integrity

8. What are two characteristics of a scalable network? (Choose two.)

- a. easily overloaded with increased traffic
- b. grows in size without impacting existing users
- c. is not as reliable as a small network
- d. suitable for modular devices that allow for expansion
- e. offers limited number of applications

9. Which device performs the function of determining the path that messages should take through internetworks?

- a. a router
- b. a firewall
- c. a web server
- d. a DSL modem

10. Which two internet connection options do not require that physical cables be run to a building? (Choose two.)

- a. DSL
- b. cellular
- c. satellite
- d. dialup
- e. dedicated leased line

11. What type of network must a home user access in order to do online shopping?

- a. an intranet
- b. the internet
- c. an extranet
- d. a local area network

12. How does BYOD change the way businesses implement networks?

- a. BYOD requires organizations to purchase laptops rather than desktops.
- b. BYOD users are responsible for their own network security, thus reducing the need for organizational security policies.
- c. BYOD devices are more expensive than devices that are purchased by an organization.
- d. BYOD provides flexibility in where and how users can access network resources.

13. An employee wants to access the network of an organization remotely, in the safest possible way. What network feature would allow an employee to gain secure remote access to a company network?

- a. ACL
- b. IPS
- c. VPN
- d. BYOD

14. What is the internet?

- a. It is a network based on Ethernet technology.
- b. It provides network access for mobile devices.
- c. It provides connections through interconnected global networks.
- d. It is a private network for an organization with LAN and WAN connections.

15. What are two functions of end devices on a network? (Choose two.)

- a. They originate the data that flows through the network.
- b. They direct data over alternate paths in the event of a link failure.
- c. They filter the flow of data to enhance security.
- d. They are the interface between humans and the communications network.
- e. They provide the channel over which the network message travels.

This page intentionally left blank

## Basic Switch and End Device Configuration

## Objectives

Upon completion of this chapter, you will be able to answer the following questions:

- How do you access a Cisco IOS device for configuration purposes?
- How do you navigate Cisco IOS to configure network devices?
- What is the command structure of Cisco IOS software?
- How do you configure a Cisco IOS device using the CLI?
- How do you use IOS commands to save the running configuration?
- How do devices communicate across network media?
- How do you configure a host device with an IP address?
- How do you verify connectivity between two end devices?

## Key Terms

This chapter uses the following key terms. You can find the definitions in the glossary at the end of the book.

kernel page 46
shell page 46
command-line interface (CLI) page 46
graphical user interface (GUI) page 46
Cisco Internetwork Operating System (IOS) page 48
firmware page 48
console page 49
Secure Shell (SSH) page 50
Telnet page 50
user EXEC mode page 53
privileged EXEC mode page 53
global configuration mode page 53
ping page 57
traceroute page 57
virtual terminal (vty) page 64
nonvolatile random-access memory page 67
random-access memory page 67
IPv4 address page 72
subnet mask page 72
IPv6 address page 72
switch virtual interface (SVI) page 74
Dynamic Host Configuration Protocol (DHCP) page 76
Domain Name System (DNS) page 76

## Introduction (2.0)

As part of your career in networking, you might have to set up a new network or maintain and upgrade an existing one. In either case, you'll configure switches and end devices so that they are secure and perform effectively based on your requirements.

Out of the box, switches and end devices come with some general configuration. But for your particular network, switches and end devices require your specific information and instructions. In this module, you will learn how to access Cisco IOS network devices. You will learn basic configuration commands and use them to configure and verify a Cisco IOS device and an end device with an IP address.

Of course, there is much more to network administration, but none of that can happen until switches and end devices are configured. Let's get started!

## Cisco IOS Access (2.1)

This section introduces the operating system used in most Cisco devices.

## Operating Systems (2.1.1)

Every end device and network device must have an operating system (OS). As shown in Figure 2-1, the portion of the OS that interacts directly with computer hardware is known as the kernel. The portion that interfaces with applications and the user is known as the shell. The user can interact with the shell by using a command-line interface (CLI) or a graphical user interface (GUI):

![](img/e71dc48d3ae3db3394e5857ab2acae75_82_0.png)

Figure 2-1 Shell, Kernel, and Hardware

- **Shell:** The shell is the user interface that allows users to request specific tasks from the computer. These requests can be made either through the CLI or a GUI.
- **Kernel:** The kernel communicates between the hardware and software of a computer and manages how hardware resources are used to meet software requirements.
- **Hardware:** Hardware is the physical part of a computer, including underlying electronics.

When using a CLI, the user interacts directly with the system in a text-based environment by entering commands on the keyboard at a command prompt, as shown in Example 2-1. The system executes the command and often provides textual output. Operating the CLI requires very little overhead; however, it does require that the user have knowledge of the underlying command structure that controls the system.

## Example 2-1 CLI Example

```
analyst@secOps ~]$ ls
Desktop  Downloads  lab.support.files  second_drive
[analyst@secOps ~]$
```

## GUI (2.1.2)

A GUI such as Windows, macOS, Linux KDE, Apple iOS, or Android allows a user to interact with a system using an environment of graphical icons, menus, and windows. Compared to a CLI, the Windows 10 GUI example in Figure 2-2 is more user friendly and requires less knowledge of the underlying command structure that controls the system. For this reason, most users rely on GUI environments.

![](img/e71dc48d3ae3db3394e5857ab2acae75_83_0.png)

Figure 2-2 Windows 10 GUI
