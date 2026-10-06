can't connect to that address and port because it's a nonroutable address. This usually results in a time-out when the upcoming file transfer is attempted and makes FTP very hard to use from behind a firewall.

# Routing the Unroutable, Part III: Application Layer Gateways

The developers of the NAPT specification (again, it's in an RFC—this time RFC 3022, “Traditional IP Network Translator”) were aware of this problem and suggested that Application Layer Gateways (ALGs) could be added to any NAPT router.
Even an ALG would need to change the contents of TCP stream for recognized protocols and commands, editing the TCP stream to change IP addresses and port numbers quoted opening up mappings to allow incoming connections as requested.
This works accept well except in the case where a protocol is unrecognized by the NAPT belonging to a particular ALG. The case can be as simple as using a different port or as complex as the use of encryption IPSec, for instance, or FTP over SSL/TLS. In the former case, the NAPT doesn't know you're sending FTP traffic because the server is not at port 21; in the latter case, the NAPT sees only encrypted data, which it can read nor modify.

# NAPsts Will Somehow Become Irrelevant

IPv6 offers a new reality. There are so many addresses in IPv6 that we will never have the exhaustion problem affected IPv4.
Yes, we know, that with IPv4, this time we mean it. Even if you had an IPv6 address to every blade of grass in your lawn, you'd have plenty of space in your IPv6 address assignment to accommodate an address for each item in your refrigerator, every device you own, and every square inch of your house. Then there would still be room to spare between those addresses.
 a result of this huge address space, there will be no NATs or NAPTs for IPv6. If you need the “accidental firewall” feature of NAPTs, you will need to get a more “deliberate” firewall, one that operates only as a firewall.

# Installing a NAT

Possibly the most likely use you will have for making a Windows Server 2012 R2 machine into a router if you want to create a NAT over which you have finer control than you would get from a normal NAT device.
Installing NAT in Windows Server 2012 R2 is relatively simple, although it has many steps:

+   1. Install the Remote Access role.

This consists of the routing components required.

+   2. Open Server Manager and change Manage  ➤ Add Roles and Features.

The familiar new Add Roles and Features Wizard appears, as shown in Figure 20.11.