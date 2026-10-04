![](bbox=[0.18, 0.1, 0.9, 0.65])

Figure 15-21 DNS Hierarchy

# The nslookup Command (15.4.4)

When configuring a network device, one or more DNS server addresses are provided that the DNS client can use for name resolution. Usually the ISP provides the addresses to use for the DNS servers. When a user application requests to connect to a remote device by name, the requesting DNS client queries the name server to resolve the name to a numeric address.

Computer operating systems also have a utility called nslookup that allows a user to manually query the name servers to resolve a given hostname. This utility can also be used to troubleshoot name resolution issues and to verify the current status of the name servers.

When the nslookup command is issued, the default DNS server configured for the host is displayed, as shown in Example 15-1. The name of a host or domain can be