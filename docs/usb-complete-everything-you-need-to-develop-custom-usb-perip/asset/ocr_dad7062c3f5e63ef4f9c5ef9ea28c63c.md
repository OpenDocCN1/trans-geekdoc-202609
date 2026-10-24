requests along with additional information about the system’s host controllers, the devices on the host controllers’ buses, and the drivers assigned to each host controller and device. Figure 17-4 shows logged requests and additional information about the request in the selected row.

The SourceUSB application can also display a tree of all of the system’s host controllers and their attached devices and provide information about the drivers assigned to each host controller and device. As with a hardware analyzer, you have great flexibility in selecting what information you want to log and view.

Another software-only analyzer is the SnoopyPro project, free with source code from www.sourceforge.net.

# Traffic Generators

Sometimes it’s useful to be able to control bus traffic and signaling beyond what you can do from host software and device firmware. Some higher-end protocol analyzers can also function as traffic generators that emulate a host or device and give you precise control over the traffic that the emulated host or device places on the bus. In addition to generating valid traffic, a traffic generator can introduce errors such as bit-stuff and CRC errors. Two protocol analyzers with these abilities are Catalyst Enterprises, Inc.’s SBAE-30 Analyzer/Exerciser and LeCroy Corporation’s CATC USBTracer/Trainer. Another option is RPM Systems’ Root 2 USB Test Host, which emulates a USB host and enables you to specify traffic to generate on the bus, control the bus voltage, and measure bus current.

# Testing

The USB-IF and Microsoft offer testing opportunities for developers of USB devices and host software. Passing the tests can earn a product the right to display the Certified USB logo and/or the Microsoft Windows logo. A logo can give users confidence that a device is thoroughly tested and reliable. A driver that passes Microsoft’s tests can be digitally signed, which gives users confidence that the driver will work without problems.