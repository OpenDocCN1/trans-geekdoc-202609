
# The OSI Model

Let’s begin with the `OSI model`, or Open Systems Interconnection model, which describes how networks communicate. It outlines the various protocols and activities, and it tells how the protocols and activities relate to each other. This model is divided into seven layers, as shown in [Table 2.6](#ch02.xhtml#ch02tab06), and was originally developed by the International Organization for Standardization (abbreviated ISO) in the 1980s.

## Table 2.6 The OSI Model

| Layer Number | Layer Name | Description | Protocols |
|---|---|---|---|
| 7 | Application | This layer interfaces directly to the application and performs common application services for the application processes. | POP, SMTP, DNS, FTP, and so on |
| 6 | Presentation | The presentation layer relieves the application layer of concern regarding syntactical differences in data representation within the end-user systems. |   |
| 5 | Session | The session layer provides the mechanism for managing the dialogue between end-user application processes. | NetBIOS |
| 4 | Transport | This layer provides end-to-end communication control. | TCP, UDP |
| 3 | Network | This layer routes the information in the network. | IP, Address Resolution Protocol, Internet Control Message Protocol |
| 2 | Data link | This layer describes the logical organization of data bits transmitted on a particular medium. The data link layer is divided into two sublayers: the Media Access Control (MAC) layer and the Logical Link Control (LLC) layer. | Serial Line Internet Protocol, Point-to-Point Protocol |
| 1 | Physical | This layer describes the physical properties of the various communications media as well as the electrical properties and interpretation of the exchanged signals. In other words, the physical layer is the actual NIC, Ethernet cable, and so forth. This layer is where bits are translated into voltages and vice versa. | None |

Many networking students memorize this model. It’s good to at least memorize the names of the seven layers and to understand basically what each one does. From a security perspective, the more you understand about network communications, the more sophisticated your defense can be. The most important thing for you to understand is that the OSI model describes a hierarchy of communication. One layer will only communicate with the layer directly above it or below it.

## Media Access Control (MAC) Addresses

A `MAC address` is a unique address for a NIC. (MAC is also a sublayer of the data link layer of the OSI model.) Every NIC in the world has a unique address that is represented by a 6-byte hexadecimal number, and ARP is used to convert IP addresses to MAC addresses. When you type in a web address, DNS is used to translate that into an IP address; then ARP translates that IP address into a specific MAC address of an individual NIC.

How is DNS is accomplished; that is, how does a URL get translated into an IP address? How does a computer know what IP goes with what URL? There are servers known as DNS servers that are set up just to do this task. If you are on a corporate network, you probably have a DNS server on your network. If you are not, then your ISP has one. These servers maintain a table of IP-to-URL entries. From time to time there are transfers of DNS data, called `zone transfers`, that allow one DNS server to send its changes to another. Across the Internet, there are root DNS servers that are maintained with centralized data for all registered URLs/IP addresses.

## Summary

This chapter cannot make you a networking expert. However, you should now have a basic understanding of how networks and the Internet work. Before you move on to subsequent chapters, you should make certain you completely understand basic hardware such as switches, NICs, routers, and hubs. You should also be familiar with the basic protocols presented in this chapter. It is important that you be comfortable with the utilities presented. It is strongly suggested that you experiment with these utilities extensively. It is also important that you be comfortable with the basics of the OSI model. Many students struggle with it at first, but at least make sure you have a general understanding of it before you move on to [Chapter 3](#ch03.xhtml#ch03), “[Cyber Stalking, Fraud, and Abuse](#ch03.xhtml#ch03).”

The material in this chapter will be critical in later chapters. If you are new to this material, you should thoroughly study this chapter before continuing. In the exercises at the end of this chapter, you will be able to practice using `IPConfig`, `tracert`, and `ping`.

## Test Your Skills

### Multiple Choice Questions

**[1](#app02.xhtml#ch02ans1).** Malek is purchasing cable to use in setting up small office networks. He wants to stock up on commonly used cable. What type of cable do most networks use?

**A.** Net cable

**B.** STP

**C.** Phone cable

**D.** UTP

**[2](#app02.xhtml#ch02ans2).** You are assigned with attaching connectors to segments of cable. What type of connector is used with network cables?

**A.** RJ-11

**B.** RJ-85

**C.** RJ-12

**D.** RJ-45

**[3](#app02.xhtml#ch02ans3).** What type of cable is used in most networks?

**A.** Unshielded twisted-pair

**B.** Shielded twisted-pair

**C.** Unshielded untwisted-pair

**D.** Shielded untwisted-pair

**[4](#app02.xhtml#ch02ans4).** John is trying to simply connect three computers in a small network. He does not need any sort of routing capability and is not concerned about network traffic. What is the simplest device for connecting computers?

**A.** NIC

**B.** Interface

**C.** Hub

**D.** Router

**[5](#app02.xhtml#ch02ans5).** Sharice is trying to teach a new technician basic networking terms. What should she tell this new technician NIC stands for?

**A.** Network interface card

**B.** Network interaction card

**C.** Network interface connector

**D.** Network interaction connector

**[6](#app02.xhtml#ch02ans6).** Which of the following is a device used to connect two or more networks?

**A.** Switch

**B.** Router

**C.** Hub

**D.** NIC

**[7](#app02.xhtml#ch02ans7).** Juan has just installed a new T1 line in a medical office. The front desk receptionist has asked what speed they can expect. A T1 line sends data at what speed?

**A.** 100Mbps

**B.** 1.54Mbps

**C.** 155Mbps

**D.** 56.6Kbps

**[8](#app02.xhtml#ch02ans8).** How big is a TCP packet header?

**A.** The size depends on the data being sent.

**B.** The size is always 20 bytes.

**C.** The size depends on the protocol being used.

**D.** The size is always 40 bytes.

**[9](#app02.xhtml#ch02ans9).** What protocol translates web addresses into IP addresses?

**A.** DNS

**B.** TFTP

**C.** DHCP

**D.** SMTP

**[10](#app02.xhtml#ch02ans10).** What protocol is used to send email, and on what port does it work?

**A.** SMTP, port 110

**B.** POP3, port 25

**C.** SMTP, port 25

**D.** POP3, port 110

**[11](#app02.xhtml#ch02ans11).** Gunther is setting up encrypted remote communications so that the server administrators can remotely access servers. What protocol is used for remotely logging on to a computer in a secure manner?

**A.** SSH

**B.** HTTP

**C.** Telnet

**D.** SMTP

**[12](#app02.xhtml#ch02ans12).** Mohammed needs to open a firewall port so that web traffic can be passed through the firewall. What protocol is used for web pages, and on which port does it work?

**A.** HTTP, port 21

**B.** HTTP, port 80

**C.** DHCP, port 80

**D.** DHCP, port 21

**[13](#app02.xhtml#ch02ans13).** What is the name for the point where the backbones of the Internet connect?

**A.** Connectors

**B.** Routers

**C.** Network access points

**D.** Switches

**[14](#app02.xhtml#ch02ans14).** You are examining a list of IP addresses. Some are internal, some are external, and some are not valid. Which of the following is not a valid IP address?
