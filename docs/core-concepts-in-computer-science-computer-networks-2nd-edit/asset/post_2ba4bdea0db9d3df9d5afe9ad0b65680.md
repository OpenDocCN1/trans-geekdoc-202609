
## Session Layer

The session layer is where connections are maintained and ended. This usually refers to application requests for data over the network. Whereas the transport layer handles the actual flow of data, the session layer acts as an announcer, making sure that the programs and applications requesting and sending data know their requests are filled. In technical terms, the session layer synchronizes data transmission.

> The Session Layer is responsible for establishing, maintaining, and terminating sessions between different devices. It serves as a link between the Transport Layer (Layer 4) and the Presentation Layer (Layer 6) in the OSI model.

Specific responsibilities of the session layer include:

- *Dialog Control: The session layer allows two systems to enter into a dialog. It allows the communication between two processes to take place either in half-duplex (one way at a time) or full-duplex (two ways at a time). For example, the dialog between a terminal connected to a mainframe can be half-duplex.
- *Synchronization: The session layer allows a process to add checkpoints to a stream of data.

![](img/f7819d05465fc14719b3ebbba980271a_55_0.png)

**Figure 3**: Session layer.

## Transport Layer

The transport layer is responsible for streaming data across the network. At this level, the data is not thought of in terms of individual packets but in terms of a conversation. To accomplish this, protocols which are defined as “rules of communication” are used. The protocols watch the complete transmission of many packets checking the conversation for errors, acknowledging successful transmissions and requesting retransmission if errors are detected.

Specific responsibilities of the transport layer include:

- *Service-Point Addressing: Computers often run several programs at the same time. For this reason, source-to-destination delivery means delivery not only from one computer to the next but also from a specific process (running program) on one computer to a specific process (running program) on the other. The transport header therefore must include a type of address called a service-point address (or port address). The network layer gets each packet to the correct computer; the transport layer gets the entire message to the correct process on computer.
- *Segmentation and Reassembly: A message is divided into transmittable segments, each segment containing a sequence number. These numbers enable the transport layer to reassemble the message correctly upon arriving at the destination and to identify and replace packets that were lost in the transmission.

![](img/f7819d05465fc14719b3ebbba980271a_56_0.png)

**Figure 4:** Transport layer.

- *Connection Control: The transport layer can be either connectionless or connection-oriented. A connectionless transport layer treats each segment as an independent packet and delivers it to the transport layer at the destination machine. A connection-oriented transport layer makes a connection with the transport layer at the destination machine first before delivering the packets. After all the data are transferred, the connection is terminated.
- *Flow Control: Like the data link layer, the transport layer is responsible for flow control. However, flow control at this layer is performed end to end rather than across a single link.
- *Error Control: Like the data link layer, the transport layer is responsible for error control. However, error control at this layer is performed end to end rather than across a single link. The sending transport layer makes sure that the entire message arrives at the receiving transport layer without error (damage, loss, or duplication). Error correction is usually achieved through retransmission.

## Network Layer

The network layer is responsible for the source-to-destination delivery of a packet possibly across multiple networks. Whereas the data link layer oversees the delivery of the packet between two systems on the same network (links), the network layer ensures that each packet gets from its point of origin to its final destination.

If two systems are connected to the same link, there is usually no need for a network layer. However, if the two systems are attached to different networks (links) with connecting devices between the networks, there is often a need for the network layer to accomplish source-to-destination delivery.

![](img/f7819d05465fc14719b3ebbba980271a_57_0.png)

Internet is a collection of interconnected networks that use common communication protocols and technologies to form a larger, global network.

Figure 5: Network layer.

Specific responsibilities of the network layer include:

- *Logical Addressing: The physical addressing implemented by the data link layer handles the addressing problem locally. If a packet passes the network boundary, one needs another system to help distinguish the source and destination systems. The network layer adds a header to the packet coming from the upper layer that, among other things, includes the logical addresses of the sender and receiver.
- *Routing: When independent networks or links are connected together to create an internetwork (a network of networks) or a large network, the connecting devices (called routers or gateways) route the packets to their final destination. One of the functions of the network layer is to provide this with mechanism.

## Data Link Layer

The data link layer is where information is converted into coherent “packets” and frames that are passed to higher layers. Essentially, the data link layer unpacks data coming in from the physical layer and translates information from the upper layers into raw data to be sent over the physical layer. The data link layer is also responsible for catching and compensating for any errors that occur in the physical layer.

Specific responsibilities of the data link layer include:

- *Framing: The data link layer divides the stream of bits received from the network into manageable data units called frames.
- *Physical Addressing: If frames are to be distributed to different systems on the network, the data link layer adds a header to the frame to define the physical address of the sender (source address) and receiver (destination address).
- *Flow Control: At the rate at which data are absorbed by the receiver is less than the rate produced by the sender, the data link layer imposes a flow control mechanism to prevent overwhelming the receiver.
- *Error Control: The data link layer adds reliability to the physical layer by adding mechanisms to detect and retransmit damaged or lost frames. It also uses a trailer added to the end of the frame to prevent duplication.

img/f7819d05465fc14719b3ebbba980271a_58_0.png)

**Figure 6**: Data link layer.

- *Access control: When two or more devices are connected to the same link, data link layer protocols are necessary to determine which device has control over the link at any given time.

## Physical Layer

The physical layer is the actual cable, interfaces, fibers, cards, switches, and other mechanical and electrical equipment that make up a network. This is the layer that transforms digital data into signals that can be sent down a wire to transmit data. These signals are often electrical, but in the case of fiber optics, they can also be non-electrical signals such as optics or any other type of pulse that can be digitally encoded. From a networking perspective, the purpose of the physical layer is to provide the architecture for data to be sent and received. The physical layer is probably the easiest layer to troubleshoot or construct, as this involves getting the hardware infrastructure hooked up and plugged in.

![](img/f7819d05465fc14719b3ebbba980271a_59_0.png)

Figure 7: Physical layer.

The physical layer is concerned with:

- *Physical Characteristics of Interfaces and Media: The physical layer defines the characteristics of the interface between the devices and the transmission medium. It also defines the type of transmission medium.
- *Representation of Bits: The physical layer consists of a stream of bits (sequence of 0’s and 1’s) without any interpretation. The physical layer defines the type of encoding (how 0’s and 1’s are changed to signals).
- *Data Rate: The transmission rate of bits sent each second is also defined by the physical layer. In other words, the physical layer defines the duration of a bit, which is how long it lasts.
- *Synchronization of Bits: The sender and receiver must be synchronized at the bits

| Physical Layer is responsible for converting digital bits into electrical, optical, or radio signals that can be transmitted over the network medium and vice versa, converting received signals back into digital data that higher layers can process |
