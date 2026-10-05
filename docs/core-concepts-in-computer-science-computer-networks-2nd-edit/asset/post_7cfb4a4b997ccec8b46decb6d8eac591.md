
- * Moving an input signal to a different input line of the multiplexer implies that the signal is moved globally, i.e. for all multiplexers associated with all other function blocks. For large PLDs, there are many function blocks, thereby increasing the probability that a particular routing for one multiplexer adversely affects the routing of the other multiplexers to which the signal is propagated.

Therefore, a need arises for a multiplexer that provides efficient and flexible control and routing options to allow reliable implementation of complex user designs without adding unnecessary complexity to the PLD, or substantially increasing the PLD size or power requirements.

![](img/f7819d05465fc14719b3ebbba980271a_69_0.png)

## CORE CONCEPT: TRANSMISSION CONTROL PROTOCOL (TCP)

Transmission Control Protocol (TCP) is usually not associated with quality of service; but one could argue that TCP offers QoS in terms of assured delivery and efficient use of bandwidth, although it provides no delay guarantees. TCP is, after all, mainly about efficiency and adaptation: how to deliver data utilizing the maximum available (but fair) share of a dynamically changing network capacity to reduce the delay.

The transmission control protocol is one of the two that make up the Internet connection suite. This protocol is combined with the Internet protocol to form the foundation of all Internet traffic. These protocols are almost inseparable in use, relying completely on each other for proper functioning; as a result, the Internet connection suite is typically abbreviated as TCP/IP (transmission control protocol/Internet protocol). The transmission control protocol is responsible for the disassembly and reassembly of data, and the Internet protocol handles the routing and transmission. Internet traffic is primarily made of small data bursts packets. These packets contain information relating to the origin and destination of the data as well as some additional information. The packets are created and reassembled by the transmission control protocol and sent over the Internet by the Internet protocol.

To illustrate this process, a document is moved from a remote computer to a local one. The computer receives the move command, and the Internet protocol determines how the document needs to move between the computers. The Internet protocol then asks the transmission control protocol to split the document up in a specific way.

# The TCP then divides up the document into packets, and the Internet protocol sends them out.

Internet protocol is the principal communications protocol in the Internet protocol suite for relaying datagrams across network boundaries.

![](img/f7819d05465fc14719b3ebbba980271a_70_0.png)

When the document packets arrive at the local computer, the TCP begins to reassemble them. It first checks to see if it has all of them and if they are in proper shape—if it needs replacements, it submits a request for the parts it needs and waits for them to arrive. After it gets all of the pieces, it reorders them in the proper sequence and assembles the document. It then sends it on to the Internet protocol, which informs the computer that the file has arrived.

These processes up the vast majority of Internet usage. Programs like web browsers, clients and file transfer systems use this basic and forth process for every interaction. This unified system sends information to one another without conversation. It is immaterial what operating system or program sent the information, as the control protocol actually did the work.

Since this is the basic cornerstone of the Internet, the protocol never changes very much. This allows systems backward compatibility over the Internet. Changes in protocols would cause older machines to permanently disconnect. Even without a common update, the system is so simple that it rarely requires any additional monitoring or attention.

TCP is often described as a byte stream, connection-oriented, reliable delivery transport layer protocol.

## Byte Stream Delivery

TCP interfaces with the application layer above and the network layer below. When an application sends data to TCP, it does so in 8-bit byte streams. It is up to the sending TCP to segment or delineate the byte stream in order to transmit data in manageable pieces to the receiver!. It is this lack of ‘record boundaries’ which give it the name “byte stream delivery service”.

## Connection-Oriented

Before communicating TCPs can exchange data, they must first agree upon the willingness to communicate. Analogous to a telephone call, a connection must first be deade before two parties exchange information.

## Reliability

A number of mechanisms help provide the reliability TCP guarantees.

- *Checksums*: All TCP segments carry a checksum, which is used by the receiver to detect errors with either the TCP header or data.
- *Duplicate data detection*: It is possible for packets to be duplicated in packet switched network; therefore TCP keeps track of bytes received in order to discard copies of data that has already been received.
- *Retransmissions*: In order to guarantee delivery of data, TCP must implement retransmission schemes for data that may be lost or damaged. The use of positive acknowledgements by the receiver to the sender confirms successful reception of data. The lack of positive acknowledgements, coupled with a timeout period (see below) calls for a retransmission.
- *Sequencing*: In packet switched networks, it is possible for packets to be delivered out of order. It is TCP's job to properly sequence segments it receives so it can deliver the byte stream data to an application.
- *Timers*: TCP maintains various static and dynamic timers on data sent. The TCP waits for the receiver to reply with an acknowledgement within a bounded length of time. If the timer expires before receiving an acknowledgement, the sender retransmits the segment.

## TCP Header Format

The combination of TCP header and TCP in one packet is called a TCP segment. Figure 14 depicts the format of all TCP segments. The size of the header without options is 20 bytes. We will briefly define each field of the TCP header.

## Nature of Transmission Control Protocol

The Transmission Control Protocol (TCP) is a connection-oriented, reliable stream-oriented transport protocol within the TCP/IP suite. The nature of TCP can be summarized by the following characteristics:

- Connection-Oriented: TCP establishes a bi-directional connection before data transfer. This connection is set up using a three-way handshake, where the client and server exchange initial sequence numbers to establish the connection.
- Reliable Data Delivery: TCP provides reliable data delivery, meaning it guarantees all packets sent from the sender will reach the receiver correctly. To ensure reliability, TCP uses acknowledgments and retransmission mechanisms. The receiver acknowledges the successful receipt of data, and if a sender does not receive an acknowledgment for a transmitted packet within a timeout period, it retransmits the packet.
- Flow Control: TCP implements flow control to manage the rate of data transmission between the sender and receiver. It ensures that the sender does not overwhelm the receiver with data using a sliding window mechanism. The receiver advertises available buffer space through window size values, and the sender adjusts its transmission rate accordingly.
- Congestion Control: TCP is designed to handle network congestion. It uses various congestion control algorithms to detect and react to network congestion, preventing network overload and packet loss. When TCP detects congestion, it reduces its transmission rate to alleviate the congestion.
- Stream-Oriented: TCP is a stream-oriented protocol, which sends data as a continuous flow of bytes rather than discrete packets. TCP breaks down application data into manageable segments and sends them orderly. On the receiving end, TCP reassembles the segments back into the original data stream.
- Full Duplex Communication: TCP enables full duplex communication, meaning data can be transmitted in both directions simultaneously. Both the sender and receiver can send and receive data independently.
- Connection Termination: When data transmission is complete, TCP performs a graceful connection termination using a four-way handshake. This ensures that all data is successfully delivered before the connection is closed.

# Transmission Control Protocol (TCP) Header
20-60 bytes

| source port number 2 bytes | destination port number 2 bytes |
|---|---|
| sequence number 4 bytes | |
| acknowledgement number 4 bytes | |
| data offset 4 bits | reserved 3 bits | control flags 9 bits | window size 2 bytes |
| checksum 2 bytes | urgent pointer 2 bytes |
| optional data 0-40 bytes |

Figure 14: TCP Header Format.

Overall, the nature of TCP is focused on providing reliable, ordered, and error-checked data transmission between devices over a network. It is the foundation for
