# Enumeration: How the Host Learns about Devices

A host retrieves interface descriptors by requesting the configuration descriptor for the configuration the interface belongs to.

An interface descriptor has nine fields. Table 4-8 lists the fields in the order they occur in the descriptor. Many devices don’t use the values in all of the fields, such as those that enable alternate settings and protocols. The following descriptions group the information by function.

# The Descriptor

bLength. The number of bytes in the descriptor.

bDescriptorType. The constant INTERFACE (04h).

# The Interface

iInterface. Index to a string that describes the interface. This value is zero if there is no string descriptor.

bInterfaceNumber. Identifies the interface. In a composite device, a configuration has multiple interfaces that are active at the same time. Each interface must have a descriptor with a unique value in this field. The default is zero.

bAlternateSetting. When a configuration supports multiple, mutually exclusive interfaces, each of the interfaces has a descriptor with the same value in bInterfaceNumber and a unique value in bAlternateSetting. The Get_Interface request retrieves the currently active setting. The Set_Interface request selects the setting to use. The default is zero.

bNumEndpoints. The number of endpoints the interface supports in addition to Endpoint 0. For a device that supports only Endpoint 0, NumEndpoints is zero.

bInterfaceClass. Similar to bDeviceClass in the device descriptor, but for devices with a class specified by the interface. Table 4-9 shows defined codes. Values from 01h to FEh are reserved for USB-defined classes. FFh indicates a vendor-defined class. Zero is reserved.

bInterfaceSubClass. Similar to bDeviceSubClass in the device descriptor, but for devices with a class defined by the interface. For interfaces that