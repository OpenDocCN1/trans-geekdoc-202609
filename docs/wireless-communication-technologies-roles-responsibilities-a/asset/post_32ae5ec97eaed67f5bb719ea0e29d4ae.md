
![](img/be689ed28322f90f68916a35ce44e55d_37_0.png)

FIGURE 2.1 VANET architecture [12].

### TABLE 2.1
### Type of Communication Comparison

| S.No. | Type of Communication | Description |
|---|---|---|
| 1 | Vehicle-to-Vehicle (V2V) Communication | V2V technology allows for two-way, direct communication between moving vehicles. This form of communication is required for usage in really real-time security systems. When automobiles are able to talk to one another, they may exchange information about their speeds and locations, which might greatly enhance road safety. If a vehicle detects an imminent collision and applies the brakes unexpectedly, it can send a signal to other vehicles to warn them. |
| 2 | Vehicle-to-Infrastructure (V2I) Communication | In V2I communication, automobiles and roadside facilities share information with one another. Some examples of this sort of infrastructure are traffic signals, road signage, toll booths, and in-road sensors. V2I communication is useful for optimizing traffic signals, managing traffic flow, and informing vehicles of road hazards, delays, and alternate routes. One way in which real-time traffic data is used to improve traffic flow and decrease congestion is by adjusting the timing of traffic lights. |
| 3 | Vehicle-to-Everything (V2X) Communication | V2X is an expanded type of communication that goes beyond just Vehicle-to-Vehicle (V2V) and Vehicle-to-Infrastructure (V2I) to also include interactions with pedestrians (Vehicle-to-Pedestrian, or V2P) and other vehicles (Vehicle-to-Other, or V2O), such as bicycles and motorcycles. The goal of V2X is to establish an all-encompassing ecosystem for traffic control and road safety. Pedestrians can be warned of oncoming automobiles using V2P communication, while motorists can be made aware of vulnerable road users like bicyclists through V2O communication. |

## 2.2.1 COMMUNICATION MODELS: BROADCAST, UNICAST, MULTICAST, AND GEOCAST

In VANETs, various communication models are used to transmit data among vehicles and infrastructure (Table 2.2).

## 2.3 WIRELESS TECHNOLOGIES ENABLING VANET SAFETY

Wireless technologies play a pivotal role in enhancing safety and communication within Vehicular Ad-Hoc Networks (VANETs), which are crucial for modern intelligent transportation systems. Below, an in-depth overview of each of the mentioned wireless technologies and their roles in ensuring VANET safety.

- 1. IEEE 802.11p (WAVE - Wireless Access in Vehicular Environments):
  - IEEE 802.11p, a standard under the Wireless Access in Vehicular Environments (WAVE) framework, is designed explicitly for VANETs. It operates in the 5.9GHz band and offers Dedicated Short Range Communication (DSRC) [13].
  - DSRC based on IEEE 802.11p is highly suitable for safety-critical applications, providing low latency, high-reliability communication among vehicles and infrastructure components. It facilitates vehicle-to-vehicle (V2V) and vehicle-to-infrastructure (V2I) communication.
  - Key safety applications include collision avoidance, traffic signal preemption, and cooperative awareness messages (CAMs) sharing real-time data on vehicle position, speed, and status.

- 2. Cellular Technologies (e.g. 4G, 5G, and Beyond) in VANET Safety:
  - Cellular technologies, including 4G LTE and 5G, offer an extended communication infrastructure for VANETs. They provide wider coverage and connectivity beyond DSRC's short range [14].
  - 4G LTE enables Vehicle-to-Infrastructure (V2I) communication, supporting applications like traffic management, navigation, and emergency services.
  - 5G and beyond are expected to revolutionize VANETs with ultra-low latency, high bandwidth, and massive device connectivity. They are well-suited for latency-sensitive safety applications like autonomous driving and cooperative collision avoidance.

- 3. Emerging Technologies: 5G Vehicle-to-Everything (V2X) Communication:
  - 5G V2X communication is a subset of 5G technology designed for VANETs. It enables vehicle-to-everything connectivity, encompassing V2V, V2I, vehicle-to-pedestrian (V2P), and vehicle-to-network (V2N) communication [11].
  - 5G V2X offers incredibly low latency (in the millisecond range), high reliability, and the capacity to handle massive device connectivity. These attributes are crucial for real-time safety-critical applications, such as autonomous driving, where split-second decisions are essential.

### TABLE 2.2
### A Comparison of Communication Models

| S.No. | Type of Communication Model | Description | Use in VANETs | Security |
|---|---|---|---|---|
| 1 | Broadcast | In a broadcast communication model, a vehicle or infrastructure unit sends data to all nearby vehicles or infrastructure nodes | Broadcast is commonly used for safety-critical messages in V2V communication. Emergency warnings, such as sudden braking or accidents, are broadcasted to nearby vehicles to ensure that all potentially affected vehicles receive the alert. | This model is ideal for safety-critical messages that require immediate attention from nearby vehicles. It ensures that potentially affected vehicles are quickly alerted to hazards, improving overall road safety. |
| 2 | Unicast | Unicast involves one-to-one communication, where data is transmitted from one vehicle or infrastructure node to a specific recipient. | Unicast can be used for less time-sensitive messages, such as navigation instructions or data exchange between specific vehicles and infrastructure units. | Unicast is useful for non-critical communication and data exchange. It can be employed for non-urgent updates and information sharing among vehicles and infrastructure units. |
| 3 | Multicast | Multicast is a one-to-many or few-to-many communication model, where data is sent to a selected group of vehicles or infrastructure nodes. | Multicast is useful for applications where a specific group of vehicles or infrastructure units needs to receive certain information. For example, a group of vehicles traveling together in a convoy can use multicast to share information among themselves. | Multicast is suitable for scenarios where specific groups of vehicles need to receive the same information simultaneously, such as coordinated maneuvers or convoy communication. |
| 4 | Geocast | Geocast is a location-based communication model that delivers data to vehicles or infrastructure nodes within a specific geographic area. | Geocast is valuable for applications where information needs to be distributed to vehicles in a particular region. For instance, roadwork information can be geocast to vehicles approaching a construction zone. | Geocast is valuable for targeted information dissemination in specific geographic areas, which can be crucial for managing localized events like accidents or roadwork. |

- 4. Comparison of Different Wireless Technologies:
  - Latency: IEEE 802.11p (DSRC) is known for its ultra-low latency, making it suitable for time-sensitive safety applications. Cellular technologies like 5G provide low latency as well, but the exact latency depends on network congestion and other factors.
  - Reliability: IEEE 802.11p and 5G V2X are designed with high reliability in mind, crucial for safety-critical applications. Cellular technologies offer robust reliability but may vary based on network conditions [15].
  - Coverage: IEEE 802.11p has a limited range, best suited for localized VANETs. Cellular technologies, especially 5G, provide broader coverage, making them suitable for urban and interurban VANETs.

## 2.4 CHALLENGES AND FUTURE DIRECTIONS IN VANET COMMUNICATION

Vehicular Ad-Hoc Networks (VANETs) hold great promise for improving road safety, traffic management, and overall transportation efficiency. However, they also face several challenges and opportunities for future development.

### 1. Spectrum Allocation and Coexistence Challenges:

- Limited Spectrum: VANETs rely on dedicated radio frequencies for communication. The limited available spectrum poses challenges, especially as the number of connected vehicles increases. Competing with other wireless services for spectrum allocation is an ongoing issue.
- Coexistence with Other Wireless Systems: Ensuring that VANETs can coexist with other wireless communication systems such as Wi-Fi and cellular networks is essential. Interference between different communication technologies can lead to disruptions in VANET communications.
- Dynamic Spectrum Access: Future VANETs may benefit from technologies like dynamic spectrum access, which allows vehicles to opportunistically use available spectrum bands without causing interference. This requires regulatory changes and efficient spectrum management.

### 2. Scalability Issues:

- Efficient Communication: As the number of vehicles on the road increases, the VANET must efficiently manage communication between a large number of vehicles. Scalability is crucial to maintain the low latency and reliability required for safety-critical applications.
- Network Overhead: The management of routing tables, addressing, and message dissemination becomes more complex with a larger number of vehicles. Developing scalable routing algorithms and efficient protocols is essential.
