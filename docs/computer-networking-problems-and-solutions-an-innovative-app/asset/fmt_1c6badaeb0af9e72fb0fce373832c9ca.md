
Shifts in operational processes and application architectures are significant changes that some businesses have avoided due to their inherent costs. These businesses have tried to replicate as closely as possible their traditional infrastructure architecture and operations, merely replacing their own hardware with a reflection cast in the public cloud mirror. This approach is analogous to “fitting a square peg into a round hole.” It is possible to take this approach when the square peg is motivated to fit into the round hole with a sufficiently sized hammer, but the result is inelegant and inefficient.

This points to a larger problem many businesses do not consider when outsourcing: the mismatch between the goals of the outsourcer and the goals of the business itself. The goal of the outsourcing business is to produce a product or service that consumers want to purchase; the goal of the outsourcer is to produce a product that the business will consume as much as possible of, at the highest possible margin. It is quite possible for the outsourcer to drive internal business decisions in a direction that is not good for the outsourcing business in order to increase the outsourcer’s revenue and margins.

For instance, it is common for cloud providers and all other vendors — public cloud providers are not unique in this regard — to add new features and functions they can use to leverage their customers into paying more, whether it actually improves their customer’s business or not, and locks the customer in to the cloud provider’s product line.

The vendor lock-in problem is particularly acute in most business environments. When a business commits to using a specific cloud vendor, that business’s operational processes become locked into how a specific vendor delivers its technology. Moving to a different vendor becomes hard, because the target vendor probably delivers its technology differently, even if the technology in question is essentially the same service.

From a networking perspective, cloud computing presents nothing new in the context of vendor lock-in. For decades, networking vendors have delivered products with limited differentiation in functionality, but via widely different consumption models. Sometimes the underlying technology is different while delivering the same result. Other times, the technology is identical, based on industry standards, but configured in unique ways. And yet other times, vendors offer truly differentiated services unavailable from anyone else.

The networking services available in cloud computing don’t break the established paradigm. All vendors offer some baseline of services, but these services can be consumed uniquely. Some might offer special features to set their product apart. The challenge for network engineers is no different than it ever has been, requiring careful comprehension of the technology’s capabilities and applicability to a business’ problems.

The risk of the all-consuming cloud provider: Some cloud providers have, in the past, used a partnership with a customer to learn how to build and support a particular business model, and then used the experience to enter the market as a direct competitor to their own customer. Providing services for unique businesses can be a great incubation strategy for cloud providers to spin up internal analogs to the customers they are supporting, eventually broadening their market reach.

### Technical Challenges of Cloud Networking

For the network engineer, cloud computing presents the challenge of providing low-latency, secure connectivity over a mix of public and private transports using a mix of physical and virtual equipment. In addition, this marvelous cloud-based transport service must also be provisioned and deprovisioned on demand in real time as workloads are stood up and torn down, consumed programmatically, and monitored centrally.

#### Latency

When you are considering how applications are deployed in cloud environments, workload placement becomes especially interesting. Assume an enterprise is deploying an application in a multicloud environment. In this scenario, workloads can be placed in one or more public clouds, as well as in a private cloud.

Developers often break a single application up into microservices, where each component of the application is separated out into a standalone service. The application is then reconstituted as a set of services communicating with one another across the network to support the same overall set of services as the original application.

The problem that microservices architectures face is latency. When communicating over distances measured in kilometers rather than meters, the time it takes packets to traverse the distance is measured in milliseconds instead of submilliseconds; it takes two such trips across the network, the Round Trip Time `RTT` to complete any transaction between the microservices making up an application. Since multiple microservices must interact to produce the same amount of data as the original, monolithic, application, these delays “stack up” to produce a total delay much greater than many developers expect. [Figure 28-2](#ch28.xhtml#ch28fig02) illustrates.

![Image](graphics/28fig02.jpg)

**Figure 28-2** *Stacked Delay in a Microservices Architecture*

In [Figure 28-2](#ch28.xhtml#ch28fig02), A requests some information from the monolithic application; the RTT across the network for processing the request and returning the information is 20ms. When B requests this same information, service 1 must request information from service 2, which must request information from service 3, etc. The total network time in the microservices case is 80ms. If there is any increase in the delay across the network for any reason, the effect is multiplied by four in the microser-vices case, because there are four RTTs involved in every service request.

In applications previously deployed on traditional infrastructure or fully contained in a localized private cloud, latency is far less of a concern. However, applications composed of many components, such as microservices, and spread over a variety of clouds can experience reduced performance due to latency.

For network engineers faced with this problem, at least two solutions present themselves.

**Work with application deployment teams to optimize workload placement.** Workloads are placed in specific clouds for a variety of reasons, including capacity, cost, and functionality. For network engineers, the key is to be involved in the application design so decisions about workload placement include a clear understanding of the infrastructure implications of those placement choices. Application developers in conjunction with infrastructure engineers and business stakeholders should make design decisions jointly.

Every design is a compromise between technical idealism and practical pragmatism. For example, network latency might be an acceptable compromise for a particular design, because the overall application performance is not impacted materially enough. On the other hand, complex applications deployed in ignorance of infrastructure realities might suffer unacceptable performance compromises.

**Bring clouds closer together.** Many data centers offer cloud exchange services, where customers can purchase direct links to public cloud providers, often through a cloud exchange. This means a network engineer can minimize the impact of latency by designing the network to bring clouds closer together.

These services come at a cost and require a purposeful routing design. A common challenge in standing up direct connections to public clouds is that the IP address blocks in question are accessible both via the public Internet and now via the newly introduced cloud exchange circuit. Routing tables must be populated so traffic is forwarded via the cloud exchange, while also avoiding asymmetric routing.

#### Populating Remote Storage
