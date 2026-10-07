
256 CONVERGENCE OF DL IN CYBER-IoT SYSTEMS AND SECURITY

**Table 12.1** ESP32 NodeMCU Feature.

| Names of the parts | Specification |
| :--- | :--- |
| ROM flash | 4M |
| Programming language for creating scripts | 2 buttons (reset and flash) |
| Total GPIO pins | 17 GPIO |
| ADC | Ranging from 1 to 10 bits |
| Operation modes | Sleep mode, Deep sleep modes and Active modes |
| Operating voltage | Approx. 3.3 V |
| Internet | IEEE 802.11 b/g/n Wi-Fi |
| programmer | CP2102 USB-to-UART |
| Module | ESP-12 |

## 12.4.1 Relay

It is a model based on communication between sender and receiver’s probabilistic outcomes, supported by few intermediary relay inputs in the relay channel in information theory. Figure 12.4 below shows a relay switch with three inputs and Table 12.2 shows the features of two-input relay circuit individually.

![](img/081dc7f102a3793cb08980a6e19b8f17_279_0.png)

**Figure 12.4** 2-input relay.

### Table 12.2 Features of relay.

| Name of components | Specification |
| :--- | :--- |
| Max. flow through a relay | AC250V: 10A |
| Total no of relays | 2 |
| Maximum possible current for each relay | 20mA |
| Minimum operating voltage | 5V |
| Contact current capacity of relay | DC30A |

## 12.4.2 DHT11

An inexpensive digital sensor is the DHT11 for measuring temperature and relative humidity. Humidity and temperature readings may be taken instantly using this sensor, which can be used with any microcontroller. It has a sensor where humidity is conductive in nature for the measurement of temperature, well as a thermistor. The humidity-sensing capacitance uses a dielectric between both electrodes. The capacitance value varies with variations in relative humidity. Analog resistance levels are measured and processed by the integrated circuit. Figures 12.5 depicts the basic diagram of DHT11.

![](img/081dc7f102a3793cb08980a6e19b8f17_280_0.png)

**Figure 12.5** DHT11.

![](img/081dc7f102a3793cb08980a6e19b8f17_281_0.png)

**Figure 12.6** Devices connected with MQTT.

The broker service determines the quantity of “customers” that can be connected to the broker. In fact, it has the ability to reach a large number of customers who are constantly publishing and subscribing. It is not just that there are lot of connected devices, but any one of them can access the data of any other at any moment. As a result, the potential for this available data are virtually limitless. It is necessary to enter the server name (io.adafruit.com), port number (1883), username, and unique API key in the Arduino IDE, as the feed name and the password along with the SSID of an Access point for WiFi that has access to the Internet, in order to subscribe or publish to the MQTT server. Compilation and upload of code to the ESP32 completed once everything is set up. You will need an MQTT library to use Adafruit’s MQTT API. It is called MQTT, or message queue telemetry transport, and it is supported by Adafruit. Adafruit’s IO may be used with Python, Ruby, and Arduino. However, several clients connected with MQTT is explained in Figure 12.6.

It is possible to use MQTT libraries. You should look for a MQTT library that supports the MQTT 3.1.1 protocol across multiple operating systems and languages.

- Arduino: The Adafruit MQTT
- Python: Adafruit IO includes an MQTT Client.

## MQTT-BASED IMPLEMENTATION OF HOME AUTOMATION SYSTEM

![](img/081dc7f102a3793cb08980a6e19b8f17_282_0.png)

**Figure 12.7** MQTT broker publish-subscribe.

- CircuitPython: Adafruit IO CircuitPython includes an MQTT Client class, IO_MQTT.
- MicroPython: MicroPython devices can connect to Adafruit using MQTT
- Ruby: Adafruit IO Ruby includes an MQTT client.

“If this, then that” is a programming conditional statement, that is where the name IFTTT comes from. The company's application, devices information, and services are all connected to the same software platform. We can use IFTTT with absolutely no change. For the purpose of sending notifications, we implemented an IFTTT server. Figure 12.7 describes the pub-sub model of MQTT broker and Figure 12.8 is the screenshot of Arduino IDE.

Our project is based on home automation. We tried to control different electronic devices from outside the home from anywhere in the world using MQTT protocol. We divided our projects into 2 parts:

i) Controlling Home Devices from Outside
In this part basically, we tried to control a bulb (electronic device) that is present inside our home from outside. To implement this we used one MQTT server called Adafruit.io. There are many other MQTT servers present, but we chose this because it has a free trial and is easy to implement. Here, as mentioned in Figure 12.9, we connect a Bulb to the NodeMCU Wi-Fi module through a relay circuit. We create a feed (light) on the Adafruit.io dashboard. According to MQTT protocol if we subscribe to that feed, then that value will be reflected in the device connected to that feed. It is just like Youtube. In Youtube, if we subscribe to a channel, then when this channel publishes a video that video comes in our Youtube home page.

## Introduction to Arduino IDE

![](img/081dc7f102a3793cb08980a6e19b8f17_283_0.png)

**Figure 12.8** Arduino IDE for development.

## MQTT-BASED IMPLEMENTATION OF HOME AUTOMATION SYSTEM 261

![](img/081dc7f102a3793cb08980a6e19b8f17_284_0.png)

**Figure 12.9** Controlling home devices from outside.

Suppose we are outside the home and forget to switch off our light. Then we can easily operate household appliances through the MQTT server.

ii) Room Temperature and Humidity Measurement
Controlling electronic devices in homes and businesses has never been easier thanks to the Internet of Things (IoT). As a bonus, we can access any data from anywhere in the world and analyze it in graphical manner. A simple room temperature monitoring system is implemented in our project. We use the NodeMCU module to read temperature and transmit it to the IoT cloud. The DHT11 sensor reads a value every 30 seconds and publishes that value to Adafruit’s dashboard, which we can access from location in real time.

262 CONVERGENCE OF DL IN CYBER-IoT SYSTEMS AND SECURITY

## 12.5 Results and Discussions

The cloud service eliminates the need for a local gateway, making the proposed system more secure than the current systems. Users and devices benefit from the broker cloud (Adafruit) in terms of processing speed. Cryptographic operations between different devices are also reduced by this method. SVC, a machine learning algorithm, learns from users' usage history in order to predict what devices they will need in the future.

To make our home more secure, we also implement a notification system during emergencies. Here we used SMTP server (IFTTT Maker). The DHT11 sensor continuously reads temperature from the environment and publishes that value in the Adafruit Dashboard. During that time, we also compare that value falls in the range we mentioned. If the room temperature is greater than the maximum range or less than the minimum range, then it will send a notification mail through IFTTT as an alert, so that we can take precautions. Figure 12.10 represents detailed results of the MQTT Broker Dashboard.

We created different feeds for controlling our devices and publishing the data.

- 1. The Light1 is used to control the light connected to NodeMCU ESP32. If we toggle the “Light” feed to “ON”, then the Light will be switch on and if we toggle the “Light1” feed to “OFF”, the Light will be switch off. And all the results of this feed are also stored in the Adafruit log in Figure 12.11.

![](img/081dc7f102a3793cb08980a6e19b8f17_285_0.png)

**Figure 12.10** Adafruit dashboard.
