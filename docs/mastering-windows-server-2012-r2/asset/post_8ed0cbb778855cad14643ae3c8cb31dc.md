
Classes are identified by the binary form to see how many of the most significant bits are set to 1, before reaching the first 0. Class A starts with 0, so the first octet in the range 0000 0000 to 0111 1111 (in decimal, 0 to 127). Class B starts with a single 1 before the first 0, as 1000 0000 to 1011 1111 (in decimal, 128 to 191). Class C starts with two 1s and then their first 0, so the range is 1100 0000 to 1101 1111 (192 to 223).

This seemed fairly equitable, with Class A getting the ability to have nearly 2^24 (16,777,216) hosts. Class B users received nearly 2^16 (65,536) hosts, and class C received nearly 256 hosts.

## Unusable Host Addresses

Why "in every network range, a number of addresses are not available to be assigned to hosts. The absolute, carved-in-stone (or at least, within the RFCs, the requirements that in any network the top and bottom ends of the address ranges—where all hosts are reserved for broadcasting."

The end of this address range—where all hosts are set to 1 (the all 1s)—is reserved for directed broadcast. So, for instance, if your network was a class B assignment and had addresses starting with the sequence 192.168.something.something, the directed broadcast would be 225 octets representing a binary sequence of 11111111. All 1s?

A packet sent to this would reach every computer on the 192.168.something network. Every computer would pass that message to its IP address, where something might be listening for broadcasted traffic. (You will see 192.168.something network appear in layers of documentation, and we will explain why in a few paragraphs.) Don't try this on your production network because you will find your network every!

The bottom of the address range—where all hosts are set to 0 (the all 0s)—is technically reserved for broadcasting. Wait, we already said that the all 1s was reserved for broadcasting, didn't we? Well, yes—true—and you won't find a system that uses all 0s for broadcasting. But back in the Internet's equivalent of the Bronze Age, Internet developments were made by different groups at once. Apparently the class chose to broadcast to all 1s, and everyone else's surprise (at the time, it was a major factor in Internet development), everyone else.

But the all 0s address isn't available for use because it also represents another "the network." In router tables, as well in network diagrams and other documentation, it refers to the network as a whole, instead of talking about the 192.168.something.something, you could now talk about the 192.168.0.0 network.

Internet addressing in IPv4 has an address concept—that all-1s and all-0s addresses, 255.255.255 and 0.0.0.0, representing something. All 0s 192.168.0.0 represents the network of machines from 192.168.0.1 to 192.168.255.254, so what would 0.0.0.0 represent? It generally represents a network of one computer—“this” computer. By extension, 255.255.255.255 represents “broadcast” to every computer out.

## Broadcast Gets Narrows: The First Unroutable Addresses

When the Internet was small, these broadcast addresses were reserved. If you wanted to know what computers a company had connected to the Internet, all you would have to do was find their network address was 192.168.0.0, and then you could enumerate their network by pinging 192.168.255.255. You would get a response from every machine they had (and you would still can, but be careful!) Then you could try to connect to random machines and see which ones existed.

Similarly, if you wanted to enumerate the entire Internet, there would be no problem error—you simply ping 255.255.255.255, and you get a response from every machine that existed.

Because of each these actions had its own risks—the first, a risk of disclosure, and the second a risk of flooding your network (or someone else's, if you could the responses to their directed broadcast!)—pretty soon routers were configured to disable packets with these destinations from crossing them.

As a result, 192.168.255.255 could now be used only from inside the 192.168.0.0 network, so if it became a directed broadcast that you could only direct yourself, and 255.255.255.255 became a global broadcast that both broadcasts reached the same place—your local subnet—and since the 192.168.255.255 directed broadcast address required qualification by the 255.255.255.255 address could be hard-coded, pretty much nobody uses the directed broadcast anymore. Unfortunately, this doesn't mean you can get that address and use it for a host.

## Routing the Unreachable, Part I: Private Addresses

The document defines that all 0s and all addresses (RFC 1122, "Requirements for Internet Hosts—Communication Layers") also defines a specific Class A as being reserved for the purpose of loopback communication. This network is 127.0.0.0, but out of 16 million address range, nobody uses ever other except the single address 127.0.0.1, which is usually given the alias localhost.

A useful caution has grown over the years is to use the first address or last address in a network as the default router. This is not only a convention, and nothing forces you to do it (if, for example, in the instance, the router does not nothing follow this convention; it is set to 192.168.0.100 for New York and 192.169.0.100 for London). However, this convention would make it simpler for the person who replaces you for the router. An example would be that if in the 192.168.0.0 network, you would use 192.168.0.1 as the default router following the first address connection.

There's network address reason why we keep using that network? Quite simply, because we know we won't get the orders for accidentally directing their traffic way. How do we do this? This address is not used by any one individual. Another RFC document (RFC 1918, "Address Allocation for Private Internets") lays out series of ranges that are reserved for private use. By default, these addresses are not routed—10.0.0.0–10.255.255.255, 172.16.0.0–172.31.255.255, 192.168.0.0–192.168.255.255.

Each of the range 172.16.0.0–172.31.255.255, 172.16.0.0 is to, how much of 172.16.0.0–172.31.255.255 is to 172.16.0.0–172.31.255.255.

192.168.0.0–192.168.255.255, 192.168.0.0 is to 192.168.0.0–192.168.255.255.

10.0.0.0–10.255.255.255, 10.0.0.0 is to 10.0.0.0–10.255.255.255.

Those of the range 172.16.0.0–172.31.255.255, 172.16.0.0 is to 172.16.0.0–172.31.255.255.
