
## Router

A router is a layer-3 device that is responsible for routing, or sending, data from one network to another network. The router uses a routing table that resides in its memory to determine the networks it knows how to send data to. [Figure 1-5](#ch01.xhtml#ch1fig5) displays a network topology and the routing table on a router. Notice in the figure that in order for router R1 to send data to the 25.0.0.0 network, it must send the data to the 24.0.0.2 address, as indicated by the routing table.

![Images](f0008-01.jpg)

**FIGURE 1-5**  
Routers use routing tables to deliver data.

The following code listing displays the routing table on a Cisco router by using the `show ip route` command. Notice in the listing that there are three routes; routes to the 23.0.0.0 and 24.0.0.0 network are known because the router is connected to those networks (notice the `C` on the left). Also, a static route (code `S`, on the left) that the administrator added has been configured to pass data to the 24.0.0.2 system to reach the 25.0.0.0 network.

![Image](p0007-02.jpg)

Routers are great network devices because they define the boundary of the network by creating what is called a *broadcast domain*, which is a group of systems that can receive one another's broadcast messages. A broadcast message is a message that is destined for all systems—and the router is strategically placed on the network to keep those broadcast messages within your network because broadcast traffic does not pass through the router.

## Load Balancer

A *load balancer* is a device that is designed to split the load between components such as servers or routers. Load balancing is the concept of trying to improve performance. Instead of having a single server or device handle all the work, you have multiple servers or devices that the workload is divided among. This increases overall performance because you have more systems working at the same time to handle all the incoming requests.

Load balancers have a number of settings that allow you to configure how the load balancer works:

- **Round-robin** Sends the request from a client to each back-end server in order. The load balancer has a list of servers and simply goes through them in order.
- **Affinity** Controls whether all requests from a client go to the same server in the load balancer or if each request can potentially be routed to a different server. Affinity essentially ties a client to a particular server.
- **Persistence** This is another method used to associate a client with a specific server within the load balancer. With persistence, the user's session cookie is used to ensure that the same server is handling all requests from the client (this is also known as a sticky session). This session cookie could come from the application or the load balancer itself.
- **Scheduling** Specifies which algorithm will be used to send the request to one of the nodes. Scheduling uses a number of configuration values, such as round-robin, affinity, and CPU load, to determine to which server to send the request.

### Active/Passive vs. Active/Active

There are two common configurations for load balancing. With an *active/passive* configuration, one system, called a node, handles all the work (the active node), while the other node (the passive node) is on standby, ready to take over if the active node fails. If the active node fails, the passive node becomes the active node and handles all the workload. With an *active/active* configuration, both nodes are online and able to handle requests, essentially splitting the workload. If one node fails, the other node handles all the workload until the failed node is recovered. With both configurations, more than two nodes can be included for extra redundancy.

With both of these setups, the load balancer has an IP address assigned to it (known as the *virtual IP*), and you configure all clients to send requests to the virtual IP assigned to the load balancer. When the load balancer receives a request sent to the virtual IP, it then forwards the request to an active node in the load balancer.

### DNS Round-Robin

Another load-balancing technique is known as DNS round-robin. With round-robin, the load-balancing solution simply sends the request to the next server on its list. The problem with round-robin is that the solution doesn't verify if that server is actually up and running without problems. An example of round-robin load balancing is the use of the Domain Name System (DNS). You can create multiple DNS records with the same name but different IP addresses, and the DNS server will send a different IP address with each response to the clients. The problem is that the DNS server does not verify that those IP addresses are used by systems that are up and running.

## Firewalls and Proxy Servers

You will learn more about firewalls and proxy servers in [Chapter 8](#ch08.xhtml#ch8), but this section gives you a quick description of the purpose of a firewall and a proxy server to introduce them as network devices.

A *firewall* is a network device that controls which traffic is allowed to enter or leave the network. The firewall filters traffic based on rules you place on the firewall indicating which traffic is allowed or not allowed to enter or leave the network. You typically start with a deny-all rule that states all traffic is denied, unless you specify otherwise by building a rule for a specific type of traffic.

![Image](exam.jpg)

> **For the Security+ exam, remember that a proxy server makes the request for the Internet resource on behalf of the user, and commonly the company filters and logs which web sites users have visited.**

A *proxy server* is a device that all clients send their Internet traffic to, and then the proxy server sends the requests to the Internet on behalf of the users. The proxy server typically implements network address translation (NAT) as well, helping to keep the internal network structure private from the outside world. There are transparent proxies that do not require the user to authenticate, but then there are also proxy server products that require the client to authenticate before they can surf the Internet. This helps control the sites that can be visited by each user and also allows the proxy administrator to log which sites each user is visiting. As a final note on proxy servers, there are also reverse proxies, which allow you to receive all inbound traffic (such as traffic to a web server), analyze the requests, and only permit safe, valid requests to reach the web server.

## Understanding Network Cabling

Cabling is the transmission medium for data sent between hosts on the LAN. Systems on the LAN can be connected together using a variety of cable types, such as unshielded twisted-pair and fiber. Each cable type has its own advantages and disadvantages, which you will examine in this section.

The two primary types of cable media that can be used to connect systems to a network are twisted-pair cable and fiber-optic cable. Transmission rates supported on each of these physical media are measured in millions of bits per second, or megabits per second (Mbps).

### Twisted-Pair Cable

Today, twisted-pair cabling dominates the popularity contest. Twisted-pair cabling gets its name from having four pairs of wires that are twisted to help reduce crosstalk or interference from outside electrical devices. Crosstalk is interference from adjacent wires. [Figure 1-6](#ch01.xhtml#ch1fig6) shows a twisted-pair cable. Just as there are two forms of coaxial cable, there are two forms of twisted-pair cabling: unshielded twisted-pair (UTP) and shielded twisted-pair (STP).

![Images](f0011-01.jpg)

**FIGURE 1-6**  
Unshielded twisted-pair (UTP) cable
