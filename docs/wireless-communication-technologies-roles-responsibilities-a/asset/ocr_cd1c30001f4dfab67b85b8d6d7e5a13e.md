the backbone of IoT sensor communication, facilitating the real-time transmission
of data from diverse IoT nodes to centralized processing units [17].
Various wireless communication protocols have been adopted to cater to the
specific requirements of IoT applications. Wi-Fi, known for its high data transfer
rates, is commonly used in IoT deployments involving multimedia streaming and
real-time monitoring. On the other hand, Zigbee and Bluetooth Low Energy (BLE)
are preferred for low power, short-range communication, making them suitable for
battery-operated IoT devices such as wearables and smart home sensors [18]. Long
Range (LoRa) and Narrowband IoT (NB-IoT) technologies have gained prominence
in IoT applications that demand long-range communication and energy efficiency,
making them suitable for smart agriculture, environmental monitoring, and smart
cities. Security and privacy are critical concerns in IoT sensor communication. As
wireless communication forms the basis for data exchange in IoT, robust security
measures are essential to protect against potential threats and breaches [19].

# 4.3.1 IoT COMMUNICATION PROTOCOLS

In the context of IoT Sensor Communication Using Wireless Technology, the
selection of appropriate communication protocols is a critical aspect of ensuring
efficient and reliable data exchange among interconnected devices and sensors.
Various IoT communication protocols have been developed to address the diverse
requirements of different applications, offering unique advantages and capabilities
to support the ever-expanding IoT ecosystem.

MQTT is a lightweight and efficient publish-subscribe messaging protocol that
excels in low-bandwidth and high-latency networks, making it ideal for IoT
applications [20]. It minimizes data transmission overhead, reducing power con-
sumption for battery-operated IoT devices. MQTT's simplicity and scalability have
led to its widespread adoption in smart home automation, industrial automation,
and telemetry systems [21]. Designed for resource-constrained devices, CoAP is a
lightweight application-layer protocol that operates over UDP, providing efficient
communication in IoT networks [22]. It is particularly suitable for IoT devices with
limited processing power and memory, such as sensors and actuators. CoAP's
simplicity and support for various message types enable seamless integration with
HTTP-based applications, extending its usability across multiple domains, including
smart cities and healthcare [23]. AMQP is a robust and feature-rich protocol designed
for high-performance messaging in enterprise-scale IoT deployments [24]. It provides
reliable message delivery, enabling complex communication patterns in large-scale
IoT systems. AMQP's support for message queuing, routing, and security features
has made it a preferred choice for mission-critical IoT applications, such as asset
tracking and supply chain management [25].

Though primarily associated with web
communication, HTTP has found application in IoT due to its ubiquity and
compatibility with existing internet infrastructure [26]. It allows seamless integration
of IoT devices with web services and cloud platforms, facilitating data exchange and
remote device management. However, HTTP's high overhead makes it less suitable
for resource-constrained IoT devices and low-bandwidth networks. DDS is a
middleware standard designed for real-time and mission-critical IoT applications