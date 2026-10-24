Table 4-6: The other_speed_configuration descriptor has the same eight fields as the configuration descriptor.

| Offset (decimal) | Field | Size (bytes) | Description |
|---|---|---:|---|
| 0 | bLength | 1 | Descriptor size in bytes |
| 1 | bDescriptorType | 1 | The constant OTHER_SPEED_CONFIGURATION (07h) |
| 2 | wTotalLength | 2 | The number of bytes in the configuration descriptor and all of its subordinate descriptors |
| 4 | bNumInterfaces | 1 | Number of interfaces in the configuration |
| 5 | bConfigurationValue | 1 | Identifier for Set_Configuration and Get_Configuration requests |
| 6 | iConfiguration | 1 | Index of string descriptor for the configuration |
| 7 | bmAttributes | 1 | Self/bus power and remote wakeup settings |
| 8 | MaxPower | 1 | Bus power required, expressed as (maximum milliamperes/2) |

active at the same time is a composite device. Each interface has its own interface descriptor and an endpoint descriptor for each endpoint the interface uses. The host loads a driver for each interface.

When two or more interfaces in a configuration are associated with the same function, the interface association descriptor can tell the host which interfaces are associated with each other. For example, a video-camera function may use one interface to control the camera and another to carry the video data.

The USB Engineering Change Notice that defines the interface association descriptor says that the descriptor “must be supported by future implementations of devices that use multiple interfaces to manage a single device function.” Devices that comply with the video-class specification must use an interface association descriptor. Class specifications that predate the descriptor of course don’t require it. Hosts that don’t support the descriptor ignore it. Support for the descriptor was added in Windows XP SP2.

To enable the host to identify devices that use the Interface Association descriptor, the device descriptor should contain the following values: bDeviceClass = EFh (miscellaneous device class), bDeviceSubClass = 02h (com-