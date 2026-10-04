
Rather than putting an appliance, or a cluster of appliances, into the path of packets flowing through the network, NFV brings the packets to the services. These services, in turn, could be scattered throughout the network, including being located anyplace on a data center fabric. If you consider the movement of traffic through the network as an optimization problem, NFV requires more granular information about where services are located in order. In essence, the service becomes the destination, rather than a logical subnet. NFV, then, will require the control plane to carry greater amounts of state.

At the same time, virtualized services are likely to move more often than services in a physical cluster or appliance; it is more difficult to unbolt, unrack, rack, and bolt an appliance than it is to respin a service on a new server. This means services move around more quickly both “because they can” (lowered cost often leads to less discipline) and because, once the network is perceived as “free,” the service “wants” to move to the highest-quality, lowest-cost compute resources possible.

There is another aspect of state to consider, as well: the distribution of policy in the network. It is simple enough to say, “smaller chunks of state spread throughout the network are easier to manage than one large configuration or state store.” Each individual piece of state is smaller and more tuned to the local need (a return to the principle of subsidiarity). On the other hand, understanding how widely distributed state interacts can be a lot more difficult; the interaction between two pieces of state in a single configuration file can be difficult to understand, and the interaction between two pieces of state configured on two different devices, widely separated in the network, and with different configuration parameters and/or styles can easily move into the “impossible” territory.

All of the additional state used to configure and manage a larger number of devices must also be carried on the network, which means a different order of magnitude of state must be carried and managed on the network. This not only eats network resources, but it also increases resilience demands on the network.

### Optimization

There are several tradeoffs to consider in the realm of optimization. First, NFV often treats the network as a “free resource.” Any time you make a resource appear to be cheap or free, you are saying you would prefer to use more of the free resource and less of more expensive resources. If the cost of the network is free, the marginal utility on network resources drops to the point where network resources are not considered when deciding where to run a particular service and why. Spreading services out across the network drives more traffic onto the network, which uses more network resources than by gathering services into clusters.

Network utilization is not just about the amount of bandwidth being carried over the network versus the amount of work being done. There is also the efficiency of troubleshooting, which directly impacts the Mean Time to Repair (MTTR), and therefore the network uptime (or measured resilience).

### Surface

Finally, there are interaction surfaces to consider. It often sounds good to automate everything and then turn the automation system over to an intent-based controller to manage the interaction between the applications running on the network, the control plane, and device configuration. Each of these new interactions, however, also represents a new interaction surface, with the implied complexity of abstraction, leaky abstractions, and other issues with interaction surfaces. Each of these interaction surfaces will require an Application Programming Interface (API), which introduces the complexity of managing these APIs over time.

### Other Tradeoffs to Consider

There are other tradeoffs to consider, as well, such as whether outsourcing as much complexity as possible to a vendor in the process of moving to an intent-based network is really a “good thing.” Internal skill sets are bound to atrophy when complex problems are outsourced, leaving the business without any local resources to call on when problems happen. Moving configuration, policy, and intent to a single device can mean a single mistake impacts a lot more devices. You are trading the centralized configuration of a clustered appliance for the centralized configuration of an orchestration system. Does this make sense? As with all things, it is important to consider the tradeoffs.

### Final Thoughts

NFV and intent-based networking are two attempts to define a simpler network for the future. The question, as always, is: “Simpler in what way—and more complex in what other ways?” NFV, combined with service chaining, the disaggregation of net-work services out of appliances and into standardized compute resources, the concept of scale-out services, and the movement toward automation and intent are all interesting trends in the network engineering world that will ultimately make contributions to the way networks are designed and operated.

The next chapter will discuss another trend likely to make a large impact on the way networks are designed and operated: the Internet of Things.

### Further Reading

Boucadair, Mohamed. “Service Function Chaining (SFC) Control Plane Components & Requirements.” Internet-Draft. Internet Engineering Task Force, October 2016. https://datatracker.ietf.org/doc/html/draft-ietf-sfc-control-plane-08.

Dolson, David, Shunsuke Homma, Diego Lopez, Mohamed Boucadair, Dapeng Liu, Ting Ao, and Vu Anh Vu. “Hierarchical Service Function Chaining (hSFC).” Internet-Draft. Internet Engineering Task Force, January 2017. https://datatracker.ietf.org/doc/html/draft-ietf-sfc-hierarchical-02.

Filsfils, Clarence, Stefano Previdi, Bruno Decraene, Stephane Litkowski, and Rob Shakir. “Segment Routing Architecture.” Internet-Draft. Internet Engineering Task Force, February 2017. https://datatracker.ietf.org/doc/html/draft-ietf-spring-segment-routing-11.

Halpern, Joel M., and Carlos Pignataro. *Service Function Chaining (SFC) Architecture*. Request for Comments 7665. RFC Editor, 2015. https://rfc-editor.org/rfc/rfc7665.txt.

Hudson, Jon, Lawrence Kreeger, Dr. Thomas Narten, Marc Lasserre, and David L. Black. *An Architecture for Data-Center Network Virtualization over Layer 3 (NVO3)*. Request for Comments 8014. RFC Editor, 2016. https://rfc-editor.org/rfc/rfc8014.txt.

K., Thomas. “User Space Networking Fuels NFV Performance.” *Intel Developer Zone*, June 12, 2015. https://software.intel.com/en-us/blogs/2015/06/12/user-space-networking-fuels-nfv-performance.

Kumar, Surendra, Mudassir Tufail, Sumandra Majee, Claudiu Captari, and Shunsuke Homma. “Service Function Chaining Use Cases in Data Centers.” Internet-Draft. Internet Engineering Task Force, February 2017. https://datatracker.ietf.org/doc/html/draft-ietf-sfc-dc-use-cases-06.

“L4-L7 Service Function Chaining Solution Architecture.” Open Networking Foundation, June 14, 2015. https://www.opennetworking.org/images/stories/downloads/sdn-resources/onf-specifications/L4-L7_Service_Function_Chaining_Solution_Architecture.pdf.
