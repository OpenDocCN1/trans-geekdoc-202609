# Power Management under Windows

Recent PCs manage power according to the Advanced Configuration and Power Interface Specification (ACPI). The specification, first released in 1997, was developed by Hewlett-Packard, Intel, Microsoft, Phoenix Technologies, and Toshiba. Revision 3.0 was released in 2004. A system that implements ACPI power management enables the operating system to conserve power by shutting down components, including suspending the USB bus, when the computer is idle.

To implement ACPI, a PC must contain an ACPI controller. An ACPI BIOS provides tables that describe the power-management capabilities of system hardware and routines that the operating system can execute.

PCs support three low-power, or sleeping, states:

In the S1 state, the display is off and drives are powered down. USB buses are suspended, but VBUS remains powered.

In the S3 state, the PCI bus’s main power supply is off and memory is not accessed, but system memory continues to be refreshed. Devices that can wake the system receive power from the PCI bus’s auxiliary supply (Vaux). In older systems, USB’s VBUS is not powered in the S3 state. In newer systems, VBUS is powered by Vaux.

In the S4 state, the system context is saved to disk and the system, including the USB bus, is powered off.

In Windows XP, you can view and change a system’s power-management options in Control Panel > Power Options. In the Power Schemes tab (Figure 16-5), you can specify when the system goes into standby and hibernation. Hibernation is the S4 state. Standby is either S1 or S3. On a system that has no USB devices that can wake the system, the standby state is S3. On a system that has a USB keyboard, mouse, or another USB device that can wake the system, the standby state is S1 due to problems in using S3 with some (misbehaving) hardware. The problems include loss of VBUS in