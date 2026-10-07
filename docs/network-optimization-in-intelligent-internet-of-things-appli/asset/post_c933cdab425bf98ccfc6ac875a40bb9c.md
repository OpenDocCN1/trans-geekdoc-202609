
27. Z. Shouran, A. Ashari, and T. Kuntoro, “Internet of Things (IoT) of Smart Home: Privacy and Security,” International Journal of Computer Applications, vol. 182, no. 39, pp. 3–8, 2019, doi: 10.50120/ijca20199918450.

28. P.C. Sharma, M. R. Mahmoodood, H. Raja, N. S. Yadav, B. B. Gupta, and V. Arya, “Secure authentication and privacy-preserving blockchain for industrial internet of things,” Computers and Electrical Engineering, vol. 108, p. 108703, May 2023, doi: 10.1016/j.compelec.2023.108703.

29. V. Thakur, M. N. Doja, Y. K. Dwivedi, T. Ahmad, and G. Khadanga, “Land records on Blockchain for implementation of Land Titling in India,” International Journal of Information Management, vol. 52, p. 101940, Jun. 2020, doi: 10.1016/j.ijinfomgt.2019.04.013.

## 15 Secure Communication and Authentication in IoT-Based UAV Networks

Jatin Sharma, Pawan Singh Mehra, Diksha Chawla, Deeppakshi Dabas, and Aatif Jamshed

## 15.1 INTRODUCTION

Unmanned Aerial Vehicles (UAVs) are aircraft that can fly autonomously and with self-guidance under remote control. These dynamic and fast-moving flying machines need consistent communication dependability, which may be attained by utilising the Mavlink protocol, which bridges the communication gap between UAVs and the Ground Control Station (GCS). The concept of the Internet of Things (IoT) describes a network of interconnected entities outfitted or acquired with flight controllers, detectors, and software, facilitating the exchange of information from drones via wireless communication. Consequently, drone swarms share similarities with the IoT framework. These networks comprise a collection of interlinked drones empowered by Internet connectivity while being gathered with integrated detectors and flight controllers. A total of 86,728 drones are enrolled in the US per FAA (Federal Aviation Administration) [1]. The drone market is projected to witness an annual growth of around 6.5%, potentially doubling by the year 2025. It has garnered significant attention across domains such as rescue operations, payload delivery logistics, photography, and others that are challenging for a single UAV to accomplish. Consequently, coordination among UAVs necessitates the exchange of commands to fulfil these multifaceted objectives. These networks of UAVs establish substantial volumes of data encompassing visual, telemetry, and detector measurements. Prevailing studies on secure UAV design predominantly center on computationally intensive methods. A primary shortcoming of prior research lies in the absence of an in-depth exploration into the entire cycle of attack and security concerns concerning UAV communication. To address these limitations, it is crucial to examine existing countermeasures and propose innovative approaches thoroughly. This chapter delves into both physical and logical attacks, presenting authentication strategies that offer insights into future directions.

DOI: 10.1201/9781003045535-20

### 15.1.1 MOTIVATION

In spite of the evident benefits offered by UAV networks, their implementation is hampered by security considerations. The issue of UAV security was brought to the forefront in 2011 when the RQ-170 drone was gathered by Iran force [2]. The potential for adversaries to launch network-based assaults whenever UAVs are engaged in tasks such as combat communication and reconnaissance in perilous situations. An illustrative case emerged during the Russia-Ukraine conflict of 2022 [3]; Ukrainian military units formed compact squads with the objective of directly engaging Russian UAVs by laser-based weaponry. An expert [4] elucidates how attackers can exploit vulnerabilities by interfering with the connections linking UAVs and base stations. UAVs containing confidential data related to military operations are susceptible to compromise. Particularly in security-sensitive contexts, encompassing surveillance, recovery, and heightened security measures is imperative. Existing studies often present only concise evaluations or surveys, focusing on a limited area of security threats or countermeasures. The absence of a comprehensive exploration in the drone network domain has prompted the need for this contemporary study. The work endeavours to bridge the discrepancies and address the security requirements. Therefore, there is a necessity for a preliminary investigation into authentication mechanisms.

### 15.1.2 CONTRIBUTION

- Presents a survey on secure communication and authentication in IoT-based UAV networks.
- Provides a summary of related work.
- This work compares with an existing survey using security parameters like mutual authentication, un-traceability, in a tabular layout.
- This work discusses the state-of-art authentication techniques.

### 15.1.3 OUTLINE OF THE CHAPTER

The arrangement of the segments is structured as follows: Section 15.2 provides an over-view of UAVs. Section 15.3 delves into the pertinent work. Security requirements for secure communication and authentication in IoT-based UAV networks is discussed in Section 15.4. Section 15.6 describes the secure communication and authentication mechanisms. Lastly, Section 15.5 encapsulates the concluding remarks and future directions.

## 15.2 OVERVIEW OF UNMANNED AERIAL VEHICLES

This section covers the complete details of UAVs.

### 15.2.1 UAV

A UAV refers to an aircraft or vehicle that operates without human intervention, capable of functioning autonomously and independently. UAVs have gained prominence

Secure Communication and Authentication in IoT-Based UAV Networks

![](img/e0b54a8aa3102369506fc5feb80a6fde_275_0.png)

FIGURE 15.1 UAV.

for their contributions in areas such as surveillance and search and rescue operations on the battlefield. The network of UAVs extends its reach to diverse fields, including wireless hotspot precision, smart urban environments, remote sensing applications, agricultural endeavours, and more. Figure 15.1 displays the constituents of the UAV elements [5].

The primary constituents of UAVs encompass:

- Motors
- Flight controller
- Power distribution board
- Electronic speed controllers
- Antenna
- Radio receiver
- Battery
- FPV camera
- Propellers
- Video transmitter

## 15.2 Category of UAVs

### 15.2.1 Weight-based [6]

- a. Nano UAV: aircraft with a weight of less than 250 g
- b. Micro UAV: aircraft with a weight greater than 250 g and less than 2 kg
- c. Small UAV: aircraft with a weight greater than 2 kg and less than 25 kg
- d. Medium UAV: aircraft with a weight greater than 25 kg and less than 150 kg
- e. Large UAV: aircraft with a weight greater than 150 kg

### 15.2.2 Altitude-based [7]

- a. High altitude UAV (HAUAV): This category of aircraft functions at extremely elevated altitudes spanning 10 km. Balloons, airplanes, and dirigibles fall within this
- b. Low altitude UAV (LAUAV): This classification is versatile and adaptable, capable of flying at altitudes up to 10 km. Vertical Takeoff and Landing (VTOL) craft are encompassed within.

### 15.2.3 Wings-based [7]

- a. Fixed-wing UAV: This refers to a pilotless aircraft with stationary wings, requiring a runway for takeoff and landing. These aircraft exhibit substantial range and resilience.
- b. Rotary-wing UAV: The rotary-wing vehicle may exist in singular or multirotor configurations, including VTOL UAVs. This wing design offers exceptional maneuvering capabilities, facilitating precise takeoff and controlled flight.
- c. Hybrid-wing UAV: It involves the integration of both stationary and rotary-wing elements.

### 15.2.4 Range-based [7]

- a. Short-range UAV: UAV capable of covering distances up to 10 km.
- b. NATO UAV: UAV capable of flying distances up to 50 km.
- c. Tactical UAV: UAV capable of flying distances by 50 km.
- d. Moderate altitude and extended endurance: UAV capable of travelling distances up to 200 km.
- e. Elevated altitude and prolonged endurance: UAV with boundless endurance.
- f. Superspeed UAV: UAV capable of covering distances exceeding 200 km.

### 15.2.3 CONNECTIONS in IoT-Based UAV Networks

- a. Air-2-Air communication (A2A): Within A2A communication, single UAV has the capacity to share data with another UAV and assume the role of a relay node, thereby extending the range of connectivity.
- b. Air-2-Ground communication (A2G): In this connection, a drone possesses the capacity to transmit crucial data to the base station. Subsequently, the base station holds the capacity to issue specific task-related control commands to the UAVs.
