# Chapter 23 · Network Software Tools and Commands

Connection-specific DNS Suffix :
Description . : Intel(D) Dual Band Wireless-AC 8265
Physical Address . : E4-70-B8-B8-23-1E4
DHCP Enabled . : Yes
Autoconfiguration Enabled . : Yes
fe88::9873:dbd5:dc79:9a5aa%14(Preferred)
IPv4 Address . : 192.168.1.21 (Preferred)
Subnet Mask . : 255.255.255.0
Lease Obtained . : Thursday, January 12, 2023 2:27:07 AM
Lease Expires : Tuesday, January 17, 2023 2:29:14 PM
Default Gateway . : 192.168.1.1
DHCP Server . : 192.168.1.1
DHCP6 ID : 98857144
DHCP6 Client ID . : 00-01-00-01-B2-B8-75-54-E1-AD-D5-96
DNS Servers . : 192.168.1.1
NetBIOS over Tcpip . : Enabled

On using DHCP for addressing, ipconfig is the easiest way to learn the address of the system. It is also possible to use ifconfig to release and renew DHCP assignments.

On Unix and Linux distributions, the standard ifconfig can display information about an interface and modify its configuration settings as well, the ifconfig command uses a different format for its output, like the following:

```
eth0: flags=4163 <BROADCAST,RUNNING,MULTICAST> mtu 1500
inet192.168.1.45 netmask 255.255.255.0 broadcast 192.168.1.255
inet fe80::215:dff::fe0:f05 prefixlen 64 scope 0x28<link>
ether 08:15:52:00:f8:04 txqueuel 1000 (Ethernet)
RX packets 53064 bytes 78323568 (78.3 MB)
RX errors 0 dropped overruns 0 frame
TX packets 33235 bytes 243084 (243.0 KB)
TX errors 0 dropped overruns 0 carrier 0 collisions 0
```

The tool is another Unix/Linux utility that is replacing ifconfig on some distributions. The tool can display and configure interface settings, much like ifconfig, but it can also do a great deal more, including static routes, multicasts, tunnels, and ARP tables.

# Nslookup/Dig

Nslookup is a Domain Name System (DNS) tool, found on both Windows and Unix/Linux platforms, that allow users to resolve hostnames and domain names into addresses, both from the command line and interactively. By default, entering nslookup www.contoso.com