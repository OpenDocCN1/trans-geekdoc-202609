# FIGURE 10-11 VPN access.

![](bbox=[0.25, 0.09, 0.78, 0.35])

the data they send between a user and the organization’s network. Using a VPN for remote access provides security and is cost-effective. The cost difference of using a VPN versus paying for a dedicated connection between two sites is significant. FIGURE 10-11 shows an example of VPN access to a network.

VPNs require your gateway equipment to have a lot of processing power to handle the encryption algorithms. You can offload this processing power to another device by using a dedicated VPN concentrator rather than having your router or firewall terminate the VPN.

In deploying a VPN, you must consider the security of the end users’ computers. Once users connect to the corporate network, their PCs could be an open portal into those resources for an attacker who gains access to the PC. For this reason, many organizations require that employees install security software on their home computers. You can also limit VPN access to laptop computers your organization owns and manages.

The three major VPN technologies in use today are as follows:

+   - Point-to-Point Tunneling Protocol (PPTP)—The Point-to-Point Tunneling Protocol (PPTP) was once the predominant VPN protocol. For many years, almost all VPNs used PPTP. It is easy to set up on client computers because most operating systems include PPTP support.

+   - Secure Sockets Layer (SSL)—The Secure Sockets Layer encrypts web communications, and many VPNs use SSL to provide encrypted communication. Users connect to an SSL-protected webpage and log on. Their web browser then downloads software that connects them to the VPN. This requires no advance configuration of the system. For this reason, SSL VPNs are quickly growing in popularity.

+   - IPSec—Internet Protocol Security (IPSec) is a suite of protocols designed to connect sites securely. Although some IPSec VPNs are available for end users, they often require the installation of third-party software on the user’s system and are not popular. Many organizations use IPSec to connect one site to another securely over the Internet. The required IPSec VPN functionality is built into many routers and firewalls, allowing for easy configuration.

VPNs provide clear benefit to an organization. They offer an inexpensive, secure replacement for dedicated connections between sites. They also enable users to connect securely