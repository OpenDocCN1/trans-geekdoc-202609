# PROBLEMS

P19. In this problem, we use the useful dig tool available on Unix and Linux hosts to explore the hierarchy of DNS servers. Recall that in Figure 2.19, a DNS server in the DNS hierarchy delegates a DNS query to a DNS server lower in the hierarchy, by sending back to the DNS client the name of that lower-level DNS server. First read the man page for dig, and then answer the following questions.

+   a. Starting with a root DNS server (from one of the root servers [a-m].root-servers.net), initiate a sequence of queries for the IP address for your department's Web server by using dig. Show the list of the names of DNS servers in the delegation chain in answering your query.

+   b. Repeat part (a) for several popular Web sites, such as google.com, yahoo.com, or amazon.com.

P20. Suppose you can access the caches in the local DNS servers of your department. Can you propose a way to roughly determine the Web servers (outside your department) that are most popular among the users in your department? Explain.

P21. Suppose that your department has a local DNS server for all computers in the department. You are an ordinary user (i.e., not a network/system administrator). Can you determine if an external Web site was likely accessed from a computer in your department a couple of seconds ago? Explain.

P22. Consider distributing a file of F = 20 Gbits to N peers. The server has an upload rate of us = 30 Mbps, and each peer has a download rate of dl = 2 Mbps and an upload rate of u. For N = 10, 100, and 1,000 and u = 300 Kbps, 700 Kbps, and 2 Mbps, prepare a chart giving the minimum distribution time for each of the combinations of N and u for both client-server distribution and P2P distribution.

P23. Consider distributing a file of F bits to N peers using a client-server architecture. Assume a fluid model where the server can simultaneously transmit to multiple peers, transmitting to each peer at different rates, as long as the combined rate does not exceed us.

+   a. Suppose that u_s/N \leq d_{min}. Specify a distribution scheme that has a distribution time of NF/u_s.

+   b. Suppose that u_s/N \geq d_{min}. Specify a distribution scheme that has a distribution time of F/d_{min}.

+   c. Conclude that the minimum distribution time is in general given by max {NF/u_s, F/d_{min}}.

P24. Consider distributing a file of F bits to N peers using a P2P architecture. Assume a fluid model. For simplicity assume that d_{min} is very large, so that peer download bandwidth is never a bottleneck.

+   a. Suppose that u_s \leq (u_s + u_1 + ... + u_N)/N. Specify a distribution scheme that has a distribution time of F/u_s.