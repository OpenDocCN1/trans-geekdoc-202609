# Rollover Cable/Console Cable

Routers typically have a command-line interface (CLI) for configuring the device, but they do not have screens or keyboards. However, they traditionally have a console port into which an administrator can plug a terminal or laptop and access the CLI. Modern routers can have a variety of interfaces for the console port, but earlier models used the RS-232 serial interface, with a DB-9 D-shell connector. Before USB, this was the interface people used to connect an external medium to their computers. Current routers might have an RJ-45 console port supporting the rollover wiring configuration, a standard Ethernet RJ-45 port, or even a mini-USB port.

A rollover cable, also known as a console cable, is a variation on the standard twisted pair design that eliminates both the twists and the pairs. A rollover cable is typically flat, not round like a UTP cable, and colored a light blue. At one end is a standard RJ-45 connector and at the other is either a DB-9 connector, as shown in Figure 22.1, or another RJ-45 and an EIA/TIA adapter that converts it to a DB-9.

![](bbox=[0.232, 0.442, 0.435, 0.626])

FIGURE 22.1 A rollover cable

Unlike UTP cables, the eight wires in a rollover cable are eight different colors, and the cable uses a nonstandard wiring scheme. Pin 1 at one end connects to pin 8 at the other end, pin 2 to pin 7, and so forth.

# Crossover Cable

For communication between network devices to occur, the signals a device sends out through the transmit pairs of the cable must arrive at the receive pairs of the destination device. Standard Ethernet cables are wired straight through, so the crossover circuit that connects the transmit to the receive pairs is located in the network switch.