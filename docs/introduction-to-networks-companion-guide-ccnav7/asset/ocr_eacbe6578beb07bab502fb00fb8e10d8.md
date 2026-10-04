Cisco offers OpenDNS, which provides secure DNS service by filtering phishing and some malware sites. You can change your DNS addresses to 208.67.222.222 and 208.67.220.220 in the Preferred DNS server and Alternate DNS server fields. Advanced features such as web content filtering and security are available to families and businesses.

Use the ipconfig /all command, as shown in Example 17-36, to verify which DNS server a Windows computer is using.

# Example 17-36 Using ipconfig /all to Verify the DNS Server in Use on a Windows Host

```
C:\Users\PC-A> ipconfig /all
(Output omitted)
Wireless LAN adapter Wi-Fi:
    Connection-specific DNS Suffix  . . : 
    Description . . . . . . . . . . . : Intel(R) Dual Band Wireless-AC 8265
    Physical Address. . . . . . . . . : F8-94-C2-E4-C5-0A
    DHCP Enabled. . . . . . . . . . . : Yes
    Autoconfiguration Enabled . . . . : Yes
    Link-local IPv6 Address . . . . . : fe80::a4aa:2dd1:ae2d:a75e%16(Preferred)
    IPv4 Address. . . . . . . . . . . : 192.168.10.10(Preferred)
    Subnet Mask . . . . . . . . . . . : 255.255.255.0
    Lease Obtained. . . . . . . . . . : August 17, 2019 1:20:17 PM
    Lease Expires . . . . . . . . . . : August 18, 2019 1:20:18 PM
    Default Gateway . . . . . . . . . : 192.168.10.1
    DHCP Server . . . . . . . . . . . : 192.168.10.1
    DHCPv6 IAID . . . . . . . . . . . : 100177090
    DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-21-F3-76-75-54-E1-AD-DE-DA-9A
    DNS Servers . . . . . . . . . . . : 208.67.222.222
    NetBIOS over Tcpip. . . . . . . . : Enabled
(Output omitted)
```

The nslookup command is another useful DNS troubleshooting tool for PCs. With nslookup, a user can manually place DNS queries and analyze the DNS responses. The nslookup command in Example 17-37 shows the output for a query for www.cisco.com. Notice that you can also simply enter an IP address, and nslookup will resolve the name.

# Note

For various reasons, it is not always possible to type an IP address in nslookup and receive the domain name. One of the most common reasons for this is that most websites run on servers that support multiple sites.