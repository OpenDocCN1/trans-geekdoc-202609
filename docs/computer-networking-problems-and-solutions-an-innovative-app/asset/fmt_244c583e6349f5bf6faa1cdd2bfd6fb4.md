
8\. Traffic engineering is a completely different way to implement Quality of Service in a network. Can you use traffic engineering to resolve all Quality of Service problems in all networks? Describe a network engineering situation or topology in which it seems like traffic engineering would be able to solve most QoS requirements and one where it would not.

9\. What percentage of traffic is generally recommended to be placed in the low-latency queue in an LLQ system? Explain why.

10\. How does SD-WAN take the complexity of managing QoS Class and Type of Service “out of the hands of humans”? What are the advantages and disadvantages of such an approach?

## Chapter 9
Network Virtualization

### Learning Objectives

After reading this chapter, you should understand:

![Image](graphics/bull.jpg)What problems network virtualization is used to solve

![Image](graphics/bull.jpg)How a tunneled packet is switched through a network

![Image](graphics/bull.jpg)What two problems every network virtualization solution must solve

![Image](graphics/bull.jpg)The general concepts of a tunnel, overlay, underlay, and over-the-top service

![Image](graphics/bull.jpg)The concept of the inner and outer header, and how each is used in a virtual topology

![Image](graphics/bull.jpg)The basic operation of segment routing

![Image](graphics/bull.jpg)The basic concept of Software-Defined Wide Area Networks

![Image](graphics/bull.jpg)A basic understanding of at least some tradeoffs in building and operating virtual topologies

![Image](graphics/bull.jpg)The concepts of shared fate and shared link risk groups

Network virtualization is, in the simplest terms possible, the creation of logical topologies built on top of a physical topology. These logical topologies are often called virtual topologies—hence the concept of network virtualization. These topologies may consist of a single virtual link across a larger network, called a tunnel, or a collection of virtual links that appear to be a complete network on top of the physical network, called an overlay.

This chapter will begin with a discussion about why virtual topologies are created and used, illustrated by two use cases. The second section of this chapter will consider the problems any virtualization solution must solve, and the third section will consider complexity and network virtualization. Following this, two examples of virtualization technologies will be considered: segment routing (`SR`) and Software-Defined Wide Area Networks (`SD-WAN`).

### Understanding Virtual Networks

Virtualization adds complexity in protocol design, network design, and troubleshooting, so why virtualize? The reasons tend to reduce to separating multiple traffic flows across a single physical network. This might sound suspiciously like another form of multiplexing because it *is* another form of multiplexing. The primary differences between the forms of multiplexing considered to this point and virtualization are

• Allowing multiple control planes to operate with different sets of reachability information across a single physical topology

• Allowing multiple sets of reachable destinations to operate across a single physical topology without interacting with one another

The multiplexing techniques considered to this point have focused on allowing multiple devices to use a single physical network (or set of wires), allowing every device to talk to every other device (so long as they know about one another from a reachability perspective). Virtualization focuses on breaking up the single physical network into multiple reachability domains, where every device within a reachability domain can communicate with every other device within the same reachability domain, but devices cannot communicate across reachability domains (unless there is some connection point between the reachability domains).

[Figure 9-1](#ch09.xhtml#ch09fig01) illustrates a network with a virtual topology laid on top of the physical topology.

![Image](graphics/09fig01.jpg)

**Figure 9-1** *A Physical and a Virtual Topology*

In [Figure 9-1](#ch09.xhtml#ch09fig01), a virtual topology has been created on top of the physical network, with the virtual link `[C,H]` created to carry traffic across the network. In order to create the virtual topology, C and H must have some sort of local forwarding information separating the physical topology from the virtual topology, which would normally pass through either E or D. This would normally take the form of either a special set of virtual interface entries in the local routing table, or a Virtual Routing and Forwarding (`VRF`) table containing only information about the virtual topology.

Considering the packet flow through the virtual topology can be helpful in understanding the concepts. What would the packet flow look like if C and H had virtual interfaces? [Figure 9-2](#ch09.xhtml#ch09fig02) illustrates.

![Image](graphics/09fig02.jpg)

**Figure 9-2** *Forwarding a Packet across a Virtual Link*

In [Figure 9-2](#ch09.xhtml#ch09fig02), the forwarding process follows these steps:

1\. A transmits a packet toward M.

2\. C receives this packet, and, examining its local routing table, finds the shortest path to the destination is through a virtual interface toward H. This virtual interface is normally called a tunnel interface; it appears, from the routing table’s perspective, like any other interface on the router.

3\. The virtual interface through which the packet needs to be transmitted has rewrite instructions that include adding a new header, the tunnel header, or outer header, onto the packet, and forwarding the resulting packet. The original packet header is now called the inner header. C adds the outer header and processes the new packet for forwarding.

4\. C now examines the new destination, which is H (remember the original destination was M). H is not directly connected, so C needs to look up how to reach H. This is called a recursive lookup, as C is looking for the path to an intermediate destination to take the packet toward, but not to, the final destination.

5\. C will now place the correct information onto the packet, in a link local header, to forward the traffic to E.

6\. When E receives this packet, it will strip the outer forwarding information, the link local header, and forward the traffic based on the first header C placed on the packet, during the initial lookup. This outer header tells E to forward the packet to H; E does not see or switch on the original inner header placed on the packet by A.

7\. E will add a new link local header so the packet will be correctly forwarded to H, and transmit the packet on the correct interface.

8\. When H receives the packet, it will strip the link local header and discover the outer header. The outer header says the packet is destined for H itself, so H will strip this header, and discover the original packet header or the inner header.

9\. H will now look up M in its local routing table and discover M is locally connected. H will place the correct link local header on the packet and transmit it through the correct interface so the packet reaches M.
