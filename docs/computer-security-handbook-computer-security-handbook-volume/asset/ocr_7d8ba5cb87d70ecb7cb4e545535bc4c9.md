throughout an area where devices can attach to the network, and every place is a potential connection point in a wireless environment.

3. Network interface card (NIC). This is the physical attachment from the computer to the LAN medium. Older NICs are internal cards; the only item that is actually seen is the physical attachment to the LAN, often an RJ-45 jack. An increasing number of adapters use the universal serial bus (USB) slots on modern computers. Although NICs range widely in price depending on their capabilities, intended use, and vendor, an internal 1 Gbps Ethernet NIC for a desktop personal computer (PC) could be purchased for less than $7, a USB Ethernet adapter for about $14, and a wireless USB adapter for less than $13 at the time of writing in January 2013.

4. Software. The three components above provide physical connectivity. Software—often called a network operating system (NOS)—is necessary for the devices to actually take advantage of the resource sharing that the LAN can provide. The NOS can support many types of services such as file sharing, print sharing, client/server operation, communications services, and more.

While the LAN needs to be examined in a holistic fashion, each of these components at each attached node also may require examination.

# 6.1.3 LAN Technology Parameters.

One final way of discussing the specific operation of the LAN is to describe the technology:

+   - **Physical topology**. The physical layout of the medium.
+   - **Logical topology**. The logical relationship of the LAN nodes to each other.
+   - **Media Access Control (MAC) Standard**. The specification describing the rules that each node follows to determine when it is its turn to transmit on the medium.
+   - **Use of the Logical Link Control (LLC) protocol**. Defines the frame format employed above the MAC layer, and additional services.
+   - **Use of higher-layer protocols**. Defines the node-to-node communicating protocols and additional higher-layer applications.

# 6.1.4 Summary.

It does not matter how a LAN is classified or described. It is essential, however, that the LAN be understood from a variety of perspectives to be able to apply a network-security examination.

# 6.2 LAN TOPOLOGY.

WANs typically use some sort of switched technology, such as traditional circuit switching, packet switching (e.g., X.25), or fast packet switching (e.g., frame relay or asynchronous transfer mode [ATM]). Indeed, point-to-point lines typically connect the network switches so that there is a single data transmission on the line at one time.

Historically, LANs have been broadcast networks, meaning that every LAN station hears every transmission on the medium. LAN topologies, then, have to support the broadcast nature of the network and provide full connectivity between all stations.

The topology of a network is used to describe two issues. The physical topology describes how the LAN stations are physically connected so that they can communicate with each other. The logical topology describes how the broadcast nature of the LAN is actually affected, and, therefore, how stations participate in the process of obtaining