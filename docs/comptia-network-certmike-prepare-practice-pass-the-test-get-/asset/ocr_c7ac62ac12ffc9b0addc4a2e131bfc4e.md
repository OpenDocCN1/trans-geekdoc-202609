The speeds of the Ethernet networks have increased over the years, but the standards are backward compatible. Connecting a Fast Ethernet port to a Gigabit switch causes the switch port to adjust its speed from 1,000 to 100 Mbps. It is also possible to manually configure a switch port to a specific speed, but this is not usually necessary.

# Port Aggregation

A mechanism for combining the bandwidth of two or more ports to create a single aggregated port with increased bandwidth. Many switches use the Link Aggregation Control Protocol (LACP) to manage port aggregations.

# Flow Control

An Ethernet standard for the regulation of transmission based on network congestion levels. A host can generate an Ethernet Pause frame with a delay value, which causes the switch to stop forwarding traffic to that host until the delay expires or the host sends another frame with a delay value of 0.

# Port Mirroring

Switches forward packets only to the destinations, which makes it difficult for administrators to monitor network traffic for a specific port. Port mirroring, when enabled, creates a relationship between the selected port and another unused port. This allows administrators to connect a protocol analyzer to the mirror port and capture network traffic.

# Port Security

To help prevent intruders from connecting unauthorized devices to the network, administrators can secure individual switch ports by specifying the MAC addresses of the only devices permitted to use them.

# Jumbo Frames

In the IEEE 802.3 standards, the default maximum payload size for an Ethernet frame is 1500 bytes. However, Ethernet equipment manufacturers have for years supporting larger frame sizes, collectively called jumbo frames. Jumbo frame sizes can vary, but a 9,000-byte maximum payload is common. Jumbo frame capability is not defined in any of the 802.3 standards, and administrators can configure switch ports to support it or not. Using jumbo frames on a network, all of the switches and adapters processing the packets must have the feature it enabled.

# Power over Ethernet (PoE)

A standard published by the IEEE 802.3 working group defines a method for Ethernet networks to supply power to remote devices over UTP cables. These devices such as Voice over IP (VoIP) phones, wireless access points, and remote video cameras to function on the network without the need for a separate power source. The first PoE standard called for the transmission of 12.95 watts of power. In later standards, Power over Ethernet Plus (PoE+) increased the power to 25.5 watts, and PoE++ increased it further, with power levels of 51 and 71.3 watts.