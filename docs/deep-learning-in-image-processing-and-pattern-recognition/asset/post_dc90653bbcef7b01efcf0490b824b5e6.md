
In this process, the node selects the node set with the highest residual energy during each hop, ensuring the user's expected reliable value for data transmission. Therefore, while improving the reliability of data transmission, the improved algorithm balances the use of energy and the residual amount in the network, prolonging the usage time of the network.

The traditional ReInForM routing algorithm does not analyze and compare the residual energy of the next hop node, resulting in poor overall transmission reliability and unbalanced network energy consumption. The improved algorithm not only improves the data coding and ensures the integrity of data transmission but also analyzes and compares the energy consumption of nodes in the path and the next hop, reducing the number of failed nodes and extending the life cycle of the network.

![](img/e4200cc4308edaf8913e513b0f96dbb6_354_0.png)

Figure 3. Selection of remaining energy nodes.

## 3. E-ReInForMIF Algorithm Steps

### 3.1. E-ReInForMIF Algorithm Flow

This research combines an EC fault-tolerant machine with node residual energy sorting and selection to propose a new routing algorithm, namely the E-ReInForMIF algorithm. The overall process for the E-ReInForMIF algorithm is shown in Figure 4.

![](img/e4200cc4308edaf8913e513b0f96dbb6_355_0.png)

### 3.2. Specific Steps of the E-ReInForMIF Algorithm

- (1) The sink node broadcasts the updated content selected by the entire path node to each other node periodically. Each node adjusts its hop count based on the received message and broadcasts the message to other neighboring nodes. In the path, each node knows the jump to the sink node by itself and its surrounding nodes;
- (2) The sending node processes the bm byte data packets, arranges them into M data slices of b bytes, and encodes them;
- (3) Calculate the transmission path: according to the source node data reliability parameter $r_s$, channel error rate $e_s$, and hop count $h_s$, use the following formula:

$$P(r_s, e_s, h_s) = \frac{\log(1-r_s)}{\log\big[1-(1-e_s)^{h_s}\big]} \quad (3)$$

Prepare for reliable data transmission through calculation and analysis;
- (4) Compare the energy consumption of each neighbor node transmitting data packets with the energy consumption of the source node to the sink node hop. According to the comparison between the former and the latter, they are classified into three categories: less than 1, the same, and more than 1. The corresponding combinations are $H^{-}$, $H^{\underline{\sigma}}$, and $H^{*}$. The incremental ordering of each aggregation node is determined by the calculation $C_{N,N'}$ of each node in the transmission path;
- (5) Select the next hop node from three sets according to the data transmission energy consumption requirements. The source node first selects the next hop node at $H^{-}$. If $1 - e_{s}$ is smaller than the calculated number of paths, additional paths need to be added when the source node transmits data. The additional number of paths is:

$$P = \frac{\log(1 - \tau_{s})}{\log[1 - (1 - e_{s})^{h_{s}}]} - (1 - e_{s}) \tag{4}$$

After the number of redundant paths is determined, select nodes in the order of $H^{-}$, $H^{\underline{\sigma}}$, and $H^{*}$ according to the three node sets sorted out previously. When P is greater than the number of nodes included in $H^{-}$, select nodes from $H^{\underline{\sigma}}$ and $H^{*}$ in turn until the selected number of paths meets the calculated probability value. If the required number cannot be reached, select again from the node set $H^{-}$ and continue to cycle this operation until the selected number of paths meets the probability requirements. Each selected node continues to create its path number and is added to the additional path number. The calculated total external path number is the total external path number created by all selected nodes. Finally, the node transmits the created path to each rally, and then transmits the residual energy value of the node, as well as the encoded data slice, to all neighboring nodes through the created path;
- (6) After receiving the data slice, the neighbor node decodes the data; the entire encoding and decoding process is performed using a system encoding method;
- (7) At this point, consider the neighbor node as the source node, calculate the number of new transmission paths again, and cycle through the previous operations until the data is transmitted to the sink node.

In the E-ReInForMIF algorithm, the nodes provide the number of data packets lost during transmission. Considering the reliability of the number of paths created, energy surplus and transmission energy consumption of the next hop nodes are analyzed to improve the overall reliability of network data transmission.

## 4. Experimental Simulation Result

The E-ReInForMIF algorithm takes the number of data packets received by the destination node and the integrity of the received data packets as measurement results, namely, the packet reception rate and accuracy. The higher the reception rate, the smaller the data packet loss rate in transmission. The greater the accuracy, the more complete the data received. The higher the data packet reception rate and accuracy, the higher the reliability of data transmission. This article compares the improved algorithm with three algorithms, which are:

Method 1: Based on the RelInForM algorithm, the data is directly allocated to the transmission path without considering the energy balance of the path nodes;

Method 2: Based on the RelInForM algorithm, distribute source data packets evenly into the transmission path without considering packet coding;

Method 3: Based on the RelInForM algorithm, add FEC coding to provide a certain fault tolerance rate.

The experiment was conducted on MATLAB 2016b; the network structure of this experiment adopts a multi-path structure, with a network coverage area of $600 \mathrm{~m} \times 600 \mathrm{~m}$ that is monitored in real-time. During the entire simulation run of 1000–2000 times, the data packet reception rate and accuracy rate of the above three algorithms were compared with those of the proposed algorithm in this article. It is proved that the proposed algorithm is the best of the four algorithms. The relevant parameters of the wireless sensor network and the performance indicators of the nodes are shown in Table 2.

**Table 2.** WSNs-related parameter settings.

| Parameter Type | Parameter Value |
| :--- | :--- |
| Number of network nodes | 100 |
| Node initial energy | 9900 J |
| Node residual energy | 9700 J |
| Transmitter amplifier energy consumption ($E_{amp}$) | 500 pJ/bit/m$^2$ |
| Destination node energy consumption ($E_{fuse}$) | 8 J |
| Radio energy consumption ($E_{elec}$) | 250 nJ/bit |
| Forwarding each data packet energy consumption | 2 J |
| Node maximum transmission distance | 100 m |
| Data packet length | 128 B |
| Control packet length | 64 bit |
| Expected reliability | 0.9 |
| Channel error rate | 0.4 |

When the network runs from 1000 to 1300 times, the data packet reception rate of the four algorithms is 1. For 1300–2000 runs, the packet reception rate of Method 3 and the proposed algorithm are still above 0.97, which has obvious advantages. For 1600–1800 runs, the data packet reception rate of the proposed algorithm in this article is slightly lower than that of Method 3 but still higher than Method 1 and Method 2. For 1800–2000 runs, the proposed algorithm is again higher than the other algorithms and remains above 0.98, as shown in Figure 5.

![](img/e4200cc4308edaf8913e513b0f96dbb6_357_0.png)

As can be seen from Figure 5, the greater the number of network operations, the clearer the difference in data packet reception rates among various algorithms. The Figure 6 simulation increases the network operation energy consumption by five times. Method 1 and Method 2 decrease rapidly and the overall data packet reception rate is not high. The difference between Method 3 and the proposed algorithm is not significant, and both have high data packet reception rates. When the network runs 1200–1600 times, the data packet reception rate of Method 3 and the proposed algorithm is almost the same. It can be seen that when the network runs 2000 times, the packet reception rates of Method 3 and the proposed algorithm
