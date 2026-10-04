
The MAC address is broken up into two sections: an Organizationally Unique Identifier (`OUI`) and a *network interface identifier*. The network interface identifier is assigned by the manufacturer of the Ethernet chipset. Companies producing Ethernet chipsets, in turn, are assigned the organizational identifiers by the Institute of Electrical and Electronic Engineers (the `IEEE`). So long as an organization (or manufacturer) always assigns addresses to a chipset with its `OUI` in the first three octets of the MAC address, and does not assign any two devices the same network interface identifier in the last three octets of the MAC address, *no two MAC addresses should be the same for any Ethernet chipset*.

Two bits within the `OUI` space are set aside to signal whether the MAC address has been locally assigned (which means the manufacturer’s assigned MAC address has been overridden by the device’s configuration), and whether the MAC address is intended as one of the following:

• Unicast address, which means it describes a single interface

• Multicast address, which means it describes a group of receivers

The MAC address consists of 48 bits; with these two bits removed, the MAC address space is 46 bits, which means it can describe 2^(46)—or 70,368,744,177,664— addressable interfaces. Because this is (potentially) not enough to account for the rapid number of new addressable devices, such as Bluetooth headsets and sensors, the length of a MAC address was increased to 64 bits to create the EUI-64 MAC address, which is constructed in the same way as the shorter 48-bit MAC address. These addresses can support 2^(62)—or 4,611,686,018,427,387,904—addressable interfaces.

### The End of CSMA/CD

The shared medium model of Ethernet deployment has largely (though not completely!) been replaced in most networks. Rather than a shared medium, most Ethernet deployments now are switched, which means the single electrical circuit, or the single wire, is broken up into multiple circuits by connecting each device to a port on a switch. [Figure 4-4](#ch04.xhtml#ch04fig04) illustrates.

![Image](graphics/04fig04.jpg)

**Figure 4-4** *Switched Ethernet Network Operation*

In [Figure 4-4](#ch04.xhtml#ch04fig04), each device is connected to a different set of wires, all of which terminate in a single switch. If the network interfaces at the three hosts (A, B, and C), and the switch network interfaces, can send or receive at any moment in time, rather than being able to do both, it is possible for A to send while the switch is also sending. In this case, the CSMA/CD process must still be followed in order to prevent collisions, even on networks where only two transmitters are connected to the same wire. This mode of operation is called half duplex.

If the Ethernet chipsets can both listen and transmit at the same time in order to detect collisions, however, this situation can be changed. The easiest way to manage this is to place the receive and transmit signals on *different physical wires* within the set of wires used in the Ethernet cable. Using different wires means there is no way for the transmissions from the two connected systems to collide, so the chipset can both transmit and receive at the same time. To enable this mode of operation, called full duplex, twisted pair Ethernet carries the signal in one direction on one pair of wires, and the signal in the opposite direction on another set of wires. In this case, CSMA/CD is no longer needed.

**Note**

The switch must learn which device (host) is connected to each port for this system to work; learning about the reachable destinations in a switched network is considered in [Chapter 15](#ch15.xhtml#ch15), “[Distance Vector Control Planes](#ch15.xhtml#ch15).”

### Error Control

CSMA/CD is designed to prevent one kind of detectable error in Ethernet: when collisions cause a frame to be malformed. Other kinds of errors can slip into a signal, however, as with any other electrical or optical system. For instance, in a twisted pair cabling system, if the twisted wires are “unwound” too much in installing a connector, one wire can transfer its signal to another wire through magnetic interference, causing cross talk. As a signal travels down a wire, it can reach the other end of the wire and reflect back along the length of the wire, as well.

How does Ethernet control for these errors? The original Ethernet standard included a 32-bit Cyclic Redundancy Check (`CRC`) in each frame, which can detect a large array of errors in transmission, as noted in [Chapter 2](#ch02.xhtml#ch02), “[Data Transport Problems and Solutions](#ch02.xhtml#ch02).” At higher speeds, and on optical (rather than electrical) transport mechanisms, however, `CRC` can fail to detect enough errors to impact the operation of the protocol. To provide better error control, later (and faster) Ethernet standards have included more robust error control mechanisms.

For instance, Gigabit Ethernet specifies an 8B10B encoding scheme designed to ensure the correct synchronization of sender and receiver clocks; this scheme also detects some bit errors, as well. Ten-gigabit Ethernet is often implemented in hardware with a Reed-Solomon code Error Correction (`EC`) system and a 16B18B encoding system, which provides good Forward Error Correction (`FEC`) and clock synchronization with 18% overhead.

**Note**

The 8B10B encoding scheme attempts to ensure there are approximately the same number of 0 and 1 bits in a data stream, which allows for efficient laser utilization and provides for clock synchronization to be embedded in the signal. The scheme works by encoding 8 bits of data (8B) into 10 transmitted bits on the wire (10B), which means there is about 25% overhead for each character transmitted. Single bit parity errors can be detected and corrected because the receiver knows how many 0s and 1s should have been received.

### Data Marshaling

Ethernet transmits data in *packets* and *frames;* the packet is made up of the preamble information, the frame, and any trailing information. The frame contains a header, which is made up of fixed length fields, and the data being carried. [Figure 4-5](#ch04.xhtml#ch04fig05) illustrates an Ethernet packet; the frame is marked out as well.

![Image](graphics/04fig05.jpg)

**Figure 4-5** *An Ethernet Packet and Frame*

In [Figure 4-5](#ch04.xhtml#ch04fig05), the preamble contains a beginning of frame marker, information the receiver can use to synchronize its clock to synchronize to the incoming packet, and other information. The destination address is received immediately after the preamble, so the receiver can quickly decide whether to copy this packet into memory or not. The addresses, protocol type, and carried data are all part of the frame. Finally, any `FEC` information and other trailers are added onto the frame to make up the final section(s) of the packet.

The type field is of particular interest, as this provides the information for the next layer up—the protocol providing the information carried in the data field—to identify the protocol. This information is opaque to Ethernet—the Ethernet chipset does not know how to interpret this information (only where it is), and how to carry it. Without this field there would be no consistent way for the carried data to be dispatched to the correct upper-layer protocol, or rather, for multiple upper-layer protocols to be properly multiplexed into Ethernet frames, and then properly demultiplexed.

### Flow Control
