packet coming from the upper layer that, among other things, includes the logical addresses of the sender and receiver.

+   - Routing: When independent networks or links are connected together to create an internetwork (a network of networks) or a large network, the connecting devices (called routers or gateways) route the packets to their final destination. One of the functions of the network layer is to provide this with mechanism.

# # Data Link Layer

The data link layer is where information is converted into coherent “packets” and frames that are passed to higher layers. Essentially, the data link layer unpacks data coming in from the physical layer and translates information from the upper layers into raw data to be sent over the physical layer. The data link layer is also responsible for catching and compensating for any errors that occur in the physical layer.

Specific responsibilities of the data link layer include:

+   - Framing: The data link layer divides the stream of bits received from the network layer into manageable data units called frames.
- Physical Addressing: If frames are to be distributed to different systems on the network, the data link layer adds a header to the frame to define the physical address of the sender (source address) and/or receiver (destination address) of the frame. If the frame is intended for a system outside the sender’s network, the receiver address is the address of the device that connects one to the next.
- Flow Control: At the rate at which the data are absorbed by the receiver is less than the rate produced in the sender, the data link layer imposes a flow control mechanism to prevent overwhelming the receiver.

# Li-Fi Data Link Layer

![](bbox=[0.303, 0.679, 0.673, 0.822])

**Figure 6**: Data link layer.

+   - Error Control: The data link layer adds reliability to the physical layer by adding mechanisms to detect and retransmit damaged or lost frames. It also uses a mechanism to prevent duplication of frames. Error control is normally achieved through a trailer added to the end of the frame.