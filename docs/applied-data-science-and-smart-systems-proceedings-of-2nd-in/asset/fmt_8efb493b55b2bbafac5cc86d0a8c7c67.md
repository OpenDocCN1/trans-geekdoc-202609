
The IoT system cannot function without sensors, just like the human heart cannot without blood. It receives physical parameters from the outside environment, converts them into electrical systems, and sends them to a primary controller, such as a Raspberry Pi. The soil moisture sensor was one of the sensors employed in this system. The soil level may be determined with this sensor. The signal produced from this sensor can either be analogue or digital. It features two copper electrodes that are used to monitor soil moisture. [Figure 27.4](#ch27.xhtml#fig27_4) show the Soil moisture sensor Esp8266.

![Figure 27.4 ESP 8266 with sensors](images/fig27_4_C.jpg)

[Figure 27.4 ESP 8266 with sensors](#ch27.xhtml#R_fig27_4)

### Node MCU (ESP8266)

The ESP8266 (Node MCU) is a microcontroller with an integrated Wi-Fi module, as depicted in [Figure 27.4](#ch27.xhtml#fig27_4). It is a 30-pin device with 17 GPIO pins. To receive data and transmit it to the associated devices, these GPIO pins are linked to a range of sensors as shown in [Figure 27.5](#ch27.xhtml#fig27_5).

![Figure 27.5 Node MCU (ESP 8266)](images/fig27_5_C.jpg)

[Figure 27.5 Node MCU (ESP 8266)](#ch27.xhtml#R_fig27_5)

The node MCU (ESP8266) contains 4MB of flash memory and 128KB of RAM for storing programs and data. The node MCU maintains the code (ESP8266). The data that the node MCU (ESP 8266) receives from various sensors is compared to data that has already been saved on the device.

It transmits pulses to the relay module, which functions as a switch to turn the pump on and off, based on the data that has been recorded. The node MCU (ESP8266) has an operating frequency range of 80–160 MHz and a voltage range of 3–3.6V.

## System development

[Figure 27.6](#ch27.xhtml#fig27_6) show the farming automation system can be constructed using the IoT to reduce water waste and boost crop yields. Using a soil moisture sensor with a Raspberry Pi Pico module and node MCU, the water level is monitored and recorded. The soil stores information about the soil’s moisture status throughout time. The Node MCU takes data in analogue values and analyses it before sending it to the Raspberry Pi Pico via the telegram program, where the user can observe the current moisture level. This is significant since the plant requires a lot of water. For a decent yield, it needs to be watered at a precise time.

![Figure 27.6 Test result](images/fig27_6_C.jpg)

[Figure 27.6 Test result](#ch27.xhtml#R_fig27_6)

### Test strategy

All objects are connected to the IoT network in order to achieve interconnectivity and data transmission capabilities over the internet and traditional media. Following that, it was perceived as a wide range of high-end devices and workplaces that were unaffected by the district. “External enablement” and “internal intelligence” were included. Examples of devices used to cultivate inner wisdom include digital control systems, smart home offices, smart video roles, mobile devices, technology systems, meters, etc. Outside enablement refers to a wide range of benefits, such as items branded with RFID (Radio Frequency Identification), as well as smart people and cars equipped with wireless terminals.

## Results and discussion

The Raspberry Pi Pico is the system’s brain. The Raspberry Pi Pico has undergone numerous updates and added new functionality. Make use of the sensor attached to the Raspberry Pi Pico board to determine the difference between the outputs. The Raspberry Pi board receives the output signal. The Raspberry Pi is the system’s brain. The Raspberry Pi now boasts a plethora of updated features. ARM-based computers are more powerful and lighter due to additional features like increased connectivity, increased I/O, and improved power efficiency. Use a sensor that is attached to the Raspberry Pi board to determine the attack’s variance. The humidity is determined by the cold signal circuit with potentiometer if the comparator’s output is high.

[Figure 27.7](#ch27.xhtml#fig27_7) depicts the yield and response graph displaying water and yield information. A signal is sent to the Raspberry Pi Pico board from the output. The Raspberry Pi is the system’s brain. The Raspberry Pi now boasts a plethora of updated features. Utilizing the sensor attached to the Raspberry Pi board, determine the resistance difference. The humidity is determined by the cold signal circuit with potentiometer if the comparator’s output is high. The Raspberry Pi board receives the output signal. The Raspberry Pi is the system’s brain. The Raspberry Pi now boasts a plethora of updated features. The Raspberry Pi board receives the output signal. The Raspberry Pi serves as the system’s brain.

![Figure 27.7 Field chart with irrigation of data](images/fig27_7_C.jpg)

[Figure 27.7 Field chart with irrigation of data](#ch27.xhtml#R_fig27_7)

[Figure 27.8](#ch27.xhtml#fig27_8) shows the chart with population of different countries. Human population is increasing at a very fast rate. To meet the growing food demands of people, we need to optimize soil quality for better and enhance crop production.

![Figure 27.8 Chart with population of different coun-tries](images/fig27_8_C.jpg)

[Figure 27.8 Chart with population of different coun-tries](#ch27.xhtml#R_fig27_8)

Many enhancements and new functionality have been added to the Raspberry Pi. Improved characteristics include better power consumption, higher connection, and expanded I/O, resulting in a more powerful, tiny, and light ARM-based computer. Utilizing the sensor that is attached to the Raspberry Pi board, determine the resistance difference. The comparator receives the signal, and a signal conditioning circuit (potentiometer, for example) determines the humidity. The Raspberry Pi board receives the output signal if the comparator’s output is high. As a result, water systems use water resources as effectively and efficiently as possible to support agriculture. Air is what the outlet is for, and it needs to be forced far down into the ground. [Figure 27.8](#ch27.xhtml#fig27_8) demonstrate chart with population of different countries. [Figure 27.9](#ch27.xhtml#fig27_9) shows different output representations as per the given data.

![Figure 27.9  Different output representations as per the given data](images/fig27_9_C.jpg)

[Figure 27.9  Different output representations as per the given data](#ch27.xhtml#R_fig27_9)

## Conclusion

It is advised to use smart monitoring to automate the area’s major crops and cut down on water waste. The technology monitors variations in soil moisture and assesses the impact on plant water requirements. The farmer receives a notice on his smartphone, and with a single button press, he can check the water level. Furthermore, the system includes an app that can be used by the farmer to view Sensor data is analyzed statistically, and changes in sensor readings are tracked over time. In addition, the system may be adjusted for various plant species thanks to a range of options in his software and mobile app. This gives the user the option to identify the kind of plant being produced and get a threshold number that is more accurate.

A common and useful application for agricultural and environmental monitoring is the analysis of soil moisture using a Raspberry Pi based on the IoT. The standard components of this system are sensors to gauge soil moisture, a Raspberry Pi for data processing, and IoT tools to allow for remote monitoring and management.

An effective strategy to manage agricultural resources and make data-driven decisions is to implement an IoT-based soil moisture monitoring system using a Raspberry Pi. This will ultimately result in higher crop yields and more environmentally friendly farming methods. For real time collection and transit, system should be more continuous in terms of internet, this is the limitation of our system. Another limitation is high cost of Raspberry Pi as compared to Arduino UNO.
