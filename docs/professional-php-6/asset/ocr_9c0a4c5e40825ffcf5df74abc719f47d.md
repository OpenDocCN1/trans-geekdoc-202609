![](bbox=[0.23, 0.09, 0.86, 0.5])

In a dual Ethernet setup, two of the servers in the setup have dual NICs. One NIC connects them into the “outside segment” (which has access to the firewall and, by definition, the Internet), and the second (which has a separate IP address on a different subnet) connects them to the “inside segment” (which does not).

The benefit of such a setup is that it physically precludes communications between servers that do not need to communicate. Typically, database servers would be set up on the “inside segment,” meaning that it is physically impossible to access database servers from the outside world, regardless of firewall rules. Security is tightened up by implication. There’s no need to worry about getting a firewall rule wrong, because there is no rule to get wrong. However, through that secondary NIC, the Web servers can still speak to the database servers, and vice versa.

Another big advantage is speed. There’s a dedicated link between the Web server and the database server, meaning the communications don’t have to compete for bandwidth with general Web traffic.

You can take this to yet another tier of segmentation, should you want to do so. If you separate out Web servers, application servers, and database servers, each can sit on its own Ethernet segment. Only the Web servers are publicly accessible to the outside world and sit on an outside segment, and they pass HTTP requests to application servers on a middle segment. Those application servers, in turn, access databases sitting on an internal segment, as shown in Figure 23-3.