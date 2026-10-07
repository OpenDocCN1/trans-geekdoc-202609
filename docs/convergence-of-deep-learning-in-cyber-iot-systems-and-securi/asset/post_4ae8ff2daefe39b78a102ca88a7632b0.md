
# MQTT-Based IMPLEMENTATION OF HOME AUTOMATION SYSTEM 263

| Created at | Value | Location |
|---|---|---|
| 2020/06/18 4:22pm | ON | X |
| 2020/06/18 4:22pm | OFF | X |
| 2020/06/18 4:22pm | OFF | X |
| 2020/06/18 12:24pm | OFF | X |
| 2020/06/18 12:24pm | OFF | X |
| 2020/06/18 11:55pm | OFF | X |
| 2020/06/18 11:55pm | ON | X |
| Record 1 through 7 of 7 (MQTT Joined) | | |

**Figure 12.11** Feed of log light.

- We make a feed called "TEMPERATURE" to publish the temperature data in the Adafruit dashboard taken by the DHT1 sensor. The data are represented both in Gauge and in a Linear Graph in Figures 12.12 and 12.13. And all the results of this feed are also stored in the Adafruit log like this:

![](img/081dc7f102a3793cb08980a6e19b8f17_286_0.png)

**Figure 12.12** Temperature feed log (graphical).

| Created at | Value | Location |
|---|---|---|
| 2020/06/18 12:21pm | 28.00 | X |
| 2020/06/18 12:21pm | 28.00 | X |
| 2020/06/18 12:21pm | 29.00 | X |
| 2020/06/18 12:21pm | 29.00 | X |
| 2020/06/18 12:21pm | 29.00 | X |
| 2020/06/18 12:21pm | 29.00 | X |
| 2020/06/18 12:21pm | 29.00 | X |
| 2020/06/18 12:24pm | 30.00 | X |
| 2020/06/18 12:03pm | 30.00 | X |
| 2020/06/18 11:58pm | 30.00 | X |
| 2020/06/18 11:58pm | 30.00 | X |

**Figure 12.13** Temperature feed log.

# CONVERGENCE OF DL IN CYBER-IoT SYSTEMS AND SECURITY

- 3. We make a feed called “HUMIDITY” to publish the Humidity data in the Adafruit dashboard taken by the DHT11 sensor. The data are represented in Figures 12.14 and 12.15 both in Gauge and in a Linear Graph. And all the results of this feed are also stored in the Adafruit log like this:

![](img/081dc7f102a3793cb08980a6e19b8f17_287_0.png)

Figure 12.14 Humidity feed log (graphical).

| Created at | Value | Location |
|---|---|---|
| 2020/06/18 5:48:32pm | 90.00 | |
| 2020/06/18 5:48:27pm | 90.00 | |
| 2020/06/18 5:48:23pm | 90.00 | |
| 2020/06/18 5:48:20pm | 90.00 | |
| 2020/06/18 5:48:09pm | 90.00 | |
| 2020/06/18 5:48:02pm | 90.00 | |
| 2020/06/18 5:47:56pm | 90.00 | |
| 2020/06/18 5:47:50pm | 90.00 | |

Figure 12.15 Humidity feed log.

- 4. In addition, we introduce a mail notification system shown in Figure 12.16. A temperature reading from the DHT11 sensor is checked to see if it is above or below the threshold value at all times. If the value is higher than the predefined limit, the following message will be sent via IFTTT server.

Be alert !!! Your room temperature exceeds the threshold value.

Webhooks via IFTTT - actson@ifttt.com
to me -

Event: Temperature Testing
Time: June 18, 2020 at 05:33:00

> The temperature exceeds the threshold value. Be alert !!!

Unsubscribe from these notifications or sign in to manage your Email service.

![](img/081dc7f102a3793cb08980a6e19b8f17_288_0.png)

Figure 12.16 Alert mail through IFTTT.

## 12.6 Conclusion

We have set up a simple implementation of the secure MQTT protocol in a smart home to control a few sensors and lights. Sensors and relay shields can be controlled wirelessly over the Internet using the ESP32 microcontroller. The coverage range of the Wi-Fi router indicates that the Internet of Things (IoT) devices can be utilized, and accessed anywhere on our premises. The Adafruit MQTT broker is used to efficiently implement the publish-subscribe model. Each client's connection is encrypted using an SSL port. MQTT's best feature is that when feeding data, the option to set quality of service level (QoS), As a result, the proposed system improves automation service and security by verifying whether the data have been made available to the public. A gateway has been eliminated in favor of using the cloud for intermediate data storage and processing, which has the added benefit of lowering the overall cost of the proposed system. For future research, we plan to conduct additional attempts that may be applied to find which broker is the most secure and to establish a connection with IoT gadgets in smart homes.

## References

- 1. BCC Research, Sensors: Technologies and global markets, BCC Research, Wellesley, Massachusetts, 2011.
- 2. Iqbal, A., Ullah, F., Kwak, K., Imran, M., Jamal, W., Noble, B., Sneddon, I.N., Interoperable Internet-of-Things platform for a smart home using objects and cloud. Sustain Soc, 30, 636–646, 2018.
- 3. Jabbar, W., Alsib, M.H., Anwar, N.S., Mahayadin, S.K., Design and implementation of IoT-based automation system for smart home, in 2018 International Symposium on Networks, Computers, and Communications (ISNCC), IEEE, pp. 1–6, 2018.
- 4. Ning, H., Shi, F., Zhu, T., Chen, L., A novel ontology with acknowledged standards in smart homes. Comput. Netw., 148, 101–107, 2019.
- 5. Kodali, R.K., Soratkal, S., MQTT based Home Automation System Using ESP866, Department of Electronics and Engineering, National Institute of Technology, Warangal, 2016.
- 6. Jabbar, W.A., Xian, T.K., Ramli, R.M., Zamrizaman, N.S., Balfajah, M., Shepelev, V., Alharbi, S., Design of Smart Home with the Internet of Things enabled, IJEAT Access, 7, 1–11, https://doi.org/10.1109/ACCESS.2019.294286/10.1109/ACCESS.2019.294286.
- 7. Thruparpathi, V and Sagar, K., Implementation of home automation system using MQTT Protocol and ESP32. IJEAT, ISSN: 2249–8538, 8, 2C, 111–113, December 2018.
- 8. MQTT, http://mqtt.org/
- 9. MQTT Version 3.1.1. Edited by Andrew Banks and Rahul Gupta, OASIS Burlington, Massachusetts, 29 October 2014.
- 10. Perrone, G., Vecchio, M., Petori, R., Giaffreda, R., The Day After Mirai: A Survey on MQTT Security Solutions After The Largest Cyber-ried Attack an army of IoT Devices, pp. 24–256, 2017.
- 11. Sonic, D. and Makwana, A., A Survey on MQTT: a protocol of Internet of Things (IoT), Research Gate: International conference on telecommunication, power analysis and computing techniques (ICTPACT – 2017), 11–16, April 2017.
- 12. Perry, L., Internet of Things for Architects, Architecting IoT solutions by implementing sensors, communication infrastructure, edge computing, analytics, and security, Packt Publishing. ISBN 1788475477, 1–10, 2018.
- 13. NodeMCU • GitHub. [Online]. Available: https://github.com/nodemcu [Accessed: 08-Dec-2019].
- 14. Kotak, J., Shah, A., Shah, A., Rajdev, P., A Comparative Analysis on Security of MQTT Brokers, Gujarat Forensic Sciences University, India, 2019.
- 15. Anthraper, J.J. and Kotak, J., Security, privacy and forensic concern of MQTT Protocol (March 19, 2019), in Proceedings of International Conference on Sustainable Computing, Technology and Management (SUSCOM-2019), February 26-28, 2019.
- 16. Locke, D., MQ Telemetry Transport (MQTT) V3.1 Protocol Specification, https://libbase.org/network/publication/locke-mqttelemetrytransportv31protocolspecification-2010, MQ Telemetry Transport (MQTT) V3.1 Protocol Specification. Locke. D. Technical Report IBM, August, 2010.
- 17. Singh, M., Rajan, M.A., Shivraj, V., Balamuraidhar, P, Secure MQTT for Internet of Things (IoT). 2015 Fifth International Conference on Communication Systems and Network Technologies, TCS Innovation Labs, Bangalore, me.
- 18. Green, J., The Internet of Things World Forum.
- 19. Galán, C., Lasheras, F., Fuzziness based semi-supervised learning for an intrusion detection. J. Comput. Appl. Math., 31, 2, 704–717, 2017.
- 20. Razzaq, M., Gill, S., Security in the Internet of Things (IoT): A comprehensive study. Int. J. Adv. Comput. Alg., 8, 3, 2023.
- 21. Kilias, C., Kambourakis, G., Stavrou, A., Voas, J., DDoS in the IoT: Mirai and other Botnets. IEEE Computer, 50, 7, 80–84, 2017.
- 22. Ashfaq, R., Wang, X., Huang, L., Long term memory recurrent neural classifier for intrusion detection. Inf. Sci., 378, 484–497, 2017.
- 23. Singh, R., Kumar, H., Singla, R., An intrusion detection system using network traffic profiling and online sequential machine learning. Expert Syst. Appl., 42, 22, 8069–8624, 2015.
- 24. Alaziez-Monreal, H., Avelela-Mata, J., Ondicol-Garcia, J., Muñoz-Castañeda, A., Garcia, I., Benavides, Multiclass classification procedure for detecting on MQTT-IoT Protocol, Research Institute of Applied Sciences in Cybersecurity (RIASC) MIC, Universidad de León, León, 1–11, 2019. Article ID 651623. https://doi.org/10.1155/2019.651623/10.1155/2019.651623.
- 25. Perdici, R., Ariu, D., Fogla, P., Giacinto, G., Lee, W., MCPad: Multiple classifier for attack payload-based anomaly detection. Comput. Net., 53, 6, 864–881, 2009.
- 26. Kwon, D., Kim, H., Kim, J., Sukh, S.C., Kim, I., Kim, K., A survey of deep learning-based network anomaly detection. Cluster Comput., 22, 949–961, Springer, 2017, https://doi.org/10.1007/s10586-017-1117-8.
