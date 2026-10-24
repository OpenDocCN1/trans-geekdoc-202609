**Automatic configuration.** When a user connects a USB peripheral to a PC, Windows detects the peripheral and loads the appropriate software driver. The first time the peripheral connects, Windows may prompt the user to insert a disk with driver software, but other than that, installation is automatic. There's no need to restart the system before using the peripheral.

**Easy to connect.** With USB, there's no need to open the computer's enclosure to add an expansion card for each peripheral. A typical PC has four or more USB ports. You can expand the number of ports by adding hubs with additional ports.

**Easy cables.** USB cable connectors are keyed so you can't plug them in wrong. A cable segment can be as long as 5 meters. With hubs, a peripheral can be as far as 30 meters from its host PC. USB connectors are small and compact in contrast to typical RS-232 and parallel connectors. To ensure reliable operation, the USB specification includes detailed requirements that all cables and connectors must meet.

**Hot pluggable.** You can connect and disconnect a USB peripheral whenever you want, whether or not the system and peripheral are powered, without damaging the PC or device. The operating system detects when a peripheral is attached and readies it for use.

**No user settings.** USB peripherals don't have user-selectable settings such as port addresses and interrupt-request (IRQ) lines so there are no jumpers to set or configuration utilities to run.

**Frees hardware resources for other devices.** Using USB for as many peripherals as possible frees up IRQ lines for the peripherals that require them. The PC dedicates a series of port addresses and one IRQ line to the USB host controller, but individual peripherals don't require additional resources or any PC programming that involves specifying port addresses or detecting hardware interrupts. In contrast, peripherals with other interfaces may require dedicated port addresses, an IRQ line, and an expansion slot.

**No power supply required (sometimes).** The USB interface includes power-supply and ground lines that provide a nominal +5V from the computer's or hub's power supply. A peripheral that requires up to 500 milliamperes can draw all of its power from the bus instead of having to provide a