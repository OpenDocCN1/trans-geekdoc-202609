![](bbox=[0.2, 0.1, 0.9, 0.28])

# Figure 12-14 IPv6 Addressing Topology with LLAs

Example 12-3 shows the configuration of an LLA on router R1.

# Example 12-3 R1 Static LLA Configuration

```
R1(config)# interface gigabitethernet 0/0/0
R1(config-if)# ipv6 address fe80::1:1 link-local
R1(config-if)# exit
R1(config)# interface gigabitethernet 0/0/1
R1(config-if)# ipv6 address fe80::1:2 link-local
R1(config-if)# exit
R1(config)# interface serial 0/1/0
R1(config-if)# ipv6 address fe80::1:3 link-local
R1(config-if)# exit
```

LLAs may be statically configured to be more easily recognizable as belonging to router R1. In Example 12-3, each of the interfaces of router R1 has been configured with an LLA that begins with fe80::1:n and a unique rightmost digit n. The 1 represents router R1.

If the topology included router R2 and you wanted to follow the same naming convention as for router R1, you would configure R2's three interfaces with the LLAs fe80::2:1, fe80::2:2, and fe80::2:3.

# Note

Exactly the same LLA could be configured on each link, as long as it is unique on that link. This is because an LLA only has to be unique on its link. However, common practice is to create a different LLA on each interface of the router to make it easy to identify the router and the specific interface.

# Syntax Checker—GUA and LLA Static Configuration (12.4.4)

Refer to the online course to complete this activity.

# Interactive Graphic