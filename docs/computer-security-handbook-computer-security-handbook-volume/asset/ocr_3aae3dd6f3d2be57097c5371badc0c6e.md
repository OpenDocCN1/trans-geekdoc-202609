community only has access to the specific service(s) advertised. Extranet services require greater consideration, as network security devices still lag in protecting the protocols and customizations routinely occurring at the Application Layer.

# 32.4.2 Extranet Concepts.

**External Service Zone.** As described in Chapter 26 of this Handbook, extranet networks are another opportunity to use zoning, largely because extranets require robust protections and make extensive use of resources in other zones. Zoning allows administrators to be more granular on the services allowed into the network, as well as providing another location for additional security mechanisms.

# N-Tier Architecture.

If an extranet system provides all aspects of a service, there exists a single point of failure and compromise. N-Tier architecture provides the ability to distribute different aspects of the service offering to additional systems. The extranet system will provide the front-end user interface; the application server facilitates the logic and processing necessary to access data; and the back-end database server stores and provides the data. Since the extranet server resides on an external service zone, the firewall policy must allow that server to connect to its next tier servers on the internal network. When possible, restrict access from the extranet server to the internal network to only necessary systems and services. This architecture helps to create a more robust infrastructure that reduces unnecessary exposures.

# TLS/SSL Encryption.

The most visible marker of TLS/SSL encryption is the little golden padlock favicon that appears in an Internet browser when connecting to a server using HTTPS. When a host attempts to connect to an extranet server, several steps occur before the encrypted session can begin. The connecting host provides SSL-related parameters to negotiate a HTTPS connection with the server. The server then replies with the negotiated SSL-related parameters and a digital certificate. The client then uses the certificate to authenticate the server. If authentication is successful, the client and server establish the encryption keys used to protect the session and begin encrypted communications.

# 32.4.3 Types of Extranet Access.

The type of systems and services able to go onto the extranet continues to grow. Providing extranet services is always subject to the needs of the organization, and the following sections provide some common examples of extranet systems.

# Vendor/Partner Information Sharing.

Businesses survive and thrive on competitive advantage, and increasingly need to share information with strategic partners. By providing access to internal information, these partners can better understand and meet the organizational needs. Enterprise Resource Planning (ERP) systems contain the data that serves as the digital lifeblood of an organization. On the extranet, vendors and business partners could have access to work with information stored in the ERP system.

# E-Commerce.

Conducting business transactions digitally can create efficiencies and reduce costs. E-commerce occurs at the business and consumer level. Businesses can use Electronic Data Interchange (EDI), which allows two entities to exchange standardized, digital versions of documents such as a purchase order and payments without human interaction. The extranet provides a means to allow business partners to exchange EDI data without granting access to the internal servers that actually process and store data. Consumers access e-commerce Websites to view and purchase goods and services.