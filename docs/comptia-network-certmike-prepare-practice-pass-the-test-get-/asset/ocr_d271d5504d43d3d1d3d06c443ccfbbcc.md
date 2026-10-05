Multiple Access When the network is clear, the host begins transmitting. The transmitted packet fills the entire shared medium before the host finishes transmitting. It is during this time that a collision can occur.

Collision Detection When the transmitting detects signals on both its transmit and receive simultaneously, it declares a signal quality error (or collision), stops transmitting data, and starts transmitting a jam signal. The jam signal alerts any other transmitting systems of the collision, causing them to discard any incoming data they have received.

Wireless devices cannot use CSMA/CD because they turn off their receivers when transmitting, so they use another mechanism called Carrier Sense Multiple Access with Collision Avoidance (CSMA/CA).

When switches replaced hubs in the IT marketplace—and in data centers around the world—Ethernet networks no longer needed a shared medium or CSMA/CD, and packet collisions as normal became largely part of the past.

# Physical Layer Specifications

The Ethernet standards include a collection of physical layer specifications, which have been updated over the years to reflect advancements in networking technologies. There are dozens of specifications supporting different network media, but only a few remained in general use.

An Ethernet specification defines the characteristics of the network medium, as what category of UTP cable to use, and also provides installation guidance, such as the maximum length of a cable segment. The limitations on cable length exist primarily to support the collision detection mechanism in CSMA/CD.

> EXAM TIP An Ethernet network, by today’s standards, typically consists of UTP cable connecting to switches. Switches have replaced hubs in all but the most outdated network installations. Candidates for the Network+ exam should be conscious of the effect that switching has on an Ethernet network.

# SWITCHING

A switch, as noted elsewhere in this book, is a connectivity device that operates at the data link layer (layer 2) of the OSI reference model. Unlike hubs, which are purely electrical devices operating at the physical layer, switches have the ability to learn about the devices on the network and maintain a record of the information they discover.

A switch is essentially a multiport device that forwards traffic selectively to its destination on the local network, rather than flooding each packet to every connected host, as a