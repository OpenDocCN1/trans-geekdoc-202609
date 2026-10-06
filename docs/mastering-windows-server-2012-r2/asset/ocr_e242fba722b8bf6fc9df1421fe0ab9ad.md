# CHAPTER 20 ADVANCED IP: ROUTING WITH WINDOWS

However, this tracerout output gives you a fairly good idea of the route toward
Microsoft's website. Don't be put off by the * responses, it is quite common to block ICMP-based
traffic to prevent probing.
Again, tracer has the parameters -4 and -6, which you can use to force the trace to go over
IPv4 or IPv6, respectively.

# Checking Your Configuration with ipconfig

ipconfig will show information about the configuration of some or all of your network cards.
ipconfig /all shows you very detailed information, and ipconfig on its owns shows a limited
subset of information. The best use of ipconfig is to ensure that your configuration
matches what it is supposed to be, at least according to the network diagrams you're trying to
match reality.

Note that a number of virtual interfaces will show up in this listing. For instance, if you have
enabled a VPN server or RRAS as a dial-up access point, an interface will be assigned for those
connections to use.

For network interfaces that address addresses through DHCP, it can be useful to run ipconfig
/renew or ipconfig /release followed by ipconfig /renew. It may be just as quick, and which
require fewer fetches, to simply unplug and unplug the associated network cable—that, too,
causes a release and renew after the DHCP server.

# Showing Routing and Neighbors

We have talked about the routing table in Windows Server 2012 R2 in this chapter, and you
find out that analyzing the routing table as if you the router can be constructive
tracing where a fault lies. If your routing table is very large and is not easily understood,
that can be a fault in itself, if that no one thoroughly understands even a small section of the
network enough to say that it is, using as is designed.

In addition to the routing table, using arp -a orsh interface ipv6 show neighbors
will let you know which computer has been talking to you the local area link. If there
are no entries in the table, except for those used by multicast addresses and loopback adapters,
this indicates that the computer is probably not able to reach any of its neighbors on the
network link. This is often a sign of a faulty cable or switch port, and swapping the cable or
plugging it into a different port at the switch is a good option to try.

A lack of neighbors may also indicate an inability to negotiate route speeds with the
switch and a new computer with a Gigabit Ethernet card. The Ethernet card always negotiated
down to 10 Mbps, and when we forced it to 100 Mbps, it would not see any other systems on the
network—its ARP table would empty out. Replacing the switch with a new switch fixed that

# Using Network Monitor

Previously exclusively for Windows Server administrators who knew it was,
and with its greatest features available only to users of Microsoft's System Management Server,
Network Monitor is now a free commodity, available from the Microsoft download site.
The current version, Network Monitor 3.3, is available from: