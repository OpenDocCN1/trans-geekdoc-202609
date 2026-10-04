# Transport Layer Protocols (14.1.3)

IP is concerned only with the structure, addressing, and routing of packets. IP does not specify how the delivery or transportation of the packets takes place.

Transport layer protocols specify how to transfer messages between hosts and are responsible for managing the reliability requirements of a conversation. The transport layer includes the TCP and UDP protocols.

Different applications have different transport reliability requirements. Therefore, TCP/IP provides two transport layer protocols, as shown in Figure 14-7.

![](bbox=[0.25, 0.32, 0.7, 0.65])

Figure 14-7 Transport Layer Protocols

# Transmission Control Protocol (TCP) (14.1.4)

IP is concerned only with the structure, addressing, and routing of packets, from original sender to final destination. IP is not responsible for guaranteeing delivery or determining whether a connection between the sender and receiver needs to be established.

TCP is considered a reliable, full-featured transport layer protocol, and it ensures that all of the data arrives at the destination. TCP includes fields that ensure the delivery of the application data. These fields require additional processing by the sending and receiving hosts.

Note

TCP divides data into segments.