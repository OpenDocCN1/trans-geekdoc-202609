renaming the files rather than deleting them, you can restore them if necessary.

# INF File Names

The INF files that ship with Windows all have file names with no more than eight characters plus the 3-character extension. Microsoft says that this is due to “technical issues with the product install,” but that INF files added after Windows is installed may use longer file names.

# What the User Sees

What the user sees on the screen after attaching a USB device can vary depending on the Windows edition, the contents of the device’s INF file, the driver’s location, whether the driver has a co-installer and is digitally signed, and whether the device has been attached and enumerated previously and has a serial number.

# Device and Class Installers

Device and class installers provide functions relating to device installation. The installers are DLLs (dynamic link libraries). Windows provides default installers for devices in supported device setup classes. A device vendor can provide a co-installer that works along with a class installer to support operations that are specific to one or more devices in a class. A co-installer can add information to the registry, request additional configuration information from the user, provide device-specific Properties pages for the Device Manager to display, and perform other tasks relating to device installation. A vendor-defined device setup class can have its own class installer. The Windows DDK documentation has information about writing installers and co-installers.

# Searching for a Driver

On boot up or device attachment, after retrieving a device’s descriptors, the operating system searches for a matching hardware key. If a key exists, the operating system has what it needs to assign a driver to the device. The hardware key’s Driver entry points to the driver key, which names the INF file.