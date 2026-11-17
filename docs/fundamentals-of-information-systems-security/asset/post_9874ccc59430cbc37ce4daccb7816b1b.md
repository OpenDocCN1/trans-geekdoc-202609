
and C from the Internet. However, two other firewalls separate subnets B and C from each other and from subnet A.

Multilayered firewalls are useful when you have networks with different security levels. For example, in Figure 10-8, general users may connect to subnet A. Users working on a secret research project might connect to subnet B. Executives might connect to subnet C. This structure provides the secret project and the executives with protection from the general user community.

## Unified Threat Management.

Firewalls are so important to network security that they have matured into devices that do far more than just packet inspection. In fact, multipurpose firewalls are more commonly referred to as unified threat management (UTM) devices. UTM devices do provide filtering as well as many other security services. Some of the services UTM devices provide include these:

- **URL filter**—This feature filters web traffic by examining the URL as opposed to the IP address.
- **Content inspection**—The device looks at some or all network packet content to determine if the packet should be allowed to pass. This type of inspection can help identify malicious content from trusted sources. This could happen if a trusted source is compromised.
- **Malware inspection**—A specialized form of content inspection, the device looks at packet content for signs of malware.

These unified services make it possible to reduce the number of devices that must analyze network packets. Fewer UTM devices can provide the same level of security as many more older devices. However, even with fewer devices inspecting packets, introducing UTM devices often slows down a network due to the sheer amount of work the devices must accomplish. It takes time to inspect and analyze each network packet at multiple layers of the network stack. For this reason, some organizations have elected a “middle-of-the-road” approach. A **web security gateway** accomplishes some of what a UTM device does, but without all the overhead. In short, a web security gateway performs URL filtering but does not examine the content of the packets.

**NOTE** One more useful feature of firewalls is that they can be configured as **load balancers**. A load balancer can dynamically route network traffic to different network segments to avoid congestion. The firewall monitors known network segments and directs traffic on a segment that is appropriate for the destination host and has available bandwidth. This can keep networks from slowing down when the demand is high.

## Virtual Private Networks and Remote Access

With the advent of telecommuting, remote access has become a common part of many corporate networks. Today many companies have employees who rarely if ever come into the corporate office. These users work at home or on the road. Even so, they still need access to corporate resources. This means opening access to more corporate resources from the Internet than IT professionals want. The trick is to allow corporate employees the access they need but to keep attackers out of these potentially open doors.

Virtual private networks (VPNs) are a good way to increase the security level of data you transmit across the public data network. They normally use encryption to protect all the data they send between a user and the organization’s network. Using a VPN for remote access provides security and is cost-effective. The cost difference of using a VPN versus paying for a dedicated connection between two sites is significant. FIGURE 10-11 shows an example of VPN access to a network.

## FIGURE 10-11 VPN access.

![](img/b2a7c1cdb4938c3b37d6925de0425ae9_368_0.png)

VPNs require your gateway equipment to have a lot of processing power to handle the encryption algorithms. You can offload this processing power to another device by using a dedicated VPN concentrator rather than having your router or firewall terminate the VPN.

In deploying a VPN, you must consider the security of the end users’ computers. Once users connect to the corporate network, their PCs could be an open portal into those resources for an attacker who gains access to the PC. For this reason, many organizations require that employees install security software on their home computers. You can also limit VPN access to laptop computers your organization owns and manages.

The three major VPN technologies in use today are as follows:

- Point-to-Point Tunneling Protocol (PPTP)—The Point-to-Point Tunneling Protocol (PPTP) was once the predominant VPN protocol. For many years, almost all VPNs used PPTP. It is easy to set up on client computers because most operating systems include PPTP support.
- Secure Sockets Layer (SSL)—The Secure Sockets Layer encrypts web communications, and many VPNs use SSL to provide encrypted communication. Users connect to an SSL-protected webpage and log on. Their web browser then downloads software that connects them to the VPN. This requires no advance configuration of the system. For this reason, SSL VPNs are quickly growing in popularity.
- IPSec—Internet Protocol Security (IPSec) is a suite of protocols designed to connect sites securely. Although some IPSec VPNs are available for end users, they often require the installation of third-party software on the user’s system and are not popular. Many organizations use IPSec to connect one site to another securely over the Internet. The required IPSec VPN functionality is built into many routers and firewalls, allowing for easy configuration.

VPNs provide clear benefit to an organization. They offer an inexpensive, secure replacement for dedicated connections between sites. They also enable users to connect securely to the organization network from remote locations. This promises increased productivity because workers can easily get to resources they need while on the road.

## Network Access Control

Network access control (NAC) systems enable you to add more security requirements before allowing a device to connect to your network. They perform two major tasks: authentication and posture checking. Although NAC is a new technology, it is growing in popularity. Many organizations now deploy NAC for both internal users and guests using their network. NAC works on wired and wireless networks.

The IEEE 802.1x standard describes the most common NAC technology. Commonly referred to as simply 802.1x or 1x, this standard tells how clients may interact with a NAC device to gain entry to the network. Software on users’ computers prompts them to log on to the network. After verifying the user’s credentials, the NAC device instructs the switch (for a wired network) or access point (for a wireless network) to grant the user access to the network. This is the authentication component of NAC.

Posture checking is an optional second use of NAC technology. When posture checking is used, the NAC device checks the configuration of the user’s computer to ensure that it meets security standards before allowing it access to the network. Some things commonly checked include the following:

- Up-to-date antivirus software
- Host firewall enabled
- Operating system supported
- Operating system patched

If users attempt to connect a noncompliant system to a network, the NAC device offers two options. The administrator can decide to block such systems from the network until they are fixed. Alternatively, the system may connect to a special quarantine network where you may fix the system before gaining access to the main network. The Extensible Authentication Protocol (EAP) is an authentication framework that defines the transport of keys and authentication credentials. EAP is commonly used in wireless network authentication. The Protected Extensible Authentication Protocol (PEAP) is basically EAP running in a TLS tunnel. PEAP provides more security than EAP for authentication exchanges.

## Wireless Networks

Wireless networks have become very popular for connecting devices within the home and office. Wireless networks can connect laptops, desktops, smartphones, and many other devices. Wireless networking allows users to work from any location in the building without worrying about finding a place to plug in a network cable.

Configuring a wireless network is quite easy and inexpensive. The question becomes, what does wireless technology do to the security of your network? If it is so easy for an employee to connect to the network, does that mean that others can connect as well?

Setting up a secure wireless network—at least one as secure as any wired network—is possible. However, it takes careful planning, execution, and testing. Properly configured
