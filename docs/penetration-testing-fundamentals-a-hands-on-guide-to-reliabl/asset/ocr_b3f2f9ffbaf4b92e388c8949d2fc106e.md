For each object added in the driver model tree, a directory in sysfs is created. The parent/child relationship is reflected with subdirectories under /sys/devices/. The subdirectory /sys/bus/ is populated with symbolic links, mirroring how the devices belong to different busses. The subdirectory /sys/class/ shows devices grouped according to classes. And /sys/block/ contains the block devices.

A symbolic link is a special sort of file that is really a pointer to another file. You can think of it as the equivalent of a shortcut in Microsoft Windows. These are also sometimes called soft links.

For device drivers and devices, attributes may be created. These are simple files; the rule is that they should only contain a single value and/or allow a single value to be set. These files show up in the subdirectory of the device driver respective to the device. Using attribute groups, a subdirectory filled with attributes may also be created.

This service has gone through quite a few name changes in its lifetime. sysfs was originally called ddfs (Device Driver Filesystem) and was initially created to debug the driver model as it was being written. Previously, debugging was performed by using procfs to export a device tree; however, that was converted to use a new file system based on ramfs. By the time the new driver model was merged into the kernel around 2.5.1, it had changed names to driversfs to be a little more descriptive. If you open any file manager and look in the /sys directory, you will see subdirectories for firmware, devices, and more. This is shown in Figure 10-1.

![](bbox=[0.11, 0.49, 0.84, 0.84])

FIGURE 10-1 The /sys Directory.

You can drill down to specifics by opening subdirectories, as shown in Figure 10-2.