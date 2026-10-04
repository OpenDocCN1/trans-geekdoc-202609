# Global Routing Prefix

The *global routing prefix* is the prefix, or network, portion of an address that is assigned by a provider, such as an ISP, to a customer or site. For example, it is common for an ISP to assign a /48 global routing prefix to its customers. The global routing prefix typically varies depending on the policies of the ISP.

Figure 12-9 shows a GUA using a /48 global routing prefix, which is a commonly assigned global routing prefix (and is therefore what most of the examples throughout this book use).

For example, the IPv6 address 2001:db8:acad::/48 has a global routing prefix that indicates that the first 48 bits (3 hextets: 2001:db8:acad); which is how the ISP knows this prefix (network) as the global routing prefix. The double colon (::) following the /48 prefix length means the rest of the address contains all 0s. The size of the global routing prefix determines the size of the subnet ID.

# Subnet ID

The *subnet ID* field is the area between the global routing prefix and the interface ID. Unlike IPv4, where you must borrow bits from the host portion to create subnets, IPv6 was designed with subnetting in mind. An organization uses the subnet ID to identify subnets within its site. The larger the subnet ID, the more subnets available.

> **Note**

Many organizations receive a /32 global routing prefix. If you use the recommended /64 prefix in order to create a 64-bit interface ID you're left with a 32-bit subnet ID. This means an organization with a /32 global routing prefix and a 32-bit subnet ID will have 4.3 billion subnets, each with 18 quintillion devices per subnet. That is as many subnets as there are public IPv4 addresses!

The IPv6 address in Figure 12-9 has a /48 global routing prefix, which is common among many enterprise networks. This makes it especially easy to examine the different parts of the address. Using a typical /64 prefix length, the first four hextets are for the network portion of the address, and the fourth hextet indicates the subnet ID. The remaining four hextets indicate the interface ID.

# Interface ID

The IPv6 *interface ID* is equivalent to the host portion of an IPv4 address. The term *interface ID* is used because a single host may have multiple interfaces, each with