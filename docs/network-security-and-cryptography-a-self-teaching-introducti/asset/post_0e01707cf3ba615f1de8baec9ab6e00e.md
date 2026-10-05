
# 14.7 SECURITY OF WIRELESS SENSOR NETWORKS (WSNs)

- A Wireless Sensor Network (WSN) is an infrastructure-less network composed of a large number of sensor nodes. These cooperatively sense and control the environment to enable its interaction with people or devices.

- Wireless Sensor Networks (WSNs) are considered as one of the core technologies in implementing Cyber Physical Systems (CPSs).

- WSNs include sensor nodes, actuator nodes, gateways, and clients. A large number of sensor nodes deployed randomly inside of or near the monitoring area form networks through self-organization.

- The data is captured at the level of the sensor node, compressed and transmitted to the gateway. Through the gateway connection, data is then passed by the base station to a server.

- Sensor nodes monitor the collected data to transmit to other sensor nodes by hopping. During the process of transmission, the monitored data may be handled by multiple nodes to get to the gateway node after multi-hop routing, and finally reach the management node through the Internet or satellite.

- It is the user who configures and manages the Wireless Sensor Network with the management node, publish monitoring missions and collection of the monitored data.

![](img/d3b56042c756fbcc011ff06f1b9f53f0_543_0.png)

FIGURE 14.11 WSN concept topology

## 14.7.1 WSN Layers:

- Transport Layer: Responsible for managing end-to-end connections. Reliable transport of data.
- Network and Routing Layer: Responsible for routing of sensors based on addressing and location awareness, sensor networking, power efficiency, and topology management. It provides more efficient routing of data. From "Node to node, node to sink, node to base station, and node to Cluster head & vice versa.\ Due to the broadcast method every node works as a router.
- Data Link Layer: Responsible for the multiplexing of data streams, data frame detection, medium access, and error control.
- Physical Layer: Responsible for frequency selection, carrier frequency generation, signal detection, modulation, and data encryption.

## 14.7.2 Security Requirements in WSNs:

- Data Confidentiality: To provide the data confidentiality, encrypted data is used so that only recipient decrypts the data to its original form. Only the authorized sensor nodes get the content of the messages.
- Data Integrity: Data received by the receiver should not be altered or modified. Original data is changed by an intruder or due to a harsh environment. The intruder may change the data according to its need and sends this new data to the receiver.
- Data Authentication: It is the procedure of confirmation that the communicating node is the one that it claims to be. The receiver needs to make verification that the data is received from an authenticated node.
- Data Availability: The services are available all the time whenever necessary.
- Source Localization: For data transmission some applications use location information of the sink node. It is essential to give security to the location information. Non-secured data can be controlled by a malicious node.

## 14.7.3 The Attack Categories in WSNs:

- **Self-Organization:** In WSN no fixed infrastructure exists, hence, every node is independent, having properties of adaptation to the different situations, and maintains self-organizing and self-healing properties.
- **Data Freshness:** Each message transmitted over the channel is new and fresh. It guarantees that the old messages cannot be replayed by any node. This can be solved by adding some time-related counter to check the freshness of the data.
- **Outider vs. Insider attacks:** Outer attacks are external attacks and the insider attacks are internal attacks. An outsider attack comes from outside the WSN. With the help of an Outer attack the bad data is inserted in the network for the services interruption. An insider attack is also known as the internal attack; these attacks come from the inside of the WSN.
- **Passive vs. Active Attacks:** Passive attacks include eavesdropping on or monitoring packets exchanged within the WSN; in active attacks, an attacker has the capability to remove or modify the messages during the transmission on the network.
- **Mote-Class versus Laptop-Class attacks:** In Monte-class attacks, an adversary attacks a WSN by utilizing a few nodes with similar capabilities to the network nodes; in laptop-class attacks, an adversary can use more powerful devices to attack a WSN. These devices have greater transmission range, processing power, and energy reserves than the network nodes.

## 14.7.4 Attacks and Defense in WSNs at Different Layers:

| Layer | Possible Type of Attacks | Defense |
| --- | --- | --- |
| Transport | Flooding Desynchronization | Client puzzles Authentication |
| Network and Routing | Spoofed, altered, or replayed routing information | Selective forwarding Sinkhole, Sybil Wormholes, Hello flood attacks Acknowledgment spoofing | Egress filtering, authentication, monitoring Redundancy, probing Authentication, monitoring, redundancy Authentication, packet leases by using geographic and temporal information Authentication, verify the bidirectional link Authentication |
| Data Link | Collision Exhaustion Unfairness | Error-correction code Rate limitation Small frames |
| Physical | Jamming Tampering | Spread-spectrum, priority messages, lower duty cycle, region mapping, mode change Tamper-proofing, hiding |

## 14.7.5 Security Protocols in WSNs:

- Sensor Protocols for Information via Negotiation (SPINs):
  - SPIN is an adaptive routing-protocol, which transmits the information first by negotiating.
  - The SPIN transmission is data-centric; it is only transmitted to the nodes that have interest in the data. This process continues until the data reaches the sink node. SPIN reduces both the network overhead and the energy consumption in the transmission. There will not be duplicate messages in the network since nodes negotiate before transmitting the data.
  - SPIN makes use of metadata of the actual data to be sent. Metadata will contain the description of the message that the node wants to send. The actual data will be transmitted only if the node wishes to receive it. SPIN makes use of 3 messages, namely,
    - ADV: Before sending a message, a node first generates the descriptor of the message to be sent. This metadata is exchanged by making use of the ADV message, ADV message informs the size, contents, and requirements of the message. This helps the receiving node on deciding transmission of the message.
    - REQUEST: After receiving the ADV message, the receiver node verifies the descriptor that the message is a duplicate and whether the receiver node's battery capabilities are enough to transmit the data. If the node is interested in the data, it replies with a REQUEST message to the sender node.
    - DATA: If the sender node receives a REQUEST message, it starts the actual transmission of data by making use of the DATA message. This is the actual data transfer phase.

## Localized Encryption and Authentication Protocol (LEAP)

- LEAP is a protocol with key management scheme that is very efficient with its security mechanisms used for large scale distributed sensor networks. It is designed to support in-network processing such as reduction of the energy consumption in network. To provide the confidentiality and authentication to the data packet, LEAP uses multiple keys mechanism. For each node four symmetric keys are used as follows:
- Individual Key: Used for the communication between source node and the sink node.
- Pair Key: Shared with another sensor node.
- Cluster Key: Used for locally broadcast messages and is shared between the node and all its neighboring nodes.
- Group Key: Used by all of the network Nodes.

## TINYSEC

- TINYSEC is a lightweight protocol and link layer security architecture for WSNs.
- It supports integrity, confidentiality, and authentication. To achieve confidentiality, encryption is done using CBC (Cipher-block chaining) mode with cipher text stealing, and authentication is done using CBC-MAC. No counters are used in TINYSEC. Hence, it doesn't check the data freshness. Authorized senders and receivers share a secret key to compute a MAC.
