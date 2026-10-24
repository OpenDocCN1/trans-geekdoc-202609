# Transferring Data

When enumeration is complete, the host has identified the device interface as a HID and has established pipes with the interface's endpoints and learned what report formats to use to send and receive data.

The host can then request reports using either interrupt IN transfers and/or control transfers with Get_Report requests. The device also has the option to support receiving reports using interrupt OUT transfers and/or control transfers with Set_Report requests.

If you don’t have example firmware for Get_Report and Set_Report, enumeration code can serve as a model. Get_Report is a control Read transfer that behaves in a similar way to Get_Descriptor except that the device returns a report instead of a descriptor. Set_Report is a control Write transfer. Unfortunately, the only standard USB request with a host-to-device Data stage is the rarely supported Set_Descriptor, so example code for control Write transfers is harder to find.

# About the Example Code

The example code in this chapter is written for the Microchip PIC18F4550 introduced in Chapter 6. The code is based on Microchip’s USB Firmware Framework. The Framework code is for the PIC18 family of microcontrollers but can give an idea of how to structure code for other CPUs. My code is adapted from Microchip’s mouse code and implements a generic HID device that exchanges reports in both directions.

Portions of the code can be useful even if your device isn’t a HID. The control-transfer examples can serve as models for responding to other class-specific and vendor-specific requests. From the firmware’s point of view, bulk and interrupt transfers are identical, so the interrupt-transfer code can serve as a model for any firmware that uses bulk or interrupt transfers.

In the Framework code, a group of system files handles general USB tasks and class-specific tasks. These files typically require no changes or only minor changes and additions for specific applications. The system files include these: