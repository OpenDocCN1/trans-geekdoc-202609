
## C. Tokens

## D. SAML

- A. The TLS protocol uses X.509 certificates for authentication between the two parties that are negotiating a secure communications channel. The same certificates that are used for authentication are also used for the encryption of the communications channels.

- B is incorrect because tokens are not used with the TLS protocol but rather commonly used with other systems as Kerberos.

- C is incorrect because tokens are not used with TLS but rather are commonly used with other systems as multifactor authentication schemes.

- D is incorrect because the Security Assertion Markup Language (SAML) is commonly used for exchanging authentication and authorization information between two parties, but it is not used with TLS.

7. The traditional approach to data center design is to use a tiered topology for layers of redundancy. Which organization publishes this widely used standard and collection of best practices?

- A. Uptime Institute
- B. IDCA
- C. NPFA
- D. BISCI

- A. The Uptime Institute publishes the most widely used standard for data center design based on a tiered-topology approach. This standard has four tiers, each progressively adding layers and requirements for redundancy and fault tolerance.

- B is incorrect because the International Data Center Authority (IDCA) established the Infinity Paradigm, which is intended to be a comprehensive data center design and operations framework. The Infinity Paradigm differs from other standards by shifting away from a tiered architecture and instead embraces a macro-level approach where the entire data center is considered as a whole.

- C is incorrect because the National Fire Protection Association (NFPA) publishes a large collection of standards regarding fire protection for almost any type of facility, and it does offer ones focused on data centers. These standards cover the overall electrical systems within data centers, including emergency procedures and requirements for the immediate cutting of power in case of an emergency.

- D is incorrect because Building Industry Consulting Services International (BISCI) issues certifications and develops standards in the area of complex cabling for data systems. The standards are focused on cabling design and setups includes specifications on power, energy, efficiency, and hot/cold aisle setups.

8. DHCP is heavily used within cloud environments to maintain network configurations in a centralized manner. Which of the following is NOT a network configuration that plays a role with DHCP?

- A. IP address
- B. Hostname
- C. MAC address
- D. Gateway

- B. Hostname resolution is provided via the Domain Name System (DNS) and is not provided as part of the network configuration for a specific server.

- A is incorrect because the IP address is one of the core network configuration items provided by DHCP to a server.

- C is incorrect because the MAC address is what the DHCP servers use to track and maintain network configuration settings for a host.

- D is incorrect because a gateway address would be assigned by a DHCP server as part of the network configuration given to the host.

9. Which component of the ITIL framework includes dependency checks?

- A. Change management
- B. Continuity management
- C. Release management
- D. Availability management

- A. The change management process oversees the entire implementation and release of changes to a production environment, including management approvals, notifications, and testing/validation. As part of the approval process, a dependency check is done to validate the scope of potential impact and to ensure that a proper validation plan is fully in place.

- B is incorrect because continuity management is focused on planning for the successful recovery of systems or services after an unexpected outage, incident, or disaster.

- C is incorrect because release management is focused on the actual execution of a production release, including validation. The main focus is on properly mapping all out steps for a release and then configuring and deploying it. Although dependency validations will be part of a release management process, they are performed after the checks will have been done as part of the change management process.

- D is incorrect because availability management is focused on making sure system resources, processes, personnel, and toolsets are properly allocated and secured to meet SLA requirements for performance.

10. Which process is used to properly maintain balanced resources across a cloud environment and to respond to changing needs from conditions due to auto-scaling?

- A. DCOM
- B. Distributed optimization
- C. Dynamic optimization
- D. Elasticity

- C. Dynamic optimization is the process through which the cloud environment is constantly maintained to ensure that resources are available when needed and that physical nodes do not become overloaded or near capacity while others are underutilized.

- A is incorrect because DCOM refers to the Distributed Component Object Model, which is a set of Microsoft interfaces and services that can be requested by systems throughout a network.

- B is incorrect because distributed optimization is a distractor term that sounds similar to the correct answer.

- D is incorrect because elasticity refers to the ability of a cloud environment to resize resources to meet current demand, either through increasing or decreasing them; dynamic optimization is the more correct answer in this case because it refers to analysis and determination, not just the ability to adjust resource levels.

11. Which TLS protocol handles the secure communications between parties, specifically the send/receive operations?

- A. Handshake
- B. Transmission
- C. Negotiation
- D. Record

- D. The TLS record protocol handles the actual transmission of secure information over the encrypted channel. It only handles the sending and receiving of secure data and relies on the handshake protocol for all information to handle the transmission.

- A is incorrect because the handshake protocol of TLS negotiates and establishes the connection between two parties and enables the secure communications channel that will handle secure data transmission. The protocol exchanges all information needed to authenticate and negotiate the encryption algorithms to be used as well as to create the session ID for the transaction.

- B is incorrect because although transmission is certainly a key function of TLS and the record protocol, it is not the name of a protocol itself.

- C is incorrect because negotiation is a component of the handshake protocol; it is not the name of a protocol itself.

12. DNSSEC relies on digital signatures and allows a client lookup to validate a DNS resolution back to its authoritative source. What is this process called?

- A. Zone signing
- B. Authentication
- C. Realm signing
- D. Domain signing

- A. Zone signing is the process of a client using digital signatures to validate a DNS resolution back to the authoritative source.

- B is incorrect because authentication is not a component of either DNS or DNSSEC.

- C is incorrect because realm signing is provided as a similar term to zone signing but is not an applicable term here, nor is it pertinent to DNSSEC.

- D is incorrect because domain signing is provided as a similar term to zone signing but is not an applicable term here, nor is it pertinent to DNSSEC.

13. A host-based IDS can suffer from security vulnerabilities if the host itself is compromised. Which of the following concepts can be best used to mitigate risk with a HIDS?

- A. Administrative privileges
- B. Read-only storage
- C. Baselines
- D. Encryption

- B. A common strategy for mitigating the corruption of a host-based IDS due to the host itself being compromised is to store the signatures and configurations for the HIDS in read-only storage. In this case, if the host is compromised, the configurations and signatures are still protected and cannot be modified by the attacker.

- A is incorrect because although administrative privileges are important to the protection of any system, if a malicious actor is able to compromise a host and obtain access, it is very likely he will be able to elevate privileges and overcome administrative controls.

- C is incorrect because although baselines are crucial to ensuring that systems meet expected configurations and that policies are enforced, if a system is compromised, the settings applied at the time of the baselines are susceptible to alteration or overriding by the attacker.

- D is incorrect because encryption is not used to protect an HIDS. In fact, encryption is actually a big impediment to HIDS analyzing traffic because it won't be able to read the encrypted packets.
