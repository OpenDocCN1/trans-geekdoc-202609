# ## 10.1.6. Configuring an ASA with CLI

# ### 10.1.6.1. The types of ASA 5505 licenses

ASA 5505 comes with an operating system, under two types of license: a “Basic license” and a “Security Plus license”. The Security Plus license supports more features.

| Characteristics | Basic license | Security Plus license |
|---|---|---|
| The maximum number of connections to the firewall | 10,000 | 25,000 |
| The maximum number of VPN sessions | 10 | 25 |
| The maximum number of VLANs to be created | 3, with the restriction that only two zones may communicate with each other. | 20, with no restrictions on communication between zones. |

# ### 10.1.6.2. Overview of CLI on ASA

The operating system on ASA devices offers a Command Line Interface (CLI) that looks similar to the one used by the IOS of Cisco routers. However, several commands are different in both operating systems.

| Command on the IOS system | The equivalent command on the ASA |
|---|---|
| enable secret password | enable password password |
| line con 0 password password login | passwd password |
| ip route | route outside |
| show ip interfaces brief | show interfaces ip brief |
| show ip route | show route |
| show vlan | show switch vlan |
| show ip nat translations | show xlate |
| copy running-config startup-config | write [ memory ] |

# ### 10.1.6.3. Configuring interfaces

- ASA 5510 has two types of interfaces:
- **routed interfaces**: these are directly configured with IP addresses. The configuration is carried out via an SVI (Switch Virtual Interface).