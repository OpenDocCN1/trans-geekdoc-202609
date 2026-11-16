> **Caution**
> 
> Distance-vector protocols like RIP can be spoofed and are subject to redirection. It is also easy for attackers to sniff RIP updates. RIP routers update each other by sending out complete routing tables every 30 seconds.

*Link-state protocols are based on Dijkstra’s algorithm. Unlike distance-vector protocols, link-state protocols determine the best path with metrics like delay or bandwidth. When this path is determined, the router informs other routers of its findings. This is how reliable routing tables are developed and routing tables reach convergence. Link-state routing protocols are considered more robust than distance-vector routing protocols. OSPF is probably the most common link-state routing protocol; it is often used as a replacement for RIP.*

OSPF is an improved link-state routing protocol that offers authentication. It is an implementation of a link-state-based routing protocol developed in the mid-1980s to overcome the problems associated with RIP. OSPF has several built-in advantages over RIP, including the use of IP multicast to send out router updates, no limitation on hop count (as with RIP), better support for load balancing, and fast convergence.

Routing protocols can be further divided and defined as interior or exterior routing protocols. RIP, OSPF, and IS-IS are three examples of interior routing protocols. Interior routing protocols are used within an organization.

Exterior gateway protocols are used by routers connecting different *autonomous systems* (ASs). An example of an exterior routing protocol is BGP, which is the core routing protocol used by the Internet. It is based on TCP and is used to connect autonomous systems.

> **Note**
> 
> An early exterior routing protocol was Exterior Gateway Protocol (EGP). This term is sometimes used to describe all exterior routing protocols.