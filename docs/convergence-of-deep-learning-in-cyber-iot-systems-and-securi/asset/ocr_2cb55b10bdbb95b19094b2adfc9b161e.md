![](bbox=[0.125, 0.105, 0.875, 0.395])

**Figure 12.6** Devices connected with MQTT.

The broker service provider determines the quantity of “customers” that can be connected to the broker. In fact, it has the ability to reach a large number of customers who are constantly publishing and subscribing. It is not just that there are a lot of connected devices, but that any one of them can access the data of any other one at any moment. As a result, the potential uses for this readily available data are virtually limitless. It is necessary to enter the server name (io.adafruit.com), port number (1883), username, and unique AIO key in the Arduino IDE, as the feed name and the password credential along with the SSID of an Access point for WiFi that has access to the Internet, in order to subscribe or publish to the MQTT server. Compilation and upload of code to the ESP32 have completed once everything is set up. You will need an MQTT library in order to use Adafruit IO’s MQTT API. It is called MQTT, or message queue telemetry transit, and it is supported by Adafruit. Adafruit’s IO may be used with Python, Ruby, and Arduino. However several clients are connected with MQTT is explained in Figure 12.6.

It is possible to use MQTT in libraries. You should look for a MQTT library that supports the MQTT 3.1.1 protocol across multiple operating systems and language.

+   - Arduino: The Adafruit MQTT
- Python: Adafruit IO Python includes an MQTT Client.