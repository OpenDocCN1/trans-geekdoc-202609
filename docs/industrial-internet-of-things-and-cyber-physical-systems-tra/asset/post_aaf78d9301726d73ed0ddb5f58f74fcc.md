
# Semantic Analysis of Videos for Tags Prediction and Segmentation

Zhao, W. L., Wu, X., & Ngo, C. W. (2010). On the annotation of web videos by efficient near-duplicate search. *IEEE Transactions on Multimedia*, 12(5), 448–461. doi:10.1109/TMM.2010.2050651

Zhao, Y., Wang, T., Wang, P., Hu, W., Du, Y., Zhang, Y., & Xu, G. (2007). Scene segmentation and categorization using neutis. In *IEEE Conference on Computer Vision and Pattern Recognition* (pp. 1-7). IEEE.

Zhou, Y., Sun, X., Liu, D., Zha, Z., & Zeng, W. (2017). Adaptive pooling in multi-instance learning for web video annotation. In *Proceedings of the IEEE International Conference on Computer Vision Workshops* (pp. 318-327). IEEE.

# Chapter 15

## ACO–Based Algorithms in Wireless Sensor Networks

**Renu Jangra**  
*Kurukshetra University, India*

**Ramesh Kait**  
*Kurukshetra University, India*

**Sarvesh Kumar**  
![ORCID](https://orcid.org/0000-0001-9459-1312)  
*Poornima University, Jaipur, India*

### ABSTRACT

Wireless sensor networks (WSN) offer great expertise that club the sensing, execution, communication, and network technology along with microelectronics and micro-mechanical devices together to study the environment. It is a new concept and a consequence of few steps in the communication field. If the original prospect of this new network works according to the planned concept, it will recover the examining and control systems used these days in the environment for consumer, medical, industries, and military sectors. The wireless technology gives the advantage of decrease in cost that cabling operation has in recent systems and also makes it possible to perform measurements in unreachable places. Many applications can work on the concept of this technology.

### INTRODUCTION

Batteries are used to generate current in the nodes. But, the batteries are discharge in fast manners which humiliate the network lifetime. Repeatedly usage of battery power corrupts the normal working of the whole network. The taxonomy of routing protocols in WSN is based on (a) style of functioning of nodes (b) the way of nodes participated in the network (c) the network structure. Therefore, the routing protocol is separated into hierarchical, data centric and location based on the foundation of the network structure. The energy efficient routing is based on the hierarchical structure. Many more algorithms also come under this group. Till now, there are so many power efficient algorithms are executed by the researchers. These are LEACH, PEGASIS, TEEEN, APTEEN, HPAR etc to get well from the energy issue. LEACH (Low Energy Adaptive Clustering Hierarchy) is one of them. The base of routing protocols is different format such as clustering, chaining, cost based etc. The immense quantity of nodes present in wireless sensor network is sometimes tricky to handle. So, the best way is to combine some nodes and make a cluster. Making a cluster is a technique called clustering; which puts a limit on the energy usage by the sensor nodes. The communication and management of nodes in the cluster is handled with the aid of the cluster head. The choice of cluster head among cluster nodes is done by the probability rule which is based on ACO. The cluster nodes send data to the cluster head who further send related information to the base station. ACO-DEEC (Ant Colony Optimization based Distributed Energy Efficient Clustering protocol) calculates the probability rule to select the cluster head that based on the parameters: distance and power of the nodes. This algorithm improves the energy usage, number of packets sent to the base station, dead nodes when evaluated with the existing protocol DEEC.

### LEACH Protocol

LEACH protocol is based on the hierarchical topology that further belongs to the hierarchical network. The author (Heinzelman, 2002) has projected that a cluster always made up of more than two nodes and its size changes with the range of the network. For proper utilization of power in the network, among all the nodes present in the cluster, one is elected as cluster head based on round robin fashion. Every node catches the opportunity to become a cluster head. LEACH is a self-organizing network work as a protocol which uses the arbitrary allotment of energy between the nodes. The crowded network made up of thousands of nodes that have been separated into the cluster having the same size. The node considered as cluster head has been divided as coordinate nodes, cluster member, and normal nodes. LEACH uses TDMA schedule for assignment of energy to nodes. If one node becomes the cluster head (CH) constantly, its energy starts to drain. To overcome this state, other nodes also catch the possibility to become the cluster head after some round or after a particular time. All the nodes present in the cluster, forward their information to the cluster head and the CH collects all the data from its entire member nodes. At last, cluster head, gathers the data and pass this data to the base station for further process (Liao, 2013). The operation of LEACH is split into two phases: a) Setup Phase b) Steady State.

- **Setup phase:** In the setup phase, all the sensor nodes available in the network are scattered into different clusters and one cluster head is selected arbitrarily from each cluster. In a cluster, sensor nodes opt a random number between 0 and 1. The selected random number is then compared with the threshold value $T(n)$, given in equation 1. If the opted value is less than the threshold (opted value < $T(n)$ value, then that node is considered as a cluster head or else that node remains as a cluster member. A message as knowledge is promoted by the cluster head once a node is selected as a cluster head.

$$
T(n) = \begin{cases} 
\frac{p}{1 - p \times (r \mod 1/p)} & \text{if } n \in G \\
0 & \text{otherwise}
\end{cases} \tag{1}
$$

Where $G$ is the grouping of that node which is not elected as CH in the last $1/p$ round; $p$ is the probability for cluster head and $n$ is the node and $r$ is a current round of the process. LEACH protocol is related with rounds so after the execution of every cycle or after $1/p$ rounds, the nodes are qualified to participate in the selection process of the cluster head. As a result, each node gets the same opportunity to become a cluster head.

- **Steady State Phase:** Once the cluster is formed in the first setup phase, based on Time Division Multiple Access (TDMA) schedule, cluster head is allocated to all the member nodes of the cluster. On the basis of this schedule, the nodes send their related data to their particular CH. After receiving the data from nodes, CH calculates the sum of its own data and data received from other nodes. Then, it transmits this aggregated value to the base station (Khediri, 2014). The time taken by the steady state phase is higher than the setup phase. After every round, the new CHs are selected and the timeline operation composed of the steady-state phase and setup phase is applicable.

### Energy Model

Primarily, the transmission model used to be a radio model that had been separated into two parts based on the transferring and receiving distance of the nodes that is a free space model and multipath fading model. There is an assumption in the free space propagation model that the transmitter and receiver antenna are positioned in an empty environment where absorbing obstacles and reflecting surfaces are not considered. But, in multipath the propagation model, obstacles and reflectors take into consideration. Therefore, the received signals have a set of reflections and/or direct wave each having its own degree of attenuation and delay. The formula for path loss is given by distance$^n$. The value of $n$ ranges from about 2 (in corridors) to 6 (for cluttered and obstructed paths). The wireless communications mostly simulated through the use of the free space propagation model.

![](img/79c91453a1cae0bf517f11c1c534feeb_336_0.png)

This model works on a straightforward hypothesis that the received signal power inversely proportional to the distance between the transmitter (TX) and the receiver (RX). The communication medium is supposed as symmetric by the protocol. The energy consumed in transferring ‘k’ bits from one node to another at a distance $d$ had been illustrated as
