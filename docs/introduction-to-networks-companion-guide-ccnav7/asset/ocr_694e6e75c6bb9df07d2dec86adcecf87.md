The offer message contains the IPv4 address and subnet mask to be assigned, the IPv4 address of the DNS server, and the IPv4 address of the default gateway. The lease offer also includes the duration of the lease.

![](bbox=[0.23, 0.18, 0.8, 0.5])

# Figure 15-23 DHCP Messages

The client may receive multiple DHCPOFFER messages if the local network has more than one DHCP server. In such a case, the client must choose between the offers and sends a DHCP request (DHCPREQUEST) message that identifies the explicit server and lease offer that it is accepting. A client may also choose to request an address that it was previously allocated by the server.

If the IPv4 address requested by the client or offered by the server is still available, the server returns a DHCP acknowledgment (DHCPACK) message that acknowledges to the client that the lease has been finalized. If the offer is no longer valid, the selected server responds with a DHCP negative acknowledgment (DHCPNAK) message. If a DHCPNAK message is returned, the selection process must begin again, with a new DHCPDISCOVER message being transmitted. After the client has the lease, it must be renewed prior to the lease expiration through another DHCPREQUEST message.

The DHCP server ensures that all IP addresses are unique; that is, the same IP address cannot be assigned to two different network devices simultaneously. Most ISPs use DHCP to allocate addresses to their customers.

DHCPv6 has a set of messages that are similar to those for DHCP for IPv4. The DHCPv6 messages are SOLICIT, ADVERTISE, INFORMATION REQUEST, and REPLY.