Furthermore, cloud consumers benefit from an increase in throughput thanks to active-active. Active standby refers to the operation of having one IPsec tunnel active and another on standby. If the active tunnel experiences any issues, traffic switches over to the standby tunnel.

A point-to-site (P2S) VPN gateway connection lets network engineers build a secure connection to the Azure virtual network from an individual end-user computer.

Connecting to a P2S network is done using the computer of the end user. Connecting to Azure VNets from a remote location, such as from home or during a conference, is an excellent solution for telecommuters. If you have only a few clients connecting to a VNet, a P2S VPN is also appropriate for S2S VPN. A P2S connection requires no public IP address or VPN device on the premises, in contrast to S2S connections. If both links’ requirements are compatible, using a P2S link and an S2S link through a single VPN gateway. Figure 6.11 depicts a typical deployment topology and shows a user and P2S VPN to establish a VPN tunnel (P2S SSTP tunnel & P2S IKE Tunnel) between Microsoft Azure and end-user devices.

# **FIGURE 6.11** Point-to-site VPN

![](bbox=[0.142, 0.395, 0.856, 0.715])

Virtual networks can be joined to each other (VNet-to-VNet) similarly to on-site locations of virtual networks. Both connectivity types provide an IPsec/IKE tunnel via a VPN gateway. You can combine communications between VNets with multisite configurations. Network topologies can be established that combine premise-to-premise and premise-to-virtual connectivity.

Using Azure's P2S solution, users can work from home quickly and easily, as the solution is cloud-based. You can quickly scale up the capacity and turn it off just as easily and quickly when you no longer need it. Using a point-to-site (P2S) VPN gateway, you can securely connect to your (VNet) virtual network from a client's personal computer.