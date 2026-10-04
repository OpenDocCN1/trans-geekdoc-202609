As shown in Figure 12-28, the five IPv6 subnets are allocated with the subnet ID field 0001 through 0005 for this example. Each /64 subnet provides more addresses than will ever be needed.

![](bbox=[0.25, 0.17, 0.78, 0.44])

Figure 12-28 Five Allocated Subnets

# Router Configured with IPv6 Subnets (12.8.4)

Configuring a router with IPv6 subnets is similar to the process for IPv4. Example 12-12 shows each of the router interfaces configured to be on a different IPv6 subnet.

# Example 12-12 IPv6 Address Configuration on Router R1

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

Interactive Graphic

# Check Your Understanding—Subnet an IPv6 Network (12.8.5)

Refer to the online course to complete this activity.