in reducing the number of sensors which in turn reduces the cost and weight of the system. In addition, to increase the deployed WN's lifetime, energy efficient routing protocols should be designed. Hence, in this process, both sensor node location and energy optimization techniques are explored in detail.

# 14.1.6 PROBLEM STATEMENT

WSN is widely used for SHM applications to detect mild cracks which when unattended may result in huge damage to human lives and the economy.

Normally WNs are deployed randomly to monitor a specified environment. This random deployment method is inappropriate, as a higher number of WNs are needed to monitor the entire structure which, in turn, increases the cost and weight of the monitoring system. So, to reduce the number of WNs, information-rich locations in the structure should be identified to deploy WNs only in these locations.

The WNs are deployed on each floor of a nine storey building. The height of each floor is assumed to be 3.33 m. Considering the distance between each floor, a WN is deployed at each floor. This in turn helps to get accurate information about each floor. Instead of placing nine WNs, one on each floor, the entire structure can be monitored with six or seven WNs by deploying WNs only at the information-rich locations. Concrete floors in between each floor may have impact on the wireless transmission and the design of network topology. However such limitations are not considered in this thesis. In the future, while deploying the WSN in real world with the necessary hardware, these limitations should be considered.

Fisher Information Matrix (FIM) is used as an evaluation metric to identify the information-rich locations in the structure. Only the locations which have higher information quality are chosen with the help of FIM out of all the available locations in the structure.

There are many algorithms available in the literature like SPEM and GA, which use the FIM matrix to find the optimal information-rich sensor locations. But they typically select the optimal sensor locations consuming more time or with low information quality. So, in this thesis, an attempt is made to design an efficient algorithm HIOGA which can find these optimal sensor locations quickly with higher information quality. Once, these optimal sensor locations are found the WNs are deployed in these locations alone and not in a random fashion.

# 14.1.6.1 Case Study I

The objective here is to select only six or seven optimal WNs among the available WNs to monitor a 9-storey building. If it is possible to monitor the entire structure with the required information quality even with seven WNs, it will be efficient in terms of both cost and weight. Hence a new HIOGA algorithm is proposed to find out this optimal number of WNs.

These WNs require some energy to transmit the information available to the sink node. If the information transmission occurs repeatedly, the WNs deployed in these optimal information-rich locations soon die away, as they are battery operated.

So, there is a need to design an energy efficient algorithm which considers remaining energy available in a WN, energy arrival rate, the energy consumed by