# 7.2.2. MAC spoofing attack

# Overview of the attack

A MAC address spoofing (ARP spoofing) attack consists of sending false ARP messages within a local network, with the aim of deviating and intercepting network traffic.

# Countermeasures

The “DAI” (Dynamic ARP Inspection) feature is used to prevent ARP spoofing attacks. It makes it possible to verify the mapping between the IPv4 addresses and the MAC addresses. In case of any anomaly from an unreliable port, the spoofed ARP packets will be ignored.

| Command | Description |
|---|---|
| switch(config)#ip arp inspection vlan vlan | Enables dynamic ARP inspection (DAI) on a specific VLAN. |
| switch(config)#interface g0/0 switch(config-if)#ip arp inspection trust | Configures a port to be a reliable port. |

# 7.2.3. The DHCP starvation attack

# Overview of the attack

A DHCP starvation attack consists of broadcasting a large number of DHCP requests with spoofed source MAC addresses. Once the number of IP addresses available in the DHCP server is exhausted, the attacker may introduce their DHCP server to respond to new DHCP requests on the network. The attacker can now capture sensitive data using a man-in-the-middle (MITM) attack.

# Countermeasures

The “DHCP snooping” feature is used to prevent attacks of this type by filtering unreliable DHCP messages.

| Command | Description |
|---|---|
| S1(config)#ip dhcp snooping | Enables the “DHCP snooping” feature on all VLANs. |
| S1(config)#ip dhcp snooping vlan vlan | Enables the “DHCP Snooping” feature on a specific VLAN. |
| S1(config)#interface g0/0 S1(config-if)#ip dhcp snooping trust | Configures a reliable port. |
| S1#show ip dhcp snooping | Displays the “DHCP snooping” configuration. |