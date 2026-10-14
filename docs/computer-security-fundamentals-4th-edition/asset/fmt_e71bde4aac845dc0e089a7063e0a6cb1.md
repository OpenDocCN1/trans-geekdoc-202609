
| POP3 (Post Office Protocol version 3) || Retrieves email. || 110 |

| NNTP (Network News Transfer Protocol) || Used for network newsgroups (Usenet newsgroups). You can access these groups over the Web via [www.google.com](http://www.google.com) and selecting the Groups tab. || 119 |

| NetBIOS || An older Microsoft protocol that is for naming systems on a local network. || 137, 138, or 139 |

| IMAP (Internet Message Access Protocol) || More advanced protocol for receiving email. Widely replacing POP3. || 143 |

| IRC (Internet Relay Chat) || Used for chat rooms. || 194 |

| SMB (Server Message Block) || Used for Windows Active Directory. || 445 |

| HTTPS || Encrypted HTTP; used for secure websites. || 443 |

| SMTPS (Simple Mail Transfer Protocol Secure) || Encrypted SMTP. || 465 |

| POP3S (Post Office Protocol version 3 Secure) || Encrypted POP3. || 995 |

| IMAPS (Internet Message Access Protocol Secure) || Encrypted IMAP. || 993 |

Each of these protocols will be explained in more detail, as needed, in later chapters of this book. You should also note that this list is not complete, as there are dozens of other protocols; but these are the basic protocols we will be discussing in this book. All of these protocols are part of a suite of protocols referred to as `TCP/IP` (Transmission Control Protocol/Internet Protocol). But no matter the particular protocol being used, all communication on networks takes place via packets, and those packets are transmitted according to certain protocols, depending on the type of communication that is occurring.

##### Ports

You may be wondering what a port is, especially since we’ve already talked about the ports that are the connection locations on the back of your computer, such as serial ports, parallel ports, and RJ-45 and RJ-11 ports. A *port*, in networking terms, is a handle, or a connection point. It is a numeric designation for a particular pathway of communications. You can think of a port as a channel number on your television. You may have one cable coming into your TV, but you can tune to a variety of channels. There are 65,535 network communications ports on your computer. This is true regardless of type of computer or operating system. The combination of your computer’s IP address and port number is referred to as a `socket`. All network communication, regardless of the port used, comes into your computer via the connection on your NIC.

So, the picture we’ve drawn of networks, to this point, is one of machines connected to each other via cables, and perhaps to hubs, switches, or routers. These networks transmit binary information in packets using certain protocols and ports.

### How the Internet Works

Now that you have a basic idea of how computers communicate with each other over a network, it is time to discuss how the Internet works. The Internet is essentially a large number of networks that are connected to each other. Therefore, the Internet works exactly the same way as your local network. It sends the same sort of data packets, using the same protocols. These various networks are simply connected to main transmission lines called `backbones`. The points where the backbones connect to each other are called `network access points` (`NAPs`). When you log on to the Internet, you probably use an `Internet service provider` (`ISP`). That ISP has a connection either to the Internet backbone or to yet another provider that has a backbone. So, logging on to the Internet is a process of connecting your computer to your ISP’s network, which is, in turn, connected to one of the backbones on the Internet.

#### IP Addresses

With tens of thousands of networks and millions of individual computers communicating and sending data, a predictable problem arises. That problem is ensuring that the data packets go to the correct computer. This task is accomplished in much the same way as traditional “snail” mail letter is delivered to the right person: via an address. With network communications, this address is a special one, referred to as an “IP” address. An IP address can be IP version 4 or version 6.

##### IPv4

An `IP address` is a series of four values, separated by periods. (An example would be `107.22.98.198`.) Each of the three-digit numbers must be between 0 and 255; thus, the address `107.22.98.466` would not be valid. These addresses are actually four binary numbers; you just see them in decimal format. Since each of these numbers is really just a decimal representation of 8 bits, they are often referred to as `octets`. So there are four octets in an IPv4 address. Recall that a byte is 8 bits (1s and 0s), and an 8-bit binary number converted to decimal format will be between 0 and 255. So you don’t have to do the math yourself, I will tell you that this rule means there are a total of over 4.2 billion possible IP addresses. You should not be concerned, however, that we will run out of new IP addresses soon. There are methods already in place (which are discussed later) to extend the use of addresses.

FYI: Converting Binary Numbers

For those readers not familiar with converting decimal to binary, there are several methods, one of which is shown here. You should be aware that the computer will do this for you in the case of IP addresses, but here’s one way—and perhaps the simplest—this is done:

Divide repeatedly by 2, using “remainders” rather than decimal places, until you get down to 1. For example, to convert decimal 31 to binary:

*   `31/2` = 15 Remainder 1

*   `15/2` = 7 Remainder 1

*   `7/2` = 3 Remainder 1

*   `3/2` = 1 Remainder 1

*   `1/2` = 0 Remainder 1

Now read the remainders from bottom to top: The binary equivalent is `11111`.

IP addresses fall into two groups: public and private. Public IP addresses are for computers connected to the Internet. No two public IP addresses can be the same. However, a private IP address, such as one on a private company network, only has to be unique in that network. It does not matter if other computers in the world have the same IP address because this computer is never connected to those other worldwide computers. Often network administrators use private IP addresses that begin with a 10, such as `10.102.230.17`.

It should also be pointed out that often an ISP will buy a pool of public IP addresses and assign them to you when you log on. An ISP might own 1000 public IP address and have 10,000 customers. Because all 10,000 customers will not be online at the same time, the ISP simply assigns an IP address to a customer when he logs on, and the ISP unassigns the IP address when the customer logs off.

The address of a computer tells you a lot about that computer. The first byte (or the first decimal number) in an address tells you to what class of network that machine belongs. [Table 2.5](#ch02.xhtml#ch02tab05) summarizes the five network classes.

**Table 2.5** Network Classes 

| Class || IP Range for the First Byte || Use |

| --- | --- | --- |

| A || 0–126 || Extremely large networks. No Class A network IP addresses are left. All have been used. |

| --- | --- | --- |

| B || 128–191 || Large corporate and government networks. All Class B IP addresses have been used. |

| C || 192–223 || The most common group of IP addresses. Your ISP probably has a Class C address. |

| D || 224–247 || These are reserved for multicasting (transmitting different data on the same channel). |

| E || 248–255 || Reserved for experimental use. |
