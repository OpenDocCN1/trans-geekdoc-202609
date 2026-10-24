+   - Pass the appropriate compatibility tests in the Windows Hardware Compatibility Test (HCT) kit provided by Microsoft.
+   - Use Microsoft’s HCT Submission Review Utility to create a report that contains test logs of the compatibility tests.
+   - Submit the hardware, test logs, drivers (if any), user documentation, other configuration utilities or accessories as needed, and fee. The hardware is submitted to a Windows Quality Online Services test location. At this writing, the fee for most devices is $250 per operating system.

Microsoft’s Web site has the latest information and downloads relating to WHQL testing.

# Digital Signatures

To earn the Windows logo, a device must use a digitally signed driver. The driver may be one of the drivers included with the operating system or the vendor may supply the driver. To obtain a digital signature, a driver must pass WHQL testing and the vendor must provide a VeriSign Digital Code Signing ID obtained from www.verisign.com. At this writing, a VeriSign ID costs $400. Microsoft uses cryptographic technology to digitally sign the driver’s catalog (.cat) file and returns the signed file to the vendor

The device’s INF file references the catalog file. The signature enables Windows to detect if the driver has been modified since it passed WHQL testing. Each INF file has its own catalog file. A single INF file can support multiple devices. Any change in an INF file, including adding a new Product ID or device release number, requires obtaining a new digital signature.

For most USB devices, the INF file of a signed driver must include a device identification string that contains the device’s VID and PID. An INF file that uses a compatible ID to identify the device only by class (and optional subclass and protocol) won’t pass the WHQL tests, except for printers.

Your driver must be signed if you want it included in Microsoft’s Windows Update. This feature of Windows makes it easy for users to update drivers installed on their systems. In some cases Windows Update can also find a driver for a newly installed device. A driver available via Windows Update