
Use NAT devices to route TCP traffic. Until we switch to using IPv6, we will need to use NAT devices to route TCP traffic from our many networked hosts to the outside world, while using only a few of the increasingly rare public IP addresses. Understanding how NAT devices change the source and destination addresses of IP packets will allow you to read network packet traces and interpret which systems are intended as recipients of data.

**Master It** A user complains that when he tries to connect to an FTP site, the connection initially succeeds, but the first time that a file listing is attempted, his connection is severed, and the server states that it cannot connect to 192.168.0.10.

What are likely causes of this problem, and how could this be addressed?

## Chapter 21
## Getting from the Office to the Road: VPNs

As mobile computing becomes more prevalent, an increasing number of users often need to remotely access their data located back in the office. Travelling salespeople, telecommuters, and IT consultants among others need to be able to securely connect and as seamlessly as possible to ensure they stay productive on the road. Virtual private networks (VPNs) are often used to meet this need.

A VPN is a private connection that is created over a public network, such as the Internet. If the users can access the Internet (hardly a café, apart, or building these days that doesn't have some form of connectivity to it), they can access the enhanced office over a VPN. Once connected, users can access any office resources just if they were there—this includes email, shared folders, and more. The Windows Server 2012 Remote Access role enables the traditional Routing and Remote Access Service (RRAS) features that you've become accustomed to previous Windows Server iterations, but your remote connectivity options get a massive upgrade with the enhanced DirectAccess functionality that also comes bundled with this role. This is a clientless, always and always managed, group policy-driven alternative VPN option that's based on the IP Security (IPSec) encryption protocol. DirectAccess provides support for Windows 7 Enterprise Ultimate or Windows 8 Enterprise clients. For legacy clients, however, you still need to use RRAS for VPN connectivity.

In this chapter, you will learn to:

- Add the Network Policy and Access Services role
- Understand the Remote Access role
- Configure a VPN server
- Explore DirectAccess

## Introducing VPNs

A VPN is used to access a private network over a public network. The public network is often the Internet, but it could also be leased lines that are shared by different companies. Figure 21.1 shows a common example of how a VPN server is configured.

### FIGURE 21.1
VPN used for mobile connectivity

![](img/41a83208e6906a3732620203b836cea7_1101_0.png)

The VPN server has at least two network interface cards (NICs). One NIC has a public IP address and can be reached by any user who has access to the Internet. The other NIC has a private address connected to the internal network.

VPN servers are often located in a demilitarized zone (DMZ), as shown in the figure. A DMZ would typically have two firewalls. One firewall provides a layer of protection to hosts in the DMZ from potential Internet attackers, and the second, internal firewall provides an extra layer of protection for clients. In others, a DMZ can be created by utilizing an interface on a single firewall and then using rules to create segmentation between DMZ and LAN. Although the figure is simplified to show the VPN server, a DMZ can be configured with more than just one server.

The mobile user uses the VPN connection to connect to the internal network by connecting to the VPN server. Once connected, the user is able to access internal resources as if they were there. One drawback is that the connection is often slower. First, mobile user would gain access to the Internet. This could be via a broadband connection, dial connection, or wireless connection. How the user connects isn't important, only that the user connects.

The specific role that supports VPNs in Windows Server 2012 R2 is the Remote Access role. The Routing and Remote Access Service within this role can be used for VPN connections. You can complement the Remote Access role by utilizing Network Policy and Access Services. Both of these roles will be described later.

## Gateway-to-Gateway VPN

Although this chapter is focused on allowing mobile users to connect, it is also possible to configure VPNs for different offices to connect. This is referred to as a gateway-to-gateway VPN and is shown in Figure 21.2.

### FIGURE 21.2
Gateway-to-gateway VPN

![](img/41a83208e6906a3732620203b836cea7_1102_0.png)

## Understanding Tunneling Protocols

When configuring a VPN, security is always a consideration. Data can't be sent across the Internet in clear without the risk of someone using a sniffer to capture it. To combat this risk, VPNs use tunneling protocols. Currently, there are three primary tunneling protocols for use in Windows VPNs: Layer 2 Tunneling Protocol (L2TP), Secure Socket Tunneling Protocol (SSTP), and Internet Key Exchange version 2 (IKE2). The Point-to-Point Tunneling Protocol (PPTP) has been used in the past but has known vulnerabilities and is used less as administrators become more concerned about security.

Both the VPN server and the VPN client must be configured to use the same tunneling protocol.

### Layer 2 Tunneling Protocol

Layer 2 Tunneling Protocol is a popular tunneling protocol used with VPNs. It commonly encrypts traffic via IPsec (which is explained later in this chapter); you'll see it expressed as L2TP/IPsec.

When used with IPsec, L2TP encrypts the data, providing confidentiality, and signs the data, providing integrity. IPsec has a weakness that prevents it from being used all the time—IPsec can't travel through a Network Address Translation (NAT).

NAT is commonly used to translate private IP addresses to public IP addresses and back to private. However, because of the way IPsec packets are put together, NAT effectively breaks IPsec. If you need to go through a NAT server, you simply can't use L2TP/IPsec.

In the past, if you had to go through a NAT server to connect to a VPN server, you'd need to use Point-to-Point Tunneling Protocol. PPTP has security concerns, so you'll rarely see it used today. However, if you need to go through a NAT server, you have another choice today—Secure Socket Tunneling Protocol.

### Secure Socket Tunneling Protocol

Secure Socket Tunneling Protocol (SSTP) is a newer protocol that was introduced with Windows Server 2008 and is fully supported in Windows Server 2012 R2. It uses Secure Sockets Layer (SSL) over port 443 to secure VPN traffic.

This is actually a big deal. SSL is a well-respected, heavily used, and well-understood security protocol. Because of this, IT administrators and security professionals are willing to trust it more than something new. That might not seem like much, but if you've ever tried to get a firewall administrator to open a port on an enterprise firewall, you know what we mean. Firewall administrators notoriously (and rightfully) want to ensure that only the necessary ports are open. And even if they're convinced that a port must be open to perform a specific task, they need to be thoroughly convinced to save the port.

However, since SSTP uses SSL over port 443, administrators are more willing to open the port (if it's not already open). They know SSL is secure, so long as SSTP is implemented for the business, it's acceptable to the firewall administrator. Additionally, if the enterprise is already hosting a web server that uses HTTPS, port 443 is already open, and you won't need to beg or bribe the firewall administrator to open the port.

An SSTP session, by first creating an HTTPS session, is encrypted with SSL, ensuring the session is secure before any data or authentication credentials are sent over the network. After the HTTPS session is established, the SSTP session sends authentication credentials and data over the encrypted channel.

A certificate must be installed on the VPN server from a trusted authority to support SSL. When VPN clients connect, the certificate is sent to the client and used to create a secure connection.

### Internet Key Exchange 2

Internet Key Exchange version 2 was introduced in Windows Server 2008 R2 as a new VPN type and is now gaining a lot of traction in Windows Server 2012 R2. The biggest advantage of IKEv2 is its ability to support VPN Connect.

VPN Connect allows clients to survive interruptions in network connectivity without losing the entire connection. After the temporary loss of network connectivity, the VPN client is able to continue without starting over.

IKEv2 is useful in environments where clients may move from one wireless client to another or even move from a wireless to a wired connection. IKEv2 requires a certificate from a trusted certificate authority, but you can use the same certificate as SSTP.
