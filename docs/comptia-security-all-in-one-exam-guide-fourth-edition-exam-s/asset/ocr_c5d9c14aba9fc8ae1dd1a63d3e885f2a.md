point in the network, the VPN concentrator. VPN concentrators come in a variety of sizes, scaling to enable VPNs from small networks to large. A VPN concentrator allows multiple VPN connections to terminate at a single network point.

# Intrusion Detection Systems

Intrusion detection systems (IDSs) are designed to detect, log, and respond to unauthorized network or host use, both in real time and after the fact. IDSs are available from a wide selection of vendors and are an essential part of network security. These systems are implemented in software, but in large systems, dedicated hardware is required as well. IDSs can be divided into two categories: network-based systems and host-based systems. Two primary methods of detection are used: signature-based and anomaly-based:

+   - **Host-based IDS (HIDS)** Examines activity on an individual system, such as a mail server, web server, or individual PC. It is concerned only with an individual system and usually has no visibility into the activity on the network or systems around it.
+   - **Network-based IDS (NIDS)** Examines activity on the network itself. It has visibility only into the traffic crossing the network link it is monitoring and typically has no idea of what is happening on individual systems.

![](bbox=[0.18, 0.52, 0.26, 0.6])

> **EXAM TIP** Know the differences between host-based and network-based IDSs. A host-based IDS runs on a specific system (server or workstation) and looks at all the activity on that host. A network-based IDS sniffs traffic from the network and sees only activity that occurs on the network.

Whether or not it is network-based or host-based, an IDS will typically consist of several specialized components working together, as illustrated in Figure 1-3. These components are often logical and software-based rather than physical and will vary

Figure 1-3
Logical depiction
of IDS
components

![](bbox=[0.35, 0.73, 0.82, 0.92])