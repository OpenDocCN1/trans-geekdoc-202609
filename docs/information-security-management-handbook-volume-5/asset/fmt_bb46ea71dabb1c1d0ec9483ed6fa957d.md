
The TCP SYN attack is a form of denial of service attack. Many wireless attacks use this method to cause a host to release its IP address and request a new IP address to a rogue wireless access point in the attempt to break the weak encryption algorithms. Carnegie Mellon’s Software Engineering Institute (2001, para 1) states, “a denial-of-service attack is characterized by an explicit attempt by attackers to prevent legitimate users of a service from using that service.”

Buffer overflows may be lumped into the DoS category, but hackers use buffer overflows typically to gain root access to a server (i.e., again think DNS or RAS server) by crashing a thread or application being run. A buffer overflow occurs when a program or process attempts to store more data than the address space (i.e., temporary data storage area or RAM) it was intended to hold (Kurtz, McClure, & Scambray, 2005). If the address space isn’t well defined (within the programs) and the input and output aren’t checked against that finite amount of address space, that extra information, which has to go somewhere, overflows into adjacent buffers and corrupts or overwrites the valid data held in them.

An address space represents the amount of space or memory available to a program. For example, think of address space as filling up an ice tray to place in the freezer. If someone were to overfill one space or cell of that ice tray, the water dumps over into the next adjacent slot. Each slot, for this analogy, represents a single program running in memory.

While both viruses and worms are malicious code, they are not the only forms. There is spyware, and mobile code in the form of Java applets or Active X, VBS scripts, etc., which can bring a network down if they are malicious in nature. Mobile code has been defined on Wikipedia as software transferred between systems (perhaps transferred across a network or via a USB flash drive) and executed on a local system without explicit installation or execution by the recipient. Examples of mobile code include JavaScript, VBScripts, ActiveX controls, and macros embedded within Office documents.

The most commonly used attack method on the Internet is to use an exploit against a known software bug (i.e., vulnerability). Most issues with security come from the application layers software vulnerabilities (i.e., OSI model). One example is the buffer overflows, which is the result of poorly written code. Another, yet different, example is an implementation issue such as the TCP SYN attacks which appeared several years ago for IPv4. This was not a software bug in implementations, but rather an attack against the base specification for TCP. Another similar example includes the vulnerabilities that appeared for the Simple Network Management Protocol (SNMP) several years ago (CERT, 2008).

Finally the most common exploit is to simply scan the network boundaries, gather information on the type of applications, services, hardware used on a particular network segment, and the IP address range for a respective network segment. Specifically, we are discussing the term footprinting (Kurtz, McClure, & Scambray, 2005). Once the network is mapped and cataloged, a hacker simply exposes the security architecture tools that protect a network segment to known vulnerabilities to gain access to an organization.

# Address Space Problems

The goal here is not to rehash a very well-documented and published problem but to discuss the address space problems from an IA perspective. Due to the manner in which IP address space has been allocated, “there are routinely over 85,000 routes in the routing tables of Internet backbone routers” (Microsoft, 2008, 1). Network Address Translator (NAT) was developed to mitigate the shrinking address space by mapping multiple “private addresses to a single public IP address” (Microsoft, 2008, 1). Unfortunately, IP-enabled phones attempt to connect to one another (i.e., Voice over IP (VoIP)) and the NAT frequently makes that configuration extremely difficult to manage (Beijnum, 2006). IPv6 introduced the Secure Internet Protocol (IPsec), which was eventually made backwards compatible for IPv4. However, when two endpoints attempt to establish the tunnel, the two ends usually can’t agree on IP addresses. This problem results because somewhere in the middle, NAT translated the IP address for one of the endpoints (Beijnum, 2006). Finally, if an individual has experience with attempting to establish an IPsec tunnel and multiple vendors are involved, then one knows it is virtually impossible to use IPsec solutions from various vendors because of the various proprietary IPsec implementations used by vendors.

# IPv6 Introduction

A brief history on the Internet was provided in the Introduction. It was stated that the original Internet designers could not have foreseen or planned for the explosive growth of the Internet. The Internet has changed from its original planned use. Routing for the current Internet is very inefficient, Quality of Service (QoS) support is lacking today’s requirement for real-time delivery of data, and the IPsec support is a patchwork project—best-case scenario.

IPv6 is the next-generation Internet, which is being designed to address many of the shortcomings of IPv4. The first RFC for IPv6 was published in 1995 and since then there have been revisions (Beijnum, 2006).

# Similarities between IPv4 and IPv6

Perhaps the easiest way to understand the similarities is to inspect the internal headers of both IP versions. [Figure 7.3](#9781466508507_epub_c07_r1.htm#fig_7.3) represents the 32-bit IPv4 header next to the 128-bit IPv6 header. The gold-colored areas are the same with the exception of the increase in bit size for the source and destination address. The “version” designation area is the same and delineates whether an IPv4 or IPv6 datagram is being sent. The areas marked in blue are the same features, but have been moved and have a new name, though they both provide the same basic features. Below are the IPv4 fields marked in blue mapped against the similar field that was moved and renamed in the IPv6 header:

1\. Type of service = traffic class

2\. Total length = payload length

3\. Time to live = hop limit

4\. Protocol = next header

![](OEBPS/images/fig_7.3.jpg)

![](OEBPS/images/line-2.jpg)

**Figure 7.3 IPv4 and IPv6 header comparison. (From Cisco, IPv6 Extension Headers Review and Considerations. [http://www.ciscosistemas.org/en/US/technologies/tk648/tk872/technologies_white_paper0900aecd8054d37d.pdf](http://www.ciscosistemas.org/en/US/technologies/tk648/tk872/technologies_white_paper0900aecd8054d37d.pdf). 2006.)**

An earlier discussion was provided on the various common attack methods for IPv4 under the common attack method subheading. It was also stated that the IP is a connectionless based protocol located on the network layer of the OSI model. If it isn’t apparent at this point, then for clarification, the upper-level layers from the OSI model (i.e., 5–7) have the same basic implementations. Hence IPv6 is vulnerable to many exploits currently used on the Internet. IPv6 inherits many of the same challenges. This is an important issue to understand for the remainder of this chapter. The IP is the network layer based upon the OSI model, so most of the common category of attacks mentioned earlier are inherited in IPv6. Think about it: if an application is poorly written, and assuming that there is no IP address embedded in the code for it to run, the TCP and UDP are the same in IPv6. So why is it commonly thought that IPv6 is more secure than IPv4?

# IPv6 Misunderstandings
