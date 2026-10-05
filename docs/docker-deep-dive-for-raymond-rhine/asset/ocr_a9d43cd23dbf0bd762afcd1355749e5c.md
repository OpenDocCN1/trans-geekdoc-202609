![](bbox=[0.231, 0.101, 0.768, 0.417])

# Figure 13.15

The MACVLAN driver creates standard Linux sub-interfaces and tags them with the ID of the VLAN they will connect to. In this example, we're connecting to VLAN 100, so we tag the sub-interface with .100 (-o parent=eth0.100).

We also used the --ip-range flag to tell the new network sub-set of IP addresses it can assign to containers. It's vital that you reserve this range of addresses for Docker, as the MACVLAN driver has no management plane feature to check if IPs are already in use.