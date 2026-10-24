# 20

# Dual-role Devices with USB On-The-Go

A USB host in a desktop system has many responsibilities, including supporting three bus speeds, managing communications with multiple devices, and providing up to 500 milliamperes to every device connected to the root hub. PCs and other desktop computers typically have the resources to implement a full USB host. But many smaller systems could benefit if they could function as hosts as well. For example, a camera could connect directly to a USB printer. A data-acquisition device could store its data in a USB drive. A PDA could interface to a USB keyboard and mouse. Two drives could exchange files.

An embedded system can incorporate a limited-capability host that supports communications with just one or a few devices. But for small systems, implementing even a limited-capability USB host can be challenging. The CPU may have limited resources, and battery-powered systems may be unable to provide the bus power that the host must make available. And a