Figure 8. Deployment of IDS

![](bbox=[0.15, 0.14, 0.85, 0.4])

contain a large volume of equally prioritised to critical data, yet potentially irrelevant data also adds to the inconveniences faced by host-based IDS. (Creech & Hu 2014)

# DEPLOYMENT OF INTRUSION DETECTION SYSTEM

# Centralized Intrusion Detection System

In a Centralized IDS (Figure 9), the packet analysis is conducted on one or a small number of nodes, with the audit component distributed, however, the accumulated audits will be forwarded to a specified location for analysis to happen. (Toulouse & Minh & Curtis 2015) With Centralized IDS, various kinds of alerts are generated with the network node or host analysed by agents, followed by the alert being transferred to a central C&C handler responsible for analysing and arriving at the correct conclusive decision. (L.N. Tidian & M. Frappier & A. Mammur 2019).

# Distributed Intrusion Detection System

Distributed IDS (Figure 10) can be established by bundling a bunch of intrusion detection systems over a large network, with communications established between a singular server and multiple clients via the centralization communication method. (J. Amudhavel et al. 2016) this centralized architecture of the distributed IDS enables the detection of a coordinated attack on an organization as well as any related distributed resources. (Vandana P et. al. 2014) A distributed IDS is the amalgamated manifestation of a network-based IDS and host-based IDS. Detection mechanism and correlation manager are the primary components of an IDS, where the entire network traffic being checked and/or monitored by the detection mechanism, with the information collected being transfer to the correlation manager, which performs a global correlation against information collected from different IDS and issue an alert notification in case of an intrusion and/or attack. The global correlation for distributed intrusion detection, coupled with