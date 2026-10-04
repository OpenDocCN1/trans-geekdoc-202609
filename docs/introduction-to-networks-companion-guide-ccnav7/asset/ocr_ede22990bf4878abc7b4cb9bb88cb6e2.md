| Subnet Address (65,536 Possible Subnets) | Host Range (254 Possible Hosts per Subnet) | Broadcast |
|---|---|---|
| 10.1.2.0/24 | 10.1.2.1–10.1.2.254 | 10.1.2.255 |
| ... | ... | ... |
| 10.100.0.0/24 | 10.100.0.1–10.100.0.254 | 10.100.0.255 |
| ... | ... | ... |
| 10.255.255.0/24 | 10.255.255.1–10.255.255.254 | 10.255.255.255 |

# Subnet Within an Octet Boundary (11.5.2)

The examples shown thus far have borrowed host bits from the common /8, /16, and /24 network prefixes. However, subnets can borrow bits from any host bit position to create other masks.

For instance, a /24 network address is commonly subnetted using longer prefixes by borrowing bits from the fourth octet. This provides an administrator with additional flexibility when assigning network addresses to a smaller number of end devices.

Table 11-7 shows six ways to subnet a /24 network.

Table 11-7 Subnetting a /24 Network

| Prefix Length | Subnet Mask | Subnet Mask in Binary (n = Network, h = Host) | Number of Subnets | Number of Hosts |
|---|---|---|---|---|
| /25 | 255.255.255.128 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nhhhhhhh<br>11111111.11111111.11111111.10000000 | 2 | 126 |
| /26 | 255.255.255.192 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nnhhhhhh<br>11111111.11111111.11111111.11000000 | 4 | 62 |
| /27 | 255.255.255.224 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nnnnhhhh<br>11111111.11111111.11111111.11100000 | 8 | 30 |
| /28 | 255.255.255.240 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nnnnhhhh<br>11111111.11111111.11111111.11110000 | 16 | 14 |
| /29 | 255.255.255.248 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nnnnnhhh<br>11111111.11111111.11111111.11111000 | 32 | 6 |
| /30 | 255.255.255.252 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nnnnnnhh<br>11111111.11111111.11111111.11111100 | 64 | 2 |