
# SSL/TLS

**Secure Sockets Layer** (**SSL**) is an encryption, server, and client authentication, and message integrity protocol. It communicates with the application and transport layers, but it does not act inside them. Netscape created SSL in order to send confidential documents over the Internet. SSL uses 40-bit encryption (SSL 2.0) or 128-bit encryption (SSL 3.0), although the 40-bit version is vulnerable to attacks due to its small key size. SSL enables a program to communicate across a network in an encrypted and authorized manner.

SSL 3.0 is the foundation for **Transport Layer Security** (**TLS**) 1.0, however, it is more adaptable. TLS’s fundamental objective is to provide data integrity and privacy between two interacting apps. When the data has to be encrypted while being transferred (in transit) through the media from one system to another, SSL and TLS are the most widely utilized protocols, as shown in *[Figure 15.5](#c15.xhtml#fig15_5)*:

![](images/Image29355.jpg)

**Figure 15.5:** Secure Socket Layer/Transport Layer Security (SSL/TLS)

# HTTP/HTTPS/SHTTP

The **Hypertext Transfer Protocol** (**HTTP**) is a web protocol for sending website data from a web server to a web client. Because HTTP is a stateless protocol, a new connection is made with each new URL typed into the web browser, whether from the original user entry or by clicking a link on the page shown. **HTTP Secure** (**HTTPS**) is an HTTP implementation that uses the SSL/TLS protocol to create a secure connection using the server’s digital certificate. SSL/TLS uses a secure channel to keep the session open. The https:// prefix is always included at the beginning of HTTPS webpages. **Secure HTTP** (**SHTTP**), despite its similarity in name, safeguards HTTP transmission in a different way. Only a single communication message is encrypted using SHTTP, not the whole session (or conversation). SHTTP is less popular than HTTPS.

# 3-D secure and SET

Visa and MasterCard suggested **Safeguard Electronic Transaction** (**SET**) to secure credit card transaction information over the Internet. It used asymmetric keys and X.509 certificates. It sent encrypted credit card information through a user’s computer’s electronic wallet. SET, on the other hand, would have needed complete cooperation from financial institutions, credit card users, wholesale and retail enterprises, and payment gateways in order to be completely implemented. It was never completely accepted. Instead of SET, Visa now pushes the 3-D secure standard. 3-D Secure is an XML-based technology that adds an extra layer of protection to credit and debit card transactions made online. Customers may get it under the label Verified by Visa. MasterCard’s implementation of 3-D Secure is known as Secure Code.

# IPsec

**Internet Protocol Security** (**IPsec**) is a set of protocols that creates a secure connection between two devices. VPNs often use IPsec as a security protocol. IPsec protects against traffic analysis by deciding on the methods to employ and implementing any cryptographic keys needed for IPsec. **Authentication Header** (**AH**), **Encapsulating Security Payload** (**ESP**), and **Security Associations** (**SAs**) are all part of IPsec. Authentication and integrity are provided by AH, while authentication, integrity, and encryption are provided by ESP (confidentiality). An SA is a configuration record for a device that needs to participate in IPsec communication. A **Security Parameter Index** (**SPI**) is a form of database that keeps track of the multiple SAs in use and guarantees that a device communicates with another device using the correct SA. As shown in *[Figure 15.6](#c15.xhtml#fig15_6)*, each device has its own SPI:

![](images/Image29364.jpg)

**Figure 15.6:** IPSec for Remote Console Management

IPsec may operate in one of the two modes – transport or tunnel. Only the message content is protected in the transport mode, but the payload, route, and header information are all protected in the tunnel mode. Both of these modes may be utilized for IPsec communication between gateways and hosts. Which hashing or encryption algorithm is employed is not determined by IPsec. The key exchange technique most widely used by IPsec is **Internet Key Exchange** (**IKE**), which is a mix of OAKLEY and **Internet Security Association and Key Management Protocol** (**ISAKMP**). OAKLEY is a Diffie-Hellman-based key establishment mechanism that was replaced by IKE. The ISAKMP was created to create and manage SAs. Authentication and key exchange are provided via IKE with IPsec. Pre-shared keys, certificates, and public-key authentication are among the authentication methods used by IKE with IPsec. A PKI is required for the most secure implementations of pre-shared keys. However, if a pre-shared key is based on basic passwords, a PKI is not required.

# Data-in-memory/processing

In-memory processing is a method of processing data sets in which all data is handled in memory rather than on the hard disk. It expects that all data will be accessible in memory, rather than simply the most recently utilized data, as is typical with RAM or cache memory. As a consequence, company reporting and decision-making are expedited. Encrypting the data in RAM is required to secure this. The **Data-Protection API** (**DPAPI**) is a Windows feature that allows you to encrypt data using the user’s login credentials. One of the most important considerations is where to keep the key since it is usually not a good idea to keep it in the same place as the data. **Software Guard Extensions** (**SGX**), which comes as standard with Skylake and subsequent Intel processors, enables you to load a program into your processor, validate its status (remotely), and safeguard its execution. Everything that leaves the processor (that is, everything that is offloaded to RAM) is immediately encrypted by the CPU, ensuring security.

# Encryption of data at rest

Data at rest refers to information that is physically stored in any digital format but is not in use. Databases, data warehouses, files, archives, tapes, offsite backups, mobile devices, and any other storage media may be used to store this information. Data encryption techniques are often used to secure data at rest. When converting plaintext to cipher text, computer algorithms apply sophisticated mathematical formulas to convert plaintext to cipher text. The key and the algorithm are the two most important parts of any encryption system. The two communicating parties utilize the same key in various encryption methods. Other encryption schemes include the use of distinct keys by the two communication parties, but the keys are connected. Symmetric algorithms, asymmetric algorithms, and hybrid ciphers are some of the encryption methods you’ll need to know about.

# Symmetric algorithms

Symmetric algorithms rely on a private, or secret key that must be kept confidential between the two parties. A private key is required for each party pair. As a result, each user with whom they talk would need a separate secret key. Consider a scenario in which there are ten distinct users. To calculate the number of keys that would be needed in this example, you would use the following formula: `# of users' × (# of users – 1) / 2`

In this example, you would calculate `10 × (10 – 1) / 2`, or 45 needed keys.
