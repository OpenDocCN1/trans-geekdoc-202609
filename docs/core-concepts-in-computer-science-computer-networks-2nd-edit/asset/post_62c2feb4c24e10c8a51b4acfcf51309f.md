
Timers are used to avoid deadlock and unresponsive connections. Delayed transmissions are used to make more efficient use of network bandwidth by sending larger “chunks” of data at once rather than in smaller individual pieces.

## Connection Termination

In order for a connection to be released, four segments are necessary due to the fact that TCP is a full-duplex protocol, meaning that each end must shut down independently. The connection termination phase is shown in figure 16.

## TCP Connection Termination

![](img/f7819d05465fc14719b3ebbba980271a_77_0.png)

**Figure 16**: TCP Connection Termination.

Notice that instead of SYN control, the connection termination phase uses the FIN control bit to signal the close of a connection.

To terminate the connection in our example, the application running on Host A signals TCP to close the connection. This generates the first FIN segment from Host A to Host B. When B receives the initial FIN segment, it immediately acknowledges the segment and notifies its destination application of the termination request. Once the application on Host B decides to shut down the connection, it sends its own FIN segment, which Host A will process and respond with an acknowledgement.

## Sliding Window and Flow Control

Flow control is a technique whose primary purpose is to properly match the transmission rate of sender to that of the receiver and the network. It is important for the transmission to be at a high rate to ensure good performance, but also to protect against overwhelming the network or receiving host.

That flow control is not the same as congestion control. Congestion control is primarily concerned with a sustained overload of network intermediate devices such as IP routers. TCP uses the window field, briefly described previously, as the primary means for flow control. During the data transfer phase, the window field is used to adjust the rate of flow of the byte stream between communicating TCPs.

In this example, there is a 4-byte sliding window. Moving from left to right, the window “slides” as bytes in the stream are sent and acknowledged. The size of the window and how fast to increase or decrease the window size is an area.

## Congestion Control

Congestion is an important issue that can arise in packet switched network. Congestion is a situation in Communication Networks in which too many packets are present in part of the subnet, performance degrades. In a network may occur when the load on the network (i.e. the number of packets sent to the network) is greater than the capacity of the network (i.e. the number of packets a network can handle).

Congestion control is different from flow control. Flow control is a data link issue, and concerns only one sender outrunning a single receiver (e.g. a point-to-point link). Congestion control is a network layer issue, and thus concerned with what happens when there is more data in the network than can be handled with reasonable packet delays, no lost packets, etc. Flow control is a local, congestion control is global. One of handling congestion is by using a flow control mechanism to reduce the traffic on the net by a particular host, hence the confusion.

Many design parameters at the data link, network and transport layers effect congestion. Setting each of these with a mind to preventing congestion to eliminate the problem. For example, a flooding algorithm is fast, but generates a lot of redundant packets. Timers in the data link layer which are set too tight cause needless retransmission of packets.

## Traffic Shaping

One of the causes of congestion is the inherent burstiness of computer network traffic. Traffic shaping means to smooth, or otherwise later, the offered traffic as a function of time. Smooth traffic is easier to deal with the bursty traffic. A subnet may be able to handle on average 10M packets in an hour, but it probably can't handle 10M packets in one minute and for the next 59 minutes.

Related to traffic shaping is the whole idea of agreeing with a network service provider to a flow specification. A flow

Sliding window protocols are used where reliable in order delivery of packets is required, such as the Data Link Layer (OSI model) as well as in the Transmission Control Protocol (TCP).

Congestion control is a critical mechanism used in computer networks to manage and prevent network congestion, which occurs when the demand for network resources exceeds its capacity.

Data-Link layer is the protocol layer in a program that handles the moving of data in and out across a physical link in a network.

## Network Software and Network Standardization

specification describes what sort of traffic you will put into the net, and what sort of quality service you expect from it. Some of the quality of service parameters are:

- loss sensitivity (number of lost bytes per unit of time)
- loss interval (the unit of time for calculating loss)
- burst loss sensitivity (how long of a burst can be tolerated)
- minimum delay (how large of a delay before the app notices)
- maximum delay variation (the variance or jitter in the inter-packet delay)
- quality of guarantee (how serious the spec is to the application)

![](img/f7819d05465fc14719b3ebbba980271a_79_0.png)

## Leaky bucket algorithm

A buffer that converts an unregulated, bursty traffic flow into a regulated, smooth, predictable flow. You put the buffer in between a traffic source and the subnet. The buffer acts like a single server queue with a finite queue length. Packets put in the buffer when it is full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

A variant on the leaky bucket is the token bucket. The bucket is filled with tokens at a certain rate. The bucket acts like a single server queue with a finite queue length. Packets put in the buffer when it is full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

A variant on the leaky bucket is the token bucket. The bucket is filled with tokens at a certain rate. The buffer acts like a single server queue with a finite queue length. Packets put in the buffer when it is full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

A variant on the leaky bucket is the token bucket. The bucket is filled with tokens at a certain rate. The buffer acts like a single server queue with a finite queue length. Packets put in the buffer when it is full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

A variant on the leaky bucket is the token bucket. The bucket is filled with tokens at a certain rate. The buffer acts like a single server queue with a finite queue length. Packets put in the buffer when it is full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

A variant on the leaky bucket is the token bucket. The bucket is filled with tokens at a certain rate. The buffer acts like a single server queue with a finite queue length. Packets put in the buffer when it is full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

A variant on the leaky bucket is the token bucket. The bucket is filled with tokens at a certain rate. The buffer acts like a single server queue with a finite queue length. Packets put in the buffer when it is full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

A variant on the leaky bucket is the token bucket. The bucket is filled with tokens at a certain rate. The buffer acts like a single server queue with a finite queue length. Packets put in the buffer when it is full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

A variant on the leaky bucket is the token bucket. The bucket is filled with tokens at a certain rate. The buffer acts like a single server queue with a finite queue length. Packets put in the buffer when it is full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

A variant on the leaky bucket is the token bucket. The bucket is filled with tokens at a certain rate. The buffer acts like a single server queue with a finite queue length. Packets put in the buffer when it is full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

A variant on the leaky bucket is the token bucket. The bucket is filled with tokens at a certain rate. The buffer acts like a single server queue with a finite queue length. Packets put in the buffer when it is full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

A variant on the leaky bucket is the token bucket. The bucket is filled with tokens at a certain rate. The buffer acts like a single server queue with a finite queue length. Packets put in the buffer when it are full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

Sliding window protocols are used where reliable in order delivery of packets is required, such as the Data Link Layer (OSI model) as well as in the Transmission Control Protocol (TCP).

Congestion control is a critical mechanism used in computer networks to manage and prevent network congestion, which occurs when the demand for network resources exceeds its capacity.

Data-Link layer is the protocol layer in a program that handles the moving of data in and out across a physical link in a network.

## Network Software and Network Standardization

specification describes what sort of traffic you will put into the net, and what sort of quality service you expect from it. Some of the quality of service parameters are:

- loss sensitivity (number of lost bytes per unit of time)
- loss interval (the unit of time for calculating loss)
- burst loss sensitivity (how long of a burst can be tolerated)
- minimum delay (how large of a delay before the app notices)
- maximum delay variation (the variance or jitter in the inter-packet delay)
- quality of guarantee (how serious the spec is to the application)

![](img/f7819d05465fc14719b3ebbba980271a_79_0.png)

## Leaky bucket algorithm

A buffer that converts an unregulated, bursty traffic flow into a regulated, smooth, predictable flow. You put the buffer in between a traffic source and the subnet. The buffer acts like a single server queue with a finite queue length. Packets put in the buffer when it is full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

A variant on the leaky bucket is the token bucket. The bucket is filled with tokens at a certain rate. The buffer acts like a single server queue with a finite queue length. Packets put in the buffer when it is full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

Sliding window protocols are used where reliable in order delivery of packets is required, such as the Data Link Layer (OSI model) as well as in the Transmission Control Protocol (TCP).

Congestion control is a critical mechanism used in computer networks to manage and prevent network congestion, which occurs when the demand for network resources exceeds its capacity.

Data-Link layer is the protocol layer in a program that handles the moving of data in and out across a physical link in a network.

## Network Software and Network Standardization

specification describes what sort of traffic you will put into the net, and what sort of quality service you expect from it. Some of the quality of service parameters are:

- loss sensitivity (number of lost bytes per unit of time)
- loss interval (the unit of time for calculating loss)
- burst loss sensitivity (how long of a burst can be tolerated)
- minimum delay (how large of a delay before the app notices)
- maximum delay variation (the variance or jitter in the inter-packet delay)
- quality of guarantee (how serious the spec is to the application)

## Leaky bucket algorithm

A buffer that converts an unregulated, bursty traffic flow into a regulated, smooth, predictable flow. You put the buffer in between a traffic source and the subnet. The buffer acts like a single server queue with a finite queue length. Packets put in the buffer when it is full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

A variant on the leaky bucket is the token bucket. The bucket is filled with tokens at a certain rate. The buffer acts like a single server queue with a finite queue length. Packets put in the buffer when it is full are thrown away. The buffer may drain onto the subnet either by some number of packets per unit time, or by some total number of bytes per unit time (helpful if packets vary greatly in size).

## Choke Packets

Routers monitor the utilization of their output and send special choke packets back to hosts whose utilization has exceeded some level. The utilization can be estimated by sampling it and blending the new value (either in use, f = 1 or not in use, f = 0) with the current value. The weight controls how rapidly the router adjusts to changes:

Unew = a * Uold + (1-a) * f

## Load Shedding

This is what routers do when they run out of buffers. If they must throw away a packet then they can at least pick the best packets to pitch. This depends on the application and on error strategy used in the data link layer. Older packets will be worse to throw away for a file transfer than newer ones, since they will cause a gap in the received packets and a go-back strategy may be employed by the data link layer. For real-time voice or video it is probably better to throw away old data (already obsolete?) and keep new packets.

Getting the application to mark packets with priority requires incentive like cheaper transmission rates for lower priority packets.

It appears to be better for routers to start dropping packets as soon as congestion seems likely, rather than wait for congestion to take over.

![](img/f7819d05465fc14719b3ebbba980271a_80_0.png)

## CORE CONCEPT: USER DATAGRAM PROTOCOL (UDP)

UDP (User Datagram Protocol) is an alternative communications protocol to Transmission Control Protocol (TCP) used primarily for establishing low-latency and loss-tolerating connections between applications on the internet.

The user datagram protocol is one of the major network protocols to transmit information on the Internet. It is part of the Internet Protocol Suite, which governs how computers communicate with servers and each other over an Internet Protocol (IP) network. When using the user datagram protocol, an application can send datagrams, or messages, to other hosts without first setting up special channels or data paths. This allows for faster communication, but is less reliable than other methods. The focus of the user datagram protocol is on data transmission. It provides no safeguards to ensure that the information actually arrives or to protect the integrity of the data as it moves. The protocol assumes that, if error checking is important, the computers doing the communication will take care of it.
