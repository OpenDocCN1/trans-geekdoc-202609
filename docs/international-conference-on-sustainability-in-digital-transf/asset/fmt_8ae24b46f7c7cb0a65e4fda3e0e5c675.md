
### Rasberry pie
The single-board Raspberry Pi 3 computer is popular in robotics. Additionally, research projects employ it. The Raspberry Pi is affordable and lightweight. That is the raspberry Pi is employed for managing the project. robot movement and for water spraying when the button is depressed.

### Temperature sensor
A cheap digital temperature sensor is the DHT11. Thermistor is used to measure the air quality and convert it to a digital signal. Data is used to transmit the digital signal pin. Although it is easy to use, it must be handled carefully. To pull up from data, a 4.7k or 10k resistor is needed the VCC pin [[14](#ch56.xhtml#ref56_14)].

### Flame sensor
A flame sensor is used to find fires when they start. The term “flame sensor” refers to the sensor’s high sensitivity to ambient light. This sensor finds fire within the vicinity of from 760 to 1100 nm. The sensor’s output is digital. This robots employ sensors for things like alarms [[15](#ch56.xhtml#ref56_15)].

### Node Mcu
Node mcu is an open source IoT platform. The node mcu is the name of the inexpensive firmware device. Both IoT applications and prototypes are developed using it. The ESP32 microcontroller in the mcu node has Bluetooth and WiFi. Ethernet as well. It uses 7 to 12 volts to work.

## Working Model of Fire Fighting Robot
Wherever there is a chance of a fire accident, the sensor module is installed. The module is made up of a Node mcu for data transfer and sensors for temperature, smoke, and flame. Node mcu will send data to the firebase as soon as the fire is discovered. The receiver is made up of two components: an Android application and a Raspberry Pi in the first half. The raspberry pi receives data from the pi camera, which is used by the android application to display video. A WIFI module is part of the Android application and is used to connect the robot and android application. Through the android application, commands are transmitted to the robot to move forward, left, right, and put out fire. The robotic vehicle is equipped with a water tanker and a wirelessly operated water-throwing pump. Using an Android application device, commands are transferred from the transmitting end to the receiver to direct the robot’s movement in various directions, including forward, backward, left, and right. Three motors are connected to the Raspberry Pi at the receiving end; two of them are used to move the vehicle, while the third one is used to move the robot’s arm. Any smartphone is capable of remote operation. [Figure 56.2](#ch56.xhtml#fig56_2) shows the flowchart of the working model [[16](#ch56.xhtml#ref56_16)].

![Figure 56.2 Flow chart shows working of fire fighting robot](images/fig56_2_B.jpg)

[Figure 56.2 Flow chart shows working of fire fighting robot](#ch56.xhtml#R_fig56_2)

### Applications
Used as a fire extinguisher.
Used in home security.
Used in server rooms in offices.

## Conclusion
As a consequence of mechanical progress, the need for human involvement has diminished, and robotics are currently being implemented across diverse sectors, including human welfare. Constantly occurring fires pose a significant hazard to individuals and their assets, and they have the potential to claim the lives of firefighters endeavouring to extinguish the blaze. Incidental fires have the potential to cause severe damage to both property and human life. In such circumstances, an autonomous firefighting device with the ability to detect and extinguish fires would be of the utmost importance. Earlier designs for firefighting robots significantly relied on sensors, such as flame detectors, to detect fire. This paper develops a framework for fire protection and detection utilizing mobile Android robots and deep learning. We implemented deep learning and its algorithms, in addition to an Android-operable firefighting device, in order to avert fires. The most prevalent locations for these fire detection and prevention systems are in residential buildings and fire extinguishers.

## References
1. [Ramasubramanian, S., Muthukumaraswamy, S. A., and Sasikala, A.](#ch56.xhtml#R_ref56_1) (2020). Fire detection using artificial intelligence for fire-fighting robots. In 2020 4th International Conference on Intelligent Computing and Control Systems (ICICCS). IEEE, 2020.
2. [Chaturvedi, R., Islam, A., Singh, P. K., and Saraswat, M.](#ch56.xhtml#R_ref56_2) (202). Nanotechnology for advanced energy system: synthesis & performance characterization of nano-fuel. In AIP Conference Proceedings (Vol. 2721, No. 1). AIP Publishing.
3. [Raj, P. Anantha, and M. Srivani](#ch56.xhtml#R_ref56_3). (2018). Internet of robotic things based autonomous fire fighting mobile robot. IEEE international conference on computational intelligence and computing research (ICCIC). IEEE, 2018.
4. [Raj, P. A., and Srivani, M.](#ch56.xhtml#R_ref56_4) (2018). Internet of robotic things based autonomous fire fighting mobile robot. In 2018 IEEE International Conference on Computational Intelligence and Computing Research (ICCIC). IEEE, 2018.
5. [Kumar, P., Singh, P. K., Nagar, S., Sharma, K., and Saraswat, M.](#ch56.xhtml#R_ref56_5) (2021). Effect of different concentration of functionalized graphene on charging time reduction in thermal energy storage system. Materials Today: Proceedings, 44, 146–152.
6. [Raj, P. A., and Srivani, M.](#ch56.xhtml#R_ref56_6) (2018). Internet of robotic things based autonomous fire fighting mobile robot. In 2018 IEEE International Conference on Computational Intelligence and Computing Research (ICCIC). IEEE, 2018.
7. [Chaturvedi, R., Sharma, A., Sharma, K., and Saraswat, M.](#ch56.xhtml#R_ref56_7) (2022). Tribological behaviour of multi-walled carbon nanotubes reinforced AA 7075 nano-composites. Advances in Materials and Processing Technologies, 8(4), 4743–4755.
8. [Bansal, S., and Tomar, V. K.](#ch56.xhtml#R_ref56_8) (2022). Challenges & security threats in IoT with solution architectures. In 2022 2nd International Conference on Power Electronics & IoT Applications in Renewable Energy and its Control (PARC). IEEE, 2022.
9. [Sowah, R. A., Ofoli, A. R., Krakani, S. N., and Fiawoo, S. Y.](#ch56.xhtml#R_ref56_9) (2016). Hardware design and web-based communication modules of a real-time multisensor fire detection and notification system using fuzzy logic. IEEE Transactions on Industry Applications, 53(1), 559–566.
10. [Sharma, A., Chaturvedi, R., Sharma, K., and Saraswat, M.](#ch56.xhtml#R_ref56_10) (2022). Force evaluation and machining parameter optimization in milling of aluminium burr composite based on response surface method. Advances in Materials and Processing Technologies, 8(4), 4073–4094.
11. [Fadlullah, Z. M., Tang, F., Mao, B., Kato, N., Akashi, O., Inoue, T., and Mizutani, K.](#ch56.xhtml#R_ref56_11) (2017). State-of-the-art deep learning: Evolving machine intelligence toward tomorrow’s intelligent network traffic control systems. IEEE Communications Surveys & Tutorials, 19(4), 2432–2455.
12. [Taiwo, O., Ezugwu, A. E., Oyelade, O. N., and Almutairi, M. S.](#ch56.xhtml#R_ref56_12) (2022). Enhanced intelligent smart home control and security system based on deep learning model. Wireless communications and mobile computing, 2022, 1–22.
13. [Bansal, S., and Tomar, V. K.](#ch56.xhtml#R_ref56_13) (2022). Simulation and analysis of 11T SRAM cell for IoT-based applications. In Advances in Communication, Devices and Networking. Singapore: Springer, (pp. 329–340).
14. [Wu, X., Dunne, R., Zhang, Q., and Shi, W.](#ch56.xhtml#R_ref56_14) (2017, October). Edge computing enabled smart firefighting: opportunities and challenges. In Proceedings of the Fifth ACM/IEEE Workshop on Hot Topics in Web Systems and Technologies (pp. 1–6).
