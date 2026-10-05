# 46

Core Concepts in Computer Science: Computer Networks

layer is responsible for error control. However, error control at this layer is performed end to end rather than across a single link. The sending transport layer makes sure that the entire message arrives at the receiving transport layer without error (damage, loss, or duplication). Error correction is usually achieved through retransmission.

# Network Layer

The network layer is responsible for the source-to-destination delivery of a packet possibly across multiple networks. Whereas the data link layer oversees the delivery of the packet between two systems on the same network (links), the network layer ensures that each packet gets from its point of origin to its final destination.

If two systems are connected to the same link, there is usually no need for a network layer. However, if the two systems are attached to different networks (links) with connecting devices between the networks, (links), there is often a need for the network layer to accomplish source-to-destination delivery.

![](bbox=[0.318, 0.503, 0.822, 0.735])

Internet is a collection of interconnected networks that use common communication protocols and technologies to form a larger, global network.

Figure 5: Network layer.

Specific responsibilities of the network layer include:

+   * Logical Addressing: The physical addressing implemented by the data link layer handles the addressing problem locally. If a packet passes the network boundary, one needs another system to help distinguish the source and destination systems. The network layer adds a header to the