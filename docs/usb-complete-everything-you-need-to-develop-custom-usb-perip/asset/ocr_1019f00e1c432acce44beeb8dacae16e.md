+   - Detect when devices are attached to and removed from the system.
+   - Communicate with newly attached devices to find out how to exchange data with them.
+   - Provide a mechanism that enables software drivers to communicate with the computer’s USB hardware and the applications that want to access USB peripherals.

At a higher level, operating system support may also mean the inclusion of class drivers that enable application programmers to access devices. If the operating system doesn’t include a driver appropriate for a specific peripheral, the peripheral vendor must provide the driver.

With each new edition of Windows, Microsoft has added class drivers. Supported device types in recent Windows editions include human interface devices (keyboards, mice, game controllers), audio devices, modems, still-image and video cameras, scanners, printers, drives, and smart-card readers. Filter drivers can support device-specific features and abilities within a class. Applications use Application Programming Interface (API) functions or other operating-system components to communicate with device drivers.

For devices that aren’t in supported classes, some vendors of USB peripheral controllers provide drivers that developers can use with the vendor’s controllers.

USB device drivers use the Windows Driver Model (WDM), which defines an architecture for drivers that run under Windows 98 and later Windows editions. The aim is to enable developers to support multiple Windows editions with a single driver, though some devices may require different drivers for Windows 98/Windows Me and for Windows 2000/Windows XP. Because Windows includes low-level drivers that handle communications with the USB hardware, writing a USB device driver is typically easier than writing drivers for devices that use other interfaces.

# Peripheral Support

On the peripheral side, each USB device’s hardware must include a controller chip that manages the details of USB communications. Some controllers