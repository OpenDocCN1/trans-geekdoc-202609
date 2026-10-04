
![](img/e71dc48d3ae3db3394e5857ab2acae75_135_0.png)

Figure 3-11 Competing Protocol Suites

- **AppleTalk:** Apple released this short-lived proprietary protocol suite in 1985 for Apple devices. In 1995, Apple adopted TCP/IP to replace AppleTalk.
- **Novell NetWare:** Novell developed this short-lived proprietary protocol suite and network operating system in 1983, using the IPX network protocol. In 1995, Novell adopted TCP/IP to replace IPX.

## TCP/IP Protocol Example (3.3.3)

TCP/IP protocols are available for the application, transport, and internet layers. There are no TCP/IP protocols in the network access layer. The most common network access layer LAN protocols are Ethernet and WLAN (wireless LAN) protocols. Network access layer protocols are responsible for delivering IP packets over the physical medium.

Figure 3-12 shows an example of the three TCP/IP protocols used to send packets between the web browser of a host and a web server. HTTP, TCP, and IP are the TCP/IP protocols used. At the network access layer, Ethernet is used in the example. However, this could also be a wireless standard, such as WLAN or cellular service.

## TCP/IP Protocol Suite (3.3.4)

Today, the TCP/IP protocol suite includes many protocols and continues to evolve to support new services. Some of the most popular TCP/IP protocols are shown in Figure 3-13.

![](img/e71dc48d3ae3db3394e5857ab2acae75_136_0.png)

Figure 3-12 TCP/IP Protocols Used for Web Client/Server Communications

![](img/e71dc48d3ae3db3394e5857ab2acae75_136_1.png)

Figure 3-13 Examples of Protocols in the TCP/IP Protocol Suite

## Application Layer

The application layer includes network applications and protocols for devices utilizing the network, including

- **Name system**
  - DNS: Domain Name System. DNS translates domain names, such as cisco.com, into IP addresses.
- **Host config**
  - DHCPv4: Dynamic Host Configuration Protocol for IPv4. A DHCPv4 server dynamically assigns IPv4 addressing information to DHCPv4 clients at startup and allows the addresses to be reused when no longer needed.
  - DHCPv6: Dynamic Host Configuration Protocol for IPv6. DHCPv6 is similar to DHCPv4. A DHCPv6 server dynamically assigns IPv6 addressing information to DHCPv6 clients at startup.
  - SLAAC: Stateless address autoconfiguration. SLAAC allows a device to obtain its IPv6 addressing information without using a DHCPv6 server.
- **Email**
  - SMTP: Simple Mail Transfer Protocol. SMTP enables clients to send email to a mail server and enables servers to send email to other servers.
  - POP3: Post Office Protocol version 3. POP3 enables clients to retrieve email from a mail server and download the email to the client's local mail application.
  - IMAP: Internet Message Access Protocol. IMAP enables clients to access email stored on a mail server as well as maintain email on the server.
- **File transfer**
  - FTP: File Transfer Protocol. FTP sets the rules that enable a user on one host to access and transfer files to and from another host over a network. FTP is a reliable, connection-oriented, and acknowledged file delivery protocol.
  - SFTP: SSH File Transfer Protocol. As an extension to Secure Shell (SSH) protocol, SFTP can be used to establish a secure file transfer session in which the file transfer is encrypted. SSH is a method for secure remote login that is typically used for accessing the command line of a device.
  - TFTP: Trivial File Transfer Protocol. TFTP is a simple, connectionless file transfer protocol with best-effort, unacknowledged file delivery. It requires less overhead than FTP.

### Web and web service

- **HTTP:** Hypertext Transfer Protocol. HTTP is a set of rules for exchanging text, graphic images, sound, video, and other multimedia files on the World Wide Web.
- **HTTPS:** HTTP Secure. HTTPS is a secure form of HTTP that encrypts the data exchanged over the World Wide Web.
- **REST:** Representational State Transfer. REST is a method of using application programming interfaces (APIs) and HTTP requests to create web applications.

## Transport Layer

The transport layer provides host-to-host communication services, including

### Connection oriented

- **TCP:** Transmission Control Protocol. TCP enables reliable communication between processes running on separate hosts and provides reliable, acknowledged transmissions that confirm successful delivery.

### Connectionless

- **UDP:** User Datagram Protocol. UDP enables a process running on one host to send packets to a process running on another host. However, UDP does not confirm successful datagram transmission.

## Internet Layer

The internet layer is used to transport packets from the originating source to the final destination. The internet layer includes

### Internet Protocol

- **IPv4:** Internet Protocol version 4. IPv4 receives message segments from the transport layer, packages messages into packets, and addresses packets for end-to-end delivery over a network. IPv4 uses a 32-bit address.
- **IPv6:** IP version 6. IPv6 is similar to IPv4 but uses a 128-bit address.
- **NAT:** Network Address Translation. NAT translates IPv4 addresses from a private network into globally unique public IPv4 addresses.

### Messaging

- **ICMPv4:** Internet Control Message Protocol for IPv4. ICMPv4 provides feedback from a destination host to a source host about errors in packet delivery.
- **ICMPv6:** ICMP for IPv6. ICMPv6 is similar in functionality to ICMPv4 but is used for IPv6 packets.
- **ICMPv6 ND:** ICMPv6 Neighbor Discovery. ICMPv6 ND includes four protocol messages that are used for address resolution and duplicate address detection.

### Routing protocols

- **OSPF:** Open Shortest Path First. OSPF is a link-state routing protocol that uses a hierarchical design based on areas. OSPF is an open standard interior routing protocol.
- **EIGRP:** Enhanced Interior Gateway Routing Protocol. EIGRP is a Cisco-proprietary routing protocol that uses a composite metric based on bandwidth, delay, load, and reliability.
- **BGP:** Border Gateway Protocol. BGP is an open standard exterior gateway routing protocol used between internet service providers (ISPs). BGP is also commonly used between ISPs and their large private clients to exchange routing information.

## Network Access Layer

The network access layer provides communication services across the physical network, typically from one network interface card (NIC) to another NIC on the same network. The network access layer includes

### Address resolution

- **ARP:** Address Resolution Protocol. ARP provides dynamic address mapping between an IPv4 address and a hardware address.

### Data link protocols

- **Ethernet:** Ethernet defines the rules for wiring and signaling standards of the network access layer.
- **WLAN:** Wireless local-area network. WLAN protocols define the rules for wireless signaling across the 2.4 GHz and 5 GHz radio frequencies.

## TCP/IP Communication Process (3.3.5)

Figures 3-14 through 3-20 demonstrate the complete TCP/IP communication process, using an example of a web server transmitting data to a client. This process and these protocols are covered in more detail in later chapters. These are the basic steps in the process:

Go to the course online to view an animation of the TCP/IP communication process.

Step 1. In Figure 3-14, the process begins with the web server preparing the Hypertext Markup Language (HTML) page as data to be sent.

Step 2. The application protocol HTTP header is added to the front of the HTML data. The header contains various information, including the HTTP version the server is using and a status code indicating that it has information for the web client.

![](img/e71dc48d3ae3db3394e5857ab2acae75_140_0.png)

Figure 3-14 Preparing HTML to Be Sent

Step 3. The HTTP application layer protocol delivers the HTML-formatted web page data to the transport layer, as shown in Figure 3-15. TCP adds header information to the HTTP data. The TCP transport layer protocol is used to manage individual conversations, in this example between the web server and the web client.

Step 4. Next, the IP information is added to the front of the TCP information, as shown in Figure 3-16. IP assigns the appropriate source and destination IP addresses. This information is known as an IP packet.

Step 5. The Ethernet protocol adds information to both ends of an IP packet, known as a data link frame, as shown in Figure 3-17.

Step 6. This data is now transported through the internetwork, as shown in Figure 3-18. The internetwork, represented by the cloud in the figure, is a collection of media and intermediary devices.
