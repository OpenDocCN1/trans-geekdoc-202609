
![](img/a29e06af76c776aadcc01782d636c0d5_34_0.png)

FIGURE 1.7 Wireless sensor network.

## 1.1.2.4 WSN Topologies

The nodes in WSN are arranged in geometric representations, called topologies [6, 9, 10]. The most common sensor network topologies are as follows (Figure 1.8):

- 1. Point-to-point (dedicated) network
- 2. Star network
- 3. Tree network
- 4. Mesh network

- 1. Point-to-point (dedicated) network topology: In dedicated topology, the nodes can communicate directly with each other. There is only one data communication path, highly securing secure communication. Since there is no central hub, each node acts as both client and server (Figure 1.9).

- 2. Star network topology: In a star topology, communication takes place through a central hub and in contrast to point-to-point topology, direct communication between sensor nodes is not possible. Hubs act as servers and nodes act as clients (Figure 1.10).

- 3. Tree network topology: In tree topology, each node is connected to the previous higher node, or parent node, and finally connects to the root node (Figure 1.11). The leading advantages of this topology are easy to expand, and errors can be easily detected. However, it has the drawback of being heavily dependent on the base cable. If the base cable cracks or breaks, the entire network collapses. The data is moved from the leaf node to the parent node and finally to the root node.

- 4. Mesh network topology: A mesh network allows all nodes to interact with each other without relying on a central hub. Data can be moved from one node to another. This is the most reliable network communication as it has no single failure point. However, this complicated structure consumes a lot of power.

![](img/a29e06af76c776aadcc01782d636c0d5_35_0.png)

**FIGURE 1.8** Wireless sensor network topologies.

![](img/a29e06af76c776aadcc01782d636c0d5_35_1.png)

**FIGURE 1.9** Point-to-point network.

![](img/a29e06af76c776aadcc01782d636c0d5_36_0.png)

## 1.1.2.5 Differences between Wireless Sensor Network and Internet of Things

Table 1.1 shows the differences between WSN and IoT.

## 1.1.3 CONVERGENCE OF IoT and WSN

The convergence of the IoT and WSNs is becoming increasingly common and important. This convergence involves combining the data collection capabilities of WSNs with the communication and data processing capabilities of IoT systems [12, 13].

Combining WSNs and IoT can enable more efficient, intelligent, and scalable data collection and analysis in a variety of applications. For example, WSNs can be used

![](img/a29e06af76c776aadcc01782d636c0d5_37_0.png)

FIGURE 1.11 Tree network.

to collect data from remote or harsh environmental conditions, while IoT can provide cloud-based processing and storage capabilities for the collected data.

It is a natural evolution of both technologies. The two technologies have many similarities, including the ability to collect and transmit data from the physical environment, low power consumption, and wireless communication. The convergence of these technologies has led to the creation of new applications and opportunities in various domains, including industrial automation, healthcare, environmental monitoring, and smart cities.

| Wireless Sensor Network | Internet of Things |
| :--- | :--- |
| WSN is anything that connects to a wireless network to collect data or monitor the environment. | IoT consists of WSN + Internet + Cloud Storage + Mobile/Web Applications. |
| WSN consists of a large number of tiny low-power devices called nodes that communicate through wireless channels for information sharing. | IoT consists of a gateway that is used to connect the devices to networks (using switches, routers, Access Points, etc.). |
| WSN follows IPv4 and it has a sink node not by gateway. | IoT follows IPv6 on the sensor network (802.15.4 MAC/PHY) and IPv4 on the internet part [11]. |
| Routing protocols in WSN include DSR, CTP, PEGASIS, LEACH, SEP, AODV, OLSR, SPIN, and TEEN. | Routing protocols in IoT include RPL, LoWWPAN, MQTT-SN, CoAP, AODV, BLE Mesh, and Zigbee. |

One of the major advantages of the convergence of IoT and WSN is the capability to integrate large-scale networks with sensor networks. This integration enables the connection and analysis of data from multiple sources, providing a better and improved view of the physical environment. For example, a smart city network can use IoT devices and WSNs to monitor traffic, air quality, and noise pollution, providing a better understanding of the city's environmental conditions.

Another benefit of this combination is the ability to reduce power consumption and increase the lifespan of the network. Using WSNs for local sensing and IoT devices for data aggregation and communication, the network can be optimized for low power consumption, reducing the need for frequent battery replacements.

It also poses several challenges, such as interoperability, security, and power management. In order to fully realize the potential of this convergence, there needs to standardization and coordination among different technologies and protocols. Additionally, security needs to be implemented to protect the sensitive data collected and transmitted by WSNs and IoT devices. Finally, efficient power management strategies need to be developed to extend the lifespan of WSN nodes and IoT devices.

Therefore, the convergence of IoT and WSN is expected to drive innovation and create new opportunities for businesses and individuals alike. The ability to collect and analyze data from the physical environment in real-time has the potential to revolutionize or transform many different industries and domains, improving efficiency, safety, and quality of life, but it also requires careful planning, coordination, and implementation to ensure its success.

## 1.1.4 Sustainable Integration of IoT and WSN for Smart Applications

The integration of the IoT and WSN can enable the development of smart applications that enhance sustainable data exchange between IoT devices and sensors, enabling real-time monitoring, control, and analysis of physical systems. Sustainable IoT is an approach to designing and implementing IoT systems in a way that prioritizes sustainability and environmental responsibility. Smart applications that use sustainable IoT technology aim to reduce energy consumption, minimize waste and environmental impact, and promote social well-being [14, 15].

Here are some key considerations for designing sustainable IoT systems for smart applications: [16]

- 1. Energy efficiency: One of the crucial considerations for sustainable integration is optimizing the energy consumption of IoT devices and sensors. WSNs typically operate on limited battery power, so energy-efficient protocols and algorithms should be employed to minimize energy consumption. Sustainable IoT systems should be designed to consume minimal power, using energy-efficient components and power management techniques and to explore energy harvesting techniques to minimize energy consumption. This includes low-power sensors, such as sleep modes and wake-on-demand, duty cycling, adaptive sampling, and data aggregation that can help prolong the network's lifetime, and leveraging renewable energy sources for power generation, including solar or kinetic energy, that can also be used for IoT devices.

- 2. Recycling and waste reduction: Sustainable IoT systems should be designed to minimize waste and promote recycling. This includes recyclable materials in IoT devices, implementing take-back programs, and designing systems that can be easily upgraded or repurposed.

- 3. Data management and analytics: Efficient data management and analytics play a vital role in sustainable IoT. IoT generates a massive amount of data from various connected devices. Sustainable IoT systems should prioritize efficient data management, minimizing the amount of data transmitted and processed to reduce energy consumption, implementing data compression techniques, edge computing, and intelligent analytics to filtering techniques can be used to minimize data transfer, and edge computing enables data processing locally to the source, reducing the need to transfer data to the cloud, conserving energy and network bandwidth. WSNs can also employ fusion techniques to combine data from multiple sensors and eliminate redundant information.

- 4. Lifecycle analysis and circular economy: Sustainable IoT systems should be designed with a lifecycle analysis approach and to support circular economy principles, taking into account the environmental impact of the system throughout its entire lifecycle, from manufacturing to disposal. Consider factors like manufacturing, deployment, operation, and end-of-life management. Promote circular economy principles by designing devices for ease of repair, upgradeability, and recycling to minimize waste and resource depletion.

- 5. Smart resource management: IoT for smart resource management to optimize resource consumption and reduce waste. Monitor and control energy usage, water consumption, and other resources in real-time, enabling efficient allocation and conservation. By leveraging IoT and WSN, real-time data can be collected, analyzed, and used to make intelligent decisions that minimize waste, improve resource allocation, and reduce environmental impact.

- 6. Social impact and inclusion: Ensure that IoT solutions contribute to social well-being and inclusivity. Consider accessibility, privacy, and security aspects to protect user data and maintain trust. Develop solutions that address social challenges and provide equitable access to smart services for all.

- 7. Collaboration and partnerships: Foster collaboration among stakeholders, including governments, initiatives, academia, and communities, to promote sustainable IoT initiatives. Encourage knowledge sharing, research, and development of sustainable practices and technologies.

# Introduction to IoT and WSN
