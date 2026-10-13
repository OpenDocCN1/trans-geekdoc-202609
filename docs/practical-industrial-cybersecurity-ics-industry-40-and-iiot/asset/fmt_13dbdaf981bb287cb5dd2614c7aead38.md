
## Chapter 3: Secure ICS Architecture

### Review Question Answers

1.  **Network firewall**. One of the first lines of defense for interboundary communications is the network firewall. For more information, see the section “Boundary Protection.”

2.  **Defense-in-depth strategy**. For more information, see the section “Boundary Protection.”

3.  **Firewall rules**. A good firewall will provide packet filtering using defined rules to reject or accept both incoming and outgoing packets. This can be more challenging to configure, but effective firewall rules are really critical to security on most networks. For more information, see the section “Firewalls.”

4.  **Network segmentation** is also referred to as zoning, and the individual layers of the security plan are referred to as security zones. A security zone is a network segment created to provide specific levels of security for specific network assets (resources and data) based on their security vulnerability or criticality. The idea is to place more valuable or critical network assets into segments or security structures that offer more protection. For more information, see the section “Security Zoning Models.”

5.  **Network segregation**. For more information, see the section “Network Segregation.”

6.  **Databases and file servers**. In this model, zoning is reduced to a two-level arrangement featuring an Application zone and a Presentation zone. The Data and Application zones are combined into a single level in this model. As such, the databases and file servers share a similar security level. For more information, see the section “Security Zoning Models.”

7.  Any device that sends an `ARP` broadcast looking for a valid network IP address (an address that is assigned to an active server or device) will receive a reply. If an attacker gains access to the network, they could see every asset in the network, including servers, users, and devices. With the right skill set and enough time, they can exploit all of these devices. If a worm, such as the famous `Stuxnet` virus, penetrates the outer perimeter security, then there is nothing to stop it from spreading to the entire network. Also, there is very little protection from any malicious activities that originate within the network. For more information, see the section “Flat Network Topologies.”

8.  A gateway must be provided in the intermediary zone (or zones) to provide them with secure access. A prime example of this is when an organization has employees, such as sales personnel, who need to access interior levels of data from remote locations. In these situations, a gateway device such as a `reverse proxy` or `terminal server` is placed in the intermediate zone to provide access to these users, along with virus and malware scanning tools. For more information, see the section “Controlling Intersegment DATA Movement.”

9.  This `ICS/IT` model was developed for the International Society of Automation (`ISA`) by the Industry-Purdue University consortium and was designed as a reference for interfacing enterprise and `ICS` systems. It has become the international standard for interconnecting enterprise and `ICS` networks. For more information, see the section “ICS Reference Architecture.”

10.  **Managed switches**. Switches can also be used to create logically secured virtual local area networks (`VLANs`). A `VLAN` is a security topology that restricts visibility of network traffic by limiting the movement of network packets so that they only pass between designated ports. For more information, see the section “Network Switches.”

11.  The security benefit of using tunneling to transmit private data between security zones is that the connectivity devices that separate the zones are unaware that the communication is part of a private network. By encapsulating the private data and protocol information within a public transmission packet, the private data is hidden to the system. Anyone scanning the tunneled transmission across the network would not be aware of the message contents. For more information, see the section “Tunneling.”

12.  In very high security applications, network devices called unidirectional security gateways or data diodes are used to create a one-way connection between networks or network segments that possess differing security classifications. For more information, see the section “Security Zoning Models.”

13.  In the `ICS/IT` network environment, the `DMZ` is not positioned between the outer security level of the corporate network and the uncontrolled Internet. Instead, it is placed between the more secure `ICS` network and the less trusted enterprise network. Another `DMZ` should be created between the corporate network and the Internet. For more information, see the section “ICS Security Zoning.”

14.  The idea of using wireless sensors, controllers, and actuators to eliminate long cable runs between `ICS` devices in the process control network has been discussed and pursued for many years. For more information, see the section “Wireless Networking.”

15.  **A Zigbee/Ethernet gateway**. In communications and digital networking, a gateway is defined as a device that interfaces a network with another network that employs a different protocol. For more information, see the section “Wireless Gateway/Routers.”

### Exam Question Answers

1.  **D**. A `VLAN` is a security topology that restricts visibility of network traffic by limiting the movement of network packets so that they pass only between designated ports. For more information, see the section “Network Switches.”
