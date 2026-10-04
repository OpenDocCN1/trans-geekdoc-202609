For each bit borrowed from the fourth octet, the number of subnetworks available is doubled, and the number of host addresses per subnet is reduced:

+   - /25 row: Borrowing 1 bit from the fourth octet creates 2 subnets supporting 126 hosts each.
- /26 row: Borrowing 2 bits creates 4 subnets supporting 62 hosts each.
- /27 row: Borrowing 3 bits creates 8 subnets supporting 30 hosts each.
- /28 row: Borrowing 4 bits creates 16 subnets supporting 14 hosts each.
- /29 row: Borrowing 5 bits creates 32 subnets supporting 6 hosts each.
- /30 row: Borrowing 6 bits creates 64 subnets supporting 2 hosts each.

![](bbox=[0.12, 0.37, 0.22, 0.42])

# Video—The Subnet Mask (11.5.3)

Refer to the online course to view this video.

![](bbox=[0.12, 0.45, 0.22, 0.5])

# Video—Subnet with the Magic Number (11.5.4)

Refer to the online course to view this video.

![](bbox=[0.12, 0.53, 0.22, 0.6])

# Packet Tracer—Subnet an IPv4 Network (11.5.5)

In this activity, starting from a single network address and network mask, you will subnet the Customer network into multiple subnets. The subnetting scheme should be based on the number of host computers required in each subnet, as well as other network considerations, such as future network host expansion.

After you have created a subnetting scheme and completed the table by filling in the missing host and interface IP addresses, you will configure the host PCs, switches, and router interfaces.

After the network devices and host PCs have been configured, you will use the ping command to test for network connectivity.

# Subnet a Slash 16 and a Slash 8 Prefix (11.6)

This section discusses and gives examples of subnetting networks that have /16 and /8 prefix lengths.

# Create Subnets with a Slash 16 Prefix (11.6.1)

Some subnetting is easier than other subnetting. This section explains how to create subnets that each have the same number of hosts.