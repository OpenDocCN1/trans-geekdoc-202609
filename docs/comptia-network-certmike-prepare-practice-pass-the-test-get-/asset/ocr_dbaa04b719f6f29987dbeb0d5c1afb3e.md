The same principles hold true for network-based firewalls, typically located between an internal network and the Internet between a screened (or perimeter) subnet and the internal network. Troubleshooters can check the firewall logs to see if any traffic related to a problematic connection was blocked by the firewall. The general rule of least privilege applies to all firewalls; let only the essential traffic through and block everything else. The difference using network-based firewalls is that the stakes are far higher since these firewalls are the network's protection against Internet intruders.

# Blocked Services, Ports, or Addresses

For network communication to occur, the systems must have the correct TCP and UDP ports open so that packets can enter and leave the systems from places. Most applications and services open the ports they need during installation, but firewalls—either on the host or on the network—can block these essential ports, rendering the application or service inaccessible from the network. When applying the least privilege principle to a network, administrators inadvertently block essential ports they were not aware an application needed. As mentioned earlier, when dealing with network communication problems, troubleshooters should always keep firewall rules in mind as potential sources of blockages.

The net command can list the open ports on a system, as shown in Chapter 23, "Network Software Tools and Commands." A port scanner can detect open ports on the network. Both are useful tools when to troubleshoot a malfunctioning (or nonfunctioning) application.

# Incorrect VLAN

As noted in this chapter, an incorrect VLAN assignment is essentially the virtualized equivalent of connecting a device to the wrong device. The device will likely be assigned an incorrect IP address and will be unable to access the user's familiar resources. It is also possible that the device could receive enhanced privileges as a result of connecting to the wrong VLAN. Troubleshooters should check the VLAN configuration at the switch when these wrong situations occur.

# DNS Issues

The Domain Name System (DNS) resolves server and domain names to IP addresses. If name resolution fails to occur, it might appear to the average user as though the network connection is down, but that might not be so. It is only the DNS that is experiencing a problem. A network might have a DNS server on the internal network, or it might be the ISP's DNS server. While, the DNS relies on other servers on the Internet, when the Internet connection goes down, DNS does as well.

In cases of DNS issues, the name resolution is not working at all or it is returning incorrect information. Troubleshooting a name resolution failure typically starts with checking that the host is configured with the correct DNS server address. If is, the next step is to check the DNS server the host is configured to use. The DNS service or