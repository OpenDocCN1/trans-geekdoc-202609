![](bbox=[0.2, 0.1, 0.78, 0.46])

Figure 9-3: Device Manager also has an option to view devices grouped by type, or function.

Viewing resources by connection or by type shows the memory and I/O addresses and interrupt request (IRQ) lines assigned to each host controller. It’s unlikely you’ll need this information when developing USB devices, drivers, or applications.

An exclamation point over a device’s icon means that the host had a problem communicating with the device or finding a driver. An X over an icon means that the device is present but disabled, possibly by the user.

By default, the Device Manager shows only attached USB devices. To view devices that have been removed but whose drivers are still installed, set the following system environment variable:

```
DEVMGR_SHOW_NONPRESENT_DEVICES=1
```

To set the variable, in Windows’ Control Panel, click System > Advanced > Environment Variables, enter the variable’s name, and set its value. Then in