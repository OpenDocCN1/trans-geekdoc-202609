
*First*, many addresses are never used because addresses are aggregated. Aggregation is the use of a single prefix (or network, or reachable destination) to represent a larger number of reachable destinations; [Figure 5-6](#ch05.xhtml#ch05fig06) illustrates.

![Image](`graphics/05fig06.jpg`)

**Figure 5-6** *Address Aggregation in IPv6*

In [Figure 5-6](#ch05.xhtml#ch05fig06):

• Hosts A and B are given `101::1` and `101::2` as their IPv6 addresses. These two hosts are, however, connected to a single broadcast segment (such as Ethernet), and hence share the same interface at C. Even though C has an address on this shared network, it actually advertises the network itself—some engineers find it helpful to think of the *wire itself*—as a reachable destination: `101::/64`.

• E receives two reachable destinations, `101::/64` from C and `102::/64` from D. By decreasing the prefix length, it can advertise a single reachable destination that includes both of these two *longer prefix* reachable destinations. E advertises `100::/60`.

• G, in turn, receives `100::/60` from E, and `110:/60` from F. Again, this same address space can be described using a single reachable destination, `100::/56`, so this is what G advertises.

How does this aggregation work in the actual address space? [Figure 5-7](#ch05.xhtml#ch05fig07) is used to explain.

![Image](`graphics/05fig07.jpg`)

**Figure 5-7** *Aggregation and Reachable Destinations in IPv6 Addressing*

The prefix length, which is the number after the slash in a reachable destination, tells you the number of bits that count in determining what is part of the prefix (and hence also what is not). The prefix length is counted from the left to the right. Any set of addresses with the same values in the numbers within the prefix length are considered to be part of the same reachable destination.

• There are 128 bits in the full IPv6 address space, so a `/128` represents a single host.

• In an address with a 64-bit prefix length (`/64`), only the left four sections of the IPv6 address are part of the prefix, or the reachable destination; the remainder, the four right sections of the IPv6 address, are assumed to either be host or subnetwork addresses that are “contained” in the prefix.

• In an address with a 60-bit prefix length (`/60`), the left four sections of the IPv6 address *minus one* hexadecimal digit are considered part of the reachable destination, or the prefix.

• In an address with a 56-bit prefix length (`/56`), the left four sections of the IPv6 address *minus two* hexadecimal digits are considered part of the reachable destination, or the prefix.

**Note**

So long as you always change the prefix length in increments of 4 (`/4`, `/8`, `/12`, `/16`, etc.), the significant digits, or the digits that are part of the prefix, will always move one to the right (as you increase the prefix length) or the left (as you decrease the prefix length).

Aggregation sometimes seems complicated, but it is an essential part of IP.

Some of the address space is consumed in autoconfiguration. While autoconfigu-ration is not covered in detail here, the interaction between autoconfiguration and IPv6 address assignment is important to consider. Some amount of address space must generally be set aside to ensure no two devices connected to the network will end up with the same identifier. In the case of IPv6, half of the address spaces (everything greater than a `/64`), within certain ranges of addresses, are set aside in order to form unique per device identifiers.

*Third*, some addresses are set aside for special use. For instance, in IPv6, the following address spaces are assigned to some special use:

• `::ffff/96` is set aside for IPv4 addresses that are “mapped into” the IPv6 address space.

• `fc00::/7` is set aside for unique local addresses (ULAs); packets with these addresses are not intended to be routed on the global Internet, but rather kept within the network of a single organization.

• `fe80::/10` is set aside for link local addresses; these addresses are automatically assigned on each interface, and are only used for communicating over a single physical or virtual link.

• `::/0` is set aside as a default route; if a network device does not know of any other way to reach a particular destination, it will forward traffic toward the default route.

*Fourth*, devices can be assigned multiple addresses. Many engineers tend to think of an address as if it describes a single host or system. In reality, a single address can be used to describe many things, including

• A single host or system

• A single interface on a host or system; a host with multiple interfaces would have multiple addresses

• A set of reachable services on a host or system; for example, a virtual machine or a particular service running on a host may be assigned an address that is different from any of the addresses assigned to the host’s interfaces

There is no necessary direct correlation between an address and a physical device, or an address and a physical interface.

### Multiplexing Between Processes

The second multiplexing mechanism is allowing multiple protocols to run over the same base layer. This form of multiplexing is provided through protocol numbers; [Figure 5-8](#ch05.xhtml#ch05fig08) illustrates.

![Image](`graphics/05fig08.jpg`)

**Figure 5-8** *The Protocol Number in IPv6*

The next header field either points to

• The next header in the IPv6 packet, if there is a next header

• A protocol number, if the next header is a transport protocol (such as TCP)

These additional headers are called optional or extension headers; some of them are fixed length, and others are TLV based; for instance:

• **Hop-by-hop options:** A set of TLVs describing actions each forwarding device should take

• **Routing:** A set of fixed length route types used to indicate the path the packet should take through the network

• **Fragment:** A fixed length set of fields providing packet fragment information (as described above)

• **Authentication header:** A set of TLVs containing authentication and/or encryption information

• **Jumbogram:** An optional data length field enabling the IPv6 packet to carry up to one byte less than 4GB of data

The next header field is 8 bits long, which means it can carry a number between 0 and 255. Each number in this range is assigned either to a specific kind of option header or a specific higher layer protocol. For instance:

• `0:` The next header is an IPv6 hop-by-hop option.

• `1:` The packet payload is the Internet Control Message Protocol (ICMP).

• `6:` The packet payload is TCP.

• `17:` The packet payload is the User Datagram Protocol (UDP).

• `41:` The packet payload is IPv6.

• `43:` The next header is an IPv6 routing header.

• `44:` The next header is an IPv6 fragment header.

• `50:` The next header is an Encapsulated Security Header (ESH).

The protocol number is used by the receiving host to dispatch the contents of the packet to the correct local process for processing; normally, this means stripping the lower (physical) layer headers off the packet, placing the packet into the input queue for the correct process (such as TCP), and then notifying the operating system the relevant process needs to run.

### Transmission Control Protocol

The primary goal of TCP is to provide what appears to be a connection-oriented transport on top of IP. As a higher layer protocol, it relies on the addressing and multiplexing capabilities of IPv6 to carry information to the correct destination host. Because of this, TCP does not require an address scheme. The focus of TCP is on flow and error control, considered in separate sections below. A short section on TCP port numbers rounds out this discussion of TCP.

#### Flow Control

TCP uses a sliding window method to control the flow of information across each connection between two hosts; [Figure 5-9](#ch05.xhtml#ch05fig09) illustrates.

![Image](`graphics/05fig09.jpg`)
