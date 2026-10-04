![](bbox=[0.26, 0.09, 0.81, 0.22])

![](bbox=[0.26, 0.27, 0.79, 0.44])

Figure 12-16 SLAAC Example

This is the process shown in Figure 12-16:

+   1. The router sends an RA message with the prefix for the local link.
2. The PC uses SLAAC to obtain a prefix from the RA message and creates its own interface ID.

# Method 2: SLAAC and Stateless DHCPv6 (12.5.3)

A router interface can be configured to send a router advertisement using SLAAC and stateless DHCPv6.

As shown in Figure 12-17, with this method, the RA message suggests devices use the following:

+   - SLAAC to create its own IPv6 GUA
- The router LLA, which is the RA source IPv6 address, as the default gateway address
- A stateless DHCPv6 server to obtain other information, such as a DNS server address and a domain name