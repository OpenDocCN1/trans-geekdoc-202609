
![](img/e71dc48d3ae3db3394e5857ab2acae75_409_0.png)

Figure 11-25 10.0.0.0/18 Network

![](img/e71dc48d3ae3db3394e5857ab2acae75_409_1.png)

Borrowing 10 bits creates 1024 subnets

![](img/e71dc48d3ae3db3394e5857ab2acae75_409_2.png)

Figure 11-26 Resulting /18 Subnets

Borrowing 10 bits to create the subnets leaves 14 host bits for each subnet. Subtracting 2 hosts per subnet (1 for the network address and 1 for the broadcast address) leaves 2^14 – 2 = 16,382 hosts per subnet. This means that each of the 1024 subnets can support up to 16,382 hosts.

Figure 11-27 shows the specifics of the first subnet.

![](img/e71dc48d3ae3db3394e5857ab2acae75_409_3.png)

## Video—Subnet Across Multiple Octets (11.6.4)

Refer to the online course to view this video.

Network Address
10. 00 00 00 00. 00 00 0000. 0000 0000 = 10.0.0.0/18

First Host Address
10. 00 00 00 00. 00 00 0000. 0000 0001 = 10.0.0.1/18

Last Host Address
10. 00 00 00 00. 00 11 1111. 1111 1110 = 10.0.63.254/18

Broadcast Address
10. 00 00 00 00. 00 11 1111. 1111 1111 = 10.0.63.255/18

Figure 11-27 Address Range for the 10.0.0.0/18 Subnet

![](img/e71dc48d3ae3db3394e5857ab2acae75_410_0.png)

## Activity—Calculate the Subnet Mask (11.6.5)

Refer to the online course to complete this activity.

![](img/e71dc48d3ae3db3394e5857ab2acae75_410_1.png)

## Lab—Calculate IPv4 Subnets (11.6.6)

In this lab, you will complete the following objectives:

- Part 1: Determine IPv4 Address Subnetting
- Part 2: Calculate IPv4 Address Subnetting

## Subnet to Meet Requirements (11.7)

This section discusses the differences between subnetting areas of a network that use private IPv4 address space and areas that use public IPv4 address space. Although the technique of subnetting is the same, there are some important considerations.

### Subnet Private Versus Public IPv4 Address Space (11.7.1)

Your organization's network may use both public and private IPv4 addresses. This affects how you will subnet your network.

Figure 11-28 shows a typical enterprise network, which includes the following components:

![](img/e71dc48d3ae3db3394e5857ab2acae75_411_0.png)

Figure 11-28 Intranet and DMZ in an Enterprise Network

- **Intranet:** This is the internal part of a company’s network, accessible only within the organization. Devices in the intranet use private IPv4 addresses.
- **DMZ:** This is part of the company’s network containing resources available to the internet, such as a web server. Devices in the DMZ use public IPv4 addresses.

The intranet and the DMZ have unique subnetting requirements and challenges.

The intranet uses private IPv4 addressing space. This means the organization can use any of the private IPv4 network addresses, including the 10.0.0.0/8 prefix, with 24 host bits and more than 16 million hosts. Using a network address with 24 host bits makes subnetting easier and more flexible. This includes subnetting on an octet boundary using a subnet mask of /16 or /24.

For example, the private IPv4 network address 10.0.0.0/8 can be subnetted using a /16 mask. As shown in Table 11-9, this results in 256 subnets, with 65,534 hosts per subnet. If an organization has a need for fewer than 200 subnets, allowing for some growth, this gives each subnet more than enough host addresses.

## Table 11-9 Subnetting Network 10.0.0.0/8 Using a /16 Prefix

| Subnet Address (256 Possible Subnets) | Host Range (65,534 Possible Hosts per Subnet) | Broadcast |
|---|---|---|
| 10.0.0.0/16 | 10.0.0.1–10.0.255.254 | 10.0.255.255 |
| 10.1.0.0/16 | 10.1.0.1–10.1.255.254 | 10.1.255.255 |
| 10.2.0.0/16 | 10.2.0.1–10.2.255.254 | 10.2.255.255 |
| 10.3.0.0/16 | 10.3.0.1–10.3.255.254 | 10.3.255.255 |
| 10.4.0.0/16 | 10.4.0.1–10.4.255.254 | 10.4.255.255 |
| 10.5.0.0/16 | 10.5.0.1–10.5.255.254 | 10.5.255.255 |
| 10.6.0.0/16 | 10.6.0.1–10.6.255.254 | 10.6.255.255 |
| 10.7.0.0/16 | 10.7.0.1–10.7.255.254 | 10.7.255.255 |
| ... | ... | ... |
| 10.255.0.0/16 | 10.255.0.1–10.255.255.254 | 10.255.255.255 |

Another option using the 10.0.0.0/8 private IPv4 network address is to subnet using a /24 mask. As shown in Table 11-10, this results in 65,536 subnets, with 254 hosts per subnet. If an organization needs more than 256 subnets, then a /24 mask can be used, with 254 hosts per subnet.

## Table 11-10 Subnetting Network 10.0.0.0/8 Using a /24 Prefix

| Subnet Address (65,536 Possible Subnets) | Host Range (254 Possible Hosts per Subnet) | Broadcast |
|---|---|---|
| 10.0.0.0/24 | 10.0.0.1–10.0.0.254 | 10.0.0.255 |
| 10.0.1.0/24 | 10.0.1.1–10.0.1.254 | 10.0.1.255 |
| 10.0.2.0/24 | 10.0.2.1–10.0.2.254 | 10.0.2.255 |
| ... | ... | ... |
| 10.0.255.0/24 | 10.0.255.1–10.0.255.254 | 10.0.255.255 |
| 10.1.0.0/24 | 10.1.0.1–10.1.0.254 | 10.1.0.255 |
| 10.1.1.0/24 | 10.1.1.1–10.1.1.254 | 10.1.1.255 |
| 10.1.2.0/24 | 10.1.2.1–10.1.2.254 | 10.1.2.255 |
| ... | ... | ... |

| Subnet Address (65,536 Possible Subnets) | Host Range (254 Possible Hosts per Subnet) | Broadcast |
|---|---|---|
| 10.100.0.0/24 | 10.100.0.1–10.100.0.254 | 10.100.0.255 |
| ... | ... | ... |
| 10.255.255.0/24 | 10.255.255.1–10.255.255.254 | 10.255.255.255 |

The 10.0.0.0/8 network can also be subnetted using any other number of prefix lengths, such as /12, /18, /20, and so on, which gives the network administrator a wide variety of options. Using a 10.0.0.0/8 private IPv4 network address makes subnet planning and implementation easy.

## What About the DMZ?

Because the devices in the DMZ need to be publicly accessible from the internet, these devices require public IPv4 addresses. The depletion of public IPv4 address space became an issue beginning in the mid-1990s. Since 2011, IANA and four out of the five RIRs have run out of IPv4 address space. Although organizations are making the transition to IPv6, the remaining IPv4 address space remains severely limited. This means an organization must maximize its own limited number of public IPv4 addresses; the network administrator must therefore subnet the network's public address space into subnets with different subnet masks in order to minimize the number of unused host addresses per subnet. This is known as variable-length subnet masking (VLSM).

### Minimize Unused Host IPv4 Addresses and Maximize Subnets (11.7.2)

To minimize the number of unused host IPv4 addresses and maximize the number of available subnets, there are two considerations when planning subnets: the number of host addresses required for each network and the number of individual subnets needed.

Table 11-11 displays the specifics for subnetting a /24 network. Notice that there is an inverse relationship between the number of subnets and the number of hosts. The more bits that are borrowed to create subnets, the fewer host bits remain available. If more host addresses are needed, more host bits are required, resulting in fewer subnets.

The number of host addresses required in the largest subnet determines how many bits must be left in the host portion. Recall that two of the addresses cannot be used, so the usable number of addresses can be calculated as 2^n − 2.

## Table 11-11 Subnetting a /24 Network

| Prefix Length | Subnet Mask | Subnet Mask in Binary (n = Network, h = Host) | Number of Subnets | Number of Hosts per Subnet |
|---|---|---|---|---|
| /25 | 255.255.255.128 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nhhhhhhh<br>11111111.11111111.11111111.10000000 | 2 | 126 |
| /26 | 255.255.255.192 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nnhhhhhh<br>11111111.11111111.11111111.11000000 | 4 | 62 |
| /27 | 255.255.255.224 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nnnhhhh<br>11111111.11111111.11111111.11100000 | 8 | 30 |
| /28 | 255.255.255.240 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nnnnhhh<br>11111111.11111111.11111111.11110000 | 16 | 14 |
| /29 | 255.255.255.248 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nnnnnhh<br>11111111.11111111.11111111.11111000 | 32 | 6 |
| /30 | 255.255.255.252 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nnnnnnh<br>11111111.11111111.11111111.11111100 | 64 | 2 |

Network administrators must devise a network addressing scheme that accommodates the maximum number of hosts for each network and the number of subnets. The addressing scheme should allow for growth in both the number of host addresses per subnet and the total number of subnets.

### Example: Efficient IPv4 Subnetting (11.7.3)

In this example, an ISP has allocated a corporate headquarters the public network address 172.16.0.0/22 (with 10 host bits). As shown in Figure 11-29, this address provides 1022 host addresses.

Note
172.16.0.0/22 is part of the IPv4 private address space; it is not an actual public IPv4 address.

![](img/e71dc48d3ae3db3394e5857ab2acae75_414_0.png)

Figure 11-29 Network Address
