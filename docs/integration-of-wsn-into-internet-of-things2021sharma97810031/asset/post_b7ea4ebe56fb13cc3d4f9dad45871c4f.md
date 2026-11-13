
information. Therefore, it is crucial to know that received data, which are to be processed, are authentic and are not a result of compromised legitimacy.

- Availability: it denotes the capability to sustain the service at almost all times. This is endangered by attacks such as denial of service and flooding. The network should be able to overcome these attacks and serve the network.
- Robustness and Survivability: this refers to the capability to isolate the damage in case of an attack. This means if a node is attacked, it should not take the whole system down with it.
- Nonrepudiation: this measurement ensures that the action done cannot be denied in any way to ensure accountability. In case of damage, it can be traced back to the action that leads to it.

## 10.3.1.2 WSN Architecture

The architecture for WSNs was mainly based on the open system interconnection reference model [18,19,20] before it was standardized in 2011 as IEEE 1451.5-802.11 [21]. WSN architecture in Figure 10.3 represents what was presented in the standard and generalizes it. Our architecture consists of seven stacked layers described in Table 10.1.

| Layer |
| --- |
| Application layer |
| Sensor layer |
| Wireless layer |
| Transport layer |
| Network layer |
| Access control layer |
| Physical layer |

| Layer | Description |
| --- | --- |
| Application | Consists of transceiver services and wireless communication modules (network capable application processors or wireless transducer interface modules) according to the standard. It is responsible for traffic management and translating data coming from different applications or queries to obtain information. |
| Sensor | Consists of the sensors to be used in the node. The sensors collect the data about their surroundings based on the requested feature. |
| Wireless | Consists of the wireless protocols through which the node will communicate with other nodes and the whole network. |
| Transport | Provides congestion avoidance and reliability. It can use either transmission control protocol or user datagram protocol as per the standard. |
| Network | Routing is a major function of this layer. Depending upon the application, it has a lot of challenges along with the fact of being resource-scarce. It also defines a reliable path for the interaction through which data are transmitted. |
| Access control | Deals with access policies, buffer management, scheduling, and error control. This is needed in a WSN to be considerate about scarce energy, reliability, high throughput, faster access, etc. |
| Physical | It provides the interface for bitstream transmission over some physical media. Frequency selection, generation of frequency, signal detection, data encryption, and modulation are this layer's responsibilities. |

FIGURE 10.3 WSN node architecture.

## 10.3.2 Security Paradigm: IoT

IoT is a group of interconnected networks of heterogeneous nature. This nature means more complexity as more and more of these heterogeneous devices are connected, as we discussed earlier, because of the vulnerability they bring together with them. According to a study done in 2019 [22], from the surveyed candidates, 28% of the candidates said that they would not own an IoT device because of the security risks they might bring with them. The same survey showed that 75% of the candidates distrust the way data are shared. IoT security includes both physical and network security, and their requirements depend upon various mechanisms and parameters [23] such as data confidentiality, integrity, privacy, triple-A, and availability. We also discuss the architecture of IoT with attacks and solutions.

## 10.3.2.1 Security Requirements

The security requirements for IoT devices depend upon the application of the device, its usage, how it shares the data, interactions, etc. Such requirements are listed below with brief definitions.

- 1. Data Confidentiality, Integrity, and Privacy: as the IoT data travel through multiple networks, encryption is a must to ensure the data are confidential. IoT devices, networks, and services are diverse and, as we discussed earlier, there is a risk associated with certain assets, and connection to them can compromise the data integrity, therefore giving access to the attacker for modifying and storing data for malicious purposes.
- 2. Authentication, Authorization, and Accounting or Triple-A Model: as discussed previously, to secure something, you need to apply the authentication mechanism to protect your service from unwanted eyes. In the context of IoT, the diverse nature and heterogeneous architecture of applications add a challenge to create a general authentication mechanism. The authorization ensures that only authorized nodes, devices, people, etc. have access to view or modify data or services. Here, the PoLPs can be proved beneficial. Another vital requirement is accounting. Accounting ensures auditing and reporting reliability of a mechanism of a secure network.
- 3. Availability: the service provided by IoT is liable for attacks on its availability. These attacks are used to block, or at least slow down, the service for a legitimate user. They can happen through jamming, replay attacks, or DoS attacks. Therefore, an IoT device or service must ensure its availability to ensure its quality of service.
- 4. Energy Efficiency: just like WSNs, these IoT devices typically have scarce resources such as power, storage, and processing. Attacks increase the consumption of these resources, which would have been otherwise utilized for handling with legitimate usage. Therefore, an IoT service should be efficient in dealing with this.

## 10.3.2.2 IoT Architecture

The network of physical objects, intelligent vehicles, devices, buildings, sensors, and software, etc. is called the IoT [24]. It is based on the connectivity between the physical and digital world via the use of sensors [25]. In this context, the architecture is a framework to define the physical parts of a network and its function, data, principles, and procedures. Due to the wide area where IoT devices are applied, there is no single universally agreed architecture of IoT. Most of the researchers agree on a three-layer architecture consisting of the application layer and network layer stacked upon the perception layer [24]. However, it is not sufficient for IoT research. Therefore, researchers have defined a five-layer architecture, as shown in Figure 10.4 [24,26], and described the architecture in detail in Table 10.2.

## 10.3.3 Security in CPS

A CPS is a system in which the mechanisms are monitored or controlled by some computer-based algorithms. These systems are heterogeneous in nature and communicate in an ecosystem of both physical and virtual assets. Because of the nature of these devices, they are very much exposed to threats that might sacrifice sensitive information or even confidential. Access grants a user to operate these systems, which might be dangerous in the wrong hands. Here, we discuss the security requirements for CPS and a CPS architecture.

| Layer |
| --- |
| Business layer |
| Application layer |
| Processing layer |
| Transport layer |
| Perception layer |

FIGURE 10.4 Five-layer architecture of IoT.

| Layer | Description |
| --- | --- |
| Business | Manages the entire system, including applications, models, and user privacy [27]. |
| Application | Responsible for enabling the user with application services. |
| Processing | Analyzes, stores, and processes large amounts of data being transported. Also, provides a diverse range of services of lower layers. Technologies such as databases, big data modules, and cloud computing are utilized here. Also known as the middleware layer. |
| Transport | Used for the transmission of sensor data collected by using the perception/physical layer. |
| Perception | This is the physical layer of the architecture that interacts with the environment and sense information based on intelligence. |

### 10.3.3.1 Security Requirements

The security in CPS should not be limited to the components involved, but it must also take into consideration the physical environments. A model has been proposed for securing CPS, which takes this into considerations, namely cyber–physical security [4]. The requirements for a typical CPS consist of five aspects described below.

- Authenticated Sensing: deals with validating the sensing process.
- Storage Security: required to prevent the tampering of data stored in both cyber and physical spaces.
- Actuation Security: refers to making sure that no actuation can take place without proper authorization.
- Feedback Security: refers to securing the necessary control systems for the feedback system of a CPS.
- Communication Security: refers to the security of the exchange of information between inter-CPS and intra-CPS.

### 10.3.3.2 CPS Architecture

Heterogeneous devices connected to communicate together forming an ecosystem of physical assets and computational capabilities which is controlled by some deterministic algorithms are called CPS [28]. The main purpose of connecting these devices is to enhance business growth and performance. The possibilities with CPS devices are endless. For example, take a look at the scenarios for cognitive CPS, which are often suffixed with the word “smart-”: an audio player that adjusts the volume depending upon the external conditions is called “smart-audio player”; “smart-car”
