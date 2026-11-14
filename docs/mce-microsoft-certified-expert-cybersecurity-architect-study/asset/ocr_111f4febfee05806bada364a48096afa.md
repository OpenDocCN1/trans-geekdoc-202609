# FIGURE 6.9 Site-to-site VPN

![](bbox=[0.14, 0.135, 0.85, 0.315])

You can create more than one VPN connection from an organization's virtual network gateway, typically connecting to multiple on-premises sites. A multisite type of connection is an extension of an S2S connection. A route-based VPN type (called a *dynamic gateway* when used with classic VNets) is required for multicomnection work. All connections through the gateway share the available bandwidth since each virtual network is restricted to only one VPN gateway.

Figure 6.10 depicts a typical deployment topology and shows a multisite, S2S VPN to establish a VPN tunnel (IPsec VPN tunnel) between Microsoft Azure and on-premises.

# FIGURE 6.10 Microsoft Azure multisite S2S VPN

![](bbox=[0.13, 0.52, 0.85, 0.79])

A VPN gateway can be set up in active-standby mode using one public IP address or in active-active mode using two public IP addresses. Setting up a VPN gateway in active-active mode is a Microsoft-recommended method in which both the IPsec tunnels are simultaneously active, with data flowing through both tunnels simultaneously.