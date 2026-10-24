
![](img/3955d77b6be34048e3bc722d0b15c2a9_483_0.png)

Figure 16-3: When a device exceeds the current limit of its hub's port, Windows warns the user and offers assistance.

## Power Switching

A bus-powered hub must support power switching that can provide and cut off power to downstream ports in response to control requests. A single switch may control all ports, or the ports may switch individually. A self-powered hub must support switching to the Powered Off state and may also support power switching via control transfers.

![](img/3955d77b6be34048e3bc722d0b15c2a9_485_0.png)

Figure 16-4: The allowed bus current in the Suspend state includes the current through the device's pull-up resistor. As Figure 16-4 shows, the pull-up current flows from the device's pull-up supply, which must be between 3.0 and 3.6V, through the device's pull-up and the hub's pull-down, to ground. In the worst case, with a pull-up voltage of 3.6V and resistors that are the minimum allowed values, the pull-up current is 238 microamperes, leaving just 262 microamperes for everything else.

High-speed devices, which don't use pull-ups in normal communications, must switch to full speed and use a pull-up when entering the Suspend state. So high-speed devices have the same restriction on available current.

In compliance testing, however, the USB-IF has granted automatic waivers to low-power devices that consume up to 2.5 milliamperes in the Suspend state.

A high-power device that supports remote wakeup and whose remote-wakeup feature has been enabled by the host can draw up to 2.5 milliamperes from the bus when suspended, including current through the pull-up resistor. Every device connects as low power, so to comply with the USB specification, a device must meet the 500-microampere limit if the host suspends the device before configuring it as high power with remote wakeup enabled (assuming no waiver has been granted).

The limits are averages over intervals of up to 1 second, so brief currents can be greater. For example, a flashing LED that draws 20 milliamperes for one tenth of each second draws an average of 2 milliamperes per second.

A device should begin to enter the Suspend state after its bus segment has been in the Idle state for 3 milliseconds. The device must be in the Suspend state after its bus segment has been in the Idle state for 10 milliseconds.

## Resuming Communications

When in the Suspend state, two actions can cause a device to enter the Resume state and restart communications. Any activity on the bus will cause the device to enter the Resume state. And if the device’s remote wakeup feature is enabled by the host, the device itself may request a resume at any time.

To resume, the host places the bus in the Resume state (the K state, defined in Chapter 18) for at least 20 milliseconds. The host follows the Resume with a low-speed End-of-Packet signal. (Some hosts incorrectly send the End-of-Packet after just a few hundred microseconds.) The host then resumes sending Start-of-Frame packets and any other communications requested by the device driver.

A device causes a Resume by driving the upstream bus segment in the Resume state for between 1 and 15 milliseconds. The device then places its drivers in a high-impedance state to enable receiving traffic from the upstream hub. A device may initiate a Resume any time after the bus has been suspended for at least 5 milliseconds. The host-controller software must allow all devices at least 10 milliseconds to recover from a Resume.

Depending on a device’s USB controller, monitoring the bus to determine whether to enter the Suspend state may require firmware support. The resume signaling is normally handled by the device’s serial interface engine and requires no firmware support.

When a device uses bus power, the USB controller may need to control power to external circuits, removing power on entering the Suspend state and restoring power on resuming. A power switch with soft-start capability can prevent problems by limiting current surges when the switch turns on. Micrel Inc. has several power-distribution switches suitable for use with USB devices. Each switch contains one or more high-side MOSFET switches with soft-start capability.

## Power Management under Windows

Recent PCs manage power according to the Advanced Configuration and Power Interface Specification (ACPI). The specification, first released in 1997, was developed by Hewlett-Packard, Intel, Microsoft, Phoenix Technologies, and Toshiba. Revision 3.0 was released in 2004. A system that implements ACPI power management enables the operating system to conserve power by shutting down components, including suspending the USB bus, when the computer is idle.

To implement ACPI, a PC must contain an ACPI controller. An ACPI BIOS provides tables that describe the power-management capabilities of system hardware and routines that the operating system can execute.

PCs support three low-power, or sleeping, states:

In the S1 state, the display is off and drives are powered down. USB buses are suspended, but VBUS remains powered.

In the S3 state, the PCI bus’s main power supply is off and memory is not accessed, but system memory continues to be refreshed. Devices that can wake the system receive power from the PCI bus’s auxiliary supply (Vaux). In older systems, USB’s VBUS is not powered in the S3 state. In newer systems, VBUS is powered by Vaux.

In the S4 state, the system context is saved to disk and the system, including the USB bus, is powered off.

In Windows XP, you can view and change a system’s power-management options in Control Panel > Power Options. In the Power Schemes tab (Figure 16-5), you can specify when the system goes into standby and hibernation. Hibernation is the S4 state. Standby is either S1 or S3. On a system that has no USB devices that can wake the system, the standby state is S3. On a system that has a USB keyboard, mouse, or another USB device that can wake the system, the standby state is S1 due to problems in using S3 with some (misbehaving) hardware. The problems include loss of VBUS in the S3 state, false device removal and arrival notifications on resuming, resetting of devices during suspend and resume, and failure to resume fully.

![](img/3955d77b6be34048e3bc722d0b15c2a9_488_0.png)

Figure 16-5: The Power Options Properties in Windows' Control Panel enable users to specify power-saving schemes that determine when USB devices must enter the Suspend state.

To enable or disable remote wakeup capability for a specific device that supports remote wakeup, in Windows' Device Manager, select the device, right-click, select Properties > Power Management, and check or uncheck Allow this device to bring the computer out of standby.

On some early Intel host controllers, a suspended root port didn't respond correctly to a remote wakeup. In addition, using remote wake-up requires work-arounds under Windows 98 Gold, Windows 98 SE, and Windows Me. With these operating systems, a device may wake up properly, but the device’s driver isn’t made aware of the wakeup so communications can’t resume. A white paper from Intel titled *Understanding WDM Power Management* by Kosta Koeman (available from the USB-IF’s Web site) details the problem and solutions. In short, a device using these operating systems shouldn’t place itself in the Suspend state unless the host requests it, and the device driver requires extra code to ensure that the wake-up completes successfully. Windows 2000 and later don’t have this problem.

## 17

## Testing and Debugging

In addition to the chip-specific development boards and debugging software described in Chapter 6, a variety of other hardware and software tools can help in testing and debugging USB devices and their host software. This chapter introduces tools available from the USB-IF and other sources. I also explain what’s involved in passing the tests that are required for devices and drivers to earn the Certified USB logo and the Windows logo.

### Tools

Without a doubt the most useful tool for USB device developers is a protocol analyzer, which enables you to monitor USB traffic and other bus events. The analyzer collects data on the bus and decodes and displays the data you request in user-friendly formats. You can watch what happened during enumeration, detect and examine protocol and signaling errors, view data transferred during control, interrupt, bulk, and isochronous transfers, and focus on any aspect of a communication you specify.
