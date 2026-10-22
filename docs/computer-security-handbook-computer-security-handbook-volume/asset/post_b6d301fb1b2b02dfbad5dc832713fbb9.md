
decreases the value by 1. If a router decreases the value to 0, it discards the packet. This process was created to prevent misaddressed packets from circulating endlessly around the Internet.

To identify hosts, attackers will use the Internet Control Message Protocol (ICMP) to ping many IP addresses (as discussed in Section 5.8.1). A reply tells the attacker that a host exists with that IP address. In addition, by guessing the initial TTL value and looking at the TTL value in the arriving packet, the attacker can guess how many router hops separate the attacker’s host from the victim host. Sending many pings to different IP addresses can help the attacker map the routers in the target network. Often, administrators will turn off ICMP traffic outside of the internal networks in order to prevent anyone who isn’t an authorized user from mapping active internal hosts.

The data field of the IP packet may contain a TCP message segment, a UDP datagram message, or something else, such as the ICMP messages we will discuss in Section 5.8.1. A value of 1 in this field indicates that the data field is an ICMP message. In turn, 6 indicates a TCP segment, and 17 indicates that the data field contains a UDP header.

The header checksum field contains a value placed there by the sender. This number is determined by a calculation based on the values of other fields. The receiving internet process redoes the calculation. If the two numbers are different, then there must have been an error along the way. If so, the router or destination host receiving the packet will simply discard the packet. There is no retransmission, so IP is not inherently reliable; however, one of the functions of TCP is to monitor the sequence numbers and initiate retransmission of missing packets. See Section 5.6.2.

## 5.5.1.4 Source and Destination IP Address.

When you send a letter, the envelope has an address and a return address. The analogous addresses in IP headers are the source and destination IP addresses. Note that IP addresses are 32 bits long. For human reading, these 32 bits are divided into four 8-bit segments, and each segment’s bits are converted into a decimal number between 0 and 255. The four segment numbers are then separated by dots. An example is 128.171.17.13. Note that this dotted decimal notation is a memory and writing crutch for inferior biological entities (people). Computers and routers work with 32-bit IP addresses directly.

Many forms of firewall filtering are based on IP addresses. In addition, many attackers spoof their packet’s source IP address (i.e., replace the real IP address with a false IP address).

## 5.5.2 IP Version 6.

Although IP Version 4 is widely used, its 32-bit IP address size causes problems: It can address only 4,294,967,296 (~10^9) devices. This relatively small size limits the number of possible IP addresses. In addition, when IP addresses were distributed, most addresses were assigned to the United States because the Internet was invented there. In fact, some U.S. universities received more IP addresses than China.

To address the limitations of the 32-bit IP address size, a new version of the Internet Protocol was created. This is IP Version 6 (IPv6). (A Version 5 was defined, but it was never used.) Exhibit 5.13 shows the IPv6 packet organization.

One obvious change is that the IP addresses are much larger—128 bits. Each IP address, then, requires four 32-bit lines to write and is equivalent to ~10^38. This will provide IP addresses to allow almost every device to be a host on the Internet—including toasters and coffeepots. To give us a sense of the scale of this enormous number, it is enough to address every single molecule of water in a cube of water over 2 km on a side. Another popular description of the difference in size of the IPv4 and IPv6 address space is that if the address space of IPv4 were represented as a square roughly 4 cm on a side,

| Version (4 bits) Value is 6 (0110) | Diff-Serv (8 bits) Can be used for Priority, etc. | Flow Label (20 bits) Marks a packet as part of a specific flow of packets; Can be used instead of the destination IP address in routing |
| Payload Length (16 bits) | Next Header (8 bits) Name of next header | Hop Limit (8 bits) |
| Source IP Address (128 bits) |  |  |
| Destination IP Address (128 bits) |  |  |
| Next Header or Payload (Data Field) |  |  |

## Exhibit 5.13 IP Version 6 Packet

the equivalent area for IPv6 address space would cover the solar system out to Pluto's orbit.

The version number field is 4 bits long, and its value is 6 (0110). There also is a Diff-Serv field and a flow label field that is 20 bits long. These fields allow the packet to be assigned to a category of packets with similar needs. All packets in this category would be assigned the same flow label and would be treated the same way by routers. However, this capability is not widely used.

There is a hop limit field that serves the same function as the time to live (TTL) field in IPv4. The payload length, in turn, gives the length of the data field in octets.

A major innovation in IPv6 is the next header field. There can be multiple headers following the first header shown in Exhibit 5.13. For instance, IPsec security is implemented with a security header. Although options are unusual in IPv4, IPv6 uses additional headers extensively. The next header field tells what the next header is. Each additional header has a next header field that identifies the next header or says that there is no next header.

## 5.5.3 IPsec.

IP, which was created in the early 1980s, initially had no security at all. Finally, in the 1990s, the Internet Engineering Task Force developed a general way to secure IP transmission. This was IP security, which normally is just called IPsec. IPsec functions by protecting a packet or most of a packet and sending the protected packet inside another packet. IPsec is a general security solution because everything within the data field of the protected packet is securely encrypted, including the transport and application layer information. This includes the transport message and the application message contained in the transport message. Originally developed for IPv6, it was extended to IPv4 as well, becoming a completely general solution. See Chapter 32 in this Handbook for further discussion of IPsec.

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_178_0.png)

Note: An ACK may be combined with the next message if the next message is sent quickly enough.

## Exhibit 5.15 Messages in a TCP Session

Attackers can use TCP connection openings to execute denial-of-service attacks that make a server unable to respond to legitimate traffic. The attacker sends a SYN segment to open a connection to the victim server. The victim server responds with a SYN/ACK message. The victim server also sets aside resources for the connection. The attacker never responds with an ACK, so this is called a half-open SYN attack. If the attacker floods a server host with SYN segments, the victim server will reserve so many resources that it will be overloaded and unable to serve legitimate connection opening attempts. The server may even crash. See Chapter 18 for discussion of denial-of-service attacks.

Ending a conversation, in contrast, normally takes four messages. One side sends a FIN segment, which the other party acknowledges. Then the other party sends a FIN segment, which the other side acknowledges. After the first side sends the original FIN segment, it will not send any new information, but it will send acknowledgments for segments sent by the other party.

There is another way to end a session or even to reject opening one. At any point, either party can send a RST (reset) message. An RST message ends the conversation abruptly. There is not even an acknowledgment. It is like hanging up in a telephone conversation.

Attackers often preface an attack by attempting to identify the IP addresses of running hosts—much like thieves casing a neighborhood. One way to do this is to send TCP SYN segments to hosts. If hosts reject the SYN segment, they often send back an RST message. As noted earlier, TCP segments are carried in the data fields of IP packets. The source IP address in the packet delivering the TCP RST segment will be that of the internal host. Whenever the attacker receives an RST segment, this verifies the existence of a working host at that packet’s IP address. Firewalls often stop RST segments from leaving a site to prevent them from reaching the attacker.

## 5.6.2 Reliability.

In addition to being connectionless or connection-oriented, protocols are either reliable or unreliable. An unreliable protocol does not detect and correct errors. Some unreliable protocols do not even check for errors. Others check for errors but simply discard a message if they find that it contains an error.

TCP is a reliable protocol. It actually corrects errors. The TCP checksum field is calculated using values from other fields. The sender places the result of its calculation in the checksum field. The receiver redoes the calculation and compares it with the transmitted value. If the receiving transport layer process finds that a message is correct (the values are the same), it sends an acknowledgment message. However, if the receiver detects an error in the TCP segment it receives (the values are different), it discards the segment and does nothing else.

How does a receiver know that there is an error in the message? The sender computes a value based on the other bits in the TCP segment (not just the header). The receiver redoes the calculation. If the two values match, the receiver sends an acknowledgment. If they do not match, the receiver merely drops the segment and does not send an acknowledgment.

If the segment arrives correctly, the original sender receives an acknowledgment. However, if the segment never arrives or is discarded because of damage, no reply is sent. If the original sender does not receive an acknowledgment in a specified period of time, it will resend the original segment. It will even use the original sequence number.

## 5.6.3 Flag Fields.

Flag field is a general name for a 1-bit field that is logical (true or false). To say that a flag field is set means that its value is 1. To say that a flag field is not set means that its value is 0.

The TCP header contains a number of flag fields. One of these is SYN. To request a connection opening, the sender sets the SYN bit. The other sends a SYN/ACK segment, in which both the SYN and ACK bits are set. Other commonly used flags are FIN, RST, URG, and PSH.

The URG flag indicates the presence of urgent data that should be handled before earlier data octets. The urgent pointer field indicates the location of the urgent data. If an application message is large, TCP will divide the application message into multiple TCP segments and send the segments individually. To help the receiving TCP process, the sending transport process may set the PSH (push) bit in the application message’s last segment. This tells the receiving transport process to push the data up to the application program immediately without buffering and delays.
