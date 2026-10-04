Notice that the subnet mask is a consecutive sequence of 1 bits followed by a consecutive sequence of 0 bits.

To identify the network and host portions of an IPv4 address, the subnet mask is compared to the IPv4 address bit for bit, from left to right, as shown in Figure 11-4.

![](bbox=[0.22, 0.25, 0.82, 0.45])

Figure 11-4 Subnet Mask Compared to IPv4 Address

Note that the subnet mask does not actually contain the network or host portion of an IPv4 address; it just tells the computer where to look for the part of the IPv4 address that is the network portion and where to look for the host portion. The process used to identify the network portion and host portion is called ANDing.

# The Prefix Length (11.1.3)

Expressing network addresses and host addresses by using dotted decimal subnet mask addresses can be cumbersome. Fortunately, there is an alternative method of identifying a subnet mask: a method called the prefix length.

The prefix length is the number of bits set to 1 in the subnet mask. It is written in “slash notation,” with a forward slash (/) followed by the number of bits set to 1. To figure out the prefix length, count the number of bits in the subnet mask and prepend it with a slash. Table 11-1 provides some examples. The first column lists various subnet masks that can be used with a host address. The second column displays the converted 32-bit binary address. The last column displays the resulting prefix length.

Table 11-1 Comparing the Subnet Mask and Prefix Length

| Subnet Mask | 32-Bit Address | Prefix Length |
|---|---|---|
| 255.0.0.0 | 11111111.00000000.00000000.00000000 | /8 |
| 255.255.0.0 | 11111111.11111111.00000000.00000000 | /16 |
| 255.255.255.0 | 11111111.11111111.11111111.00000000 | /24 |