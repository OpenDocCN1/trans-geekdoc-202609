# Test Your Understanding

+   10.
+     a. What is the main access control threat to Ethernet LANs?
+     b. What is the main access control threat to wireless LANs?
+     c. Why is the access control threat to wireless LANs more severe?
+     d. Is eavesdropping usually a concern for wired LANs, wireless LANs, or both?

# 4.5 Ethernet Security

4.5 Explain how to secure Ethernet networks.

# Ethernet and 802.1X

We will begin looking at the specifics of LAN security with Ethernet and 802.1X. The 802.1X standard provides access control to prevent illegitimate clients from associating with a network. We will begin with Ethernet because 802.1X is relatively easy to implement in wired LANs.

Figure 4-18 illustrates the main elements of Ethernet and 802.1X security. 802.1X makes the Ethernet workgroup switch¹⁰ (3) the gateway to the network. The user’s computer connects via UTP to a wall jack or directly to the switch. Speaking more precisely, the computer connects to a specific port on the workgroup switch. That port is the real point of access control. Not surprisingly, the name of the 802.1X standard is Port-based Access Control.

> > The 802.1X standard provides access control to prevent illegitimate clients from associating with a network.

Figure 4-18 Ethernet and 802.1X

![](bbox=[0.3, 0.6, 0.88, 0.87])

¹⁰ A workgroup switch is the switch to which a client connects. By contrast, core switches connect switches to other switches. Workgroup switches provide access to the network, so placing access control in workgroup switches is an obvious choice.