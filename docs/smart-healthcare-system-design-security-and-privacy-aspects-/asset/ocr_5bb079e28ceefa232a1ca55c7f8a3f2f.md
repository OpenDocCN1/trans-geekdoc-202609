![](bbox=[0.0, 0.1, 0.85, 0.42])

**Figure 10.23** Data storage with and without the proposed algorithm.

This study proposes reducing data transmissions which could lead to significantly reducing the processing time and bandwidth used in the overall network (i.e., from publisher to subscriber device via MQTT broker). In this chapter, the tracertoute command is applied in the RasPi and monitoring server using tracert and tracert commands, respectively (see Figures 10.24 and 10.25). This command is used to determine the number of intermediate routers which are required in the transmission process from the source to the ultimate receiver.

Figure 10.26 shows the difference between the total number of transmitted bytes with and without implementing the proposed algorithms.

The calculation of the number of devices was achieved in two stages: the first stage was from the RasPi to the MQTT broker, and the second stage was from the monitoring server to the MQTT broker, and was based on Figures 10.24 and 10.25. The summation of both stages gives the total number of devices which took part in the communication between the RasPi and the monitoring server. The total transmitted bytes were calculated as the total number of devices x total number of transmitted bytes of