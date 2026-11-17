![](bbox=[0.17, 0.08, 0.88, 0.39])

Figure 11.4 Overall wiring diagram for wheelchair fall detection proposed system.

# 11.5.1 ESP32 DEV Module

The ESP32 Dev Module is a versatile microcontroller board. It features built-in Wi-Fi and Bluetooth connectivity. It is ideal for IoT applications, prototyping, and development. It is powered by the ESP32 chipset, offering high performance. It supports a wide range of sensors and peripherals.

# 11.6 Experimental Results

Hardware: The hardware implementation of the wheelchair fall detection with IoT system involved integrating the system directly into the wheelchair itself. The wheelchair is equipped with an ESP32 microcontroller, a gyroscope sensor, a buzzer, and a secure button. These components work in conjunction to detect falls and transmit relevant data for analysis and alerting purposes. The gyroscope sensor and buzzer are affixed to the inner left-hand side of the wheelchair. These sensors are linked to a breadboard. Once a person is seated in the wheelchair, the sensors activate. The collected data from the wheelchair fall detection system are then sent to the Blynk mobile application. Both the user and authorized individuals can monitor the wheelchair’s status using the application. The system