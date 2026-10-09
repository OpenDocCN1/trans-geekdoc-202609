system interface is a security risk and may prove harmful to the network. This makes the presence of suitably enhanced authentication and authorization procedures imperative for the secure usage of the IoT network, with all other entities such as server, user and gadget having their own unique identity to use the network safely.

+   3.  **Insecure assistance of IoT:** The open ports of all connected gadgets need examination and verification to ensure that the devices are not vulnerable to intrusion, thus improving the protection of the IoT network against cyber-attack.

+   4.  **Poor Transport Encryption/Integrity Verification:** Strategies such as managing network and portable application data movement, and disallowing any data to move into the transport layer via encryption protocols such as secure sockets layer (SSL) and updated Transport layer security (TLS) can be utilised in order to subdue such a vulnerability.

+   5.  **Vulnerable Cloud Interface:** Primarily, a check against rudimentary vulnerabilities needs to be conducted on all cloud interfaces. The default username and password is preferred by most unskilled users, which is an instance that needs to be avoided in order to make the security of a cloud interface more robust.

+   6.  **Vulnerable Mobile Interface:** The ease of wireless network connectivity for IoT devices via a mobile interface requires a validation security guideline in order to check information presentation associated to remote systems.

+   7.  **Scarcity of appropriate Security Configuration:** Multiple strategies such as provision of a diverse degree of access to network clients, encryption and usage of a robust secret key can be avail in order to fortify the security design of the IoT network, enabling it to perform rudimentary interruption identification to the network.

+   8.  **Insecure Software/Firmware:** Constantly updating with time and circumstances, as well as the dynamic nature of needs in an IoT environment, IoT devices need to ensure that the update documents of IoT devices are encoded and transmitted via encrypted interface. Further, updates as well as the update server from which they originate should be signed and confirmed in order to reduce the chances of IoT networked device intrusion.

+   9.  **Low Physical Security:** The probability of an intrusion into the IoT network is inversely proportional to the physical security of the IoT network. The physical mediums being utilized within the network need to secure against rudimentary replacement, data encryption and its subsequent storage, and abstatining port access from malevolent users. Strong gadget assembly to protect against device dismantling also needs to be ensured.

# Suggested Intrusion Detection Techniques for IOT

+   SVELTE intrusion detection system in IoT: Designed for IOT network, this type of IDS utilises the network mapping information for analysis in order to identify any intrusion to the IoT network. Consisting of an incorporated firewall and 6LoWPAN Mapper to collect information regarding IoT network and build it by using RPL (IPv6 routing Protocol for Low-Power), it is a resource friendly and successful IDS.

SVELTE (Figure 14) is a real-time IDS which is specifically geared to meet the requirement for for IPv6-connected IoT devices (Shahid Raza, Linus Wallgren and Thiemio Voigt, 2013). SVELTE collects information regarding to its connected nodes to create a network graph (Figure 15). Once it detects