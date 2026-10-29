# 4.3.2. IoT platforms interoperability approach

A central goal of the BIG IoT architecture is to facilitate the integration of IoT platforms through the BIG IoT ecosystem. Both infrastructure as well as device-level platforms are targeted. From an architectural perspective, specifically considering the implementation of the BIG IoT API and integration with marketplaces, we have identified the following types of IoT platforms:

Type 1: Server Infrastructure or Cloud based IoT Platform assumed to be “always online” and anytime accessible by applications or services via the Internet.

Type 2: Device-level IoT Platform, hosted on devices that are unconstrained⁴ with respect to communication, compute and memory resources assumed to be “always online” whereby connectivity and communication resources is assumed to be charged on a “flat-rate” plan.

Type 3: Device-level IoT Platform, hosted on devices that are unconstrained with respect to communication, compute and memory resources, but are “not always online”.

Type 4: Device-level IoT Platform, hosted on devices that are unconstrained with respect to communication, compute and memory resources, but are connected to the Internet via a “pay-per-use” plan, Type 4 devices are often also of Type 3.

Type 5: Device-level IoT Platform, hosted on devices that are constrained⁵ with respect to communication, compute and/or memory resources.

4. Unconstrained in this context means that the device will be able implement/use the BIG IoT API, which will be based on typical Web/Internet technologies (e.g. HTTP, WebSockets). An example of an unconstrained device is a Raspberry Pi. Also, other devices that are able to run Linux and support typical Web/Internet technologies are considered unconstrained in this context. A micro-controller based Sensor is not considered unconstrained.

5. Constrained in this context means with respect to the implementation of the BIG IoT API, which will be based on typical Web/Internet technologies (e.g. HTTP, WebSockets). An example of constrained devices are low-cost sensors, using a micro-controller. A Raspberry Pi is not considered a constrained device.