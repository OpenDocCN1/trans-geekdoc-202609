# Secure Network Devices and Protocols 275

![](bbox=[0.246, 0.124, 0.69, 0.442])

FIG. 5.21
Redundant network architecture.

to say that all circuits go down eventually. Static routes would require manual reconfiguration.
Routing protocols are the answer. The goals of routing protocols are to automat-ically learn a network topology and learn the best routes between all network points. The should route go down, backup routes should be chosen, and chosen quickly. Ideally this should happen even while the network engineers are asleep.
Convergence means that all routers on a network agree on the state of routing. A network that has no recent outages is “converged”: all routers see routes as available. Then a circuit goes down. The routers closest to the outage know right away; routers that are further away will know. The network lacks convergence: some believe all circuits are up, while others know one is down. A goal of routing protocols is to make convergence as fast as possible.
Routing protocols come in two basic varieties: Interior Gateway Protocols (IGPs), like RIP and OSPF, and Exterior Gateway Protocols (EGPs), like BGP. Private networks use Intranets and EGPs are used on public networks like the Internet. Routing protocols support Layer 3 (Network) of the OSI model.

# Distance Vector Routing Protocols

Metrics are used to determine the “best” route across a network. The simplest metric is hop count. In Fig. 5.21, the hop count from the data center to each office via T3 is 1. Additional paths are available from the data center to each office, such as the T3 to Office B, followed by the T1 to Office A.