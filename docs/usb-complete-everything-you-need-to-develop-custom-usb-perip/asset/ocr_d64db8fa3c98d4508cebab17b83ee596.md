# The OTG Descriptor

During enumeration, a device that supports HNP or SRP must include an OTG Descriptor in the descriptors returned in response to a Get_Descriptor request for the Configuration descriptor.

Table 20-2 shows the fields of the descriptor. The bmAttributes field tells whether the device supports HNP and SRP. A device that supports HNP must support SRP. The A-device doesn’t need to know in advance if a device supports SRP, but this information is included in the descriptor for use in compliance testing.

# Feature Codes for HNP

The OTG supplement defines three codes for use in Set_Feature requests.

A code of b_hnp_enable (03h) informs the B-Device that it can use HNP. The A-device sends this request if all of the following are true: the A-device supports HNP, the A-device will respond to HNP when the bus is suspended, and the B-device connects directly to the A-device, with no hubs in between.

A code of a_hnp_support (04h) informs the B-device that the A-device supports HNP and the B-device is directly connected (no hubs), but the B-device isn’t yet allowed to use HNP. The A-device can send this request before configuring the B-device. The A-device can then enable HNP at a later time, when the A-device is finished using the bus.

A code of a_alt_hnp_support (05h) notifies the B-device that the currently connected port does not support HNP, but that the A-device has an alternate port that does support HNP.

# OTG Controller Chips

Several manufacturers offer controller chips designed for use in OTG devices. To function as a peripheral, the controller must include device-controller circuits similar to those in the controllers described in Chapter 6. As