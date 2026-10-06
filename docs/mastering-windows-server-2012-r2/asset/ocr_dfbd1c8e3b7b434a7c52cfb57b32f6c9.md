will work with any switches, including non-intelligent/team-aware ones, since all of the intelligence required to support NIC Teaming is handled inside Windows Server 2012. Figure 4.2 shows an example of switch-independent teaming.

# FIGURE 4.1
Switch-dependent teaming

![](bbox=[0.388, 0.199, 0.773, 0.335])

# FIGURE 4.2
Switch-independent teaming

![](bbox=[0.388, 0.37, 0.743, 0.563])

LACP Similar to static teaming, the Link Aggregation Control Protocol (LACP) mode requires that the switches be preconfigured to enable LACP. Once enabled, it can be used to automatically combine multiple NICs into one logical link any time the switch is reconfigured. This removes administrative overhead and makes the network admin's job easier.

When you've chosen the teaming mode, you need to decide on how the traffic is handled once it passes through your team NIC. Windows Server 2012 R2 has following load-balancing modes to work with:

**Address Hash** When packets are received on your team using this mode, they get inspected and then hashing algorithm is carried out on the destination—typically the port, IP, and MAC addresses. Using the results of the algorithm, the NIC team determines which physical NIC will be used to send the packet.

**Hyper-V Port** This mode can be deployed when you are configuring a NIC team to be used with the Hyper-V role (hence the name). It's not a prerequisite for configuring your virtual networking, but it does have some benefits over address hashing when using Hyper-V. For example, it can be more predictable when sending packets through NICs that are used for Hyper-V, particularly if the team is connected to an external virtual switch.