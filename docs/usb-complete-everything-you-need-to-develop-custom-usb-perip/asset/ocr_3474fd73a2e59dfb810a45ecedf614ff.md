# Device Descriptor

The device descriptor contains basic information about the device. This descriptor is the first one the host reads on device attachment and includes the information the host needs to retrieve additional information from the device. A host retrieves a device descriptor by sending a Get_Descriptor request with the high byte of the Setup transaction's wValue field equal to 1.

The descriptor has 14 fields. Table 4-2 lists the fields in the order they occur in the descriptor. The descriptor includes information about the descriptor itself, the device, its configurations, and any classes the device belongs to. The following descriptions group the information by function.

# The Descriptor

bLength. The length in bytes of the descriptor.

bDescriptorType. The constant DEVICE (01h).

# The Device

bcdUSB. The USB specification version that the device and its descriptors comply with in BCD (binary-coded decimal) format. If you think of the version's value as a decimal number, the upper byte represents the integer, the next four bits are tenths, and the final four bits are hundredths. So version 1.0 is 0100h; version 1.1 is 0110h, and version 2.0 is 0200h. Note that version 1.1 is not 0101h. Also remember that a 2.0 device does not have to be high speed. Any new low- or full-speed design should comply with the latest version of the specification.

idVendor. Members of the USB-IF and others who pay an administrative fee receive the rights to use a unique Vendor ID. The host may have an INF file that contains this value, and if so, Windows uses the value to help decide what driver to load for the device. Except for devices used only in-house where the user is responsible for preventing conflicts, every device descriptor must have a valid Vendor ID in this field.

idProduct. The owner of the Vendor ID assigns a Product ID to identify the device. Both the device descriptor and the device's INF file on the host may contain this value, and if so, Windows uses the value to help decide