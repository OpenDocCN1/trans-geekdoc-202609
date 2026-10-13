
## Introduction

In the previous chapter you were introduced to the components used to build basic *operational technology (OT)* network structures. This chapter will build on that basic information to explain how those components are organized to produce secure OT network architecture. This will involve two major topic areas:

* Network segmentation and security zoning
* Wireless security

As indicated previously, the best *cybersecurity design* for a production plant is to keep the OT and IT networks separated from each other, both logically and physically, and to not provide a path to the OT network from the Internet. This will reduce the risk to the OT network associated with remote attackers gaining access to it through the IT network.

An isolated industrial process control network is normally a relatively safe and secure network environment. Threats are typically limited to natural and human accidents, physical access attacks, and malicious activities associated with disgruntled employees. These networks often have no connection to the Internet, where so many potential threats arise. In addition, they are based on devices and software that fewer individuals are aware of (and highly competent with) than their counterparts in the enterprise world.

When a connection is created between the ICS operational technology and corporate IT networks, the risk level to the OT network increases significantly. This is due to the additional attack vectors presented to the OT network through the IT network and its Internet connections. So, the best security option for interconnected OT and IT networks that is often practiced is to limit the network connections between the corporate IT network and the OT network to a single point of contact, as illustrated in [Figure 3.1](#c03.xhtml#c03-fig-0001).

![FIGURE 3.1 Connecting the OT and IT networks](images/c03f001.png)

[**FIGURE 3.1**](#c03.xhtml#R_c03-fig-0001) Connecting the OT and IT networks

IT functions have become an integral part of the OT network to provide critical interfaces and interactions. IT/OT network interoperability is increasingly being used to maximize process productivity through monitoring, record keeping, maintenance, planning, and work scheduling. Of course, the cyber threats associated with these expanded/integrated networks are increasing concurrently.

## Boundary Protection

With the industry continuing to press toward IT/OT connectivity, the goal becomes to establish *boundary protection* between the two networks that will permit the desired information to move between the networks while protecting the OT network from the threats associated with the IT network, non-ICS personnel, and the Internet.

Fortunately, the enterprise networking environment has already created a number of boundary protection devices and techniques that can be used for this purpose. These devices and techniques include the following:

* Access control strategies
* Gateways
* Routers
* Firewalls
* Intrusion detection systems (IDSs)
* VLANs
* Encryption and tunnels
* Antivirus and anti-malware products
* Network segregation and segmentation techniques
* DMZs
* Proxies

All the items mentioned in this list can and should be applied to guarding the ICS from the rest of the world.

### Firewalls

The most common first line of defense between internetwork segments is a *firewall*. These devices consist of a combination of hardware and software used to control network traffic between untrusted or less secure networks and a protected network. This is accomplished by monitoring the network traffic and applying access rules to it to allow authorized traffic to pass through.

Firewalls can be implemented in various ways in different network arrangements. A firewall might be a mission-specific *hardware firewall device*, or it may be a function that is built into a router or switch, or it may be implemented in a computer that has multiple Ethernet interfaces. It can even be a pure *software firewall* installed on a host computer like any other application. Many network appliances are available that offer firewall and security capabilities along with other network features.

In a corporate or industrial network environment, an IT administrator controls firewall installations and configurations. The advantage of the network firewall is that it enables the administrator to control the flow of information to all the devices attached to their network, as illustrated in [Figure 3.2](#c03.xhtml#c03-fig-0002).

![FIGURE 3.2 Network firewall](images/c03f002.png)

[**FIGURE 3.2**](#c03.xhtml#R_c03-fig-0002) Network firewall

Firewalls used in OT environments are typically purpose-built to specifically monitor OT traffic and allow or reject traffic entering the OT or one of its subnets. Many IT firewall suppliers provide OT-specific capabilities with their products. The major challenges with using firewalls for OT security is implementing proper firewall rules to provide the protection needed in a given environment.

Firewalls generally act as gateway devices, authenticating and granting access to both network applications and protocols. They can also be configured to act as a proxy server, provide network address translation, and also act as a DHCP server. Firewalls will typically also filter not only incoming traffic but outgoing traffic as well.

A configured firewall will provide *packet filtering* using defined rules to reject or accept both incoming and outgoing packets. This can be more challenging to configure, but effective *firewall rules* are critical to security on most networks.

A *packet filtering firewall* can be established through routers by configuring them with packet filtering rules to allow or deny client access based upon factors such as a source address, destination address, or port number. There are two types of packet filtering firewalls to consider: *static packet filtering* and *stateful packet filtering*.

*Static* or *stateless packet filtering firewalls* do not keep track of the state of a connection between two devices. They operate in much the same manner as any *access control list (ACL)* does. This makes this variety of firewalls somewhat faster than other firewall options. They also tend to be relatively inexpensive and easy to maintain. Conversely, static packet filtering firewalls offer fewer security features than other firewall options.

*Stateful packet filtering firewalls* do keep track of the connection state between entities. These firewalls collect network connection information and maintain *dynamic state tables* that are used for subsequent connections. As illustrated in [Figure 3.3](#c03.xhtml#c03-fig-0003), this enables ports to be opened and closed as needed. Once a client has completed a communication session, the stateful packet filtering firewall closes the specific port used until it is requested again.

Newer firewalls will also provide *quality of service (QoS)* functionality, which allows for the prioritization and differential treatment of network traffic based on special rules or policies. A common use for QoS is to ensure that a VoIP phone system will always have enough bandwidth for phone service, regardless of how busy the network is.
