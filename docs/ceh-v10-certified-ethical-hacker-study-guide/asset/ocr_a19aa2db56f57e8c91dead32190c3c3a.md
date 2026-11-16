# FIGURE 11.2 Wireless infrastructure network

![](bbox=[0.305, 0.135, 0.705, 0.385])

To demonstrate that idea, take a look at Figure 11.3. This is a Wireshark capture with monitor mode enabled on the wireless interface. This means Wireshark gets everything down to the radio headers, which is the layer 1/2 set of headers for the frame. This particular system is not connected to any wireless network. You can think of that as having a wired interface being disconnected. As that's the case, Wireshark shouldn't be seeing anything, and if monitor mode was turned off, even with promiscuous mode on, there wouldn't be anything in the capture.

# FIGURE 11.3 Wireshark capture of radio traffic

![](bbox=[0.155, 0.575, 0.855, 0.925])