
This unit transmits temperature and humidity data via a radio transceiver‑equipped wireless information unit (WIU) and wireless sensor unit (WSU) (`[Holliday et al., 1990](#ch27.xhtml#ref27_1)`). Zigbee‑based wireless sensor networks (WSN) are used to accomplish this. There is a standard at Western Illinois University (WIU) for providing data to online services. Even though this technology succeeds in automating tasks, there are drawbacks (`[Knight et al., 2017]`). The solenoid valve in this study regulates the opening and closing of the valve, while the microcontroller manages the signal in the sensor‑based IoT irrigation system. The water process is initiated and the water flow is regulated in response to changes in the ambient temperature and humidity. When the humidity is low, water your plants; when the moisture content is back to normal, stop watering. Microcontrollers and GSM are interfaced via `MAX232` (`[Knight et al., 2015]`). Although automatic water use is the desired outcome, this technology accomplishes it in a more sophisticated manner (`[Marthaler et al., 2023](#ch27.xhtml#ref27_3)`). In order to optimize agricultural water use, this study presents an automatic water management and field monitoring system (`[Knight et al., 1992](#ch27.xhtml#ref27_2)`). The automatic systems are based on WSN (`[Brar et al., 2022](#ch27.xhtml#ref27_21)`). A wireless network of temperature and humidity sensors that are placed in the field is a feature of the system. Data is transferred from the sensor to the microcontroller (`[Khattar et al., 2020](#ch27.xhtml#ref27_8)`) via the Zigbee protocol (`Attema, 2007`). Farmers receive information via a `PIC 18F77` microcontroller with GPRS support and a GSM modem (`[Singh et al., 2020](#ch27.xhtml#ref27_12)`). The `PIC` microcontroller’s usage of RISC determines how long the program will run (`Gutiérrez, 2013`).

The author `Teka (2019)` has developed an `intelligent` drip irrigation system that is controlled by an `ARM9` processor and is automatic. The soil’s pH and nitrogen content are continuously shifting throughout this process. `GSM` modules are employed for situational monitoring and control (`[Anand et al., 2015](#ch27.xhtml#ref27_9)`, `2017`). In this instance, the soil’s moisture content is estimated using an acoustic‑based technique. This strategy’s primary goal is to speed up the measurement of soil moisture (`Prasad et al., 2018`). According to `[Li et al. (2016) and 2020](#ch27.xhtml#ref27_11)`, the two primary variables in this process are soil water saturation and sound speed. It was thus discovered that the speed of sound varies with soil type and that it diminishes with increasing soil moisture. Farmers are unable to use this technique, despite the fact that it can be used to quickly determine the moisture content of a soil sample (`[Mallikarjuna et al., 2022](#ch27.xhtml#ref27_13)`). The system was developed using an automated irrigation system equipped with a soil moisture sensor and a smartphone or tablet (`[Mallikarjuna, 2022](#ch27.xhtml#ref27_15)`). With the help of this technology, people can conserve water and increase water duration control. For calibration, the model was tested with a range of crops and soil samples at varying soil moisture levels.

Nevertheless, by utilizing more soil samples from various locations and climates, this outcome could be enhanced. We’ll look at other soils in addition to soil moisture. `Singer et al. (2021)` investigates electronic gadgets that gather and transmit physical data to users via IoT. Finding quick fixes for issues and presenting workable solutions are the goals of this project. IoT‑based smart agriculture can make use of 4G to 8G communication (`Sandeep et al., 2023`). According to `Kai et al. (2022)`, security‑enhanced features are crucial for safeguarding sensitive data in IoT‑based smart farming. It is possible to use heterogeneous nodes to gather data from agricultural fields (`Shabana et al., 2023`).

## Objectives
This paper is aimed to design a framework for the analysis of soil moisture using Raspberry Pi‑based on IoT. The objective of the paper is to construct a system which can be utilized to optimize soil parameters, reduce water waste and boost better crop yield. Another objective is to publish data on Telegram which enables farmers to increase crop yield.

## Proposed methodology
Numerous technologies are at one’s disposal, such as video smart working, code management systems, smart home offices, electronic products, and more. External assistance has a lot of advantages. Such as being RFID (Radio Frequency Identification) labeled, being shrewd, and so on. Background information for this paper comes from a questionnaire survey as well as a FADN agricultural product. Based on their business structure, the businesses studied can be classified as natural persons or legal entities. Natural person businesses made up 14.3% of the agricultural entities studied. Legal entities accounted for 85.7% of the total.

System starts with deployment of sensor circuitry consist specific set of sensors and Raspberry Pi Pico collect data from farming land, if data gathered successfully then it is transmitted to remote location. After that there is optimization of the crop data to increase crop yield and finally important information regarding published data published on telegram as shown in `[Figure 27.1](#ch27.xhtml#fig27_1)`.

```
![Figure 27.1 Flowchart of soil moisture detection monitoring system](images/fig27_1_C.jpg)
```

`[Figure 27.1](#ch27.xhtml#R_fig27_1)`

The plant part is the first section, and it has sensors for detecting the environment around the plant. The DHT11 soil sensor is a cheap soil moisture sensor that can be used to track soil moisture, just like other soil moisture sensors. The moisture sensor outputs a high level when the soil is dry, and a low level otherwise. In contrast to other soil moisture sensors, this one has a variable sensitivity and gives the IoT hub raw data.

### IoT hub
You can connect your devices to the internet via IoT hub service which has devices to communicate in both directions. The IoT hub connects various services to the real world. The data from the sensors is updated on a regular basis. The primary function of the IoT hub is to monitor and connect all connected IoT devices.

### Analytics in streams
The IoT hub offers the service of stream analytics, which is necessary for data transmission from the IoT hub. Basically, this service’s fundamental characteristic is its capacity to stream millions of records per second, or millions of pieces of data, in real time.

`[Figure 27.2](#ch27.xhtml#fig27_2)` shows the system execution in which system starts collecting data and transmit it to remote location for optimization and then published on telegram. Also, `[Figure 27.2](#ch27.xhtml#fig27_2)` shows the system description, the Raspberry Pi Pico, node MCU, and soil moisture sensor are among the components used in this system.

```
![Figure 27.2 The proposed system's component parts](images/fig27_2_B.jpg)
```

`[Figure 27.2](#ch27.xhtml#R_fig27_2)`

### Raspberry Pi
`[Figure 27.3](#ch27.xhtml#fig27_3)` explains Raspberry Pi which is a little computer. Simply described, the Raspberry Pi is a robust and portable computer with an ARM processor. Moreover, the Raspberry Pi 3 Model B includes HDMI, Ethernet, USB ports, and Wi‑Fi modules. RISC OS Pi is one of the Raspberry Pi’s operating systems. It supports multimedia applications and has a compact computer‑like appearance. This is true due to HDMI and graphics support. Yet, as a result of its instead of an HDD or a solid‑state drive, we can utilize a micro SD card to start the OS of the Raspberry Pi Pico soil moisture sensor (SSD).

```
![Figure 27.3 Circuit details of Raspberry Pi](images/fig27_3_C.jpg)
```

`[Figure 27.3](#ch27.xhtml#R_fig27_3)`
