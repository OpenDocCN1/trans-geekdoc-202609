![](bbox=[0.12, 0.09, 0.92, 0.26])

# EXHIBIT 6.15 Two LANs Interconnected via a Bridge

A bridge is a simple frame store-and-forward device. Like all stations on the LAN, a bridge examines the destination address of any transmitted frames. If a transmission on LAN #1 contains a destination address of a station on LAN #2, the bridge will forward the frame. If a transmission contains an unknown destination address, the bridge will also forward the frame.

Although a bridge bases its decisions on the MAC address, it is not an intelligent device; that is, it knows that a station with a particular MAC address is in one direction or another, but it does not know precisely where that station is. Because bridges have to build tables containing all of the stations’ addresses that they learn, bridges do not scale particularly well to large networks. Bridges also extend the broadcast domain (i.e., if a frame transmitted on LAN #1 is sent to the broadcast address, it will be forwarded to LAN #2).

# 6.6.4 Routers.

A router is conceptually similar to a bridge in that it is also a store-and-forward device. A router, however, works at the Network Layer and is therefore a much more powerful device than a bridge. As Exhibit 6.16 shows, every LAN device has both a MAC (hardware) and Network Layer (software) address (in this case, IP is the sample Network Layer address). Because Network Layer addresses are hierarchical, the networks themselves have a network identifier number (the NET_ID in Exhibit 6.16). Network Layer addresses are well suited to environments where intermediate devices have to find a best route between networks.

Like a bridge, a router is considered to be just another station on a LAN to which it is attached. If the router sees a transmission on LAN #1 (with a NET_ID of 192.168.16.0) containing a destination address of a station on another network, it will route the packet to the correct destination network, even if that means going through another router to get there.

This example also demonstrates another major difference between bridges and routers. In a bridged environment, a station on LAN #1 sends a frame to some MAC address and has no knowledge of whether the intended destination is on the same LAN or not; the bridge will forward the frame if necessary, but this is all transparent to sender

![](bbox=[0.15, 0.88, 0.9, 0.93])

# EXHIBIT 6.16 Two LANs Interconnected via a Router