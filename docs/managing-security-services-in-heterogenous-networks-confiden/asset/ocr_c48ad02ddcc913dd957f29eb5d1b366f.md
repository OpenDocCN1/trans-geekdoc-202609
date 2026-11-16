Node is HIGH & Eligible to participate in the routing process and act as CH.

2.4.2.7 Energy Model In this work, the energy model used is similar to the works presented in [24] and [25]. The transmission energy is needed for an 1-bit message more than a distance d as per the following (1)

![](bbox=[0.28, 0.24, 0.85, 0.3])

where $d_0 = \sqrt{\epsilon_{fs}/\epsilon_{mp}}$

The reception energy required for an 1-bit message is given in equation (7).

![](bbox=[0.42, 0.39, 0.85, 0.42])

where E_{elec} – electronic energy 
\epsilon_{fs} – amplifier energy in free space and 
\epsilon_{mp} – amplifier energy in multipath.

2.4.2.8 Cluster-Based Routing Algorithm In this section, a new cluster-based secure routing algorithm called IWFCSRA has been developed for effective routing in this work. The steps of the proposed algorithm are as follows:

+   STEP 1: Let DTS = 0, IDTS = 0;
+   STEP 2: Each node communicates with neighbor nodes to know the DTS at particular time interval.
+   STEP 3: Source node broadcasts requests to its neighboring nodes. The simulation timer is started.
+   STEP 4: All nodes receive the request from their neighbors and check whether it is the right destination or not. If it is, an acknowledgement is sent to its neighboring nodes.

+   STEP 5: Calculate the DTS for all the nodes using the formula
+   DTS (t1, t2) = PS (t1, t2)/ACKR (t1, t2)

+   STEP 6: Calculate the AvgDTS for the network using the formula
+   AvgDTS (t1, t2) = Sum (DTS<t1, t2>)/n