# Technology Concerns

Of the five architectural layers in this example, four will need to be secured:

+   1. The *presentation layer* will not be secured or trusted. Communications between the client and the Web server will be encrypted at the *network layer*.
+   2. The *network layer* will need to filter unwanted traffic, to prevent denial of service (DoS) attacks and to monitor for possible intrusions.
+   3. The *middle layer* will need to prevent unauthorized access, be tamper-proof, contain effective monitoring, and support efficient and effective processing.
+   4. The *application layer* will need to prevent unauthorized access, support timely processing of transactions, provide effective audit trails, and process confidential information.
+   5. The *internal layer* will need to prevent unauthorized access, especially through Internet connections, and to protect confidential information during transmission, processing, and storage.

# Step 2: Develop Security Services Options.

The four security services reviewed in this example are the most critical in an e-commerce environment. Other services such as nonrepudiation and data classification are important but not included in order to simplify the example. Services elected are:

+   - Trusted communication
+   - Authentication and identification
+   - Monitoring and auditing
+   - Access control

Many security services options are available for the B2C case, with more products and protocols on the horizon. There are five architectural layers for each of the services defined in Step 1.

+   1. **Presentation layer.** Several different options can be selected for trusted communication. While the most common application-level protocol is the Hypertext Transfer Protocol (HTTP); the ever increasing need for privacy and assurance of integrity argues for the use of its more secure encrypted sibling, Transport Layer Security,³ the successor to Secure Socket Layer (SSL) protocol,⁴ in conjunction with certificates in a Public Key Infrastructure (PKI), to authenticate and cryptographically secure the communications pathway. The use, or possible use, of wireless connections somewhere in the path only increases the importance of secured, encrypted paths. Because the client is untrusted, the client’s authentication, audit, or access control methods cannot be relied on.
+   2. **Network layer.** Virtual private networks (VPNs) are considered best practice for secure network layer communication. Firewalls are effective devices for securing network communication. The client may have a personal firewall. If the client is in a large corporation, there is a significant likelihood that a firewall will intervene in communications. If the client is using a home or laptop computer, then a personal firewall may protect traffic. There will also be a firewall on the B2C company side of the Internet.