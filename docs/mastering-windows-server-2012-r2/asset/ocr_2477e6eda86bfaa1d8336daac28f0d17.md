# CHAPTER 21 GETTING FROM THE OFFICE TO THE ROAD: VPNs

# FIGURE 21.1
VPN used for mobile connectivity

![](bbox=[0.318, 0.105, 0.902, 0.25])

The VPN server has at least two network interface cards (NICs). One NIC has a public IP address and can be reached by any user who has access to the Internet. The other NIC has a private address connected to the internal network.

VPN servers are often located in a demilitarized zone (DMZ), as shown in the figure. A DMZ would typically have two firewalls. One firewall provides a layer of protection to hosts in the DMZ from potential Internet attackers, and the second, internal firewall provides an extra layer of protection for internal clients. In others, a DMZ can be created by utilizing an interface on a single firewall and then using rules to create the segmentation between DMZ and LAN. Although the figure is simplified to show the VPN server, a DMZ can be configured with more than just a VPN server.

The mobile user uses the VPN connection to connect to the internal network by connecting to the VPN server. Once connected, the user is able to access internal resources as if they were located in the internal network. One drawback is that the connection is often slower.

First, the mobile user would gain access to the Internet. This could be via a broadband connection, a dial-connection, or a wireless connection. How the user connects to the Internet isn't important, only that the user connects. The VPN server then routes traffic between the mobile user and the internal network.

The specific role that supports VPNs in Windows Server 2012 R2 is the Remote Access role. The Routing and Remote Access Service within this role can be used for both VPNs and direct-dial connections. You can complement the Remote Access role by utilizing policy-driven network and client security through deployment of the Network Policy and Access Services role. Both of these roles will be described in detail later.

# Gateway-to-Gateway VPN

Although this chapter is focused on allowing mobile users to connect, it's also possible to configure VPNs for two different offices to connect. This is referred to as a gateway-to-gateway VPN and is shown in Figure 21.2.

In a gateway-to-gateway VPN, two VPN servers are connected over the public network. It's common for the public network in this situation to be separate leased, but the Internet can also be used. This allows users in the branch office to easily connect to resources at the main office via the VPN. Users may notice that connectivity is slower, but otherwise the connection appears just as if the server were located in the remote office.