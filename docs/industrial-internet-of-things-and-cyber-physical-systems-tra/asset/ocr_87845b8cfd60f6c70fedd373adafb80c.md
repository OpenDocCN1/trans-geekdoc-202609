# Comprehensive Survey of Routing Protocols for Wireless Body Area Networks (WBANs)

# Table 5. Assessment of Secure Routing Schemes based on Trust

| Scheme | Model | Trust Convergence | False Reporting Mechanism | Energy Aware | Network Overhead | Fault Detection |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| TRÉ (Boukerche & Ren, 2009) | Aggregated sum of packet forwarding ratio | No | No | No | High | No |
| Re-Trust (He et al., 2012) | Aggregated sum of packet forwarding ratio | No | No | No | High | No |
| ReTrust (Y, Gao & Liu, 2014a) | Weight-based Aggregated sum of packet forwarding ratio | No | No | No | High | No |
| CATMS (Karthik & Anantharamya, 2018) | Weight-based Aggregated sum of packet forwarding ratio | No | No | No | High | Yes |
| CENTRA (Tajeddine et al., 2015) | Aggregated sum of packet forwarding ratio | Slow | No | No | High | No |
| TQR (B. Wang et al., 2014) | Weight-based aggregated sum of direct and indirect trust | Moderate | No | No | High | No |
| TSRF (Duan et al., 2014) | Weight-based aggregated sum of direct and indirect trust | Moderate | Yes | No | Low | No |
| RA- AODV (Al- hammadani & Allen, 2014) | Aggregated sum of packet forwarding ratio | Slow | No | No | Moderate | No |
| FR-AODV (Eissa et al., 2013) | Feature Attributes (Repute and Identity) | Slow | No | No | Moderate | No |
| LTB-AODV (Marching & Data, 2012) | Intrusion Detection System | Moderate | Yes | No | High | No |
| R-AODV (Channa & Ahmed, 2011) | Aggregated sum of packet forwarding ratio | Slow | No | No | High | Yes |
| SORI (Qi He et al., 2008) | Aggregated sum of packet forwarding ratio | Slow | No | No | High | No |

To protect against selfish behavior of nodes a secure routing scheme referred to as SORI is proposed in (Qi He, Dapeng Wu, & Khosla, 2008). SORI introduced punishment and reward-based system to encourage nodes for participating in packet forwarding. The scheme is comprised of three main components (i) the monitoring component to observe the behavior of neighboring nodes (ii) the reputation propagation component is responsible for evaluating the trustworthiness of nodes (iii) the punishment component that penalizes the selfish node for their misconduct. A node drops the received packet from a node whose reputation value is below the threshold value and decreases its reputation value. Furthermore, it is responsible for informing the selfish behavior of nodes to other nodes in the network, so that it should be punished by other nodes as well. SORI authenticate each node and packet by incorporating one hash function and Message Authentication Code (MAC). However, incorporating these complex methods in resource constraint wireless sensor network is not feasible.

The summary and comparison of the above trust-aware routing schemes in tabular form in terms of most common parameters related to trust is shown in Table 5 re-drawn from (Adnan Ahmed, Abu Bakar, et al., 2015)