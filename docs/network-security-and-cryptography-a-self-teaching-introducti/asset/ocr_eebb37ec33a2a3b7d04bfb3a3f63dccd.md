# 12.5.6 Anti-Replay Window

It is a sliding window protocol used at the recipient end. Let the window size be W and suppose at any time, the right edge of the window is aligned with slot number N as shown in Figure 12.8. Initially, all slots are unmarked.

![](bbox=[0.344, 0.246, 0.693, 0.00376])

FIGURE 12.8 Anti-Replay Window.

The received packets are processed as follows:

+   1. If the packet sequential number falls within the window and is (unmarked), then its ICV is a new packet (i.e., the slot in the window is checked. If the packet passes the ICV verification, then the packet is accepted and the corresponding slot in the window is marked, indicating that a valid packet has been received.

+   2. If the packet sequential number falls within the window but the corresponding slot has already been marked, then it indicates that the valid packet with the same sequence number has already been received; the new packet is taken as a replay packet and is rejected. Also, if the sequence number falls within the window, but its authentication, the packet is rejected. These are Auditable events.

+   3. If the packet sequence number falls to the left of the window, then the packet is taken as a Replay Packet and is discarded. This is also an audit-event.

+   4. If packet sequence number falls to the right of the window and the packet passes ICV verification, then the window is slid to the right such that the sequence number of the new packet is aligned with the right edge of the window. The packet is accepted as a valid packet and its slot is marked.