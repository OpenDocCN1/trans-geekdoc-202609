
The sensor management systems of several devices can be controlled from one common platform (a hub or smartphone). Unlike other systems, Samsung SmartThings offers a capability-based sensor management system. With SmartThings, applications interact with smart devices based on their capabilities. So, once the capabilities that are needed by a SmartApp are specified and once the capabilities that are provided by an IoT device are identified, the devices based on the device’s declared capabilities are selected for use within a specific SmartApp.

![](img/3531370aa21067bbdc45128741d34edb_49_0.png)

Fig. 4.3: An example of the sensor management system for Android.

(Source: https://www.researchgate.net/publication/322975901_A_Survey_on_Sensor-based_Threats_to_Internet-of-Things_IoT_Devices_and_Applications )

Cisco, the industry leader in IoT platforms, offers an integrated solution for the management of IoT devices. The Cisco IoT/M2M architecture is composed of four layers; some are similar to those described in the conventional Cisco network architecture.

![](img/3531370aa21067bbdc45128741d34edb_50_0.png)

Figure 4.4: IoT/M2M network architecture layers

Source: https://www.cisco.com/c/en/us/about/security-center/secure-iot-proposed-framework.html

The Internet of Things covers a wide range of industries and use cases across cross-platform deployments and cloud systems in real-time. Hence, there exist certain standards and protocols to allow the communication between the devices and servers in more interconnected ways. The major IoT protocols at various layers in the IoT architecture stack are displayed in the following figure (Source: Simon Ford - Director of IoT Platforms ARM):

![](img/3531370aa21067bbdc45128741d34edb_51_0.png)

Fig 4.5: Major IoT protocols at various layers

Many communication technologies such as Wi-Fi, Bluetooth, Zigbee and cellular are well known, but there are also several new emerging networking options such as Thread used as an alternative for home automation applications, and Whitespace TV technologies being implemented in major cities for wide area IoT-based use cases.

## 1. WI-FI

Wi-Fi is the choice for many developers because of its wide existing infrastructure as well as its ability to handle high quantities of data with rapid data transfer.

## 2. BLUETOOTH

Bluetooth, a short-range communication technology is expected to be the key for wearable products in particular, connecting to the IoT via a smartphone in most of the cases. The new Bluetooth Low Energy (BLE) or Bluetooth Smart is a significant protocol for IoT applications as it offers significantly reduced power consumption.

## 3. ZIGBEE

Zigbee, like Bluetooth, has a large installed base of operation, more in industrial settings. Zigbee/RF4CE offers low-power operation, high security, robustness and high scalability with high node counts and is well positioned to take advantage of wireless control and sensor networks in M2M and IoT applications.

## 4. CELLULAR

IoT applications requiring operations over longer distances can leverage GSM/3G/4G cellular communication capabilities. Cellular is capable of sending high quantities of data, especially for 4G; however, the expense and power consumption is deemed to be high for many applications. Cellular can be ideal for sensor-based low-bandwidth-data projects that will send very low amount of data over the Internet.

## 5. LOWPAN

6LowPAN (IPv6 Low-power wireless Personal Area Network) is a network protocol that defines encapsulation and header compression mechanisms.

## 6. Thread

Thread is a relatively new IP-based IPv6 networking protocol aimed at the home automation environment. It is primarily designed as a complement to Wi-Fi as it recognizes that while Wi-Fi is good for many consumer devices that it has limitations for use in a home automation setup.

## 7. LoRaWAN

LoRaWAN targets wide-area network (WAN) applications and is designed to provide low-power WANs with features specifically needed to support low-cost mobile secure bi-directional communication in IoT, M2M and smart city and industrial applications. LoRaWAN is optimized for low-power consumption and can support large networks with millions and millions of devices.

| Protocol | Standard | Frequency | Range | Data Rates |
|---|---|---|---|---|
| Wi-Fi | 802.11n | 2.4GHz and 5GHz | Approximately 50m | 600 Mbps maximum, but 150-200 Mbps is more typical |
| Bluetooth | Bluetooth 4.2 core specification | 2.4GHz (ISM) | 50-150m (Smart/BLE) | 1Mbps (Smart/BLE) |
| ZigBee | ZigBee 3.0 based on IEEE802.15.4 | 2.4GHz | 10-100m | 250kbps |
| Cellular | GSM/GPRS/EDGE (2G), UMTS/HSPA (3G), LTE (4G) | 900/1800/1900/2100MHz | 35km max for GSM; 200km max for HSPA | 35-170kbps (GPRS), 120-384kbps (EDGE), 384Kbps-2Mbps (UMTS), 600kbps-10Mbps (HSPA), 3-10Mbps (LTE) |

| Protocol | Standard | Frequency | Range | Data Rates |
|---|---|---|---|---|
| 6 Low-PAN | RFC6282 | Used over a variety of networking media, including Bluetooth Smart (2.4GHz) or Zigbee or low-power RF (sub-1-GHz) | N/A | N/A |
| Thread | Thread, based on IEEE802.15.4 and 6Low-PAN | 2.4GHz (ISM) | N/A | N/A |
| LoRa WAN | LoRaWAN | Various | 2-5km (urban environment), 15km (suburban environment) | 0.3-50 kbps |

Fig 4.7: Different IOT protocols and their parameters

IoT will impact all areas cutting across consumer and industrial usage. While smart home, wearables and personal trackers are good use cases for consumers, IoT can be leveraged across all areas of design, manufacturing, storage, transportation, maintenance and live performance tracking through the value addition cycle of products and services to dramatically enhance the productivity and profitability of organizations.

The different prominent application domains in Industrial and Consumer IoT applications are summarized in the following image:

![](img/3531370aa21067bbdc45128741d34edb_55_0.png)

Fig 4.8: IOT classifications and use cases

As of now, IoT is extensively used in the following areas:

- Tagging and monitoring the movements and performance parameters of automobiles, animals, accessories, and dependents.
- Information collection and dissemination for optimum agricultural output.
- Automatic meter reading and energy utilization management for all electrical devices.
- Security and surveillance systems for a wide variety of establishments and connected homes.
- Building automation and maintenance services.
- Machine to Machine connectivity offering communication, ecommerce and collaboration opportunity through high levels of automation.
- Smart cities to effectively manage delivery of efficient products and service across every area that touches a citizen’s life.
- Telemedicine and healthcare for remotely measuring and tracking the health parameters to offer quick resolution to patients in remote areas.

The key steps for implementing IIOT projects are displayed in the following image:

| 5 Steps to start and optimize IIOT Projects |
|---| 
| Build partnerships |
| Clarify business outcomes and ROI |
| Start small |
| Security first |
| Architect for analytics |

*Fig 4.9: Steps to implement IIOT projects*

The paper, Blockchain Technologies for the Internet of Things: Research issues and challenges, Mohamed Amine Ferrag, Makhlouf Derdour, Mithun Mukherjee, Member, IEEE, Abdelouahid Derhab, Leandros Maglaras, Senior Member, IEEE, Helge Janicke highlight the various studies undertaken across a number of IoT related domains that are impacted by the blockchain implementation.

Centralized platforms can offer innumerable services through cloud-based platforms by converting every dumb object into intelligent and communicable systems. Governments across the world have realized the potential of IoT and are implementing various projects under the category of ‘Smart Cities’, while service, technology and infrastructure providers are leveraging advanced technologies and innovation to dramatically optimize and enhance the capability and productivity of systems across every field we can think of.
