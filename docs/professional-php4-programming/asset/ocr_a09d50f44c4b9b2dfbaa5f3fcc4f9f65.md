# # Distributed and Hierarchical System

The primary problem that the DNS system attempts to solve is to provide a hostname to IP address mapping. This gives rise to the question, why isn't all the mapping data stored in a flat file? This was how name resolution used to work before the days of DNS. With time, the burgeoning number of hosts and the dynamic nature of such a mapping table rendered this approach impracticable. Thus the DNS system was designed to be a distributed and hierarchical system:

![](bbox=[0.072, 0.225, 0.903, 0.508])

The picture above illustrates the naming hierarchy of a simple network belonging to a small company, foowidgets.com. The .com domain is called the top-level domain. foowidgets.com is a sub-domain to the .com top-level domain. Within the foowidgets.com sub-domain there exist several other sub-domains that correspond to various departments.

When a client wishes to talk to a machine, say money in the foowidgets.com domain, it needs to obtain the IP address of money.virtual.foowidgets.com. The client contacts the local DNS server asking it for the IP address of the target machine money.virtual.foowidgets.com. The local DNS server in turn talks to the DNS server in charge of the .com domain asking it for the IP address of the target machine. The .com server replies back saying that it should ask the DNS server for the domain foowidgets.com.

When asked the same question, the foowidgets.com DNS server responds by referring it further to the DNS server corresponding to the virtual.foowidgets.com domain. The virtual.foowidgets.com DNS server responds with the IP address of money.virtuál.foowidgets.com. There are two ways in which this can be done:

+   - The original client processes each of the referrals itself until it reaches the DNS server that is able to provide a resolution response.
+   - The client initiates an iterative query sequence where each DNS server in the referral chain passes the query to the server ahead of it and passes the response back to the DNS server preceding it.