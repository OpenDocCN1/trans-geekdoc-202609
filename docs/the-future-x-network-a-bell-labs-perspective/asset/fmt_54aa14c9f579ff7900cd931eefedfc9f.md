
Looking at electrical energy generation, it is obvious that this is a market that is largely premised on dynamic tuning to instantaneously and continuously match demand, with the optimum (lowest cost) source chosen to supply demand at all times. The highest cost sources (for example, natural gas turbines) are only being used to meet the unexpected or uncommon demand peaks. Energy utilities benefit significantly when peaks are reduced and demand is spread out more evenly. This is closely analogous to the information networks, which likewise are most efficient when highly utilized.

Dynamic real-time pricing, where energy pricing tracks demand level, has been used successfully by energy utilities to reduce peak demand, with significantly greater reductions when automated mechanisms are employed, as demonstrated in [figure 9](#10-9781315365756_chapter-chap4.xhtml#fig4_9).

![](images/fig4_9.jpg)

The internet advertising market is another example. This market is an example of real-time bidding (RTB) for another temporal commodity — context-sensitive ad space availability. With RTB, advertisers have just 100 ms to consider the context of a user and bid for each ad space, and the highest bidder’s ad is then displayed. Following the deployment of automated demand-side platforms in 2007, RTB has grown steadily to over 40 percent of the display ad market, with sizable gains claimed as compared with non-RTB ads, as shown in [figure 10](#10-9781315365756_chapter-chap4.xhtml#fig4_10).

It is clear that such dynamic marketplace mechanisms, finely tailoring offers and usage to personalized needs, can transform markets — driving volume, efficient utilization and enhanced monetization. Again, all of these effects apply equally to the network capacity market, illustrating the great potential of tailoring bandwidth services to the needs of the global cloud ecosystem.

The large-scale compute virtualization trend that swept the ICT industry over the past decade is now driving inflection in the networking industry as well. The dynamic needs of virtualized workloads were instrumental in driving the need for SDN. The same advances in virtualization technologies, multi-core commodity servers and distributed systems software are now making it possible to develop high-performance, scalable network operating systems that interface with and control the underlying infrastructure capabilities based on both virtualized and optimized hardware systems in real time. The confluence of these technology trends is creating the exact set of capabilities or “perfect storm” of technology supply that is coincident with the latent end-user demand and the burgeoning demand of the IoT, and will drive widespread changes in communications and information networking architectures, capabilities and business models.

![](images/fig4_10.jpg)

## The future

Future wide area networks will be driven by technology advances in software-defined network control, optimized tunable network fabric and automated federation between networks. In this section, we describe the key innovations that we believe will be instrumental in shaping the future of the WAN.

### The network OS

It has long been the dream of network operators to be able to dynamically provision new network services as easily as web services. In computing infrastructure, this automation is offered by the OS, which manages the sharing and abstraction of the underlying compute, memory, storage and input/output (I/O) for applications and creates the notion of optimal resources for secure execution for each application. If we extend this analogy, as shown in [figure 11](#10-9781315365756_chapter-chap4.xhtml#fig4_11), to realize the vision of rapid network service creation will require a network OS.

![](images/fig4_11.jpg)

Just as the PC or smartphone OS platforms provide a programming abstraction that decouples applications from multivendor hardware, the network OS will provide a centralized network abstraction that decouples the underlying specifics of network elements and domains from network apps, which are network services that require real-time interaction with the network. The network OS would be instantiated as a logically centralized platform with an intuitive interface for network consumers that allows the network to be programmed and also provides the perception of seemingly infinite network resources.

A high-level architecture for such a network OS is shown in [figure 12](#10-9781315365756_chapter-chap4.xhtml#fig4_12). The network OS unifies the fragmented management and control planes of the different network domains and also provides the intelligence needed to rapidly configure end-to-end network services across different technologies. Therefore, the ideal network operating system enables the following:

1. Real-time network control through simple, extensible network interfaces
2. Exposure of service-relevant physical layer capabilities in the underlying network fabric, extensible to accommodate new innovations
3. Unified operations of disparate network domains and technologies

The network OS provides the essential abstraction and control, but it relies on many underlying capabilities to allow optimization of the network resources and the creation of the illusion of seemingly infinite capacity. The key capabilities are the ability to maintain network state, a hybrid control plane, simplified, intent-based service definition, a network description language and federation control. We discuss each of these capabilities in more depth below.

![](images/fig4_12.jpg)

### Maintaining network state

**Network state** includes information about such things as network inventory, connectivity and current resource utilization as well as ongoing and scheduled network outage and maintenance events. The global network state captures the operational view of the complex and fragmented network domains and provides the basis on which services are defined, provisioned and instantiated on the network fabric.

The centralized view of network state supports agile service provisioning and dynamic on-demand network services, and derives real-time contextual information about the network and services to devise appropriate responses to different network events. By leveraging the network state, the network OS scales up or scales down the necessary network resources and functions across network layers and network technologies. In this way, it meets the changing needs of the service and responds to changing network conditions such as failures and underlying network impairments. To support the dynamics of network services and track real-time network events for large network topologies, the network OS maintains an up-to-date view of the network state using scalable performance monitoring tools. An accurate view of the network state is enhanced by a resiliency infrastructure with mechanisms for fast (< 1 second) error or failure detection of logical and physical elements and the subsequent recovery mechanisms that are triggered by these events.

### Hybridizing the control plane

Recent studies have shown that using sophisticated path computation on a centralized controller instead of the current distributed constrained shortest path first (CSPF) computation approach can lead to as much as 25 percent more revenue-generating traffic being accommodated in the network ([figure 13](#10-9781315365756_chapter-chap4.xhtml#fig4_13)). Moreover, by careful spreading of traffic in the network, overall congestion due to highly utilized links on shortest paths is reduced as well.
