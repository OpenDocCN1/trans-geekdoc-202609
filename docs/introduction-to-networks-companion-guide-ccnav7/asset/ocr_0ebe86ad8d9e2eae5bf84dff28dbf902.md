As shown in Table 11-2, the network address has all 0 bits in the host portion, as determined by the subnet mask. In this example, the network address is 192.168.10.0/24. A network address cannot be assigned to a device.

# Table 11-2 Network, Host, and Broadcast Addresses

| Description | Network Portion | Host Portion | Host Bits |
|---|---|---|---|
| Subnet mask: 255.255.255.0 or /24
11111111 11111111 11111111 | 255 255 255 | 0
00000000 | |
| Network address: 192.168.10.0 or /24
11000000 10100000 00001010 | 192 168 10 | 0
00000000 | All 0s |
| First address: 192.168.10.1 or /24
11000000 10100000 00001010 | 192 168 10 | 1
00000001 | All 0s and a 1 |
| Last address: 192.168.10.254 or /24
11000000 10100000 00001010 | 192 168 10 | 254
11111110 | All 1s and a 0 |
| Broadcast address: 192.168.10.255 or /24
11000000 10100000 00001010 | 192 168 10 | 255
11111111 | All 1s |

# Host Addresses

Host addresses are addresses that can be assigned to devices such as host computers, laptops, smartphones, web cameras, printers, routers, and so on. The host portion of the address is the bits indicated by 0 bits in the subnet mask. A host address can have any combination of bits in the host portion except for all 0 bits (which would be a network address) or all 1 bits (which would be a broadcast address).

All devices in the same network must have the same subnet mask and the same network bits. Only the host bits differ and must be unique.

In Table 11-2, notice that there is a first host address, and there is a last host address:

+   - **First host address:** The first host in a network has all 0 bits, with the last (rightmost) bit as a 1 bit. In this example, it is 192.168.10.1/24.
- **Last host address:** The last host in a network has all 1 bits, with the last (rightmost) bit as a 0 bit. In this example, it is 192.168.10.254/24.

Any addresses between and including the first and last host addresses—in this case, 192.168.10.1/24 through 192.168.10.254/24—can be assigned to devices on the network.