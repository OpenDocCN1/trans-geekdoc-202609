
Routers implement routing protocols to route packets between networks. The packet forwarding performed by these intermediary devices involves examining the network layer addressing in the packet header. In all cases, the data portion of the packet—that is, the encapsulated transport layer PDU or other data—remains unchanged during the network layer processes.

## Characteristics of IP (8.1.3)

IP was designed as a protocol with low overhead. It provides only the functions that are necessary to deliver a packet from a source to a destination over an interconnected system of networks. The protocol was not designed to track and manage the flow of packets. These functions, if required, are performed by other protocols at other layers, primarily TCP at Layer 4.

These are the basic characteristics of IP:

- *Connectionless*: There is no connection with the destination established before sending data packets.
- *Best effort*: IP is inherently unreliable because packet delivery is not guaranteed.
- *Media independent*: Operation is independent of the medium (that is, copper, optical fiber, or wireless) carrying the data.

## Connectionless (8.1.4)

IP is connectionless, meaning that no dedicated end-to-end connection is created by IP before data is sent. Connectionless communication is conceptually similar to sending a letter to someone without notifying the recipient in advance. Figure 8-3 illustrates this key point.

![](img/e71dc48d3ae3db3394e5857ab2acae75_307_0.png)

A letter is sent.

Figure 8-3 Letter Analogy of Connectionless Communication

Connectionless data communications work on the same principle. As shown in Figure 8-4, IP requires no initial exchange of control information to establish an end-to-end connection before packets are forwarded.

![](img/e71dc48d3ae3db3394e5857ab2acae75_308_0.png)

A packet is sent.

Figure 8-4 IP is Connectionless

## Best Effort (8.1.5)

IP does not require additional fields in the header to maintain an established connection. This process greatly reduces the overhead of IP. However, with no pre-established end-to-end connection, senders are unaware whether destination devices are present and functional when sending packets; they also are not aware of whether the destination receives a packet or whether a destination device is able to access and read a packet.

IP does not guarantee that all packets that are sent are, in fact, received. Figure 8-5 illustrates the unreliable, or best-effort delivery, characteristic of IP. As an unreliable network layer protocol, IP does not guarantee that all sent packets will be received. Other protocols manage the process of tracking packets and ensuring their delivery.

![](img/e71dc48d3ae3db3394e5857ab2acae75_308_1.png)

Figure 8-5 Best-Effort Delivery

## Media Independent (8.1.6)

Unreliable means that IP does not have the capability to manage and recover from undelivered or corrupt packets. This is because while IP packets are sent with information about the location of delivery, they do not contain information that can be processed to inform the sender about whether delivery was successful. Packets may arrive at the destination corrupted, out of sequence, or not at all. IP provides no capability for packet retransmissions if errors occur.

If out-of-order packets are delivered, or if packets are missing, then applications using the data, or upper-layer services, must resolve these issues. This allows IP to function very efficiently. In the TCP/IP protocol suite, reliability is the role of TCP at the transport layer.

IP operates independently of the media that carry the data at lower layers of the protocol stack. As shown in Figure 8-6, IP packets can be communicated as electronic signals over copper cable, as optical signals over fiber, or wirelessly as radio signals.

![](img/e71dc48d3ae3db3394e5857ab2acae75_309_0.png)

Figure 8-6 IP Packets Cross Multiple Media Types

The OSI data link layer is responsible for preparing an IP packet for transmission over the communications medium. This means that the delivery of IP packets is not limited to any particular medium.

There is, however, one major characteristic of the media that the network layer considers: the maximum size of the PDU that each medium can transport. This characteristic is referred to as the *maximum transmission unit (MTU)*. Part of the control communication between the data link layer and the network layer is the establishment of a maximum size for a packet. The data link layer passes the MTU value up to the network layer. The network layer then determines how large packets can be.

In some cases, an intermediate device, usually a router, must split up an IPv4 packet when forwarding it from one medium to another medium with a smaller MTU. This process is called *fragmenting the packet*, or *fragmentation*. Fragmentation causes latency. IPv6 packets cannot be fragmented by the router.

Interactive Graphic

## Check Your Understanding—IP Characteristics (8.1.7)

Refer to the online course to complete this activity.

## IPv4 Packet (8.2)

The ability to provide the end-to-end transfer of data by the network layer is based on the content and interpretation of the Layer 3 header. This section examines the structure and contents of the IPv4 header.

## IPv4 Packet Header (8.2.1)

IPv4 is one of the primary network layer communication protocols. The IPv4 header of a packet is used to ensure that this packet is delivered to its next stop on the way to its destination end device.

An IPv4 packet header consists of fields containing important information about the packet. These fields contain binary numbers that are examined by the Layer 3 process.

## IPv4 Packet Header Fields (8.2.2)

The binary values of each IPv4 packet header field identify various settings of the IP packet. Protocol header diagrams, which are read left to right and top to bottom, provide visuals to refer to when discussing protocol fields. The IP protocol header diagram in Figure 8-7 identifies the fields of an IPv4 packet.

![](img/e71dc48d3ae3db3394e5857ab2acae75_311_0.png)

Figure 8-7 IPv4 Packet Header Fields

Significant fields in the IPv4 header include the following:

- **Version:** This field contains a 4-bit binary value set to 0100 that identifies this as an IPv4 packet.
- **Differentiated Services, or DiffServ (DS):** Formerly called the Type of Service (ToS) field, the DS field is an 8-bit field used to determine the priority of each packet. The 6 most significant bits of the DiffServ field are the differentiated services code point (DSCP) bits, and the last 2 bits are the explicit congestion notification (ECN) bits.
- **Header Checksum:** This field is used to detect corruption in the IPv4 header.
- **Time-to-Live (TTL):** The TTL field contains an 8-bit binary value that is used to limit the lifetime of a packet. The source device of the IPv4 packet sets the initial TTL value. It is decreased by 1 each time the packet is processed by a router. If the TTL field decrements to 0, the router discards the packet and sends an *Internet Control Message Protocol (ICMP)* Time Exceeded message to the source IP address. Because the router decrements the TTL of each packet, the router must also recalculate the header checksum.

- **Protocol:** This field is used to identify the next-level protocol. This 8-bit binary value indicates the data payload type that the packet is carrying, which enables the network layer to pass the data to the appropriate upper-layer protocol. Common values include ICMP (1), TCP (6), and UDP (17).
- **Source IPv4 Address:** This field contains a 32-bit binary value that represents the source IPv4 address of the packet. The source IPv4 address is always a unicast address.
- **Destination IPv4 Address:** This field contains a 32-bit binary value that represents the destination IPv4 address of the packet. The destination IPv4 address is a unicast, multicast, or broadcast address.

The two most commonly referenced fields are the Source IPv4 Address and Destination IPv4 Address fields. These fields identify where the packet is coming from and where it is going. Typically, these addresses do not change while a packet is traveling from the source to the destination.

The Internet Header Length (IHL), Total Length, and Header Checksum fields are used to identify and validate a packet.

Other fields are used to reorder a fragmented packet. Specifically, the IPv4 packet uses Identification, Flags, and Fragment Offset fields to keep track of the fragments. A router may have to fragment an IPv4 packet when forwarding it from one medium to another with a smaller MTU.

The Options and Padding fields are rarely used and are beyond the scope of this chapter.

![](img/e71dc48d3ae3db3394e5857ab2acae75_312_0.png)

## Video—Sample IPv4 Headers in Wireshark (8.2.3)

Refer to the online course to view this video.

![](img/e71dc48d3ae3db3394e5857ab2acae75_312_1.png)

## Check Your Understanding—IPv4 Packet (8.2.4)

Refer to the online course to complete this activity.

## IPv6 Packet (8.3)

This section introduces the successor of IPv4: IPv6.
