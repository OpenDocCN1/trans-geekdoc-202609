node. Once this recognition is complete, it may spoof the DODAG root's address and gain control over the network. Identity attacks are used as a foundation for further operations.

# 10.4 SECURITY SOLUTIONS BASED ON INTRUSION DETECTION SYSTEM

An IDS is responsible for monitoring network traffic to identify potentially malicious behaviour and sends notifications when these activities are detected. This section explores several IDS-based security solutions to detect RPL protocol routing attacks. Contrary to WSNs, which do not presuppose continual access to the sink node, the IoT assumes that the sink node (6LoWPAN border router) is always available.

# TABLE 10.1
Design Requirements [16]

| Design Requirements | Description |
|---|---|n| RPL specification compliance | This covers the DODAG structure, control message exchange logic, and the Trickle mechanism. |
| Low overhead | Even security solutions for LLNs should include resource availability. A “low-budget” strategy focuses on exchanging messages and uses the standards to verify the system and identify anomalies. Maintaining control overhead leads to conserving energy in transceivers which are the major consumers of constrained devices. |
| Scalability | The network size is sufficient for evaluating IDS in terms of its ability to safeguard the protocol, even if it is significantly expanded in terms of connected devices. Scalability shouldn't compromise the need for low overhead. |
| Robustness Extensibility | Due to the variety of attacks, IDS must be able to detect all them. IDS can be expanded to handle more scenarios, such as it can be used as a “static” binary rationale to detect whether a threat pattern is recognized or not. Systems should use all existing technological assets to stay up-to-date and prepare for unexpected attacks. |
| Low false (negative/positive) detections | The frequency of false positives/negatives affects a system's efficiency and detection accuracy. IDS should be accurate, not robust and expandable. It should deliver alerts for targeted attacks while limiting false positives. If this is not, the network operator must monitor the control overhead and the number of node changes, the packet delivery rate, and the number of RPL local repairs. This, it helps distinguish between normal and unexpected processes and attacks. |
| Mobility support | Mobile IoT applications functioning under mobility is the main challenging problem as it requires connection handovers and extra topology management. Basic security measures should address both stationary and mobile nodes, and the simple solutions are not available in the literature. |