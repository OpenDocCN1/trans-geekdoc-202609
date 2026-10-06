
# Digital Evidence Examination

The digital investigator will image the devices seized using a write blocker in their laboratory. Never view a device at the scene, as a quick check to see if evidence is there when deciding to seize an exhibit or will damage the forensic integrity of the device.

# Seize Any Backups That Involve the Suspect's Device

Where a mobile device is seized, place it in flight mode, recording this action in your notes. A Faraday bag is a special device designed to reduce the ability of a mobile device to access a network, preventing an opportunity for a suspect to remotely wipe the device in transport. You can also remove the SIM card.

Identify the location of the evidence, finder serial number, model number, hostname, MAC address (where possible), IP address (where possible), time, date of seizure, photo of exhibit in situ, and snapshot of system prior to remediation.

Verify and account for all evidence seized with the person from whom it is being taken. This may be a complainant, witness, or suspect.

# Final Inspection Prior to Leaving

Conduct a final inspection to ensure that nothing has been left behind, such as investigators' notebooks, evidence, personal mobile phones, and so on. All of these items have been left at crime scenes before, requiring a hurried return to the location to recover an item.

# Identifying the Network Architecture

When an investigation requires an understanding of the flow of data through a network, creating or obtaining a network architecture topology assists the investigator visually understand the system infrastructure. This understanding helps the investigator locate potential points of evidence collection and open new lines of inquiry.

This sort of inquiry may be relevant when the investigator needs to understand how an attacker worked their way through a network from the time of breaching the corporate firewall to locating and removing data.

A network system administrator may have a topology diagram or be able to produce one from network tools or their own resources.

Corporate network architectures can be very complex. The history of the organization may show a series of system administrators building on the work of each other.

![](img/72f0382a5bc36845e84220db7d6f6b77_150_0.png)

**FIGURE 10.9** Network cabling.
Source: Photo © Graeme Edwards.

Also, there will be series of switches, routers, and Ethernet cables connecting switches to physical devices through walls and following pathways that cannot be seen.

Figures 10.9 through 10.12 show how complex portions of the cyber scene can be when dealing with a large corporation. While this will not always be what you find and not even relevant to your investigation, should you find a scene like this, depending on the circumstances there may be a requirement to have at least an understanding of how the data travels through this network to a compromised physical device. Remember, this is all evidence and the defense lawyer has the right to ask questions in court about this evidence they decide to.

This will be particularly relevant in an investigation when a person placed a physical device on the network with the aim of capturing all data as it travels through the network.

![](img/72f0382a5bc36845e84220db7d6f6b77_151_0.png)

**FIGURE 10.10** Ethernet cabling. Source: Photo © Graeme Edwards.

10.9 shows a potential starting point should you be required to map your network. The network administrator should be able to provide valuable support and direction in this instance.

You may find that an organization takes the opportunity to invest in their network architecture and cyber security. The corporation that 10.9 through 10.12 relate to took such an opportunity.

The following is a list of questions the investigator should ask the complainant’s IT staff to assist in understanding the architecture.

# Network Diagrams

A network diagram will show the architecture of a network. The diagram should show all devices; however, in some cases a criminal will attach a device to capture network traffic that is not recorded on any network diagram.

A network map shows the devices connected to a network. Devices connected to a Local Area Network (LAN) identify themselves through the MAC

![](img/72f0382a5bc36845e84220db7d6f6b77_152_0.png)

**FIGURE 10.11** Tracing Ethernet cabling 1.
Source: Photo © Graeme Edwards.

unique to each communication channel on a device. For example, a laptop computer connected to a LAN may have a unique MAC address for the Ethernet connection and a separate MAC address if the connection is through a wireless channel.

As mentioned previously, devices also have a subnet address beginning with the IP address (for example, 192.168.\***). These numbers are mapped to the router. Within the router is a routing table that connects the MAC address (28:cf:e9:22:e7:b5) and subnet address (192.168.212.75).

The investigator who is studying the traffic on a network originating from IP address 192.168.212.75 can find the MAC address 28:cf:e9:22:e7:b5. This is unique to each communication channel on a device. The IP address and subnet address (192.168.212.75) are mapped to the router.

The network allows users to access the services. The network cable connects the device to the router.

![](img/72f0382a5bc36845e84220db7d6f6b77_153_0.png)

**FIGURE 10.12** Tracing Ethernet cabling 2.
Source: Photo © Graeme Edwards.

Within the router is a routing table that connects the MAC address and subnet address. The investigator who is studying the traffic on a network originating from IP address 192.168.212.75 can find the MAC address 28:cf:e9:22:e7:b5. This is unique to each communication channel on a device. The IP address and subnet address (192.168.212.75) are mapped to the router.

The network allows users to access the services. The network cable connects the device to the router.

The following is a list of questions the investigator should ask the complainant’s IT staff to assist in understanding the architecture.

# Public Address Range

The IP address range is the range of IP addresses the public may use to access the organization. Asking the system administrator or searching domain registration sites (such as centralops.net) can yield valuable information.

# Private/Internal Addressing

The range of subnetted IP addresses within an organization that external parties do not see or have access to. In the example above, this range of addresses would start with 192.168.1 and the number of addresses would be dictated by the needs of the organization.

# Remote Access Point

A remote access point is a hardware device that allows a user to connect a wireless device to a wired network. An example of a remote access point is a router.

# Domain Name Servers

A Domain Name Server (DNS) serves as the pathway from a user within a network and the Internet. When a user seeks to go to a website they have not been before, they do not know the pathway. The DNS server will receive the request, locate the web address the user is seeking, and send a reply with the address to the user's device. The user may connect to the web address.

# Demilitarized Zone Zones

A demilitarized zone (DMZ) is the external-facing portion of a network, such as a web server. The only data that can be viewed is that which the owner has specifically allowed to be viewed, meaning that external visitors cannot directly access private corporate data.

# Domain Controllers

A domain controller operates within a Microsoft Windows environment responding to security authentication requests. Examples of requests include passwords and the permissions of a user to access specific resources, including data.

# Servers/Databases

Servers and databases contain corporate data of value to an attacker. A cybercriminal may steal copies of the data, delete the data, or modify it. The latter strategy is particularly damaging to a company, as they make decisions based on the accuracy of data stored on a database.
