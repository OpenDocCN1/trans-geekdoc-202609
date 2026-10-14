
is normally very difficult to do. However, if the attacker sends an RST message, which terminates a connection, this protection is greatly reduced. In fact, it is fairly easy to send RST messages that close legitimate open connections. Security that results from the inherent operation of a standard is called incidental security.

### Security Explicitly Designed into the Standard

A second issue is security explicitly designed into the standard. Most standards were initially created without any security. If security was added in later versions, it was often done in an awkward way. For instance, IP, which is the main protocol for delivering packets over the Internet, originally had no security. The IPsec standards were created to address this weakness, but IPsec is burdensome and not widely used.

### Security in Older Versions of the Standard

Third, even when security is added to a standard, it usually is added only to later versions of the standard. If a company uses an older version of the standard, it is limited in terms of the security it can implement.

### Defective Implementation

A fourth issue is the security of defective standards implementations in vendor products. These defective implementations may create vulnerabilities that attackers can exploit even if the standard itself is highly secure.

### Test Your Understanding

- 7. List the four security problems with protocols. Write one sentence describing each.

## A.4 Core Layers in Layered Standards Architectures

Standards are complex. A common way to deal with complex problems is to break them down into smaller parts. Figure A-8 shows that standards are divided into three **core layers**. Collectively, these layers have the functionality needed to allow any application program on one host on one network of an internet to interoperate with another program on another host on any other network of the internet.

The highest core layer governs the interactions of *applications*. For instance, World Wide Web access is governed by the Hypertext Transfer Protocol (HTTP). In World Wide Web access, the two application programs—the browser on the client PC and the webserver program on the webserver—have to send messages governed by the HTTP standard.

The middle core layer is the *internet core layer*. Standards at this layer govern how packets are delivered across an internet, including the global Internet. One of the main standards at the internet core layer is the Internet Protocol (IP).

The lowest core layer is the *single-network core layer*. Standards at this layer govern the transmission of frames across the switches and transmission lines in a single network (a LAN or WAN).

| Super Layer | Description |
|---|---|
| Application | Communication between application programs on different hosts attached to different networks on an internet. |
| Internetworking | Transmission of packets across an internet. Packets contain application layer messages. |
| Network | Transmission of frames across a network. Frames contain packets. |

Figure A-8 Three Core Standards Layers

### Test Your Understanding

- 8. a. What are the three core standards layers?
  - b. Distinguish between the single-network core layer and the internet core layer.
  - c. At what core layer do you find LAN standards?
  - d. At what core layer do you find WAN standards?
  - e. At what core layer do you find standards for the global Internet?

## A.5 Standards Architectures

Standards are created by standards agencies. The first action of a standards agency is to produce a broad layering plan called a standards architecture. Next, standards agencies create standards for the individual layers. Figure A-9 shows two popular layered standards architectures and relates these to the three core layers we just saw.

### Test Your Understanding

- 9. What is a standards architecture?

### The TCP/IP Standards Architecture

The Internet Engineering Task Force (IETF) is the standards agency for the Internet. Its standards architecture is called TCP/IP—a name taken from two of its most important standards, TCP and IP. Figure A-9 shows that TCP/IP has four layers. The bottom layer—the subnet access layer—corresponds to the single-network core layer. The top layer is the application layer, which corresponds to the application core layer. The two middle layers—the internet and transport layers—correspond to the internet core layer. TCP/IP is primarily used to govern internetworking. Dividing the internet core layer into two TCP/IP layers permits greater division of labor in standards development. The highest layer is the application layer.

IETF documents are publicly available at no charge. Most of these documents are requests for comments (RFCs). Some RFCs are Internet Official Protocol Standards, but not all are. Periodically, an RFC specifies a current list of Internet Official Protocol Standards. To find an RFC, search for it in any search engine. For instance, to find the initial RFC for the Internet Protocol, search for “RFC 791” in any search engine.

| Super Layer | TCP/IP | OSI | Hybrid TCP/IP-OSI |
|---|---|---|---|
| Application | Application | Application | Application |
|  |  | Presentation |  |
|  |  | Session |  |
| Internet | Transport | Transport | Transport |
|  | Internet | Network | Internet |
| Single network | Subnet access | Data link | Data link |
|  |  | Physical | Physical |

Figure A-9 Layered Standards Architectures

### Test Your Understanding

- 10. a. Which organization creates Internet standards?
  - b. What is the name of its standards architecture?
  - c. What is an RFC?
  - d. How can you tell which RFCs are Internet Official Protocol Standards?

### The OSI Standards Architecture

The other standards architecture shown in the figure is OSI, which is rarely spelled out by its full name, the Reference Model of Open Systems Interconnection. OSI is governed by two standards agencies. One is ISO, the International Organization for Standardization. The other is ITU-T, the International Telecommunications Union-Telecommunications Standards Sector. (No, the official names and the official acronyms do not match.)

Figure A-9 shows that OSI divides the three core layers into a total of seven layers. OSI single-network standards use the bottom two OSI layers—the physical and data link layers, which we will discuss in more detail later. OSI’s market dominance is so strong at the physical and data link layers that the IETF rarely develops standards at these layers. The “subnet access” indication in the TCP/IP framework basically means, “Use OSI standards here.” The OSI network and transport layers correspond to the internet and transport layers of TCP/IP. OSI divides the application core layer into three layers—session, presentation, and application.

### Test Your Understanding

- 11. a. Which two standards agencies govern OSI? (Just give their acronyms.)
  - b. Distinguish between OSI and ISO.
  - c. How many layers does the OSI architecture have?
  - d. Which of these layers are similar to the layers in TCP/IP?
  - e. Compare the TCP/IP application layer with comparable OSI layers.

### The Hybrid TCP/IP–OSI Architecture

Which of these two standards architectures is dominant? The answer is, “neither.” What nearly all firms use today is the hybrid TCP/IP-OSI standards architecture, which Figure A-9 illustrates. This hybrid architecture uses OSI standards at the physical and data link layers and TCP/IP standards at the internet and transport layers. Corporations also use standards from some other standards architectures at the internet and transport layers, but TCP/IP standards dominate.

At the application core layer, the situation is complex. Both OSI and TCP/IP standards are used, often in combination. In fact, OSI application standards often reference TCP/IP application standards and vice versa. Although OSI and TCP/IP are often viewed as rivals, this is not the case at all. Several other standards agencies also create application core layer standards, complicating the picture even further.

### Test Your Understanding

- 12. a. What architecture do most firms actually use?
  - b. In the hybrid TCP/IP–OSI architecture, which layers come from OSI?
  - c. Which come from TCP/IP?
  - d. From what standards architecture do application layer standards come?

## A.6 Single-Network Standards

As noted earlier, OSI standards are dominant in the two single-network layers—the physical and data link layers. These are the two layers that define LAN and WAN standards. Figure A-10 shows how the physical and data link layers are related.

### Test Your Understanding

- 13. What two layers define LAN and WAN standards?

### The Data Link Layer

The path that a frame takes through a single network is called a data link. The source computer sends the frame to the first switch, which forwards the frame to the next switch along the data link, which forwards the frame further. The last switch along the data link passes the frame to the destination computer (or router, if the packet in the frame is destined for a computer on another network).

Figure A-10 Physical and Data Link Layers

![](img/073342643701cc54eb7875c41ab92ef2_552_0.png)
