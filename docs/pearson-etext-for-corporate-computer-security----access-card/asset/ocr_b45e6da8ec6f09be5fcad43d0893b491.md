In order to understand how ARP poisoning works, we will first look at how ARP normally works. Then we will see how ARP requests and replies can be used in ARP poisoning and an ARP DoS attack.

# Normal ARP Operation

Figure 4-14 shows how ARP would normally work on a LAN. If the gateway (router) receives a packet addressed to an internal host (10.0.0.1) it sends an ARP request to every host on the LAN asking if they have that IP address (Step 1).

Only the host that has the requested IP address responds. All other hosts ignore the request (Step 2). In this example, Host A had the IP address requested (10.0.0.1). Host A responds with an ARP reply that contains its physical, or MAC, address (A1-A1-A1-A1-A1-A1) (Step 3).

The switch records the MAC addresses of the gateway and Host A, as well as their respective port numbers. The gateway receives the ARP reply and records Host A’s IP address and corresponding MAC address (Step 4).

Now that the gateway has Host A’s MAC address, it can forward all packets addressed to 10.0.0.1. The switch looks only at the MAC address as the packet is passed from the gateway to Host A. The switch does not look at IP addresses on the packets.

Other hosts on the LAN cannot see any packets addressed to Host A because the switch forwards packets based on the port numbers and MAC address in its switching table. Since the gateway addressed the packet to A1-A1-A1-A1-A1-A1 it must go out to port 1, as shown in the switching table. No other host can see Host A’s traffic.

**THE PROBLEM** The problem with ARP requests and replies is that they do not require authentication or verification. All hosts trust all ARP replies. ARP spoofing uses false ARP replies to map any IP address to any MAC address. Spoofed ARP replies are broadcast to other hosts on the LAN. This allows an attacker to manipulate ARP tables on all LAN hosts.

# Figure 4-14 Normal ARP Traffic

![](bbox=[0.1, 0.68, 0.75, 0.95])