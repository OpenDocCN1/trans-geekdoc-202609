| Version | Bandwidth | Range |
|---------|-----------|-------|
| 3.0     | 25Mbps    | 10 meters (33 feet) |
| 4.0     | 25Mbps    | 60 meters (200 feet) |
| 5.0     | 50Mbps    | 240 meters (800 feet) |

# Other Wireless Protocols

There are several other wireless communication protocols, including the following:

+   - ANT+: This wireless protocol is often used with sensor data such as in bio sensors or exercise applications.
+   - ZigBee: This standard was developed by a consortium of electronics manufacturers for mainly residential applications of wireless devices related to appliances and security. It is based on the 802.15.4 standard. What appears to be confusing is that the standard is represented by the name “ZigBee” rather than a number. The term ZigBee is used similar to the way the term Wi-Fi is used.
+   - Z-Wave: This wireless communications protocol is used primarily for home automation. It uses a low-energy radio for appliance-to-appliance communication using a mesh network.

# Data Transmission

We've seen, briefly, the physical connection methods; but how is data actually transmitted? To transmit data, a packet is sent. The basic purpose of a cable is to transmit packets from one machine to another. It does not matter whether the packets are part of a document, a video, an image, or just some internal signal from the computer. So what, exactly, is a packet? As we discussed earlier, everything in a computer is ultimately stored as 1s and 0s, called bits, which are grouped into sets of eight, each called a byte. A packet is a certain number of bytes divided into a header and a body. The header is 20 bytes at the beginning of the packet that tells you where the packet is coming from, where it is going, and more. The body contains the actual data, in binary format, that you wish to send. The aforementioned routers and switches work by reading the