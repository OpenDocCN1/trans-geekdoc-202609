# Transport-Layer Protocols

We have seen that the IP protocol does not guarantee reliable delivery of data packets and that it delegates this function to the higher layers. The layer above the IP layer is the transport layer that is commonly represented by either TCP or UDP. Applications have a choice whether to use TCP or UDP. This choice is often dictated by performance and reliability requirements of the applications.

# The Transmission Control Protocol (TCP)

TCP provides the means for a reliable end-to-end communication channel. TCP allows applications to bind to port numbers before communicating with each other. It is a connection-oriented protocol which means that the communicating entities assume that they are connected together one-to-one, analogous to a telephone connection in which the two callers are talking to each other over a dedicated line. Applications built over TCP are provided with a stream to write their data into.

The TCP module is responsible for ensuring that the data is delivered reliably to the destination without the application having to bother about network-congestion and packet loss. This comes with an extra cost, as we shall see when we look at UDP. The TCP protocol provides the following functionality:

+   **Stream-based I/O** Data is presented to applications at both receiving and transmitting ends as a data stream on which normal read and write operations can be performed, almost giving the impression of sequentially reading or writing from a file. Sometimes certain events need to be processed with a higher priority and cannot wait until the data preceding them has been processed (for example, the user interrupts a file-transfer program). In this case, TCP sends out-of-band data, which is processed at a higher priority than regular data transfer.

+   **Acknowledgment-based delivery** TCP packets are encapsulated in IP packets. However, the delivery of TCP packets is backed by an acknowledgment scheme to ensure that the packets are indeed delivered reliably. In the event that a packet is not acknowledged as delivered by the destination within a given time interval, the TCP protocol layer re-sends the packet to the destination.

+   **Congestion avoidance and flow control** Two communicating hosts may not have the same capacity to handle data. This requires data to be sent at a rate at which it can be processed by the destination. If the data transfer rate is too slow, the recipient host's resources are not fully utilized; if it is too fast, the recipient host is quickly overwhelmed. TCP takes care of the rate of data flow so that the data transfer is optimal. Since physical networks experience congestion due to high volumes of network traffic, TCP attempts to avoid or mitigate congestion.

Many popular protocols such as HTTP and SMTP are built over TCP. We shall see more about using the TCP protocol when we look at the section discussing sockets.