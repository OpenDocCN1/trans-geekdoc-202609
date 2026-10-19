link layer. In terms of the OSI model, it covers layers 1 and 2. The network layer includes everything that is required to move data between networks. It corresponds to the IP protocol but also Internet Control Message Protocol (ICMP) and Internet Group Management Protocol (IGMP). In terms of the OSI model, it corresponds to layer 3.

The transport layer includes everything required to move data between applications. It corresponds to TCP and UDP. In terms of the OSI model, it corresponds to layer 4. The application layer covers everything specific to a session or application, in other words, everything relating to the data payload. In terms of the OSI model, it corresponds to layers 5 through 7. Owing to its coarse structure, it is not well suited to describe application-level information exchange.

As with the OSI model, data that is transmitted on the network enters the top of the stack, and each of the layers, with the exception of the physical layer, encapsulates information for its peer at the beginning and sometimes the end of the message that it receives from the next highest layer. On the remote host, each layer removes the information that is peer encapsulated before the remote layer passes the message to the next higher layer. Also, each layer processes messages in a modular fashion, without concern for how the other layers on the same host process the message.

![](bbox=[0.02, 0.5, 0.99, 0.82])

Figure 4.2 — The TCP/IP Reference Model, with comparison to OSI stack
(From Held, G., A Practical Guide to Content Delivery Networks, Auerbach Publications, Boca Raton, FL, 2006. With permission.)

# IP Networking

Internet protocol (IP) is responsible for sending packets from the source to the destination hosts. Because it is an unreliable protocol, it does not guarantee that packets