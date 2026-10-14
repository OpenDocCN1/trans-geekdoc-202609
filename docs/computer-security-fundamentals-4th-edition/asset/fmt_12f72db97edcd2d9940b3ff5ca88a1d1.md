
1. Using one of the preferred web resources listed in this chapter, find three policy or procedure documents from that resource.

2. List the documents you selected.

3. Write a brief essay explaining why those particular documents are important to your organization’s security.

**Exercise 1.5:** Learning About the Law

1. Using the Web, journals, books, or other resources, find out if your state or territory has any laws specific to computer security. You might find the following websites helpful:

    [www.pbs.org/wgbh/pages/frontline/shows/hackers/blame/crimelaws.html](http://www.pbs.org/wgbh/pages/frontline/shows/hackers/blame/crimelaws.html)

    [www.cybercrime.gov](http://www.cybercrime.gov)

2. List three laws that you find for your region and provide a brief one- or two-sentence description of each.

#### Projects

**Project 1.1:** Learning About a Virus

1. Using web resources from [Appendix A](#app01.xhtml#app01) and sites such as [www.f-secure.com](http://www.f-secure.com), find a virus that has been released in the past 6 months.

2. Research how the virus spread and what damage it caused.

3. Write a brief (half to one page) paper on this virus. Explain how the virus worked, how it spread, and any other essential information you can find.

**Project 1.2:** Considering the Law (a Group Project)

Write a description of a computer law that you would like to have passed, along with specifics related to its implementation, enforcement, and justification.

**Project 1.3:** Recommending Security

1. Using the Web, journals, or books, locate security recommendations from any reputable source, such as the SANS Institute. Any of the sites mentioned in the “[Online Security Resources](#ch01.xhtml#ch01lev1sec8)” section of this chapter would be a good choice.

2. List five of those recommendations.

3. Explain why you agree or disagree with each of these five recommendations.

Case Study

In this case study we will consider a network administrator for a small, family-oriented video store. The store is not part of a chain of stores and has a very limited security budget. It has five machines for employees to use to check out movies and one server on which to keep centralized records. That server is in the manager’s office. The administrator takes the following security precautions:

*   Each machine is upgraded to Windows 10, with the personal firewall turned on.

*   Antivirus software has been installed on all machines.

*   A tape backup is added to the server, and tapes are kept in a file cabinet in the manager’s office.

*   Internet access to employee machines is removed.

Now consider these questions:

1.  What have these actions accomplished?

2.  What additional actions might you recommend?

## Chapter 2. Networks and the Internet

Chapter Objectives

After reading this chapter and completing the exercises, you will be able to do the following:

*   Identify each of the major protocols used in network communication (for example, FTP and Telnet) and what use you can make of each of them

*   Understand the various connection methods and speeds used on networks

*   Compare and contrast a hub and a switch

*   Identify what a router is and what it’s used for

*   Understand how data is transmitted over a network

*   Explain how the Internet works and the use of IP addresses and URLs

*   Recount a brief history of the Internet

*   Use network utilities such as `ping`, `IPConfig`, and `tracert`

*   Describe the OSI model of network communication and the use of MAC addresses

### Introduction

To be able to manage network security, you will need knowledge about how computer networks operate. Those readers who already have a strong working knowledge of network operations may choose to skim this chapter or perhaps give it a quick read as a review. For other readers new to computer networking, studying this chapter will give you a basic introduction to how networks and the Internet work, including a history of the Internet. This understanding of networks and the Internet will be crucial to your comprehension of later topics presented in this book.

In this chapter we will begin by examining the basic technologies, protocols, and methods used for networks and the Internet to communicate. Then we will take a look at the history of the Internet. This information forms the background knowledge you will need to understand various cyber attacks and how they are defended against. In the exercises at the end of the chapter, you will be able to practice using some protective methods, such as `IPConfig`, `tracert`, and `ping`.

### Network Basics

Getting two or more computers to communicate and transmit data is a process that is simple in concept but complex in application. Consider all the factors involved. First you will need to physically connect the computers. This connection usually requires either a cable that plugs into your computer or wireless connection. The cable then is plugged either directly to another computer or into a device that will, in turn, connect to several other computers.

Of course, wireless communication is being used with more frequency, and wireless connection, obviously, doesn’t require a cable. However, even wireless communication relies on a physical device to transmit the data. There is a card in most modern computers called a *network interface card,* or NIC. If the connection is through a cable, the part of the NIC that is external to the computer has a connection slot that looks like a telephone jack, only slightly bigger. Wireless networks also use a NIC; but rather than having a slot for a cable to connect to, the wireless network uses radio signals to transmit to a nearby wireless router or hub. A wireless router, hub, or NIC must have an antenna to transmit and receive signals. These devices are connective devices that will be explained in detail later in this chapter.

#### The Physical Connection: Local Networks

As mentioned, using cables is one of the ways that computers are connected to each other. The cable connection used with traditional NICs (meaning not wireless) is an RJ-45 connection. (*RJ* is short for Registered Jack, which is an international industry standard.) In contrast to the computer’s RJ-45 jacks, standard telephone lines use RJ-11 jacks. The biggest difference between jacks involves the number of wires in the connector, also called the *terminator*. Phone lines have four wires (though some have six wires), whereas RJ-45 connectors have eight wires.

If you look on the back of most computers or the connection area of a laptop, you will probably find two ports that, at first glance, look like phone jacks. One of the two ports is probably for a traditional modem and accepts a standard RJ-11 jack. The other port is larger and accepts an RJ-45 jack. It would be extremely rare to find a modern computer that did not have a NIC.

This standard connector jack must be on the end of the cable. The cable used in most networks today is a Category 5 or Category 6 cable, abbreviated as Cat 5 cable or Cat 6 cable. The specifications for cable are laid out in ISO/IEC 11801. [Table 2.1](#ch02.xhtml#ch02tab01) summarizes the various categories of cable and their uses.

**Table 2.1** Cable Types and Uses 

| Category || Specifications || Uses |

| --- | --- | --- |

| 1 || Low-speed analog (less than 1MHz) || Telephone, doorbell |

| 2 || Analog line (less than 10MHz) || Telephone |

| 3 || Up to 16MHz or 100Mbps (megabits per second) || Voice transmissions |

| 4 || Up to 20MHz/100Mbps || Data lines, Ethernet networks |

| 5 || 100MHz/100Mbps || Most common a few years ago; still widely used |

| 6 || 1000Mbps (some get 10Gbps) || Most common type of network cable |

| 6a || 10Gbps || High-speed networks |

| 7 || 10Gbps || Very high-speed networks |

| 8 || 40Gbps || Not yet commonly found |
