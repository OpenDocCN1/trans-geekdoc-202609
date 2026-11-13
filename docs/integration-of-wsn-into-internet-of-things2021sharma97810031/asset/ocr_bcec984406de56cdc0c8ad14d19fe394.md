manager to establish a connection to the devices [39,40]. In source routing, the network manager puts into the packet all the necessary information for routing, but this can only be used for network diagnosis because if a node fails, the packet will be lost. Superframe routing is like graph routing, but the difference is the links can only be used to establish superframes. The proxy routing is a graph routing that is used by the device when they are put in a network. In the absence of security keys, the proxy routing will be used.

# ### 2.2.4.4 Data Link Layer

The data link layer performs several tasks related to the multiplexing of data. In the media access control (MAC) layer, there is a specific problem called _co-channel interference_. This problem is solved at this level using the MAC protocol. Error handling is included here. On the other hand, there is another issue in the physical layer named multipath fading and shadowing. This one is also fixed in this layer [41]. MAC protocols have some essential characteristics like scalability and stability. On the other hand, this protocol is not optimally developed for energy efficiency. In terms of energy, the protocol might not be feasible, but there are other different characteristics of the MAC protocol that are important for the WSN [42]. The design of MAC protocols has been dominated by scalability, stability, and fairness [43].

# ### 2.2.4.5 Physical Layer

This one is the first layer of the sensor network. After this layer, the device is connected to the physical world for data collection. In this layer, data encryption is used so that the intercepted data are not understandable for the attacker without the key. Career frequency is selected for the modulation so that the data can be sent to other nodes. The IEEE 802.15.4 standard is recommended at this layer. A summary of layer-specific recommended protocols is given in Table 2.3.

**TABLE 2.3**
**Summary of Layer-Specific Recommended Protocols [44,45]**

| Layer | Recommended Protocols |
| :--- | :--- |
| Physical layer | IEEE 802.15.4 |
| Datalink layer | MAC |
| Network layer | PEAS (probing environment and adaptive sleeping), GAF, SPAN, ASCENT, AFECA, CLD (controlled layer protocol), MTE (minimum transmission energy), LEACH (the low-energy adaptive clustering hierarchy) [46]
Minimum energy communication network (MECN) protocols [47]
Power-efficient gathering in sensor information systems (PEGASIS) [48]
sensor protocols for information via negotiation (SPIN) [49]
Cougar [50]
Directed diffusion [51]
Rumor routing and gradient-based routing (GBR) |
| Transport layer | Sensor transmission control protocol (STCP)
Price-oriented reliable transport protocol (PORT)
Pump slow fetch quick (PSFQ) |