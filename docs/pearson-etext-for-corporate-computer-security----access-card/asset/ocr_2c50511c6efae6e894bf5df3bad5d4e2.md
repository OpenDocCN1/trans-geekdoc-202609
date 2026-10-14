# Why VPNs?

Why bother to transmit over untrusted networks at all? In the case of Internet VPNs, the answer is simple economics: Internet transmission is far less expensive per bit transmitted than commercial wide area networks (WANs) such as Frame Relay. The Internet’s enormous size brings large economies of scale.

VPNs on wireless LANs, in turn, allow a company to enjoy the benefits of mobility despite the questionable security of many WLANs—especially those in wireless hot spots. In a later chapter, we will see how VPNs can defeat “evil twin” attacks on wireless clients.

# Host-to-Host VPNs

Figure 3-25 illustrates three types of VPNs. The simplest type is the host-to-host VPN. As exemplified by VPN 1, a **host-to-host VPN** connects a single client over an untrusted network to a single server. When you connect to an e-commerce server on the Internet, the server usually creates a host-to-host VPN between itself and your browser before you begin entering sensitive information such as credit card numbers.

> A host-to-host VPN connects a single client over an untrusted network to a single server.

# Remote Access VPNs

In turn, a **remote access VPN** connects a single remote PC over an untrusted network to a site network (see VPN 2 in Figure 3-25). Remote access VPNs provide employees working at home or traveling access to a secured internal corporate network. VPNs can also provide secure network access to selected customers, supplier representatives, or other approved communication partners.

Remote access users connect to a **VPN gateway**, which authenticates them and gives them access to authorized resources within the site. Note that this gateway gives remote users access to *multiple* computers within the site, while a host-to-host VPN only gives you access to a *single* computer.

> A remote access VPN connects a single remote PC over an untrusted network to a site network.

# Site-to-Site VPNs

Finally, **site-to-site VPNs** (see VPN 3 in Figure 3-25) protect all traffic flowing over an untrusted network between a pair of sites. These may be two corporate sites or a corporate site and either a customer site or a supplier site. The site-to-site connection cryptographically protects the traffic of many simultaneous conversations taking place between various computers in the two sites. In site-to-site VPNs, sending VPN gateways encrypt outgoing messages. Receiving VPN gateways then decrypt incoming messages and pass these messages to the correct destination hosts in the receiving site.²⁷

²⁷ Although many companies build their own VPNs, quite a few outsource their VPNs to managed VPN providers. These providers, most of which are ISPs, install all necessary hardware at the customer’s site, do configuration, and manage the customer’s VPNs on an ongoing basis. Outsourcing reduces the skills a company’s security staff must have and reduces internal security labor costs. It also gives predictable costs. Although outsourced VPNs are convenient, companies are often reluctant to use them because customer companies lose control over their VPN security.