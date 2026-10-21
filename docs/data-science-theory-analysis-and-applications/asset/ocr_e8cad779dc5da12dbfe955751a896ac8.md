“membership vector.” The membership vector is an integral value assigned to each peer when the peer joins. Each peer creates links to other peers on multiple levels based on the membership vector. In SGs, queries are forwarded by higher level links to other peers when a single key and its assigned peer are searched. This is because higher level links can efficiently reach the searched key with less hops than the lower level links. In case of range queries that specify the beginning and end of keys to be searched, the queries are forwarded to the peer whose key is within the range or less than the end of the range. The number of hops to key search is represented to O(log n) when n is denoted as the number of peers. In addition, the average number of links on each peer is represented as log n.

# 5.3.2.2  Phase Differences

Currently, we have proposed a large-scale data collection schema for distributed TPBS [12]. In [12], we employ “CSF” that stores and merges multiple small size messages into a large message along a multihop tree structure on a structured overlay for TPBS, taking into account the delivery time constraints. This makes it possible to reduce the overhead of network process even when a large number of sensor data is published asynchronously. In addition, we have proposed a collection system considering phase differences [13]. In the proposed method, the phase difference of the source node Nᵢ is denoted as dᵢ (0 ≤ dᵢ < Cᵢ). In this case, the collection time is represented as Cᵢp + dᵢ (p = 0, 1, 2, …). Table 5.4 shows the time to collect data in the case of Figure 5.15, where the collection cycle of each source node is 1, 2, or 3. By considering phase differences like Table 5.4, the collection time is balanced within each collection cycle, and the probability of load concentration to the specific time or node is decreased. Each node sends sensor data at the time base on his collection cycle and phase difference, and other nodes relay the sensor data to the sink node. In this chapter, we call phase differences as “PS.” Figures 5.17 and 5.18 show an example of the data forwarding paths on SGs without and with PS, respectively.

# 5.3.3  EVALUATION

In this section, we describe the evaluation of the proposed SG-based method with PS by simulation.

**TABLE 5.4**

**An Example of the Collection Time Considering Phase Differences**

| Cycle | Phase Difference | Collect Time |
|---|---:|---|
| 1 | 0 | 0, 1, 2, 3, 4, … |
| 2 | 0 | 0, 2, 4, 6, 8, … |
|  | 1 | 1, 3, 5, 7, 9, … |
| 3 | 0 | 0, 3, 6, 9, 12, … |
|  | 1 | 1, 4, 7, 10, 13, … |
|  | 2 | 2, 5, 8, 11, 14, … |