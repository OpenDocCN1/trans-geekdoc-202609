+   Also, the ESP Header contains a sequence number that is to be used by sliding window protocol for rejection of replay packets.

+   The main disadvantage of Transport Mode is that the packets are prone to traffic-analysis attack by which an adversary can determine the source and destination IP addresses.

+   Since the mode provides protection only to the layers of transport and above, it is called Transport Mode.

| Original IP Header | ESP Header | TCP Header | Payload | ESP Trailer | ESP Auth |
| --- | --- | --- | --- | --- | --- |
| (Transport Mode IP-V4 Packet with ESP) |

FIGURE 12.6 Transport Mode formats of IP-V.4 Packets.

# ## 12.5.5 Tunnel Mode

+   1. The Tunnel Mode provides protection to the entire packet, including the IP-Header.

+   2. This mode is used when the communicating nodes are protected by firewalls. The Tunnel Mode facilitates creation of a Virtual Network (VPN) between the source Firewall and the destination Firewall.

+   3. All incoming/outgoing packets are routed through firewalls.

+   4. In ESP, the entire outgoing packet, including the original IP Header, is encrypted at the outgoing firewall and a new IP-Header is pre-ended to the encrypted packet.