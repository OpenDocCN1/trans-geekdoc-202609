
Forwarding traffic over the fewest number of links (and therefore through the fewest number of network devices) would consume the smallest amount of resources, but cold and hot potato routing both choose some longer-length path in order to satisfy a policy constraint. This trades the efficient use of resources for the efficient operation of a protocol or service in order to increase revenue. Other policies may be applicable to routing systems, as well, such as choosing the path with the highest bandwidth, or the path that takes traffic to the geographic exit point closest to the user. Whatever the policy, it will generally represent a tradeoff between one kind of optimization over some other kind of optimization, and require additional state of some sort to implement.

### Resource Segmentation

Many times networks are logically divided to control access to specific resources. The network shown in [Figure 17-2](#ch17.xhtml#ch17fig02) will be used to illustrate.

![Image](graphics/17fig02.jpg)

**Figure 17-2** *Overlays as a Form of Segmentation*

[Figure 17-2](#ch17.xhtml#ch17fig02) shows three different networks:

• Network A shows the base (routed) topology.
• Network B shows one set of devices and links that must be connected to one another.
• Network C shows a second set of devices and links that must be connected to one another.

In [Figure 17-2](#ch17.xhtml#ch17fig02), host B must only be able to connect to server L, and host A must only be able to connect to H. It is simple enough to provide this kind of segmentation through simple packet filters configured at G and K, of course, but further requirements may rule out using simple packet filters. For instance:

• There may be a requirement for traffic passing between A and H to use the path `[C,E,F,K,G]`; this mixes a traffic engineering requirement with a service access requirement.
• There may be a requirement for servers H and L to not even be able to *see* routes and other information from the other topology. This might be very difficult if the two servers are participating in the routed control plane, as might be the case if they are hosting many virtual machines (`VMs`), each of which needs to advertise its own IP address into the control plane.

When you reach this level of requirement, a common solution is to create an overlay network, often using tunnels to do the heavy lifting of separating the network into several virtual topologies. In [Figure 17-2](#ch17.xhtml#ch17fig02), these requirements are met with an overlay. In network B, a tunnel would be built starting at the inbound interface of D facing host B (the tunnel headend). This tunnel would be carried across G and K, finally terminating on the interface on K that connects to L (the tunnel tailend). To draw traffic from B to L, there must be some routed control plane to pull traffic into the tunnel headend so it is routed across the tunnel toward L. In network C, a tunnel would be built starting at the inbound interface of C, facing A. The tunnel is carried across C, E, F, K, and G, and terminates at the outbound interface at G facing H. Again, there must be some control plane to draw data across this tunnel, so traffic sourced from A is pulled into the tunnel at C and is presented to G as a “raw IP packet” (without the tunnel headers) so that G can switch the packet to H.

The routing information that draws traffic through these two tunnels may actually be carried in a separate control plane. In this case, the underlay control plane will provide reachability to the tunnel endpoints, while the overlay control plane will draw traffic through the tunnel. This separation of control planes allows the different topologies, the underlay and the overlay, to be completely separated; reachability and topology information is not shared between these two control planes.

The same is true of the traffic being drawn through the network; the two flows are separated by being tunneled. Not only is the traffic being separated by tunneling, but the path of the flow is also being engineered through the network. Tunneling, and the fuller concept of an overlay, is useful in meeting a lot of different policy requirements; this is why overlays are so widely used in network engineering.

### Flow Pinning for Application Optimization

Elephant flows and mouse flows are two classes of flows that engineers often encounter. An elephant flow is typically a large, persistent data flow. Any flow taking up more than around 20% of the available bandwidth of a single link and persisting for more than two or three minutes might, for instance, be classified as an elephant flow. Mouse flows, on the other hand, are much lower bandwidth, say less than 1% of the available bandwidth on any link, and tend to last for very short periods of time. Most flows of traffic can be divided into elephant and mouse flows. *What should be done about elephant and mouse flows?*

One solution is to interleave the packets from each flow, which allows each flow fair access to the available bandwidth. While Quality of Service (`QoS`) is one solution, another solution is to pin particular traffic flows to particular paths, or path pinning. [Figure 17-3](#ch17.xhtml#ch17fig03) is used to explain further.

![Image](graphics/17fig03.jpg)

**Figure 17-3** *Pinning an Elephant Flow in a Network*

In [Figure 17-3](#ch17.xhtml#ch17fig03), A begins a flow that will last several hours, and consumes 20% of the available bandwidth on a link (assume all links are the same bandwidth, 100Mbps), and terminates at H. At about the same moment, B sends a series of short-term small flows terminating at H. Given just one path will be chosen as the best between C and G, both flows will follow the same path, say along the path `[C,E,G]`. Mixing the two flows in this way can cause both to suffer from a performance perspective. To understand the problem, it is best to consider the rate at which packets can be serialized onto the wire:

• **64-byte packet onto a 100Mbps link:** .05ms
• **1,500-byte packet onto a 100Mbps link:** .12ms
• **9,000-byte packet onto a 100Mbps link:** .72ms

Assume the entire network is capable of 9,000-byte packet sizes (the Maximum Transmission Unit, or `MTU` is 9,000 bytes end to end), and the elephant flow is actually shipping 9,000-byte packets. For the mouse flow, assume the packet size is 64-byte packets (at least in one direction). If a single mouse flow packet is trapped behind a single elephant flow packet, the mouse flow packet will be held for .72ms before it can be serialized onto the physical interface. If there is always one packet from each flow alternating, there can be some significant performance reduction, but both applications would likely still work well enough.

But what happens if the interleaving between the two flows is less than optimal? For instance, what if there is a series something like the sequence of packets shown in [Figure 17-4](#ch17.xhtml#ch17fig04)?

![Image](graphics/17fig04.jpg)

**Figure 17-4** *A Problematic Mixture of Packets from Elephant and Mouse Flows*

The difference between the shortest and longest spacing between mouse flow packets is .05ms and .288ms. The difference between the shortest and longest spacing between elephant flow packets is .05ms and .15ms. These variations might seem to be minimal, but even minimal variations show up as jitter end to end. This kind of jitter, particularly on a larger scale, is problematic for flow control and error correction. In this case, even though the elephant flow is overwhelmingly larger than the mouse flow, both are still negatively impacted. This same sort of problem is common in data center fabrics, as well. [Figure 17-5](#ch17.xhtml#ch17fig05) illustrates.

![Image](graphics/17fig05.jpg)

**Figure 17-5** *Traffic Engineering in a Data Center Fabric*
