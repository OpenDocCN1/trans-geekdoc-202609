
VPN services such as GoToMyPC25 to malicious VPNs such as botnet command-and-control channels and reverse tunnels. Although VPN sites such as GoToMyPC can be useful, it is up to the organization to decide if this is an acceptable means of ad hoc remote access. Some of the key issues to consider with this type of VPN service are that it bypasses internal security controls such as packet and content inspection, and the third party is creating and managing the VPN connection.

Malicious VPNs are a source of continuing concern. Botnet command and control channels can use encryption to evade network defenses that protect information. A reverse tunnel works by redirecting network traffic destined for a listening port to the same port on another host. For example, if a compromised FTP server had an active reverse tunnel, any user attempting to connect to that FTP server would redirect to another FTP server. Beyond the compromised host theory, malicious people already on the internal network may establish an outgoing VPN connection in an effort to hide network traffic.

The most elusive of all are applications that provide embedded VPN-like services. Peer-to-Peer (P2P) networks tunnel file sharing through proprietary and encrypted protocols. Skype26 not only has the ability to create encrypted voice calls, but also has VPN-like capabilities that allow encrypted file transfers. Network defenses should be able to detect the setup of these sessions and stop them before the connection is completed.

It is up to the organization to develop internal network security defenses and policies necessary to protect against all elusive VPNs.

## 32.3.3.11 Impact of IPv6.

Mass migration to IPv6 is still occurring at a slower pace than one may expect, even though IPv6 was developed in the late 1990s and the allocation of the last remaining available IPv4 address blocks to regional Internet registries occurred in 2011. As of the writing of this Handbook in early 2013, only about 12 percent of networks in global BGP tables are advertising IPv6 prefixes. Although most organizations continue to ignore the risks and ramifications of delaying enterprise IPv6 transition plans, it is likely that the protocol is already in their environment. Almost all modern operating systems have dual IPv4 and IPv6 network stacks, usually enabled by default, and typically prefer IPv6 by default. IPv6 and its associated transition technologies have specific implications for VPNs.

Without ubiquitous end-to-end IPv6 connectivity, there are several IPv6 transition technologies (such as 6to427 and Teredo28) that allow IPv6 capable systems at both ends to tunnel communication over legacy IPv4 networks. The 6to4 method encapsulates the IPv6 packet in the payload of IPv4 protocol type 41 packets and requires the use of relay routers along with at least one globally assigned IPv4 address.29 Teredo encapsulates IPv6 packets in the payload of UDP datagrams and also uses relay routers. UDP allows for better traversal of environments using NAT.

These technologies lessen the barrier to adoption of IPv6 by enhancing reachability of IPv6-enabled services; however, these technologies are also often not well understood or managed. Most network and security administrators learn the hard way that when working as designed, a connection (VPN or local) to an IPv6-enabled resource over a transition technology may traverse the organization’s border more than once—adding severe latency and passing data through several relay routers not controlled by the organization.

These transition technologies have serious security impacts on both the local network and VPN connection—misconfigurations and lack of experience being the most dangerous. Without properly configuring (and testing) both endpoints, it is possible for the IPv6 traffic to take an unsecure path before (or even after) entering the VPN tunnel, putting data in the clear and therefore at risk. It is critical for network administrators and VPN users to have a valid, tested IPv6 configuration to ensure IPv6 traffic (both native and tunneled) is traversing only the secured VPN tunnel and not traversing any encapsulated tunnel not controlled by the organization. Unless this threat is managed, data may be vulnerable even when an organization thinks its VPN is providing added security to a remote site or worker.

These transition technologies, many of which enabled by default, also tend to set up tunnels and connections automatically. Endpoint configuration, especially on client workstations, must be centrally configured or managed to disable these automatic connections or to specify specific configurations so that unintended tunnels are not configured.

IPv6 also has native support for IPsec (both AH and ESP) through the use of extension headers30 (versus proprietary IPsec clients), though its use is optional. Configuration and use of IPsec in an IPv6 environment requires the same discipline in choosing and configuring cryptographic options as IPv4. It is also possible to use IPv4 IPsec to protect IPv6 transition technology tunnels, as unencrypted tunnel sessions would otherwise be vulnerable to interception and/or manipulation without this protection. Both of these options are generally misunderstood and often unconfigured on networking and VPN devices. Organizations should only consider native IPsec for IPv6 after a thorough education and planning process.

## 32.4 EXTRANETS.

As the necessity for convenient access to data increases, so do the challenges associated with providing the protections required to secure this type of access.

## 32.4.1 Information-Assurance Goals.

Allowing external entities to access internal data remotely has major information-assurance implications. The main information-assurance goals of extranets are protecting shared information assets, preventing information exposure, and minimizing ancillary risks.

### Protecting Shared Information Assets.

Much of the current information security market focuses on protecting hosts and networks from digital threats. Although the loss of a server or portion of the network undoubtedly causes issues, there may be areas of greater concern. Organizations develop and sustain competitive advantage by manipulating data collected or created into valuable and actionable information. By mitigating the risks associated with external access, there is less chance for a breach of information security to occur.

### Preventing Information Exposure.

The concept of least privilege is essential when designing system access. One would not expect a financial analyst to have access to proprietary product specifications. The same concepts hold true when assigning access to external entities. Identity management provides an accountability mechanism for providing rights and monitoring actions of issued accounts. Access management provides the enforcement mechanism that keeps those accounts from viewing or changing data not explicitly necessary. The fusion of these two principles reduces the risk of inappropriate or unexpected access.

### Minimize Ancillary Risks.

It does not take long for Internet-facing systems to come under attack. Minimizing Internet attack vectors occurs from the Network Layer to the Application Layer. The extranet servers are not all-purpose systems. The network protection policies should restrict access to these services so that the Internet community only has access to the specific service(s) advertised. Extranet services require greater consideration, as network security devices still lag in protecting the protocols and customizations routinely occurring at the Application Layer.

## 32.4.2 Extranet Concepts.

### External Service Zone.

As described in Chapter 26 of this Handbook, extranet networks are another opportunity to use zoning, largely because extranets require robust protections and make extensive use of resources in other zones. Zoning allows administrators to be more granular on the services allowed into the network, as well as providing another location for additional security mechanisms.

### N-Tier Architecture.

If an extranet system provides all aspects of a service, there exists a single point of failure and compromise. N-Tier architecture provides the ability to distribute different aspects of the service offering to additional systems. The extranet system will provide the front-end user interface; the application server facilitates the logic and processing necessary to access data; and the back-end database server stores and provides the data. Since the extranet server resides on an external service zone, the firewall policy must allow that server to connect to its next tier servers on the internal network. When possible, restrict access from the extranet server to the internal network to only necessary systems and services. This architecture helps to create a more robust infrastructure that reduces unnecessary exposures.

### TLS/SSL Encryption.

The most visible marker of TLS/SSL encryption is the little golden padlock favicon that appears in an Internet browser when connecting to a server using HTTPS. When a host attempts to connect to an extranet server, several steps occur before the encrypted session can begin. The connecting host provides SSL-related parameters to negotiate a HTTPS connection with the server. The server then replies with the negotiated SSL-related parameters and a digital certificate. The client then uses the certificate to authenticate the server. If authentication is successful, the client and server establish the encryption keys used to protect the session and begin encrypted communications.

## 32.4.3 Types of Extranet Access.

The type of systems and services able to go onto the extranet continues to grow. Providing extranet services is always subject to the needs of the organization, and the following sections provide some common examples of extranet systems.

### Vendor/Partner Information Sharing.

Businesses survive and thrive on competitive advantage, and increasingly need to share information with strategic partners. By providing access to internal information, these partners can better understand and meet the organizational needs. Enterprise Resource Planning (ERP) systems contain the data that serves as the digital lifeblood of an organization. On the extranet, vendors and business partners could have access to work with information stored in the ERP system.

### E-Commerce.

Conducting business transactions digitally can create efficiencies and reduce costs. E-commerce occurs at the business and consumer level. Businesses can use Electronic Data Interchange (EDI), which allows two entities to exchange standardized, digital versions of documents such as a purchase order and payments without human interaction. The extranet provides a means to allow business partners to exchange EDI data without granting access to the internal servers that actually process and store data. Consumers access e-commerce Websites to view and purchase goods and services.
