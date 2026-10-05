# Network Coding based Protocols in the Wild

This is a fair question. My intuition is the following: in practice, network coding may be implemented at any layer of the OSI model above the network layer. However, the origins of network coding are precisely at the network layer. This means that routers and switches must implement some form of network coding (i.e. they should be able to operate over packets and mix them together). Aside from these developments, you must also deploy these devices across the globe. You can see how replacing the whole internet could be a bit unfeasible.

You're now thinking that you've been reading all of this nothing... Let me hold you back on those thoughts. While it may take “some time” to see network coding widespread across the globe, the concepts of network coding can be developed at higher layers in particular at the application layer. You'll see it in a minute.

# Building a new internet (with network coding)

Applications of network coding (multicast/broadcast/p2p), which represent a somewhat limited use case, but network coding can have a global impact. How may you ask? It's simple: we can use the network coding to develop new transport layer protocols, one of the cores of communication networks and used in every application that needs to access the Internet.

# The heart of the network - the transport layer

HTTP rings a bell to you, right? It is an application protocol for transmitting hypermedia documents and resources. Basically, the foundation of the web as we know it. Under the hood, HTTP uses TCP (transmission control protocol) to reliably exchange data between two endpoints. However, the performance of TCP is severely impaired by the presence of packet loss and latency. The reason is two-fold:

+   - TCP (general) interprets packets loss as congestion and reduces its transmission rate
- TCP is based on ARQ and therefore highly dependent on feedback packets to operate

Now, the first point is not really valid in today’s world, specifically when speaking about WiFi/mobile. Packets get for many reasons! Interference, signal propagation issues, faulty hardware and so on. If you’re experiencing random packet losses why should you reduce your transmission rate? These losses do not necessarily mean that you are congesting the network...

The second point, we've discussed a little bit. Do we really need to wait for acknowledgments to be able to operate a reliable transport protocol? If you are sending untouched data, you will need your packet sequencing and everything in between. If you are using coding, not really… Any packet can be used to recover useful data.

So instead of reasoning about losses as signals of congestion, we may look at how much information is passing through the channel (good put). This way, you’ll get a