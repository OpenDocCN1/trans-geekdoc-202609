Windows requests exclusive access to Input reports from system keyboards and pointing devices, so applications can’t directly read the reports that describe keypresses, mouse movements, and mouse-button clicks. Instead, the operating system handles this data at a lower level. For example, a Visual-Basic application doesn’t have to read mouse clicks to find out if a user has clicked on an option button because the button’s click event executes automatically on a button click.

If a system has multiple keyboards or pointing devices, Windows treats them all as a single “virtual” keyboard or pointing device. If you want to limit the applications that can access a keyboard or pointing device, or if you want to determine which keyboard or pointing device is the source of input, you need to either provide a digitally signed filter driver or design a vendor-specific device that the host doesn’t identify as a system mouse or keyboard.

# IrDA Bridge

The IrDA (Infrared Data Association) interface defines hardware requirements and protocols for exchanging data over short distances via infrared energy. A USB IrDA bridge converts between USB and IrDA data and enables a host to use USB to monitor, control, and exchange data over an IrDA interface.

# Documentation

The specification for USB IrDA bridges is *IrDA Bridge Device Definition*. The current version at this writing is 1.0. The IrDA specifications are available from *www.irda.org*.

# Overview

The data in an IrDA link uses the Infrared Link Access Protocol (IrLAP), which defines the format of the IrDA frames that carry data, addresses, and status and control information. The IrLAP payload consists of the address, control, and optional information (data) fields in an IrLAP frame. In addition to the IrLAP payload, each frame contains an error-checking value and markers for the beginning and end of the frame.