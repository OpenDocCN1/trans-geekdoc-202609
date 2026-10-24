# Bandwidth Use of Low- and Full-speed Devices

Because a 2.0 hub acts as a host controller in managing transactions, low- and full-speed devices share 1.x bandwidth only with devices that use the same transaction translator. So if two full-speed devices connect to their own 2.0 hubs on a high-speed bus, each device can use all of the full-speed bandwidth it wants. When the hub converts to high speed, the 1.x communications will use little of the high-speed bandwidth.

However, for bulk transactions, the extra transaction with the host in each split transaction can slow the rate of data transfer with a full-speed device on a busy bus that is also carrying high-speed bulk traffic.

Many hubs provide one transaction translator for all ports, but a single hub can also have a transaction translator for each port that connects to a low- or full-speed device.

# The Hub Controller

The hub controller manages communications between the host and the hub. The communications include enumeration along with other communications and actions due to events at downstream ports.

As it does for all devices, the host enumerates a newly detected hub to find out its abilities. The hub descriptor retrieved during enumeration tells the host how many ports the hub has. After enumerating the hub, the host requests the hub to report whether there are any devices attached. If so, the host enumerates these as well.

The host finds out if a device is attached to a port by sending the hub-class request Get_Port_Status. This is similar to a Get_Status request, but sent to a hub with a port number in the Index field. The hub returns two 16-bit values that indicate whether a device is attached as well as other information, such as whether the device is low power or in the Suspend state.

The hub controller is also responsible for disabling any port that was responsible for loss of bus activity or babble. Loss of bus activity occurs when a packet doesn’t end with the expected End-of-Packet signal. Babble occurs when a device continues to transmit beyond the End-of-Packet signal.