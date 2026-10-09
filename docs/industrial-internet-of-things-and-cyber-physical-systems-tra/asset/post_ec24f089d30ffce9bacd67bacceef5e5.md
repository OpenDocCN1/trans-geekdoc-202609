
probability function as well as the parameters that are the power of the node and the length between the node and a base station. It is considered that a large path between nodes will be having more energy and vice versa. The steps followed by the ants in the ACO-DEEC are: Ants selects the next cluster head using the start rule and select optimal one using revise rule.

- **Start Rule:** Let an ant is positioned on the cluster head node ‘i’ and choose next cluster head node ‘j’ using equations (1) and (2).

$$P = \frac{Distance_{i} * \alpha + Phero_{i} * \beta}{\sum_{i=0}^{N_{i}} \big( Distance_{i} * \alpha + Phero_{i} * \beta \big)} \tag{1}$$

where P = The probability function to select a cluster head among the nodes.

Phero$_{i}$ = Value of the pheromone.

$$Phero_{i} = \frac{\tau_{i,j}^{\alpha} * \eta_{i}^{\beta}}{\sum_{i=0}^{N_{i}} \tau_{i,j}^{\alpha} * \eta_{i}^{\beta}} \tag{2}$$

where, $\tau^{ij}$ is the intensity of the pheromone, $\alpha$ and $\beta$ are the controlling parameters, $\eta_{i}$ is the heuristic information.

$$\eta_{i} = \frac{1}{I_{e} - e} \tag{3}$$

where, $I_e - e$ = Original energy of the node.

e = Actual energy of the node.

If any node has less power, then it has less chance to select as a CH.

- **Revise Rule:** When an ant search the next CH then the value of pheromone on that node is updated according to equation (4).

$$\tau_{i,j} \big( t + 1 \big) = \big( 1 - \rho \big) \tau_{i,j} \big( t \big) + \rho \Delta \tau_{i,j} \big( t \big) \tag{4}$$

where $\Delta \tau_{i,j} \big( t \big)$ is the update in pheromone and $\rho$ is used to stop the creation of extra pheromone.

## Proposed Algorithm (ACO-DEEC)

1. Create the network and initialize the initial probability ($\rho$), number of nodes (n), number of rounds r max, Initial energy $E_o$, $\rho$, $E_{fs}$, $E_{amp}$, $E_{Tx}$ and $E_{bx}$.
2. Compute the standard (average) energy of the network.
3. Calculate the probability function of each node by taking into account the power of the node and the length of the node from the Base station.
4. Probability function is calculated using formula.

   $P = \frac{Distance_i * \alpha + Phero_i * \beta}{\sum_{i=0}^{N_i}(Distance_i * \alpha + Phero_i * \beta)}$

   $Phero_i = \frac{\tau_{ij}^\alpha * \eta_{ij}^\beta}{\sum_{i=0}^{N_i}\tau_{ij}^\alpha * \eta_{ij}^\beta}$

   $\eta_{ij} = \frac{1}{I - e}$

5. If a node is CH in the previous round, then the node is a part of group G wherever G is a set of those nodes which are qualified to turn into a CH and that node, choose an unsystematic number between zero and one else node become a cluster member node and transfer data to the relevant CH.
6. If the chosen unsystematic number is less than the threshold function, then that node is a CH else node is a cluster member and sends data to the relevant CH.
7. Calculate the energy left, dead nodes and packets received to the base station for the nodes.

# SUMMARY

The Wireless Sensor Network is a network used to make an analysis of surroundings such as temperature, pressure, motion and so on by the help of its base station and thousands of sensor nodes that are deployed in the surrounding. The communication among sensor nodes taken place via a base station and wireless radios. The entity that does the job of sensing is named as a sensor. These sensors are competent in translating objects, things into signals that are effortlessly being analyzed and planned. The dimension, physical safety, power, memory storage, unpredictable communications, low expenses, energy efficient is the unique properties of a wireless sensor network. Beyond all these properties, there are numerous issues regarding the deployment of nodes, power consumption, heterogeneity, topology, reliability and scalability, a medium of transmission, etc. that have been faced by the wireless sensor network.

Among the above challenges, the issue of management of power is the main concern. For the smooth working of the wireless sensor network, it is necessary that power should be stable throughout the network. Batteries are used to generate current in the nodes. But, the batteries are discharged in fast manners which humiliate the network lifetime. Repeated usage of battery power corrupts the normal working of the whole network. By enhancing the cluster head probability selection formula and using the ACO approach in the selection of the optimal path between the cluster head and the base station, MALP handles the proper energy utilization, better execution time and increment in the lifespan of the network.

The outline of diverse basic ant colony algorithms explained and it can also be used in getting the solution of upcoming investigating problems. ACO excellently works in the area of the metaheuristic optimization problem to provide better solutions. The main major concern in a wireless sensor network is better energy utilization in the sensor node by making it more efficient using the proposed algorithm MALP. By enhancing the cluster head probability selection formula and using the ACO approach in the selection of the optimal path between the cluster head and the base station, MALP handles the proper energy utilization, better execution time and increment in the lifespan of the network. Hence, the overall performance of MALP is better than the existing LEACH. The main goal of LEACH is to improve the network lifetime and saves the energy consumption of nodes.

Clustering has been used in WSN routing protocol for saving the energy of the sensor nodes. The energy-based routing protocols DEEC and ACO-DEEC divide the large network into clusters. Wireless Sensor network is the fastest growing technology in the field of research. As with any other area, it also requires good security as its infrastructure is established in the inaccessible environment and it does the critical task of sensing, collecting, tracking, and processing of data. The research on WSN security is making progress at a remarkable speed. There is not any complete document that catalogs the security concern and the risk models which create exclusive threats to the wireless sensor networks. The establishment of the whole setup is only fruitful if there is a secure communication happened with it. So, the security of the network is required for the secure and correct delivery of data. Attackers are always ready either to steal the data or corrupt it for their own use. So, need security as these networks are constructed for isolated observation. An illegal change in the sensed data may lead to incorrect information to be reached at the judgment creator. It is a big deal to provide security to WSN as its infrastructure is set up in a remote place. As the literature studied, there are many security protocols designed to provide security in WSN. We also work on the same concern and designed a security protocol. We apply the cryptography algorithms AES and RSA as a security measure on our proposed algorithm ACO-DEEC and they named as AES ACO-DEEC and RSA ACO-DEEC. Also, compare both algorithms based on different parameters. The AES ACO-DEEC works better in most cases than RSA ACO-DEEC. In this thesis, the proposed algorithms provide energy-efficient, secure and good routing protocol.

## Result Analysis

In our objective, we proposed the algorithm that wastes less energy, superior routing path and having good quality safety procedures with the aid of ACO algorithms and its variation, special tools, etc. that can facilitate the researchers to carry out their assignment or research. The analysis of basic ACO on TSP Problem shows that the best possible solution for the proposed algorithm results on the values provided in the parameters. The three alternatives of ACO is also discussed named as AS, ACS, and MMAS. We can explore and evaluate the variants of ACO on the basis of heterogeneous parameters setting. Analysis

# ACO-Based Algorithms in Wireless Sensor Networks

![](img/79c91453a1cae0bf517f11c1c534feeb_344_0.png)

![](img/79c91453a1cae0bf517f11c1c534feeb_344_1.png)

shows that the algorithm's behavior varied with the behavior of factors like a count of ants, a factor that makes a decision of controlling the concentration of pheromone on the path, pheromone controlling parameter ($\alpha$), visibility deciding parameter ($\beta$), pheromone handling parameter ($\rho$) and iterations. In our experimental analysis, the conclusion is that the ant colony system performs superior among the three (AS, ACS, and MMAS) in comparison to other algorithms in the following manner. When there is an increase in the count of ants and iterations, then the expenditure of a path covered by ants and used time is less in case of ACS. The algorithm ACS is also working fine respective to the length of the path visited by the ants when manipulating besides a grouping of $\alpha$ and $\beta$ parameters. When parameters values are initialized as $\alpha = 1$; $\beta = 1$; $\rho = 0.05$; Q = 1; m (number of ants) = 40, then on increasing the number of iterations, at start of execution cost changes but after 100 iterations onward cost is unchanged and minimum. With increasing the number of ants, the cost goes down and after m=50 onward it remains constant. Our experimental analysis shows that at m=50, the best possible solution is generated in terms of cost and length of the tour. The selection of the values of $\alpha$; $\beta$, m and $\rho$ are opting on the
