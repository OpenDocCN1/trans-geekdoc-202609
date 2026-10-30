| Layer | Commonly Used Protocols |
|---|---|
| Application | HTTP, SNMP, SMTP, FTP, Telnet |
| Presentation | XDR |
| Session | SSL, TLS |
| Transport | TCP, UDP |
| Network | IP, ICMP |
| Data link | IEEE 802.3 (Ethernet), IEEE 802.5 (Token Ring), ARP, RARP |
| Physical | IEEE 802.3 (Ethernet) hardware, IEEE 802.5 (Token Ring) hardware |

**Table A-1** Common Protocols by OSI Layer

represent virtual connections, and the associated activities and protocols are also listed for most layers (the protocols are also listed in Table A-1). These dotted lines are virtual—data does not actually cross them, although it appears as though it does. The true path of data is down to the physical layer and back up to the same layer on another machine.

# Application Layer

The application layer is the typical interface to the actual application being used. This is the layer of the communication stack that is typically responsible for initiating the request for communication. For example, Internet Explorer is an application program that operates in the application layer using HTTP to move data between systems. This layer represents the user’s access to the system and the network. While it appears that the application is communicating directly with an application on another machine, this is actually a virtual connection. The application layer is also sometimes referred to as layer 7 in the OSI model. Several protocols are commonly found in the application layer, including Hypertext Transfer Protocol (HTTP), Simple Mail Transfer Protocol (SMTP), and Simple Network Management Protocol (SNMP).

In the OSI model, the application layer actually communicates with the presentation layer only on its own machine. In the Internet model, the immediate level below the application layer is the transport layer, and this is the only layer directly called by the application layer in this model. As a result of the “missing” presentation and session layers in the Internet model, the functionality of these OSI layers is performed by the application layer.

The session layer functionality present in the Internet model’s application layer includes the initiation, maintenance, and termination of logical sessions between endpoints in the network communication. The session layer functionality also includes session-level accounting and encryption services. The presentation layer functionality of the OSI model is also included in the Internet model’s application layer, specifically functionality to format the display parameters of the data being received. Any other functions not specifically included in the lower layers of the Internet model are specifically included in the application layer.