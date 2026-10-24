
The host continues to learn about the device by requesting the one or more configuration descriptors specified in the device descriptor. A request for a configuration descriptor is actually a request for the configuration descriptor followed by all of that descriptor's subordinate descriptors. A Windows host begins by requesting just the configuration descriptor's nine bytes. Included in these bytes is the total length of the configuration descriptor and its subordinate descriptors.

Windows then requests the configuration descriptor again, this time using the retrieved total length. The device responds by sending the configuration descriptor followed by the configuration's interface descriptor(s), with each interface descriptor followed by any endpoint descriptors for the interface. Some configurations also include class- or vendor-specific descriptors that extend or modify another descriptor. These descriptors follow the descriptor being extended or modified. Each descriptor begins with its length and type. The Descriptors section in this chapter has more on what each descriptor contains.

## 11. The host assigns and loads a device driver

(except for composite devices). After learning about a device from its descriptors, the host looks for the best match in a device driver to manage communications with the device. In selecting a driver, Windows tries to match the information in the PC's INF files with the Vendor ID, Product ID, and (optional) release number retrieved from the device. If there is no match, Windows looks for a match with any class, subclass, and protocol values retrieved from the device. If the device has been enumerated previously, Windows can use information in the system registry instead of searching the INF files. After the operating system assigns and loads the driver, the driver may request the device to resend descriptors or send other class-specific descriptors.

An exception to this sequence is composite devices, which can have different drivers assigned to different interfaces in a configuration. The host can assign these drivers only after the interfaces are enabled, which requires the device to be configured (as described in the next step).

## 12. The host's device driver selects a configuration.

After learning about a device from the descriptors, the device driver requests a configuration by sending a Set_Configuration request with the desired configuration number. Some devices support only one configuration. If a device supports multiple configurations, the driver can decide which configuration to request based on information the driver has about how the device will be used, or the driver can ask the user what to do or just select the first configuration. The device reads the request and enables the requested configuration. The device is now in the Configured state and the device’s interface(s) are enabled.

For composite devices, the host assigns drivers at this point. As with other devices, the host uses the information retrieved from the device to find a matching driver for each active interface in the configuration. The device is now ready for use.

The other two device states are Attached and Suspend.

**Attached state.** If the hub isn’t providing power to a device’s VBUS line, the device is in the Attached state. The absence of power may occur if the hub has detected an over-current condition or if the host requests the hub to remove power from the port. With no power on VBUS, the host and device can’t communicate, so from their perspective, the situation is the same as when the device isn’t attached at all.

**Suspend State.** A device enters the Suspend state after detecting no bus activity, including Start-of-Frame markers, for at least 3 milliseconds. In the Suspend state, the device should limit its use of bus power. Both configured and unconfigured devices must support this state. Chapter 16 has more about the Suspend state.

## Enumerating a Hub

Hubs are also USB devices, and the host enumerates a newly attached hub in exactly the same way as other devices. If the hub has devices attached, the host enumerates each of these after the hub informs the host of their presence.

## Device Removal

When a user removes a device from the bus, the hub disables the device's port. The host learns that the removal occurred after polling the hub, learning that an event has occurred, and sending a Get_Port_Status request to find out what the event was. Windows removes the device from the Device Manager's display and the device's address becomes available to another newly attached device.

## Tips for Successful Enumeration

Successful enumeration is essential. Without it, the device and host can't perform any additional communications. Most chip vendors provide example code to get you started. Even if your device uses a different class or has other differences, the example code can serve as a model. If your controller interfaces to an external CPU, you may have to adapt code written for another chip.

In general, a device should assume nothing about what requests or events the host will initiate and should just concentrate on responding to requests and events as they occur. The following tips have specific advice about how to avoid common problems.

**Don't assume requests or events will occur in a specific order.** The USB 2.0 specification says nothing about what order a host might choose in sending control requests during enumeration. A host might also choose to reset the bus at any time, and the device must detect the reset and respond appropriately.

**Be ready to abandon a control transfer or end it early.** On receiving a new Setup packet, a device must abandon any transfer in progress and begin the new one. On receiving an OUT token packet, the device must assume that the host is beginning the Status stage of the transfer even if the device hasn't sent all of the requested data in the Data stage.

**Don't attempt to send more data than the host asks for.** In the Data stage of a Control Read transfer, a device should send no more than the amount of data the host has asked for. If the host requests nine bytes, the device should send no more than nine bytes.

**Send a zero-length data packet when required.** If the device has less than the requested amount of data to return and if the amount of data is an exact multiple of the endpoint’s maximum packet size, the device should indicate that there is no more data by returning a zero-length data packet in response to the next IN token packet.

**Stall unsupported requests.** A device shouldn’t assume it knows every request the host might send. The device should return a STALL in response to any request the device doesn’t recognize or support.

**Don’t set the address too soon.** In a Set_Address request, the device should set its new address only after the Status stage of the request is complete.

**Be ready to enter the Suspend state.** A host can suspend the bus when the device is in any powered state, including before the device has been configured. When the bus is suspended, the device must reduce its use of bus power.

**Test under different host-controller types.** Some host controllers schedule multiple stages of a control transfer in a single frame, while others don’t. Devices should be able to handle either way. Chapter 8 has more about host controllers.

## Descriptors

USB descriptors are the data structures, or formatted blocks of information, that enable the host to learn about a device. Each descriptor contains information about the device as a whole or an element of the device.

All USB devices must respond to requests for the standard USB descriptors. The device must store the information in the descriptors and respond to requests for the descriptors.

## Types of Descriptors

As described earlier in this chapter, during enumeration the host uses control transfers to request descriptors from the device. As enumeration progresses, the requested descriptors concern increasingly small elements of the device: first the entire device, then each configuration, each configuration’s interface(s), and finally each interface’s endpoint(s). Table 4-1 lists the descriptor types.

The higher-level descriptors inform the host of any additional, lower-level descriptors. Except for compound devices, each device has one and only one device descriptor that contains information about the device as a whole and specifies the number of configurations the device supports. Each device also has one or more configuration descriptors that contain information about the device’s use of power and the number of interfaces supported by the configuration. Each interface descriptor specifies zero or more endpoint descriptors that contain the information needed to communicate with an endpoint. Each endpoint descriptor has information about how the endpoint transfers data. An interface with no endpoint descriptors must use the control endpoint for communications.

On receiving a request for a configuration descriptor, a device should return the configuration descriptor and all of the configuration’s interface, endpoint, and other subordinate descriptors, up to the requested number of bytes. There is no request to retrieve, for example, only an endpoint descriptor. Devices that support both full and high speeds support two additional descriptor types: device_qualifier and other_speed_configuration. These and their subordinate descriptors contain information about the device’s behavior when using the speed not currently selected.

A string descriptor can store text such as the vendor’s or device’s name. Other descriptors can contain index values that point to these string descriptors, and the host can read the string descriptors using Get_Descriptor requests.

In addition to the standard descriptors, a device may contain class- or vendor-specific descriptors. These descriptors offer a structured way for a device to provide more detailed information about itself. For example, an interface
