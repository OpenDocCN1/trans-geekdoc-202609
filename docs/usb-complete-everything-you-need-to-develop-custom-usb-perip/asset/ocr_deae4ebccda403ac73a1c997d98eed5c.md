available current so its devices and the hub combined don’t exceed the allowed current.

Like other self-powered devices, a self-powered hub may also draw up to 100 milliamperes from the bus so the hub interface can continue to function when the hub’s power supply is off. If the hub’s power is from an external source, such as AC power from a wall socket, the hub is high power and must be capable of supplying 500 milliamperes to each port on the hub. If the hub uses battery power, the hub may supply 100 or 500 milliamperes to each port on the hub.

# Over-current Protection

As a safety precaution, hubs must be able to detect an over-current condition, which occurs when the current used by the total of all devices attached to the hub exceeds a preset value. When the port circuits on a hub detect an over-current condition, they limit the current at the port and the hub informs the host of the problem. Windows warns the user when a device exceeds the current limit of its hub port (Figure 16-3).

The USB 2.0 specification says only that the current that triggers the over-current actions must be less than 5 amperes. To allow for transient currents, the over-current value should be greater than the total of the maximum allowed currents for the devices. In the worst case, seven high-power, bus-powered downstream devices can legally draw up to 3.5 amperes. So a supply for a self-powered hub with up to seven downstream ports would provide much less than 5 amperes at all times unless something goes very wrong.

The USB specification allows a device to draw larger inrush currents when it attaches to the bus. This current is typically provided by the stored energy in a capacitor that is downstream from the over-current protection circuits so the protection circuits don’t see the inrush current. If the inrush current is too large, the device will fail the USB-IF’s compliance tests.