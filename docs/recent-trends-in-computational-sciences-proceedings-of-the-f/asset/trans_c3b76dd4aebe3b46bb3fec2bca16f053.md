
[12] D. Kim and S. An PKC-Based DoS Attacks-Resistant Scheme in Wireless Sensor Networks, IEEE Sensors Journal, 16(8) (2016) 2217–2218. doi: 10.1109/JSEN.2016.2519539

[13] J. Wu, K. O, M. Dong, and C. Li, A Hierarchical Security Framework for Defending Against Sophisticated Attacks on Wireless Sensor Networks in Smart Cities, IEEE Access, 4 (2016) 416–424. doi: 10.1109/ACCESS.2016.2581338

[14] L. Shi, Q. Liu, J. Shao, and Y. Cheng, Distributed Localization in Wireless Sensor Networks Under Denial-of-Service Attacks, in IEEE Control Systems Letters, 5(2) (2021) 493–498. doi: 10.1109/LCSYS.2020.3003789

[15] Ghidshalyal, S Mishra A K. Gupta, et al. Analysis of Denial of Service (DoS) attacks in Wireless Sensor Networks[J], IJRET: International Journal of Research in Engineering and Technology, 3 (2023) 2319–2326.

[16] Debroy, S., Calyam, P., Nguyen, M., Neupane, R.L., Mukherjee, B., Eraralla, A.K. and Salah, K., 2020. Frequency-minimal Utility-maximal Moving Target Defense DDoS in SDN-based Systems. IEEE Transactions on Network and Service Management, 17(2), pp.890–903.

[17] Zhijun

[18] Albadani, A., 2021. Machine Learning Approach for Combating Distributed Denial of Service Attacks in Modern Networking Environments. IEEE Access, 9, pp.42236–42264.

[19] Nassif, A.B., Talib, M.A., Nasir, Q., Albadani, H., and Albab, F.D., 2021. Machine Learning for Cloud Security: A Systematic Review. IEEE Access.

# A novel method to improve the performance of mobile nodes using a proactive approach in military MANET's

Nayanashree

Department of Information and Communication Technology, Manipal Institute of Technology, Manipal Academy of Higher Education. Manipal, India

Padmanabhan Ramaswamy

EISHA Communications System Private Limited

S. Raghavendra & Ramyashree

Department of Information and Communication Technology, Manipal Institute of Technology, Manipal Academy of Higher Education, Manipal, India

ORCID ID: 0000-0003-2733-3916, 0000-0002-0237-2444

**ABSTRACT:** A Mobile Ad hoc network (MANETs) is a collection of self-configuring, multiphop networks. These networks are self-forming and self-healing, which makes deployment easier and reduces the need for centralized networks. Performance is one of the most important research issues that MANETs implemented in the military domain encountered. Maintaining a tactical network's low power consumption, high throughput, minimal latency, little routing overhead, and higher packet delivery ratios is the key difficulty. When compared to previous work, our suggested algorithm can improve some of the factors: throughput, energy consumption. In this paper, we introduce a proactive approach to improve the performance of ad hoc networks in areas like military. We propose a new routing algorithm named Actor-critic reinforcement algorithm for this purpose. Simulation results (based on NS3 version 2.6) showed that our protocol is very efficient. The simulation results show that our proposed protocol effectively to improve throughput, reduce bandwidth, save energy as well as improve packet delivery ratio at major nodes.

*Keywords:* MANETs, Actor-critic reinforcement algorithm, mobile ad hoc, major nodes and minor nodes

# 1 INTRODUCTION

Over the past decades, there has been a progressive shift from wired networks to wireless networks. Among the wireless networks currently in use, MANET is the most distinctive and significant application. The limited transmission range of MANET nodes makes it impossible for source and destination to directly communicate when they are outside of their transmission zones.

A mobile ad hoc network (MANETs) is an Internet made up of mobile nodes that is not by any infrastructure or base stations, routing policy is another name for a routing protocol. There are three categories for routing protocols. There are several different proactive, Reactive and hybrid routing methods can be used to create a safe and effective path from source to destination. In proactive routing systems, the source node establishes a path to the destination using predetermined network information. Routing protocols that are proactive are those based on table-driven routing. The sensor nodes update the routing path on a periodic basis, while routing protocols that are reactive are those whose routing paths are kept on demand by the network. As

![](img/a35f8e852e0ee65e528c95ad0821783b_255_0.png)

Figure 1. Battlefield communication scenarios using tactical MANETs.

opposed to reactive and reactive routing protocols, hybrid routing protocols combine their features. In a hybrid routing protocol, the source collects network data while simultaneously using preset data to construct a path to the destination. Routing, security, and quality of service (QoS) are the three main challenges in the MANETs that can be rectified in the future to increase communication's effectiveness and dependability. Zones are defined in hybrid routing protocols. A table-driven routing path is followed within each zone, and a demand-driven routing path is followed outside the zone.

There are numerous protocols developed to enhance MANET's network performance, however, the current protocol still needs to be improved. To enhance the performance at military nodes, Special Routing Protocol for Military MANET was developed. It was able to demonstrate improvement at significant nodes. The reactive algorithm Deep reinforcement learning is used to pick the cluster heads. Path traversal is done using the Special Routing Protocol for Military MANET method. Better bandwidth usage between the nodes is one the major goal.

Figure 1: Individual or company units must communicate with one another and battlefield status because they are dispersed over the battlefield. The main strategy and concept are what we want to concentrate on describing. We widely distinguish between two categories of network nodes: big nodes, such as commanders or operational equipment with a functional cluster, are referred to as Super-Peers (SP) or major nodes, and normal nodes, such as soldiers or military equipment, are referred to as Peers (P) or minor nodes. High throughput, interference avoidance, high packet delivery ratio, and node scalability are the major goals. Reliability maintenance using reactive routing technology.

The primary goals are to prevent flooding which causes packet loss, to offer high throughput, scalability, which allows any number of nodes to be added or deleted, and to assure reliability. There is a possibility of lowering energy consumption and reducing delay nodes.

# 2 LITERATURE SURVEY

Abid et al. [1] has demonstrated the viability of DRL approaches for cluster and data management via edge computing in IoT networks. The key goal is to choose the CH that can best allocate resources in a network to meet user service and SLA standards while considering the environment's nature. The suggested technique requires less convergence to train the network to behave optimally. In the IoT network's dynamic and load environment.

Shruti et al. [2], investigated various routing protocols to enhance MANET's power management and effectiveness. These protocols include three adaptive routing, global state routing, destination sequence distance vector routing, wireless routing, etc. Each of these procedures' key traits and operational specifics are explored. The outcomes of several protocols are compared and computed.

Vu Khanh et al. [3], Proposed a revolutionary technique to enhance mobile ad hoc network performance. The author distinguishes between major nodes and regular nodes.
