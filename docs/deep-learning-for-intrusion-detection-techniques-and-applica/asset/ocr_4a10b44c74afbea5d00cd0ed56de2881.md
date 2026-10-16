![](bbox=[0.12, 0.15, 0.88, 0.42])

Figure 1.2 Intrusion detection system.

characteristics. All types of IDSs are required to provide certain functionalities, including the identification of significant events, alerting for identified important events, recording information, and generating reports (Figure 1.2).

The difference between IDS and IPS is outlined in Table 1.1.

IDSs, as shown in Figure 1.3, can be grouped into categories such as intrusion detection technologies, intrusion detection methodologies, and intrusion detection approaches [1].

# 1.1.4.1 Intrusion Detection Technologies

ID technologies are generally classified into four types:

+   - An intrusion detection system based on network.
+   - An intrusion detection system based on host.
+   - An intrusion detection system based on wireless technology.
+   - An intrusion detection system based on network behavioral analysis.

# *An Intrusion Detection System Based on Network*

Network-based IDS (NIDS), as shown in Figure 1.4, is tasked with overseeing network traffic to ensure the security of network devices [11]. These systems scrutinize various protocols, including application, transport, and network protocols. The analysis in NIDS primarily occurs at the application layer, although hardware layer analysis is also possible. Typical components of NIDS include management servers, sensors, multiple consoles, and database servers. With the exception of sensors, these components are commonly found in other IDS technologies. Sensors play a crucial role in monitoring and analyzing network activities. These network IDSs are usually distinct physical devices separate from the systems under surveillance, strategically located upstream on the network. Their design is intended to monitor multiple systems on a shared network. NIDSs often operate covertly, escaping