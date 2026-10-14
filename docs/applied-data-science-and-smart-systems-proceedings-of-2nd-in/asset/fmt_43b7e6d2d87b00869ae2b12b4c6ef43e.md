
进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

**Attacks using replication:** The attacker sets up malicious nodes that have the same ID as the real nodes and are loaded with hacked cryptographic data. Instead than capturing a significant number of nodes, the deployment of numerous replicas makes it simple to compromise the whole network.

WSN is essential to C4ISRT systems, which stand for Surveillance, Command, Control, Communications, Computation, Intelligence, Reconnaissance, and Targeting. A very promising sensing method for military C4ISRT is created by sensor networks’ fast exploitation, self-organization, and error accepting characteristics. Sensor nodes are intended as sensor blotches that are spread around the area to be detected in the border monitoring application. The sensor nodes transmit the data to the network entrance via the sensor blotch. Also, the entrance is in responsibility of transmitting that data to the base station. The base station connects to database clones of the secure systems that are only accessible to authorized personnel. Finally, several user interfaces are used to display the information to the military workforce.

### A. Replication methods

**Attack node replication attack:** In a node duplication attack, a copy of the recognized vertex that is present into the network tries to contact nearby nodes that are within its wireless communication range. Even if the attacker is unsuccessful in creating a link with a valid node, it will continually carry out the same procedure throughout the network.

**Attack on access points:** Access points are the information aggregation hubs that send data to the sink. An advanced technique called access point replication allows an attacker to take control of a section of the network. Successful access point replication makes it simpler for the attacker to capture the network.

**Attack on sink replication:** Sink replication is a sophisticated assault against WSNs. Many WSNs simply utilize one sink to collect data. After completing sink replication, the attacker will have complete control over the network. Even though WSNs have numerous sinks, sink duplication causes more harm.

### B. Different replication methods

#### Fully replicated tables

Whole table replication is the phrase used to describe the replication of all data. This includes both new and updated information that is replicated from the beginning to the end. Costs are frequently greater since this replication technique needs a lot of processing power and network bandwidth. But, as will be discussed later in this article, whole table replication can be helpful for retrieving data that has been hard destroyed as well as data that does not have replication keys.

#### Replication in a transaction

Using this approach, whenever data is modified, and the user database receives updates after complete first copies of the data are being created from origin to destination by the data replication software. This is a more effective replication technique since fewer rows are copied when data is changed. Transactional replication is widely used in server-toserver configurations.

#### Quick replication

With snapshot replication, data is duplicated precisely for the given interval. In contrast to other techniques, snapshot replication doesn’t fully account for data changes. This type of replication is used because data changes are most likely to happen rarely, such when publishers and subscribers finish their first synchronizations.

#### Fusion of replication

This type of replication is widely used in server-toclient configurations because it enables both the subscriber and publisher to make dynamic changes to the data. Using merge replication, which consolidates information from several databases into one, makes it more challenging.

#### Incremental replication based on keys

Only data that has changed since the last update is transferred using this technique, sometimes referred to as key-based incremental data collection. Keys can be viewed as database elements that lead to data replication. Because each update only involves a few row copies, the costs are very low. The drawback is that this replication mode cannot be used to retrieve data that has been permanently deleted since the key value is also removed along with the record.

It is difficult to locate these replications in WSNs. Several academics have suggested methods for recognizing these dangerous assaults.

## V. Modes of data acquisition

A WSN’s primary objective is to gather information about the region in which it is located and then communicate that information to the sink, which may be far away. The events occurring in the deployment zone are then determined or reconstructed using the information obtained. The deployed nodes normally scan and capture data regularly but transfer the gathered data to the actuator, based on the technique of data acquisition, which may be one of the following([Ahmed et al., 2018](#ch14.xhtml#ref14_4)) .

1.  **Periodic data acquisition:** In this mode, the nodes will regularly communicate the information they have acquired to the sink in addition to periodically collecting the information themselves. The rate at which the acquired data is transferred to the sink would typically be significantly higher than the frequency of data sampling. This is because the node typically uses far less energy for sensing and computing than for delivering the information, but there are rare applications where the contrary has been demonstrated to be true ([Elappila et al., 2018](#ch14.xhtml#ref14_13)).

2.  **Event-based data acquisition:** In this mode, the deployed nodes may scan and gather data on a regular basis, but they will only send the data when a certain predefined event takes place. As the nodes won’t transmit frequently in this mode, there is a tendency for the network life to be substantially greater than in periodic data acquisition mode. Applications requiring regular information about the event region, such as habitat monitoring, are not suited for this mode.

3.  **Query-based data acquisition:** In this mode, the deployed nodes may periodically look for and compile data, but they will only formally request and transfer the data. This technique, sometimes referred to as interest propagation, involves the sink initiating a query that spreads across the network. The data that nodes have access to will only be delivered to those that satisfy the query’s requirements. One of the main criteria of this mode is that the query must be disseminated to all nodes in the least amount of time and energy.

4.  **Hybrid data acquisition:** It combines the first three types. One or more of the aforementioned data collecting modes may be employed by various parts of the deployed nodes.

Environmental applications for WSN include coal mining, tsunami, earthquakes, flood detection, gas leak detection, forecasting of forest fires, cyclones, water quality, range of rainfall, volcanic eruption, and more. The network helps in the implementation of safety procedures to some extent since it provides early identification and forecasting of all these natural disasters. The sensor gathers the information, then it is transferred to the master station over the net. This aids in both alerting people to the approaching disaster and implementing precautionary actions. The monitoring of forest fires, air pollution, coal mining, gas leaks, and water quality will all benefit from this.

## VI. Single node architecture

In a WSN, the architecture of a sensor node is very simple and it is subdivided into three primary units: (i) the processing unit; (ii) the communication unit; and (iii) the sensing unit. A sensor node’s block diagram is shown in [Figure 14.3](#ch14.xhtml#fig14_3).

![Figure 14.3 Sensor nodes architecture](images/fig14_3_B.jpg)

[Figure 14.3 Sensor nodes architecture](#ch14.xhtml#R_fig14_3)

1.  **Processing unit**
