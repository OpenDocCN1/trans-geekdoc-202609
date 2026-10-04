+   - **Cut-through switching:** With this frame forwarding method, the switch forwards the frame before it is entirely received. At a minimum, the destination address of the frame must be read before the frame can be forwarded.

A big advantage of store-and-forward switching is that the switch determines whether a frame has errors before propagating the frame. When an error is detected in a frame, the switch discards the frame. Discarding frames with errors reduces the amount of bandwidth consumed by corrupt data. Store-and-forward switching is required for quality of service (QoS) analysis on converged networks where frame classification for traffic prioritization is necessary. For example, voice over IP (VoIP) data streams need to have priority over web-browsing traffic.

Figure 7-20 shows the store-and-forward process.

![](bbox=[0.35, 0.38, 0.85, 0.6])

> A store-and-forward switch receives the entire frame, and computes the CRC. If the CRC is valid, the switch looks up the destination address, which determines the outgoing interface. The frame is then forwarded out the correct port.

Figure 7-20 Store-and-Forward Switching

# Cut-Through Switching (7.4.2)

In cut-through switching, the switch acts on the data as soon as it is received, even if the transmission is not complete. The switch buffers just enough of the frame to read the destination MAC address so that it can determine which port to use to forward the data. The destination MAC address is located in the first 6 bytes of the frame, following the preamble. The switch looks up the destination MAC address in its switching table, determines the outgoing interface port, and forwards the frame on to its destination through the designated switch port. The switch does not perform any error checking on the frame.

Figure 7-21 shows the cut-through switching process.