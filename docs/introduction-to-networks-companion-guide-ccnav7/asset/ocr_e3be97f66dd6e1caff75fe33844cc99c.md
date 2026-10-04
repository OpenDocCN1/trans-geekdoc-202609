# Dynamic Addressing for IPv6 GUAs (12.5)

This section discusses the different ways a device can automatically create or receive an IPv6 GUA.

# RS and RA Messages (12.5.1)

If you do not want to statically configure IPv6 GUAs, don’t worry. Most devices obtain their IPv6 GUAs dynamically. This section explains how this process works when using Router Advertisement (RA) messages and Router Solicitation (RS) messages. This section gets rather technical, but when you understand the difference between the three methods that a router advertisement can use, as well as how the EUI-64 process for creating an interface ID differs from a randomly generated process, you will have made a huge leap in your IPv6 expertise!

For the GUA, a device obtains the address dynamically through Internet Control Message Protocol version 6 (ICMPv6) messages. IPv6 routers send out ICMPv6 RA messages every 200 seconds to all IPv6-enabled devices on the network. An RA message is also sent in response to a host sending an ICMPv6 RS message, which is a request for an RA message. As shown in Figure 12-15, these messages work as follows:

![](bbox=[0.25, 0.53, 0.8, 0.73])

Figure 12-15 ICMPv6 RS and RA Messages

+   1. RS messages are sent to all IPv6 routers by hosts requesting addressing information.
2. RA messages are sent to all IPv6 nodes. If Method 1 (SLAAC only) is used—as described in the next section—the RA includes network prefix, prefix length, and default gateway information.