# Chapter 17

![](bbox=[0.13, 0.11, 0.88, 0.57])

Figure 17-4: SourceUSB's application shows USB I/O requests at a host computer. These requests are for mouse communications.

But a software analyzer can't show anything that the host-controller or hub hardware handles on its own. For example, the analyzer won't show how many times an endpoint NAKed a transaction before returning an ACK or the precise time a transaction occurred on the bus.

Some software analyzers use a filter driver that loads when the operating system loads the driver for the device being monitored. Because the filter driver isn't loaded until the host has enumerated the device, the analyzer can't show the enumeration requests and other events that occur at device attachment.

Sourcequest, Inc.'s SourceUSB is a software analyzer that records USB I/O requests and other events, including enumeration requests. You can view the