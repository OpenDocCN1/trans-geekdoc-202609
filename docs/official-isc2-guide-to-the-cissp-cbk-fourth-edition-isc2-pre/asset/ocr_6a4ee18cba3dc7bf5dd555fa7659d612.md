# Description of Risk

Malicious users may intercept or monitor plaintext data transmitting across an unencrypted network and gain unauthorized access to that, jeopardizing the confidentiality of the sensitive data.

# Recommendations

Covered data must be encrypted when transmitted across any network to protect against eavesdropping of network traffic by unauthorized users. In cases where source and target endpoint devices are within the same protected subnet, covered data transmission must still be encrypted as recommended below due to the potential for high negative impact of a covered data breach. The types of transmission may include client-to-server, server-to-server communication, as well as any data transfer between core systems and third-party systems.

Email is not considered secure and must not be used to transmit covered data unless additional email encryption tools are used.

When attempting to secure data in transit, the security practitioner should consider the following recommendations to design secure transmission of data.

+   1. Where the covered device is reachable via Web interface, Web traffic must be transmitted over Secure Sockets Layer (SSL), using only strong security protocols, such as SSLv3, and Transport Layer Security v1.1 or v1.2 (TLS).
+   2. Covered data transmitted over email must be secured using cryptographically strong email encryption tools such as PGP or S/MIME. Alternatively, prior to sending the email, users should encrypt covered data using compliant File Encryption tools and attach it to email for transmission.
+   3. Non-Web covered data traffic should be encrypted via application level encryption
+   4. Where an application database resides outside of the application server, all connections between the database and application should also be encrypted using FIPS compliant cryptographic algorithms.
+   5. Where application level encryption is not available for non-Web covered data traffic, implement network level encryption such as IPSec or SSH tunneling.
+   6. Encryption should be applied when transmitting covered data between devices in protected subnets with strong firewall controls.

Examples of insecure network protocols and their secure alternatives include: