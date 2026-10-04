software tools. In such a case, it is necessary to modify the MAC address with a new NIC or make modifications by using software.

# Frame Processing (7.2.3)

Sometimes a MAC address is referred to as a burned-in address (BIA) because the address is hard coded into read-only memory (ROM) on the NIC. This means that the address is permanently encoded into the ROM chip.

# Note

With modern PC operating systems and NICs, it is possible to change the MAC address in software. This is useful when attempting to gain access to a network that filters based on BIA. Consequently, filtering or controlling traffic based on the MAC address is no longer as secure as it once was.

When the computer boots up, the NIC copies its MAC address from ROM into RAM. When a device is forwarding a message to an Ethernet network, as shown in Figure 7-9, the Ethernet header includes the following:

+   - **Source MAC address:** This is the MAC address of the source device NIC.
- **Destination MAC address:** This is the MAC address of the destination device NIC.

| Destination Address | Source Address | Data |
|---|---|---|
| CC:CC:CC:CC:CC:CC | AA:AA:AA:AA:AA:AA | Encapsulated data |
| Frame Addressing |  |  |

![](bbox=[0.25, 0.56, 0.92, 0.85])

Figure 7-9 The Source Prepares a Frame to Send to the Destination