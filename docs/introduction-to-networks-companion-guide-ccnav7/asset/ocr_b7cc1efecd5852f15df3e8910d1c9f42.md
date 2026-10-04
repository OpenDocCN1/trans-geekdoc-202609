media could be subject to interference, distortion, or loss that would substantially change the bit values that those signals represent.

A transmitting node creates a logical summary of the contents of the frame, known as the cyclic redundancy check (CRC) value. This value is placed in the Frame Check Sequence (FCS) field to represent the contents of the frame. In the Ethernet trailer, the FCS provides a method for the receiving node to determine whether the frame experienced transmission errors.

# Layer 2 Addresses (6.3.3)

The data link layer provides the addressing used in transporting a frame across a shared local medium. Device addresses at this layer are referred to as physical addresses. Data link layer addressing is contained within the frame header and specifies the frame destination node on the local network. It is typically at the beginning of the frame, so the NIC can quickly determine if it matches its own Layer 2 address before accepting the rest of the frame. The frame header may also contain the source address of the frame.

Unlike Layer 3 logical addresses, which are hierarchical, physical addresses do not indicate on what network a device is located. Rather, a physical address is unique to a specific device. A device still functions with the same Layer 2 physical address even if the device moves to another network or subnet. Therefore, Layer 2 addresses are only used to connect devices within the same shared medium on the same IP network.

Figure 6-23 through 6-25 illustrate the function of the Layer 2 and Layer 3 addresses. As an IP packet travels from host to router, router to router, and finally router to host, at each point along the way, the IP packet is encapsulated in a new data link frame. Each data link frame contains the source data link address of the NIC sending the frame and the destination data link address of the NIC receiving the frame.

In Figure 6-23, the source host encapsulates the Layer 3 IP packet in a Layer 2 frame. In the frame header, the host adds its Layer 2 address as the source and the Layer 2 address for R1 as the destination.

In Figure 6-24, R1 encapsulates the Layer 3 IP packet in a new Layer 2 frame. In the frame header, R1 adds its Layer 2 address as the source and the Layer 2 address for R2 as the destination.

In Figure 6-25, R2 encapsulates the Layer 3 IP packet in a new Layer 2 frame. In the frame header, R2 adds its Layer 2 address as the source and the Layer 2 address for the server as the destination.