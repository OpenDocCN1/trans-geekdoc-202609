![](bbox=[0.15, 0.1, 0.9, 0.38])

FIGURE 14.4 PDR on Speed of 10m/s.

![](bbox=[0.15, 0.48, 0.9, 0.75])

FIGURE 14.5 PDR on Speed of 15m/s.

# 14.2.7.2 Packet Loss

The Packet Delivery Ratio versus various numbers of nodes at various speeds is depicted in Figures 14.6–14.8 based on the observations of Tables 14.2–14.4. DSDV loses packets at a higher rate than AODV: at 5 m/s, AODV loses 292 packets compared to DSDV’s 2880, at 10 m/s, AODV loses 84 packets compared to DSDV’s 2482, and at 15 m/s, AODV loses 248 packets compared to DSDV’s 2264. As network congestion grows and more packets are discarded due to collisions, loss decreased as the number of nodes increased.

# 14.2.7.3 End to End Delay

The average E2E Delay for various numbers of nodes operating at various speeds is depicted in Figures 14.9–14.11 based on findings from Tables 14.2–14.4. The average AODV delay is reduced at 10 nodes and reaches its maximum delay at 40 nodes. As node density increases, post-route setup calculation requirements decrease, requiring less time. Semi-fixed values are used in DSDV. In the simulation situations, it was observed that the DSDV routing protocol exhibits a lower end-to-end delay when compared with the AODV routing protocol. On average, the OADV was