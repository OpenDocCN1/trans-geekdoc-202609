
The distribution of the bandwidth is done among several stations, depending upon the time within `TDMA`. While sending the data, the allocation of time is done by every single station, and the respective data is transmitted by every station within the time slot allocated. The commencement of the respective slot, in addition to the slot location, should be known by every single station. The synchronization among various stations is required by `TDMA`.

### [1.3.4 FDMA](#ch01.xhtml#c_sec1_003_004)

Several frequency bands are obtained by dividing the available bandwidth within `FDMA`. The data is sent by allocating a band by every station where the reservation of the band is done for the entire duration. Smaller bands of the remaining frequency are used to separate the frequency bands of various stations. The loads out of various low-bandwidth channels are combined by `FDMA` and are transmitted with the help of a channel with high bandwidth.

![](Images/inline1_1.jpg)

## [1.4 Results and Discussion](#ch01.xhtml#c_sec1_4)

`Network Simulator-2` is used to implement this method using the simulation patch files. The experimental verification is performed by using `NS-2`. An open-source option, as well as working at packet level, is provided by an open network simulation program. The users have executable commands that use the input argument named as `Tcl` scripting language. The name of the `Tcl` script is fed as the input argument of `NS-2` executable command of `NS` by the users. The creation of the simulation trace file is most of the circumstances.

The outputs of `NS-2` might be text-based or animation-based afterward on the simulation. Tools like `nam` and `xgraphs` are used for interpreting such outcomes in a graphical or interactive way. An appropriate subset of text-based information is extracted by the users for analyzing specific network performance and is transformed toward a possible presentation.

Clustering and routing are performed by using 21 sensor nodes within this simulation. This method outperforms the previous methods, as shown in the simulation.

The system parameters utilized in the simulations are shown in [Table 1.1.](#ch01.xhtml#table1_1) This method uses application traffic as `CBR` (`Constant Bit Rate`), and it supports the traffic control in the network. The routing protocol serves as `AOMDV`, and the application of it is done for routing within the network. `DEEH-CH`, `DCEMRA`, and `SC-MCHMP` are the routing techniques that are implemented to perform outcomes of the network. With the consideration of packet size as 1024 bytes, the transmission rate is 1024 bytes/0.1 ms, having a maximum speed of 35 m/s in addition to the total simulation time of 20 sec.

[Table 1.1 Simulation Table of Proposed Network](#ch01.xhtml#Ttable1_1)

| Network Parameter || Value |

| --- | --- |

| Application Traffic Protocol || `CBR` |

| --- | --- |

| Rate of Transmission || 1024 bytes/0.1 ms |

| Radio Range || 250 m |

| Data Packet Size || 1024 bytes |

| Channel data rate || 40 Mbps |

| Maximum speed || 35 ms/s |

| MAC protocol || `MAC/802\_11`, `MAC/CSMA/CA`, `Mac/TDMA`, `MAC/FDMA` |

| Routing protocol || `AOMDA` |

| Network Simulation time || 20 secs |

| Number of nodes used in simulation || 21 |

| Network Area || 500 × 500 |

| Routing methods || `DEEH-CH`, `DCEMRA`, `SC-MCHMP` |

The end-to-end delay versus simulation time is illustrated in [Figure 1.1](#ch01.xhtml#fig1_1), which includes comparing proposed protocol `SC-MCHMP` and previous techniques like `DCEMRA` and `DEEH-CB`. The `SC-MCHMP` outperforms in terms of reduced end-to-end delay for communication among nodes. The multichannel allocation accomplishes using the `CSMA` or `CA`, `TDMA` modes, and this method has a 25% delay compared to the previous approaches. The maximum score of the route (in `SC-MCHMP`, less delay yields higher scores) ensures fewer delay in the selected paths, and more number of packets are getting delivered within a short time.

![Figure 1.1 Performance on delay.](Images/fig1_1.jpg)

[Figure 1.1 Performance on delay](#ch01.xhtml#Ffig1_1).

The simulation results of energy consumption are shown in [Figure 1.2](#ch01.xhtml#fig1_2), which displays the graphs of energy level ratio vs simulation time. Based on the proposed protocol, the loss ratio improves with the reduction of energy conservation compared to the existing methods, such as `DCEMRA` and `DEEH-CB`. The collision-free data transmission out of the `CH` nodes toward the `SINK` results in reducing energy consumption and energy levels by 28%. Due to the reduced delay and the reduced number of retransmissions, the energy consumes less than the existing protocols.

![Figure 1.2 Energy consumption.](Images/fig1_2.jpg)

[Figure 1.2 Energy consumption](#ch01.xhtml#Ffig1_2).

The network performance is discussed in [Figure 1.3](#ch01.xhtml#fig1_3), which presents the graphs of simulation time versus throughput. In this approach, a network's performance improves where the data saves more than the previous methods. This paper includes the throughput with an average of 34 Kb/s. Compared with the earlier approaches, the data transmission is done exclusively to the loss, and the network performs effectively. The `SC-MCHMP` always suggests less delay and interference-free paths. The packet delivery to the target node is mostly not disturbed during transmission, which drastically improves the throughput rate.

![Figure 1.3 Network performance.](Images/fig1_3.jpg)

[Figure 1.3 Network performance](#ch01.xhtml#Ffig1_3).

The network lifetime vs. a number of nodes is shown in [Figure 1.4](#ch01.xhtml#fig1_4). The `SC-MCHMP` improved the network lifetime performance compared to the existing methods, namely `DEEEH-CB` and `DCEMRA` due to the optimized energy consumption and the higher load balancing among the `SNs`. The network lifetime achieves an improvement of 13% owing to the changes in transmission and receiving nodes. Due to the reduced energy consumption ratio in `SC-MCHMP`, the network lifetime improves with optimized energy consumption.

![Figure 1.4 Network lifetime vs communication range.](Images/fig1_4.jpg)

[Figure 1.4 Network lifetime vs communication range](#ch01.xhtml#Ffig1_4).

The characterization of network lifetime vs. communication range is presented in [Figure 1.5](#ch01.xhtml#fig1_5). The network's lifetime is enhanced using the lower communication range in this proposed method compared to the previous techniques, such as `DEEEH-CB` and `DCEMRA`. A comparable performance is possessed by this `SC-MCHMP` approach within the overall communication ranges. An increase of 24% is attained in the network lifetime by increasing the general communication range. Compared with the other techniques, the network lifetime increases with the rise in the distance between the nodes. The proposed `SC-MCHMP` method gives a similar performance in all the different communication ranges. The estimation of `RSSI` for score calculation provides a feasible path for all environments compared with previous protocols.

![Figure 1.5 Network lifetime vs nodes.](Images/fig1_5.jpg)

[Figure 1.5 Network lifetime vs nodes](#ch01.xhtml#Ffig1_5).

## [1.5 Conclusion](#ch01.xhtml#c_sec1_5)
