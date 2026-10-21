
## AI-Based Manufacturing, Engineering and the Internet of Things

Wang, Z. H., Liu, Y. M., Gong, D. Y., & Zhang, D. H. (2018). A new predictive model for strip crown in hot rolling by using the hybrid AMPSO-SVR-based approach. Steel Research International, 89(7), 1800003. https://doi.org/10.1002/srin.201800003

Xiao, D., Huang, Y., Zhang, X., Shi, H., Liu, C., & Li, Y. (2018, October). Fault diagnosis of asynchronous motors based on LSTM neural network. In 2018 Prognostics and System Health Management Conference (PHM-Chongqing) (pp. 540–545). IEEE. https://doi.org/10.1109/PHM-Chongqing.2018.00098

![](img/3d190e19625a7567e7b93c8e95b18d9c_222_0.png)

FIGURE 14.1 A mobile ad hoc network.

### 14.2 MANET ROUTING PROTOCOLS

The ad hoc routing protocol’s job is to regulate node choices made when sending packets between devices in MANET (Bhambri et al., 2023; Anchugam & Thangadurai, 2015). A node has no knowledge of the network topology when it joins or attempts to join. It learns the topology by proclaiming its presence or receiving signals from nearby nodes. The implementation of the routing protocol affects the route discovery process in a network. Every time an envelope must be sent to a destination reached by several nodes, the Routing Protocol is also required (Bhambri et al., 2022; Ibrahim et al., 2022). Because nodes in mobile ad hoc networks might move unpredictably, joining or leaving the network, the routing methods for wired networks cannot be employed. This implies that a path that is ideal at one point in time might not be appropriate at another.

#### 14.2.1 AODV Routing Protocol

The ad hoc on-demand distance vector (AODV) routing protocol routes are only known to the station as the next hop and destination pair; they are established as needed in the routing database of AODV.

#### 14.2.2 DESTINATION SEQUENCED DISTANCE VECTOR PROTOCOL (DSDV)

The DSDV routing protocol has been enhanced to overcome the count to infinity problem. Every node keeps a routing table with entries for each additional node in the network. Each node keeps track of the shortest hops required to send a packet to its destination via its neighbours, and it selects that neighbour as the subsequent node (Quy et al., 2018). It is a proactive protocol; therefore any time the topology changes or at regular intervals, the nodes send their routing tables to their close neighbours (Ritu & Bhambri, 2022). The sequence number of a node must be increased when sending an update message (Quy et al. 2019a). A broadcast message can be received by a node at any time from its locality. It contrasts the fields for the sequence number and hop count of the incoming message in its routing table with the relevant entry (Mahmoud et al., 2015). The node changes its routing database with distances being recalculated using the updated sequence number and hop count if there is a discrepancy between the two. In response to Route ERRor (RERR) warnings, DSDV invalidates all routes that include broken links in their routing database. These routes receive an unlimited metric and an increased sequence number right away (Jamal et al., 2022).

#### 14.2.3 COMPARISON BETWEEN AODV AND DSDV PROTOCOLS

The AODV and DSDV routing protocols differ in a few ways. Firstly, unlike DSDV, AODV only updates routing information when it is necessary to do so. It does not routinely update the routing data. By contrast, DSDV will upgrade the nodes’ routing table on every occasion. Every node frequently shifts positions. There is no recurrent updating in AODV. There is no cycle topology in DSDV; instead, routing information propagates continuously. DSDV has a significantly lower packet delivery latency than on-demand protocols. When compared to table-driven protocols, AODV has a higher first-packet delivery time. There is a route to every other neighbour node in DSDV that is not present in AODV.

#### 14.2.4 SIMULATION ENVIRONMENT

NS-2 is free, open source, and supports a variety of networks, including wired networks, wireless ad hoc modes, and managed wireless modes. NS-2 is used for simulation. Additionally, NS-2 is more realistic than other simulators due to its vast model library, effective simulation design, and its ability to produce good results (Bhambri et al., 2021). It is an object-oriented tool command language and C++ discrete event simulator. It is appropriate for evaluating various protocols, traffics, and creating new protocols. Both the NS-wireless and Excel applications visually represent the performance indicators by monitoring the movements and occurrences of the nodes inside the simulated network. The NS-2 software also provides a visual depiction of the network, shown in Figure 14.2.

![](img/3d190e19625a7567e7b93c8e95b18d9c_223_0.png)

FIGURE 14.2 Architecture of NS-2.

#### 14.2.5 PERFORMANCE METRICS

Packet delivery ratio, packet loss, throughput, and average end-to-end delay were all factors taken into account in the development of this model (E2E).

##### 14.2.5.1 Packet Delivery Ratio (PDR)

The PDR is the percentage of datagram created by CBR sources that were successfully delivered to the locations they were intended for. The service quality of the routing protocol is improved by a higher delivery ratio. The calculation of the Packet Delivery Ratio is shown in Equation (14.1)

Packet Delivery Ratio = Received packets / Sent packets ×100 (14.1)

##### 14.2.5.2 Packet Loss

The MAC layer, as well as the network layer, may experience mobility-related packet loss (Ritu and Bhambri, 2023). Here, network layer packet loss is the main focus. When a packet reaches the network layer and a viable path to the receiver is identified. In the absence of a route, the packet is buffered. When a packet needs to be buffered but the buffer is already full, the packet is dropped. It can also be dropped when the buffer time is too long. Packet loss is determined as shown in Equation (14.2):

PER = Total Packet Sent – Total Packet received (14.2)

##### 14.2.5.3 Average End to End delay

It comprises retransmission delays at the MAC, interface queue queuing, and data packet buffering during route discovery (Sangwan et al., 2021). It is the interval of time between the source node’s packet sending and the destination node’s packet receiver.

##### 14.2.5.4 Throughput

The ratio of total data sent from a transmitter to a receiver is known as throughput (Ritu and Bhambri, 2022). The throughput measures how quickly the most recent communication is delivered to the recipient. Bits per second, or bytes (byte/sec or bit/sec), are used to measure throughput. In every network, a high throughput is the only option.

#### 14.2.6 SIMULATION PARAMETER

TABLE 14.1 Simulation Parameter

| Parameter | Value |
| --- | --- |
| Number of nodes | 15, 25, 35, 45, 55 |
| Simulated Period | 55s |
| Internet Size | 500 m × 500 m |
| Size of a Packet | 55 bytes |
| Vitality of Nodes | 1000 J |
| Simulator | NS-2 |
| Antenna Type | Omni directional |
| MAC Type | IEEE802.11 |
| Agent | TCP |
| Routing Protocol | AODV & DSDV |

#### 14.2.7 SIMULATION RESULTS

In this concept, a rectangular region of 500*500 unit squares has a number of randomly distributed networks. Awk was used to manage the trace files generated by the simulations of the AODV and DSDV protocols. Packet delivery ratio, throughput, packet loss, and end-to-end delay values were plotted on graphs. These values were found in Tables 14.2–14.4.

##### 14.2.7.1 Packet Delivery Ratio

Figures 14.3–14.5 display the Packet Delivery Ratio for various numbers of nodes operating at various speeds based on the findings in Tables 14.2–14.4. At 5 m/s,

TABLE 14.2 Speed of 5 m/s

| # Nodes | PDR[%] AODV | PDR[%] DSDV | Packet loss AODV | Packet loss DSDV | E2E [ms] AODV | E2E [ms] DSDV | Throughput [kbps] AODV | Throughput [kbps] DSDV |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 15 | 100 | 5.66 | 0 | 3082 | 6.13 | 4.13 | 544.11 | 30.81 |
| 25 | 98.71 | 28.5 | 42 | 2336 | 20.39 | 4.02 | 537.13 | 155.06 |
| 35 | 90.85 | 2.75 | 299 | 3177 | 25.19 | 4.13 | 494 | 28.2 |
| 45 | 69.12 | 34.04 | 1009 | 2155 | 55.58 | 4.16 | 376.06 | 185.21 |
| 55 | 98.04 | 3.49 | 64 | 3153 | 34.33 | 4.16 | 533.44 | 37.72 |
