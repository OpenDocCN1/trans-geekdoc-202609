every network device that touches the message must decrement this field. Since the packet may pass through multiple network devices in a second, the initial definition of this field isn't relevant anymore and the TTL really indicates the number of network devices (routing devices, essentially) the message can pass through. Once the field hits 0, the message is dis- carded and an error message is returned to the sender. This field is 8 bits long.

**Protocol** This is a numeric value indicating what the next protocol is. It is an 8-bit field and tells the receiving system what headers to look for in the transport header. In the case of the packet in Figure 2.9, the value is 17, which means it's a UDP message.

**Checksum** This is a 16-bit value that is used to determine whether the header is intact. It is defined as a 1's complement sum of the 16-bit words in the header.

**Source Address** This is the IP address that sent the message. It is 4 octets in length.

**Destination Address** This is the IP address that the message is going to. It is also 4 octets in length.

# Octets vs. Bytes

You will sometimes see the term _octet_ used and you may be wondering why we use the term _octets_ instead of _bytes_ since what we are referring to is a value that is 8 bits in length. The reason is that the RFCs were written to be implemented on any system. When these protocols were defined, a byte wasn't always 8 bits. Some bytes were 10 bits, oth- ers were 12, and some were 8. To be very clear, the word _byte_ wasn't used. Instead, a value that was 8 bits was an octet. If the word _octet_ is used, there is no confusion.

# Addressing

IP version 4 addresses are 4 octets long. They are commonly shown as being separated by a period (.). Because of this, they are sometimes referred to as dotted quads. Since each value is 8 bits, there are potential values of 0 to 255. Not all values, especially in the first two octets, are used, however. There are some addresses that are held in reserve, for various reasons. For a start, the address range 127.0.0.0–127.255.255.255 is reserved for loopback addresses. These are addresses that refer to the host they are assigned to. Commonly, the loopback address on systems is 127.0.0.1, though any address in that range could be used.

RFC 1918 also carves out ranges of IP addresses that are used for private networks. By convention, these addresses are not routable over the Internet. Most networks will do something to block source addresses from these ranges coming into their space, since they should never be originating from the outside of a network. The ranges for these private addresses, meant to be used by any network that doesn't have public IP addresses, are 10.0.0.0–10.255.255.255, 172.16.0.0–172.31.255.255, and 192.168.0.0–192.168.255.255.