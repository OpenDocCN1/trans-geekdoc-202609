These networks operate in half-duplex mode, meaning only one device can send or receive at a time. Therefore, a process is needed to govern when a device can send and what happens when multiple devices send at the same time.

If two devices transmit at the same time, a collision occurs. For legacy Ethernet LANs, both devices detect the collision on the network. This is the Collision Detect (CD) portion of CSMA/CD. The NIC compares data transmitted with data received, or it recognizes that the signal amplitude is higher than normal on the media. In the event of a collision, the data sent by both devices is corrupted and needs to be re-sent.

Figures 6-17 through Figure 6-19 demonstrate the CSMA/CD process in legacy Ethernet LANs that use a hub.

In Figure 6-17, PC1 has an Ethernet frame to send to PC3. The PC1 NIC needs to determine whether any device is transmitting on the medium. If it does not detect a carrier signal (in other words, if it is not receiving transmissions from another device), it assumes that the network is available to send.

The PC1 NIC sends the Ethernet frame when the medium is available.

![](bbox=[0.22, 0.52, 0.85, 0.75])

# Figure 6-17 PC1 Sends a Frame

In Figure 6-18, the Ethernet hub receives and sends the frame. An Ethernet hub is also known as a multiport repeater. Any bits received on an incoming port are regenerated and sent out all other ports, as shown in the figure.

If another device, such as PC2, wants to transmit but is currently receiving a frame, it must wait until the channel is clear.