
The `rtt` cannot, generally, be changed, because it is normally bounded by the physical distance and link speed between the sender and receiver. One of the best ways to reduce total data transfer time, then, is to simply reduce the number of round trips required between the sender and receiver to transfer a given stream or block of data. `QUIC`’s startup is designed to reduce the number of round trips required to set up a new connection from the three-way handshake of `TCP` to a 0 round trip time startup process.

To do this, `QUIC` uses a series of cryptographic keys and hashes (see [Chapter 10](#ch10.xhtml#ch10), “[Transport Security](#ch10.xhtml#ch10),” for more information); the process is

1. The client sends the server a hello (`CHLO`) containing a proof demand, which is a list of certificate types the client will accept to verify the server’s identity; a set of certificates the client has access to; and a hash of the certificate the client intends to use in this connection. One specific field, the source address token (`STK`) will be left blank, because no communication has occurred with this server before.

2. The server will use this information to create an `STK` based on the information provided in the client’s initial hello and the client’s source IP address. The server sends a reject (`REJ`), which contains this `STK`.

Once the client has the `STK`, it includes this in future hello packets. If the `STK` matches the previously used `STK` from this IP address, the server will accept the hello.

**Note**

This IP address/`STK` pair can be stolen, and hence the source IP address can be spoofed by an attacker with access to any communication with this pair included. This is a known problem in `QUIC`, addressed in the `QUIC` documentation pointed to in the “Further Reading” section at the end of the chapter.

In comparison, `TCP` requires at least one-and-a-half `rtts` to set up a new session: the `SYN`, the `SYN-ACK`, and then the following `ACK`. How much time does moving to a single `rtt` connection time save? It depends on the implementation of the client and server applications, of course. However, many web pages and mobile device apps must connect to many different servers (perhaps hundreds) to build a single web page or application screen. If each of these connections is reduced from one-and-a-half `rtts` to a single `rtt`, there could be a significant performance impact.

### Reducing Retransmissions

`QUIC` uses a number of different mechanisms to reduce the number of retransmitted packets:

• Including Forward Error Correction (`FEC`) in all packets; this allows the receiver to (often) rebuild corrupted information rather than request the information to be resent.

• Using negative acknowledgments (`NACKs`) rather than `SACK` or the triple `ACK` mechanism to request retransmission of specific sequence numbers; this prevents ambiguity between a request for a retransmission and network conditions that cause multiple acknowledgments to be sent.

• Using fast acknowledgments, as described previously for `TCP`.

• Using the `CUBIC` congestion avoidance window control.

The `CUBIC` congestion avoidance mechanism is the most interesting of these. `CUBIC` attempts to perform a binary search between the last window size before a packet drop and some lower window size calculated using a multiplicative factor. When a packet loss is detected (either through an `RTO` timeout or through a `NACK`), the maximum window size (`WMAX`) is set to the current window size, and a new minimum window size (`WMIN`) is calculated.

The sender’s window is set to `WMIN` and then quickly increased to a window size halfway between `WMIN` and `WMAX`. Once the window reaches this halfway point, the window size is increased very slowly in what is called probing, until the next packet drop is encountered. This process allows `CUBIC` to find the maximum transmission rate just below the point where the network begins dropping packets fairly quickly.

### Reducing Head of Line Blocking

A “single transaction” across the Internet is often not a “single transaction,” but rather a large collection of transactions across a number of different servers. To build a single web page, for instance, hundreds of elements, such as images, scripts, Cascading Style Sheet (`CSS`) elements, and Hypertext Markup Language (`HTML`) files need to be transferred from the server to the client. There are two ways these files can be transferred: in serial or in parallel. [Figure 5-11](#ch05.xhtml#ch05fig11) illustrates.

![Image](graphics/05fig11.jpg)

**Figure 5–11** *Multiple Element Transfer Options*

In [Figure 5-11](#ch05.xhtml#ch05fig11), three options are illustrated to transfer multiple elements from a server to a client:

• In the serialized option, the elements are transferred one at a time across a single session. This is the slowest of the three possible options, as the entire page must be built element by element, with smaller elements waiting on larger ones to transfer before they can be displayed.

• In the multiple streams option, each element is transferred over a separate connection (such as a `TCP` session). This is much faster, but it requires multiple connections to be built, which can negatively impact the client and server resources.

• In the multiplexed option, each element is transferred separately across a single connection. This allows each element to be transferred at its own rate, but with the resource overhead of the multiple streams option.

Some form of multiplexed transfer mechanism tends to provide the fastest transfer rate with the most efficient use of resources, but how should this multiplexing be implemented? The Hypertext Transfer Protocol version 2 (`HTTPv2`) allows a web server to multiplex multiple elements across a single HTTP session; since HTTP runs on top of `TCP`, this means a single `TCP` stream can be used to transfer multiple web page elements in parallel. However, a single dropped packet at the `TCP` level means every parallel transfer within the HTTP stream must be paused while `TCP` recovers (this is a form of fate sharing).

`QUIC` solves this problem by allowing multiple `HTTPv2` streams to reside within a single `QUIC` connection. This reduces the transport overhead at the client and server, while providing optimal delivery of the web page elements.

### Path MTU Discovery

One of the core issues of the argument between Asynchronous Transfer Mode (`ATM`) and the Internet Protocol (`IP`) was the fixed cell size. While `IP` networks rely on variable length packets, `ATM`, in order to facilitate faster switching speeds, and in order to interoperate better with the many different Time Division Multiplexing (`TDM`) physical layers, specified fixed length cells. `IPv4`, in particular, not only provides for a variable length packet, but fragmentation in flight. [Figure 5-12](#ch05.xhtml#ch05fig12) illustrates.

![Image](graphics/05fig12.jpg)

**Figure 5–12** *Packet Fragmentation Example*

In [Figure 5-12](#ch05.xhtml#ch05fig12), if A sends a packet toward E, what size should it make the packet? The only link A really knows about is the link between itself and B, which is marked having a 1,500 octet Maximum Transmission Unit (`MTU`) size. If A sends a 1,500 octet packet, however, the packet will not be able to pass through the [C,D] link. There are two ways to solve this problem.

The first is for C to fragment the packet into two smaller packets. This is possible in `IPv4`; C can determine the packet will not fit on the next link over which the packet should be forwarded, and break the packet into two smaller packets. There are a number of problems with this solution, of course. For instance, the process of fragmenting a packet requires a lot more work on the part of C, possibly even moving the packet out of the hardware switching path into the software switching path.
