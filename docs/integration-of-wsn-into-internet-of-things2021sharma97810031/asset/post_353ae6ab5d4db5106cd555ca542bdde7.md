
storm-prone areas need to be near real time. Hence, another characteristic important for sensor networks is the freshness of data. The data have to be relatively recent to be used so that the output derived from the information is reliable and near real time.

## 2.3.2 Security Requirements of WSN Data

Wireless sensor data are very crucial for the robust functionality of the system. There are some basic security requirements for WSN data:

- Interception of Data: The sensor data collected cannot be intercepted by any means. Generally, eavesdropping happens in the sensor network infrastructure. This event can also be called a breach of confidentiality. So, the intercepted information in the sensor network is one of the requirements.

- Unmodified Information: Sensor data inside the network should not be accessed by any kind of unauthorized nodes or parties. Hence, message integrity must be ensured. If it is not guaranteed, the nodes/parties involved with the network will receive inadequate information, which will lead to erroneous results. The authenticity and integrity of messages over the WSN are core to its intended functioning. The attacker can disable this integrity by modifying or tampering data in the system or the nodal application.

- Nonfabricated Information: The network cannot be compromised, as it will cause trust issues. Inaccurate data can be fed into the sensor node so that data authenticity is hampered. Transmitting false messages over the WSN reduces the authenticity of the overall results delivered to the user. If an attacker has enough access to fabricate transmission in the WSN, it indicates that the WSN is also vulnerable to service denial and other severe attacks.

- Frequent Message Sending: At times, the interacting parties are confused about the authenticity and security of the communication protocol when the nodes send authentic messages repeatedly. This can lead to issues with data transfer, as the nodes will be busy capturing the wrong information.

- Interruption: All layers identified in layer-specific categorization are vulnerable to interruption attacks. It interferes with a WSN channel and may cause service denial by affecting the network availability. Layer-specific precautions should be adopted for such attacks. The relationship among the various security requirements and their characteristics is shown in Table 2.4.

## TABLE 2.4 Relationship of Security Requirements for Wireless Sensor Networks and WSN Data

| WSN Security | Characteristics | WSN Data Security Req. |
| :--- | :--- | :--- |
| Confidentiality | The data should not be leaked; eavesdropping | Interception |
| Integrity | Makes sure that the data do not get corrupted by any means of breaching of integrity. Information remains authentic, trustworthy, and consistent in integrity. Protection from unauthorized nodes or parties. | Unmodified information |
| Authenticity | Authentic data communication between the parties Trust between parties End node data need to be authentic Feeding wrong data into the sensors will cause unauthentic access | Nonfabricated information |

## 2.3.3 Attacks and Countermeasures on Wireless Sensor Networks

Security attacks in the WSN can range from spoofing [51], jamming, interference, and disruption of routing protocols, affecting the energy consumption of the sensor nodes. Countermeasures have been proposed by researchers and scientists, for example designing secure routing protocols and modifying algorithms for tackling the attacks against the network. Machine learning techniques are being used to predict and analyze the attack pattern and energy consumption of WSNs. This will ultimately assist in the possible detection and prevention of WSNs [52].

There are five layers of the WSNs, as mentioned Section 2.2.4. Protocol stack- or network stack-based attacks of WSNs could be characterized according to these five layers [53,54]. These are explained as follows.

### 2.3.3.1 Physical Layer Attacks and Countermeasures

Jamming Mechanisms: These are external active attacks wherein the perpetrator aims to make the WSNs indefinitely unavailable for the intended purpose by disrupting the system through some means; this is a case of DoS attack. It hampers by distorting the WSN signals during transmission, transmitting garbage signals to imitate real traffic, toggling the WSN nodes between unproductive modes for energy-efficient jamming, and jamming on command upon traffic detection. The attacker uses a high energy-based signal to the broadcasting network to disrupt the operation. This DoS attack can be categorized as constant (data packet gets corrupted during transmission), random (this method saves energy by alternating between sleep and active jamming), and reactive (provides jamming signal after detecting data transmission) attacks [55].

The spread-spectrum technique can be used to counter it. Though in the MAC layer, it can be solved by the admission control mechanism. The packet delivery ratio is used to detect all types of jamming signals. To detect jamming attacks, analyzing traffic history is very crucial. The effective use of algorithms applied over the transmission data could statistically analyze the traffic history.

Radio Interference: The attacker will continuously interrupt WSN signals through maliciously intended radio signals. The attacker produces a large amount of interference intermittently or continuously. If latency is introduced in revealing keys, implemented by symmetric-key algorithms, these attacks could be reduced. This is handled by delaying some time interval of disclosure of cryptographic key [56].

Tampering and Destruction: The WSN can be particularly vulnerable if the perpetrator can tangibly handle the nodes. It could allow sensitive data to be read and accessed from the nodes, including any encryption key that is in place. The attacker gets access to the physical nodes and extracts sensitive information (cryptographic key and other data) [57].

Nodes should have better physical security measures implemented to avoid these attacks. Self-destruction upon sensing unauthorized access could be initialized to protect the WSN from being compromised through a node. Effective self-resilient fault-tolerant protocols could also be adopted to help against these.

### 2.3.3.2 Data Link Layer Attacks and Countermeasures

Exhaustion: A malicious node requests continuous transmission over the channel to disrupt the MAC protocol. Thus, it creates starvation for the other nodes by draining the energy. If the perpetrator gains access to a node or can transmit to the WSN channel, they may endeavor to repeatedly communicate through the channel and thereby disallow transmission of legitimate data from other nodes through the channel as MAC would be disrupted.

This can be handled by limiting the rate of MAC admission control and time-division multiplexing. Admission to the MAC should be limited by rate limitation to avert excessive requests and wastage of resources in the WSN. Time-division multiplexing allows each node a particular time to communicate in the network and, as such, limits persistent exhaustion attempts by compromised nodes [58].

Collision: It is very much similar to exhaustion. It occurs when the data of two nodes transmit in the same frequency. After collision, the data packet becomes mismatched between the host and the client. So, corrupted data go to the receiving end, and hence, the change would be unacceptable on the destination node and result in loss of data. Error-correction can be used against this problem. Collisions caused by this attack can be averted by using error correction codes in the receiving ends to avoid data loss. It should be noted that the receiving end of the information should implement this method.

Unfairness: The performance of WSNs could be minutely affected by an attacker tampering with MAC properties to disrupt the process unfairly. This partial DoS attack hampers the throughput. To counter this problem, small frames can be used where every individual node can use the channel for a short duration.

Interrogation: A security threat is introduced when the attacker persistently abuses flow control signals to exploit the MAC protocol of a WSN. The attacker exploits the system’s “request to send/clear to send (RTS/CTS)”. An attacker continuously sends RTS messages to get the CTS from a targeted node. For example, unbarred RTS signals could ultimately return a CTS signal from any node of the WSN, making the entire WSN vulnerable [59]. It can be handled by putting a limit on the RTS message to node from the same identity. Antireplay mechanisms after detecting the attack and setting strong link-layer authentication can be an effective countermeasure of this type of attack.

Sybil Attack: This type of attack exists in the data link layer. All the data come to a single malicious node. Because of this, the aggregate node acts as many
