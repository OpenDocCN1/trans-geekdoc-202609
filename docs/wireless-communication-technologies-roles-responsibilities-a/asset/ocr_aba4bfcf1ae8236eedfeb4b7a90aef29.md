cryptographic approaches. Security at the device level is achieved by safelisting, traffic filtering, ensuring the security of pairing protocols, booting and transmission approaches, fault tolerance, light access control of resources, data protection using storage and transmission, authentication, identity, and authorization management. Implementing security algorithms on IoT devices must consider power, memory, and embedded network protocol/Operating System limitations [21,22]. The primary security features of this level are as follows [23]:

+   - Chip Security: Trusted Platform Modules (TPM) are used by a few vendors and act as a trust basis by protecting sensitive data and credentials.
+   - Secure Booting: Ensures that only protected software is authorized to work.
+   - Physical Security: Anti-tamper approach consists of Evidence, Resistance, Reaction, and Discovery. This is implemented at the fog level and Synchronized with the security policy and device’s threat pattern. The effort involved while accessing the components and the following concerns of an intrusion are determined. The primary security assessment factors are the node’s physical location and access level. Physical attacks are vulnerable on fog nodes in public locations, such as shopping centers or utility poles.

# 5.3.4 COMMUNICATION LAYER

In this level, insecure channels and IoT networks are highly susceptible. The primary attacks are snooping, sleep deficiency, Sybil attacks, MITM, and sinkholes. The network is secured using dependable message integrity authentication (SHA or MD5 hash algorithms), routing approaches, and point-to-point encryption. The cryptographic approaches utilized for encryption are categorized in two ways: symmetric algorithms (e.g. DES, Blowfish, AES, Skipjack) or asymmetric techniques (e.g. Rabin’s approach and Elliptic Curve). Symmetric techniques do not perform heavy computation like asymmetric; hence they are most suited with minimal power of 8 or 16-bit IoT nodes. The primary characteristics of IoT security are as follows [24]:

+   - Data Centered Solutions: These ensure that data is encrypted correctly while at rest or transmitted, even if leaked; it has no significance for unauthorized devices and applications.
+   - Firewalls & Intrusion Prevention System: Data traffic terminating at the node is analyzed to identify invasions and secure the transmission layer.

# 5.3.5 CLOUD LAYER

SQL or malicious code injections, Cross-site scripting (XSS), Denial of Service (DoS), remote code execution, and brute force are a few attacks targeting the cloud. The primary IoT aspects of this layer are as follows [25]:

+   - Sensitive Information Storage: Disclosure can be prevented by encrypting the data in the rest state such that negotiated third parties prohibit data access.