
# **TABLE 3.1**
Comparison of Sensor Types Utilized in Smart City Applications

| Sensor Type | Measurement | Application | Advantages | Disadvantages |
| --- | --- | --- | --- | --- |
| Humidity | Moisture | Building automation, energy management, Agriculture, HVAC systems, building automation | Low cost, easy to install Helps prevent mold and moisture damage | Limited to temperature measurement only |
| Air Quality | Pollutants | Environmental monitoring, traffic management, public health | Can detect various pollutants | Can be expensive, requires regular calibration |
| Noise | Sound level | Traffic management, public safety, noise pollution control | Can measure noise accurately | May be affected by other sounds or environmental factors |
| Vibration | Vibration | Structural health monitoring, industrial automation, transportation systems | Can detect vibration in structures or machinery | Can be expensive, may require complex installation |

including managing traffic, ensuring safety, and controlling noise pollution. Noise sensors can monitor decibel levels in a range of settings, such as congested streets, open spaces, and noisy factories.

Vibration sensors: These sensors gauge the intensity of environmental vibrations. They are essential to many smart city applications, including public transport, factory automation, and monitoring health infrastructure. Using vibration sensors, the level of vibration in a building, bridge, or other structure may be determined. Installing these sensors may be advantageous for both the infrastructure of public transport and vehicles.

Table 3.1 summarizes the many sensor types utilized in smart city applications, along with the benefits and drawbacks of each. The table demonstrates that there are trade-offs in consideration, such as cost and accuracy, when deciding on a sensor. To make sure the IoT-WSN framework effectively supports the smart city application, the right sensors must be chosen after thorough consideration of the data requirements and application demands.

## 3.4 SELECTING COMMUNICATION PROTOCOLS

Once sensors have been chosen, the right communication protocol must be specified so data can be sent from the sensors to the central monitoring system. Considerations including data rate, range, power consumption, and cost will inform the protocol selection. In smart city applications, the four types of communication protocols are typically used [31–33]:

### 3.4.1 Wi-Fi

A communication protocol called Wi-Fi (Wireless Fidelity) offers wireless connectivity for a variety of gadgets and applications. It is appropriate for a variety of smart city applications due to its high data transfer rates and operation in the 2.4 GHz and 5 GHz frequency ranges. We will go into Wi-Fi in this section, looking at its main benefits, features, and in the context of the integrated IoT-WSN framework for smart cities.

With the help of Wi-Fi technology, devices can wirelessly join a local area network (LAN), which enables them to communicate and share data with one another and the internet. It is dependent on the IEEE 802.11 standard family, which establishes the requirements for wireless networks. Access points (APs) that send and receive data signals make up Wi-Fi networks, together with devices that connect to these APs to access the network.

The high demand transmission rates of Wi-Fi allow us to establish fast and dependable connections, which makes them appropriate for use with high-bandwidth applications like video streaming, real-time monitoring, and cloud-based services. As a result, Wi-Fi is a great option for many smart city cases, using surveillance systems, open Wi-Fi hotspots, and intelligent transportation systems.

The ubiquity and accessibility of Wi-Fi is another characteristic. Worldwide, homes, businesses, areas, and all cities have Wi-Fi networks. This large infrastructure facilitates the deployment of Wi-Fi-enabled devices and offers extensive coverage for applications related to smart cities. To connect sensors, devices, and infrastructure to provide smooth communication and data exchange, municipalities can make use of existing Wi-Fi networks.

Wi-Fi networks can also be readily scaled and expanded to support an increase in the number of users and devices. To boost network capacity and increase coverage, several access points can be used throughout. Roaming is a feature of Wi-Fi networks that enables seamless switching between access points for devices. This scalability is essential in smart cities since there are increasingly more connected devices and people that need wireless access.

Wi-Fi can be used as a communication protocol for many IoT devices and sensors within the integrated IoT-WSN architecture. It is possible for these gadgets to connect to the internet and send information to centralized systems for additional processing and analysis. Wi-Fi-enabled sensors, for instance, can gather information on energy usage, garbage management, traffic movement, and air quality in smart city applications, offering crucial insights for urban planning and management.

Strong security protections are provided by Wi-Fi to safeguard data transmitted across the network. Wi-Fi supports several security protocols, including WPA2 and WPA3, which offer encryption and authentication tools to guarantee secure communication. This is essential for protecting sensitive data in applications for smart cities, such as transaction data, personal information, and surveillance footage.

Additionally, Wi-Fi technology provides a variety of deployment possibilities. It supports a variety of network topologies, including mesh networks, where several APs come together to create a self-healing network that can quickly adjust to environmental changes. Mesh networks improve network coverage and stability, which qualifies them for extensive smart city deployments.

As a result of its widespread adoption, Wi-Fi is a communication technology that is essential to the integrated IoT-WSN framework for smart city applications. It is the best option for establishing connections between devices and facilitating seamless communication in smart city environments due to its fast transfer rates, wide availability, scalability, strong security features, and flexibility. Wi-Fi networks are used in a variety of applications, including smart transportation systems, public Wi-Fi hotspots, and surveillance. Cities can create effective, dependable, and secure wireless connectivity by utilizing Wi-Fi technology, establishing the groundwork for smarter and more interconnected urban environments.

### 3.4.2 BLUOTH

A wireless system called Bluetooth makes possible for devices to interact and exchange data across short distances. It is now a commonplace technology that can be found in many gadgets, smartphones, computers, wearables, and IoT. The key characteristics, benefits, and uses of Bluetooth will be covered in more detail in this section where we analyze the integrated IoT-WSN framework for smart cities.

Bluetooth employs low-power radio waves to link devices and operates in the 2.4 GHz frequency band. It adheres to the Bluetooth Core Specification, which establishes the communication standards and protocols. In the master-slave architecture used by Bluetooth devices, one device serves as the master and manages communication with one or more slave devices. The low power consumption of Bluetooth is one of its main benefits. The energy-efficient nature of Bluetooth makes it appropriate for battery-operated devices and applications that need a long battery life. As many IoT devices and sensors rely on finite power in smart city applications is very advantageous. Both traditional Bluetooth and Bluetooth Low Energy (BLE) are available as Bluetooth communication options. For applications needing more bandwidth, such as audio streaming and file transfer, classic Bluetooth offers faster data transmission rates. BLE, on the other hand, is perfect for IoT devices and sensors needing recurring data updates because it is optimized for low power consumption and supports intermittent data transfer.

Bluetooth's simplicity of use and smooth communication further benefits. No complicated setups are required to pair and connect Bluetooth devices. Devices that have been linked instantly connect when they come into range, giving users a convenient and trouble-free experience. This functionality is crucial in settings like smart cities where a lot of devices need to connect and communicate with one another easily.

Additionally, Bluetooth enables several profiles and make certain features and applications possible. For instance, the Bluetooth Health Device Profile (HDP) enables the transmission of health-related data from wearable devices to healthcare systems, while the Bluetooth Hands-Free Profile (HFP) permits hands-free communication within devices. These profiles increase Bluetooth's functionalities and enable a variety of use cases for smart cities.

Furthermore, Bluetooth offers strong security safeguards to safeguard data while it is being transmitted. To provide safe communication between devices, it supports
