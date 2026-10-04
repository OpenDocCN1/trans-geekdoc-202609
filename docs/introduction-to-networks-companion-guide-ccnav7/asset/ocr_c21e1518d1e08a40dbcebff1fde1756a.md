# Example 17-11  Verifying the IP Configuration on a Windows Host

```
C:\Users\PC-A> ipconfig
Windows IP Configuration
(Output omitted)
Wireless LAN adapter Wi-Fi:
    Connection-specific DNS Suffix  . :
    Link-local IPv6 Address . . . . . : fe80::a4aa:2dd1:ae2d:a75e%16
    IPv4 Address. . . . . . . . . . . : 192.168.10.10
    Subnet Mask . . . . . . . . . . . : 255.255.255.0
    Default Gateway . . . . . . . . . : 192.168.10.1
(Output omitted)
```

You can use the ipconfig /all command to view the MAC address, as well as a number of details regarding the Layer 3 addressing of the device, as shown in Example 17-12.

# Example 17-12  Verifying Complete Addressing Information on a Windows Host

```
C:\Users\PC-A> ipconfig /all
Windows IP Configuration
    Host Name . . . . . . . . . . . : PC-A-00H20
    Primary Dns Suffix  . . . . . . : cisco.com
    Node Type . . . . . . . . . . . : Hybrid
    IP Routing Enabled. . . . . . . : No
    WINS Proxy Enabled. . . . . . . : No
    DNS Suffix Search List. . . . . : cisco.com
(Output omitted)
Wireless LAN adapter Wi-Fi:
    Connection-specific DNS Suffix  . :
    Description . . . . . . . . . . : Intel(R) Dual Band Wireless-AC 8265
    Physical Address. . . . . . . . : F8-94-C2-E4-C5-0A
    DHCP Enabled. . . . . . . . . . : Yes
    Autoconfiguration Enabled . . . : Yes
    Link-local IPv6 Address . . . . : fe80::a4aa:2dd1:ae2d:a75e%16(Preferred)
    IPv4 Address. . . . . . . . . . : 192.168.10.10(Preferred)
    Subnet Mask . . . . . . . . . . : 255.255.255.0
    Lease Obtained. . . . . . . . . : August 17, 2019 1:20:17 PM
    Lease Expires . . . . . . . . . : August 18, 2019 1:20:18 PM
    Default Gateway . . . . . . . . : 192.168.10.1
    DHCP Server . . . . . . . . . . : 192.168.10.1
    DHCPv6 IAID . . . . . . . . . . : 100177090
    DHCPv6 Client DUID. . . . . . . : 00-01-00-01-21-F3-76-75-54-E1-AD-DE-DA-9A
    DNS Servers . . . . . . . . . . : 192.168.10.1
    NetBIOS over Tcpip. . . . . . . : Enabled
```