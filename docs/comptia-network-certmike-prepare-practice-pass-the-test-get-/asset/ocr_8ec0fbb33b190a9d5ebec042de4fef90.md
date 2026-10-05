They are notated in decimal form, the subnet masks are based on the use of binary values; network identifier bits have a value of 1, and host identifier bits are 0s. Therefore, the Class B subnet mask in binary form is as follows:

```
11111111 11111111 00000000
```

The also call for a default gateway value, which is the IP address of a router on the local network that the system should use to access other networks. In a routing table, the default gateway entries 0.0.0.0 as its network destination address.

# Creating Subnets

Classful addressing allows network administrators to modify the subnetting strategy to accommodate the needs of the network. They do this by borrowing of the identifier bits from the network address and using them to create a subnet identifier. For example, a Class B network address has 16 identifier bits, allowing the administrator to create addresses for 65,534 hosts. Few networks need this many host addresses, so the administrator can borrow some of the host bits to create subnets.
By using the 8 bits of the third octet as a subnet identifier, as shown in Figure 4.2, the administrator can create up to 256 subnets, each of which has up to 254 hosts.

| Class B | Network Identifier | Subnet Identifier | Host Identifier |

> FIGURE 4.2 Subnetting a Class B address

To indicate that the network address has been subnetted, the administrator changes the subnet mask for each of the host addresses. The subnet identifier in the third octet is now considered part of the network address, so the subnet mask in binary form substitutes 1s for in that third octet, as follows:

```
11111111 11111111 11111111 00000000
```

In decimal form, therefore, the subnet mask for each of the host addresses becomes 255.255.255.0.

# Classless Addressing

Subnetting along octet boundaries is easy but not always practical for every network. To provide greater flexibility, it is also possible to subnet a network anywhere, not just between octets. To illustrate, an administrator can take the same network address from the previous example and borrow only 4 bits for the subnet identifier instead of 8. This leaves the resulting network have up to 16 subnets, each with up to 4,094 hosts. This process is called classless addressing.
In this case, administrators use a technique called variable length subnet masking (VLSM) because the boundary between the network and host bits falls within an octet. Therefore,