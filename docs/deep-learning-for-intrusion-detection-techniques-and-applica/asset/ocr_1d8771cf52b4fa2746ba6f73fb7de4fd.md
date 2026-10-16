# **Table 1.1**  Difference between IDS and IPS.

| Feature | Intrusion detection system (IDS) | Intrusion prevention system (IPS) |
|---|---|---|
| *Objective* | Detect and monitor unauthorized activities, but do not take direct action to prevent them. | Actively identify and prevent unauthorized activities by taking immediate actions, such as blocking or dropping malicious traffic. |
| *Action Taken* | Passive: generates alerts and reports to notify administrators of potential threats. | Active: takes automated actions to prevent identified threats, such as blocking malicious packets, resetting connections, or alerting administrators. |
| *Placement* | Positioned strategically to monitor network traffic but not directly in the traffic flow. | Placed inline within the flow of network traffic, actively participating in the traffic flow between the source and destination. Usually positioned just behind the firewall. |
| *Manual Intervention* | Requires manual intervention from administrators to investigate and respond to alerts. | Minimizes manual intervention by automatically taking actions based on predefined security policies. |
| *Prevention Capability* | Primarily focused on detection and reporting; does not actively prevent threats. | Actively prevents threats by taking immediate actions to block or drop malicious traffic. |
| *Use Cases* | Suitable for environments where detection and reporting are the primary concerns, and immediate prevention is not critical. | Ideal for environments where real-time threat prevention is crucial to mitigate potential risks promptly. |

![](bbox=[0.114, 0.627, 0.626, 0.827])

**Figure 1.3**  Intrusion detection system classification.