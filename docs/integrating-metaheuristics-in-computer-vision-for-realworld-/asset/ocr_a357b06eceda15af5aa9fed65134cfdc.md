# 12.3.3 LPG Detecting System

LPG is common in use among the household and the commercial purposes like cooking, lighter, etc. LPG consists of Propane and Butane and some other gases which is highly inflammable. If there is a leakage in LPG gas in house or any other area it will cause a fire accident, the area affect by it will be also in vast expense. An ethanol is added to the LPG so that most people can easily detect the losses as it has odour. Though it may work if there is people in the house, what if no one is nearby. In these cases, a gas leak detector becomes vital and helps protect people from the dangers of gas leaks. So, with IoT we can make a security system which can detect, off the regulator, switch on the ventilation fans and send user an emergency message.

# Components Required

+   1. NodeMCU ESP866
+   2. MQ2 sensor
+   3. Buzzer
+   4. Relay
+   5. DC motor

# 12.3.3.1 Materials Description

# 12.3.3.1.1 NodeMCU ESP8266

NodeMCU is a microcontroller which has a Wi-Fi module, which is the special thing about this chip. It can be encoded using Arduino IDE. Wi-Fi is nothing but a Wireless radio wave which can used to send and receive information. In this project, nodeMCU is used so that we can communicate with the user using Wi-Fi. When the system senses the leakage, it needs to stop the leakage and alert the surrounding first. Then a message is sent to the user through Wi-Fi. The corresponding code must be loaded into the microcontroller, to which WI-FI is connected.

# 12.3.3.1.2 MQ2 Sensor

MQ2 sensor is highly sensible to butane, propane, LPG, and smoke. So, it is used in this project. It is made up of SnO2 which is highly reactive to LPG gas. The sensors conductivity is increased with increase in concentration of gases. It gives analog output.

# 12.3.3.1.3 Buzzer

Buzzer is device used to make noise, here it is used to make sound when the LPG is detected that alert the people.

# 12.3.3.1.4 Relay

Relay switch is used to control the main switch board using the microcontrollers. It gives connection without disturbing the main. Here we use to switch on the ventilation fan.