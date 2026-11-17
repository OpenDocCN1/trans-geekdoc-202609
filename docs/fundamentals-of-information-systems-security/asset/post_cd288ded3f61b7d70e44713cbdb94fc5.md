
![](img/b2a7c1cdb4938c3b37d6925de0425ae9_83_0.png)

- 1. Mobile node (MN) connects to foreign agent (FA).
- 2. FA assigns care of address (COA) to MN.
- 3. FA sends COA to home agent (HA).
- 4. Correspondent node (CN) sends message to MN.
  - a. CN's message for MN goes first to HA.
  - b. HA forwards message to COA.
  - c. FA forwards message to MN.

between segments on a LAN and stay connected without the interruption that would normally happen using standard TCP/IP. Users will not even realize that their devices might move from one network to another as they move about. Users can maintain a connection to the network as long as the mobile device stays within network coverage. The network device can switch between cellular and Wi-Fi and still provide transparent connections.

FIGURE 2-4 demonstrates how Mobile IP provides connection transparency for several entities working together to ensure that mobile devices can move from one network to another without dropping connections:

- **Mobile node (MN)**—The mobile device that moves from one network to another: The MN has a fixed IP address regardless of the current network.
- **Home agent (HA)**—A router with additional capabilities over standard routers, the HA keeps track of the MNs it manages. When an MN leaves the local network, the HA forwards packets to the MN’s current network.
- **Foreign agent (FA)**—A router with additional capabilities connected to another network (not the HA network), the FA assigns the MN a local address. When the MN connects to another network that supports Mobile IP, it announces itself to the FA.
- **Care of address (COA)**—The local address for the MN when it connects to another network, the FA assigns the COA to the MN and sends it to the HA when the MN connects. In many cases, the COA is actually the FA address. The HA forwards any packets for the MN to the COA. The FA receives the packets and forwards them to the MN.
- **Correspondent node (CN)**—This is the node that wants to communicate with the MN.

Suppose an MN leaves the home network and connects to some other network. When the MN connects to a new network, the FA sends the COA to the HA. Then a CN wants to communicate with the MN. The CN sends a message to the MN’s IP address. The network routes the packet to the MN’s home network. The HA receives the packet and forwards it to the COA. The FA forwards the packet to the MN.

## New Challenges Created by the IoT

In the introduction to this chapter, you learned about the five key challenges that the IoT must overcome:

- **Security**—How do you keep the bad guys out if you enable the IoT for your personal and professional life?
- **Privacy**—How do you protect your family’s identity and privacy data from theft or unauthorized access that can lead to identity theft?
- **Interoperability and standards**—How well do IoT manufacturers and ASP developers ensure that devices communicate securely?
- **Legal and regulatory compliance**—What role do the international, federal, and state levels contribute toward legal, tax, and regulatory requirements regarding IoT-related business transactions that involve payment for goods and services?
- **E-commerce and economic development issues**—What are the economic rules of engagement for conducting business on the World Wide Web? How is IoT connectivity and information sharing to be deployed globally?

### Security

Remember, the security triad consists of confidentiality, integrity, and availability (CIA). What if an individual or a business connects something to the Internet without security in mind? What if there is nothing of value or of a sensitive nature to steal; do you still connect? What should a user or a business do before connecting to the Internet? These same questions hold true for devices that connect via the IoT. You, the user, are the owner of your asset and the information contained in that asset, so it is critical that you decide what is at risk if you connect your personal life, home, and business content to the Internet. You have to have a high degree of trust to connect your identity, social and family life, home, and professional life to the Internet. Or you have to have a high degree of trust that you can enable your own security controls as a defense strategy for connecting your assets to the IoT. Regardless of your defense strategy, there are risks, threats, and vulnerabilities everywhere. So, where does trust come into play? As an individual user of the Internet, do the same human protocols and human etiquette apply online? What is acceptable or unacceptable behavior; and who or what organization defines what is acceptable or unacceptable?

The Internet is already filled with hackers and bad guys. Security and data breaches are occurring every day. Now people and businesses want to connect more devices via the IoT phenomenon? It is already happening. Each day there are more Internet-connected devices and people. Businesses continue to expand their online presence, and new applications are being developed and sold via the Internet. Software products and distribution are no longer done via CD or DVD. Once software licensing is paid for online, you can immediately download the software to your device and install it. People are becoming more dependent on their electronic devices and real-time connectivity. This increasing level of dependency on Internet connectivity and IoT device access is not going away. It is increasing. As people and businesses become even more dependent on the IoT, so will the opportunities for bad guys to attack, steal, and damage. This is why security is the greatest challenge for the IoT to overcome. Who will act as the governing body? What policies and procedures or code of conduct should people and businesses abide by when interacting with the IoT? Security has global issues that impact all humans, governments, and businesses.

The following summarizes the security challenges of IoT devices:

- IoT devices such as sensors or consumer items (Internet-connected TV) are deployed in large quantities. Depending on the criticality of the application, an outage could impact many endpoints if attacked.
- IoT devices are ubiquitous and can have wide reach into the user or household population. For example, electrical meters that are Internet connected introduce a critical infrastructure vulnerability if an attack could be replicated and pushed to individual endpoints.
- IoT devices that are not updated or maintained properly may permit vulnerabilities to become entry points into your network or organization. This is the equivalent of a vendor announcing an End of Life (EOL) support timeline for a product or software application.
- IoT upgrades can be difficult to distribute and deploy, leaving gaps in the remediation of IoT devices or endpoints. Cars that have Wi-Fi access and onboard computers require software patches and upgrades from the manufacturer. This maintenance must be performed for all cars requiring the upgrade to remediate a software vulnerability.
- IoT devices typically do not provide the user or owner with any inside visibility or knowledge of how the device works and connects to the Internet. Vendors or service providers that have remote access to an IoT device may be able to pull information or data from your IoT device without your permission. Review of the product warranty and IoT communications and data sharing with a service provider may be part of your use agreement.
- IoT devices typically are not physically secure and can be located anywhere in public areas or outside your house. Your home's electrical panel, cable TV, or fiber optic cable points of entry are typically not that secure. Security is lacking for Wi-Fi-connected IoT devices on public or open Wi-Fi networks.
- Environmental IoT devices are typically out in the open capturing readings and measurements for scientific reasons or research reasons. If an IoT device can act as a point of entry into an IP data network, a vulnerability in one device is compounded if there are many IoT devices out there.

### Privacy

How do you protect your family’s identity and privacy data from theft or unauthorized access that can lead to identity theft? Do you even know what your privacy rights are as an individual living in your state and country? Are those same privacy rights extended to the Internet and IoT devices? Who owns the data in your IoT devices? Privacy has many layers. First is you and your own identity and private data. Then you extend privacy to your spouse or other family members. Families require a privacy strategy to ensure that all family members’ privacy data are kept confidential. Leakage of one family member’s private data may be the opportunity for other family members’ private data to be compromised.
