Example 12-2 shows the commands required to configure the IPv6 GUA on the GigabitEthernet 0/0/0, GigabitEthernet 0/0/1, and Serial 0/1/0 interfaces of R1.

# Example 12-2 IPv6 GUA Configuration on Router R1

```
R1(config)# interface gigabitethernet 0/0/0
R1(config-if)# ipv6 address 2001:db8:acad:1::1/64
R1(config-if)# no shutdown
R1(config-if)# exit
R1(config)# interface gigabitethernet 0/0/1
R1(config-if)# ipv6 address 2001:db8:acad:2::1/64
R1(config-if)# no shutdown
R1(config-if)# exit
R1(config)# interface serial 0/1/0
R1(config-if)# ipv6 address 2001:db8:acad:3::1/64
R1(config-if)# no shutdown
```

# Static GUA Configuration on a Windows Host (12.4.2)

Manually configuring the IPv6 address on a host is similar to configuring an IPv4 address.

As shown in Figure 12-13, the default gateway address configured for PC1 is 2001:db8:acad:1::1. This is the GUA of the R1 GigabitEthernet interface on the same network. Alternatively, the default gateway address can be configured to match the LLA of the GigabitEthernet interface. Using the LLA of the router as the default gateway address is considered best practice, but either configuration will work.

Just as with IPv4, with IPv6, statically configuring addresses on clients does not scale to larger environments. For this reason, most network administrators enable dynamic assignment of IPv6 addresses.

There are two ways in which a device can obtain an IPv6 GUA automatically:

+   - Stateless address autoconfiguration (SLAAC)
- Stateful DHCPv6

SLAAC and DHCPv6 are covered in the next section.