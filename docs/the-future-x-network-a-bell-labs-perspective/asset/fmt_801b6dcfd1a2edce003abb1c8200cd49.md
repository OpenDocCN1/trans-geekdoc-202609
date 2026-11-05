
Over the past decade there has been much research into a concept known **as content-centric networking** (CCN) or, equivalently, **information-centric networking** (ICN), for which the idea was to replace the IP layer (which is host address based) with a new I/CCN layer that is content name based. The fundamental thinking has been that the location of an object (file) was less important than the name of the file, because the requested file was stored and could be found in multiple locations, so routing based on the name was more efficient than routing based on the location. However, this logic becomes questionable when the number of objects becomes very large and the interest in each object more limited, as will be the case with the advent of more user-generated content and with the rise of loT. Therefore, we believe that a hybrid approach, which combines the current IP-based data plane with edge SDN control and cloud-based **interest brokers** and translates user-expressed interests to eventual content-server addresses, will be adopted in the future, rather than the clean-slate **routing paradigm** envisaged by I/CCN.

This hybrid approach is illustrated in [figure 24](#10-9781315365756_chapter-chap4.xhtml#fig4_24). Here, a user interested in a type of video content sends an interest packet expressing that interest using a well-defined namespace. This interest packet is forwarded at the IP layer to an edge SDN switch, which sends the packet to an interest broker. The interest broker translates the request to a specific content item using metadata about content items and users’ interests, and returns the content name to a local stream broker, which then returns an appropriate local server address for this content item to the user. The user then contacts the content server directly to obtain the desired video stream. In this architecture, the global interest brokers and the local stream brokers have the necessary metadata about user interests and content locations for translation of user interests to the appropriate stream server address. The IP forwarding plane together with edge SDN control is then just responsible for forwarding requests between the users and interest brokers and for setting up the paths for stream delivery.

This interest-based model can be applied to all forms of content, including static, dynamic and streaming data as well as generic client-server applications.

![](images/fig4_24.jpg)

Furthermore, it leverages the current IP data plane and does not require the tunable network fabric to support a completely new forwarding plane, as is the case with conventional I/CCN approaches. In addition, any new form of content-based routing can be supported by simply modifying the interest broker function, rather than modifying the underlying IP network fabric.

## Dynamic connectivity marketplace

As discussed earlier, as networks become programmable, and connectivity customers of all types adapt their operations to take advantage of new elastic service flexibility, dynamic cloud networking will become the fastest growing segment of the overall network connectivity market. Large multinational enterprises, global service providers and CDNs, and web-scale cloud data center companies have the scale and sophistication to be the first to take advantage of this new networking paradigm. Because these types of companies are typically global in scope, new forms of dynamic multi-provider programmable networks will be essential to satisfy the predominant upfront demand. Multiple new business models will likely emerge, with two primary options being what we term “alliances” and “brokered marketplaces”.

Similar to the Star Alliance and OneWorld alliances in the airline industry, global network provider alliances or consortia will likely form to establish automatically federated **cloudnets** that provide global reach with ubiquitous local access in each geographic market. These alliances will likely each be anchored on one or more large global network providers. These global-local federations will be made possible by the combination of the tunable network fabric and programmable SDN control within each provider network, and the broader network OS, which federates control over this consortium of autonomous networks.

Ultimately, an open brokered connectivity marketplace will develop. As we have seen across a variety of industries, any market with fast and easy access to a valuable but ephemeral commodity (seats on a flight, ads on a web page, electrical energy on a transmission line, cloud capacity, or gigabits per second on a fiber) will naturally move toward a spot market with dynamic or even real-time pricing. Spot markets more efficiently balance supply and demand, raise the utilization (and thus efficiency) levels of expensive infrastructure, and ultimately maximize economic value within an industry.

Indeed, this development will bring about many changes and new opportunities:

• As in other spot markets, dynamic brokers and aggregators will emerge (or evolve) to efficiently match up large numbers of consumers and suppliers of on-demand capacity in real time

• Large cloud provider and network provider data centers will become the natural exchange hubs of this market, as they represent the source and destination for much of the demand

• Real-time access will open up a much greater opportunity to mix and match different suppliers, types of connection technologies (fiber, microwave, satellite, free-space optics) and reliability levels, as diverse alternate paths become plentiful and readily accessible — all of which will enhance the creation of new economics and business models

• Like other dynamic marketplaces, the supply and demand, as well as the pricing and provisioning of this on-demand connectivity exchange, will be primarily transaction-driven, instead of relying on long- or even medium-term contracts

• New multi-tiered pricing and auction models, making extensive use of analytics-enabled optimization, will be designed to address the dynamic, context-dependent nature of capacity transactions and facilitate real-time bidding to ensure maximum monetization of service opportunities

• Ultimately, as on-demand programmable network functions and capacity become the norm, the legacy static capacity remaining for lease will become relegated to discount stock, in some cases absorbed as part of higher-value on-demand offerings by the real-time aggregators.

![](images/fig4_25.jpg)

In such a dynamic world, those entities (cloud providers, enterprises, service providers, network providers or brokers) with the most automated operations and best alliances with global-local reach will stand to benefit the most, and will be able to leverage their dynamic agility — as supplier or consumer of bandwidth — to win in the marketplace.

## End-to-end perfect future network

In the coming “everything digital” era, the networks of the future must be built around fundamentally different operating principles that allow optimization from top-to-bottom and end-to-end, with massive scale and multinetwork automated service federation, all accessed by programmatic interfaces. The overall architecture of this network is depicted in [figure 25](#10-9781315365756_chapter-chap4.xhtml#fig4_25).

The essential building blocks of this network with seemingly infinite capacity are:

• A highly scalable, tunable network fabric built around data center switching hubs embedded in the network as edge clouds, disaggregated SDN-controllable network functions and components, adaptive impairment-aware multi-layer IP/optical optimization, elastic optical metro transport and ultra-scalable core routers and transport

• A network OS that fully automates and exposes the tunable network fabric and optimizes the federation of control across multiple network domains and network operator boundaries.

![](images/fig4_26.jpg)
