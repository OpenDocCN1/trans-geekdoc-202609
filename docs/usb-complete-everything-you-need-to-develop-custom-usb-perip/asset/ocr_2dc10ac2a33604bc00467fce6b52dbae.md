![](bbox=[0.12, 0.11, 0.88, 0.32])

![](bbox=[0.12, 0.35, 0.88, 0.55])

Figure 15-5: The device’s port has a stronger pull-up than the hub’s. The location of the pull-up tells the hub whether the device is low or full speed. High-speed devices are full speed at attachment.

signal line is more positive on an idle line. Figure 15-5 illustrates. As Chapter 4 explained, the hub has a pull-down resistor of 14.25 to 24.8 kilohms on each of the port’s two signal lines, D+ and D-. A newly attached device has a pull-up resistor of 900 to 1575 ohms on either D+ for a full-speed device or D- for a low-speed device. When a device is attached to a port, the line with the pull-up is more positive than the hub’s logic-high input threshold. The hub detects the voltage, assumes a device is attached, and detects the speed by which line is pulled up.

After detecting a full-speed device, a 2.0 hub determines whether the device supports high speed by using the high-speed detection handshake. The handshake occurs during the Reset state that the hub initiates during enu-