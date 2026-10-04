To understand the differences between TCP and UDP, it is important to understand how each protocol implements specific reliability features and how each protocol tracks conversations.

In addition to supporting the basic functions of data segmentation and reassembly, TCP also provides the following services:

+   - **Establishes a session:** TCP is a *connection-oriented protocol* that negotiates and establishes a permanent connection (or session) between source and destination devices prior to forwarding any traffic. Through session establishment, the devices negotiate the amount of traffic that can be forwarded at a given time, and the communication data between the two can be closely managed.
- **Ensures reliable delivery:** As a segment is transmitted over a network, it might for many reasons become corrupted or lost completely. TCP ensures that each segment that is sent by the source arrives at the destination.
- **Provides same-order delivery:** Because networks may provide multiple routes that can have different transmission rates, data can arrive in the wrong order. By numbering and sequencing the segments, TCP ensures that segments are reassembled in the proper order.
- **Supports flow control:** Network hosts have limited resources (that is, memory and processing power). When TCP is aware that these resources are overtaxed, it can request that the sending application reduce the rate of data flow. TCP does this by regulating the amount of data the source transmits. This process, called *flow control*, can prevent the need for retransmission of the data when the resources of the receiving host are overwhelmed.

For more information on TCP, search the internet for RFC 793.

# TCP Header (14.2.2)

TCP is a *stateful* protocol, which means it keeps track of the state of a communication session. To track the state of a session, TCP records which information it has sent and which information has been acknowledged. The stateful session begins with the session establishment and ends with the session termination.

A TCP segment adds 20 bytes (that is, 160 bits) of overhead when encapsulating the application layer data. Figure 14-9 shows the fields in a TCP header.

# TCP Header Fields (14.2.3)

Table 14-1 describes the fields in the TCP header.