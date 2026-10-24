# Table 6-2: Cypress Semiconductor’s EZ-USB family is compatible with the 8051 microcontroller.

| Feature | AN21xx (EZ-USB) | CY7C646xx (EZ-USB-FX) | CY7C68013 (EZ-USB-FX2) |
|---|---|---|---|
| Speed | Full | Full | Full/High |
| Number of endpoints | 13, 16, 31 | 31 | 11 |
| Compatibility | 80C320, 8051 | 80C320, 8051 | 80C320, 8051 |
| RAM (bytes) | 256 + 4-8K combined data and program memory | 256 + 4-8K combined data and program memory | 256 + 8K combined data and program memory |
| Program memory type | RAM, serial EEPROM, external parallel | RAM, serial EEPROM, external parallel | RAM, serial EEPROM, external parallel |
| Internal program memory (bytes) | 4–8K combined data and program memory | 4–8K combined data and program memory | 8K combined data and program memory |
| External memory bus (bytes) | 64K | 64K | one or two 64K buses |
| General-purpose I/O pins | 16–24 | 16–40 | 16–40 |
| Other I/O | 2 UARTs, I²C | 2 UARTs, I²C | 2 UARTs, I²C |
| Power Supply Voltage | 3–3.6 | 3–3.6 | 3–3.6 |
| Number of Pins | 44, 48, 80 | 52, 80, 128 | 56, 100, 128 |

more complicated compared to other chips. The options are useful because they make the chip very flexible, so I’ll describe them in some detail.

When an EZ-USB wants to use firmware stored in the host, the device enumerates twice. On boot up or device attachment, the host attempts to enumerate the device. But how can the host enumerate a device with no stored firmware? Every EZ-USB contains a core that knows how to respond to enumeration requests and can control communications when the device first attaches to the bus. The EZ-USB core is independent from the 8051 core that normally controls the chip after enumeration. The EZ-USB core communicates with the host while holding the 8051 core in the reset state.

The EZ-USB core also responds to vendor-specific requests that enable the chip to receive, store, and run firmware received from the host. For basic