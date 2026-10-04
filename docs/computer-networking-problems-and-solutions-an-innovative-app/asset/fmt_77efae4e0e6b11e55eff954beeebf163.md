
4. IS-IS and OSPF rely on sequence numbers to indicate which piece of information being flooded through the network is the most recent. Read `RFC7602` and `RFC5310`. Describe the problem caused by this reliance and how IS-IS resolved this problem. Are there problems with the solution standardized in `RFC7602`?

5. Compare OSPF and IS-IS data marshalling using the complexity model described earlier in the book (`state/optimization/surface`). Where do you think these two protocols have traded off state for optimization? Do the multiple LSA types and reliance on IP fragmentation represent an interaction surface that increases the complexity of OSPF?

6. Describe the security issue created by the link state age-out and reflood behavior of both OSPF and IS-IS. Find and describe the solution proposed in the IETF.

7. Consider DIS/DR election on a point-to-point link that is considered a broadcast medium (such as a point-to-point Ethernet link). Will electing a DR/DIS and creating a pseudonode reduce overall complexity or increase it? What features have been implemented in commercial implementations of OSPF and IS-IS to mitigate the result?

[1](#ch16.xhtml#ch16fn1). Katz, “OSPF and IS-IS: A Comparative Anatomy.”

[2](#ch16.xhtml#ch16fn2). White and Retana, *IS-IS: Deployment in IP Networks*.

[3](#ch16.xhtml#ch16fn3). Mirtorabi et al., “OSPFv3 LSA Extendibility.”

[4](#ch16.xhtml#ch16fn4). Retana and White, “BGP Custom Decision Process.”

# Chapter 17  
Policy in the Control Plane

## Learning Objectives

After reading this chapter, you should understand:

![Image](graphics/bull.jpg)How to define control plane policy

![Image](graphics/bull.jpg)Hot and cold potato routing as examples of control plane policy

![Image](graphics/bull.jpg)How to create virtual topologies as a policy implementation mechanism

![Image](graphics/bull.jpg)Basic traffic engineering concepts, such as flow pinning

The last several chapters have considered the many variations on finding a set of loop-free paths through a network. In the explanation of the Border Gateway Protocol (`BGP`), however, you might have noticed the emphasis on various policies, rather than strictly finding loop-free paths. This chapter, then, will continue the emphasis on policy begun in the preceding chapter.

The first question to answer is: what is policy? Unfortunately, there is no simple answer. The best way to answer this question is through examples; these will be considered in the following section. The second section of this chapter will draw lessons from these examples, and then consider problems and solutions in the control plane policy space.

**Note**

Control policy is often difficult to separate conceptually from data plane policy, such as packet filtering and Quality of Service (`QoS`). In fact, the two overlap in many places, such as the control plane carrying QoS markings that are then applied to packets, or drawing packets into a null interface, effectively dropping them. These sorts of corner cases are avoided here for clarity.

### Control Plane Policy Use Cases

Often the best way to understand a concept is through examples. This section examines three examples of policy being used in the control plane to fulfill business requirements: determining where traffic should exit a provider network, optimizing application performance by pinning elephant flows, and increasing or providing security through network segmentation. The next section draws a set of lessons from these examples.

#### Routing and Potatoes

Service providers normally live within a world of tight budgets, application requirements, and business drivers. The mixture of these three can make for some strange situations when routing between providers of various kinds. Specifically, cold potato routing is designed to keep traffic inside the provider’s network for as long as possible, while hot potato routing is designed to push traffic to the closest exit point possible. The result of mixing these two is sometimes called (tongue in cheek) mashed potato routing. [Figure 17-1](#ch17.xhtml#ch17fig01) is used to explain.

![Image](graphics/17fig01.jpg)

**Figure 17-1** *Routing and Potatoes*

Assume `AS65000` is an edge provider, or perhaps an “enterprise” network connected to two upstream providers, `AS65001` and `AS65003`. `AS65001`, `AS65003`, and `AS65004` are transit providers, and `AS65002` is a content provider. Some of the policies and business drivers for those policies in this collection of networks might be

• `AS65001` wants to draw as much traffic from `AS65000`, across link C, as possible. The more this link is filled up, the more likely `AS65000` is to purchase an upgraded link. There is actually little `AS65001` can do to attract traffic, of course, other than perhaps trying to convince the administrators in `AS65000` to ship more traffic their direction, or trying to improve the performance of the link from the perspective of some sort of traffic engineering system `AS65000` might have configured on their end of the link.

• `AS65001` wants to forward any traffic entering at link C to the closest exit with a route to the destination. For instance, if `AS65003` is advertising a route to K, on the right side of the diagram, `AS65001` will prefer the exit through link D, even though it might not be the shortest overall path to the destination. Normally, `AS65001` would implement this sort of policy using `BGP`’s local preference, or by relying on the underlying Interior Gateway Protocol (`IGP`) metric to draw traffic to the closest exit point out of the Autonomous System (`AS`). This is called hot potato routing. Why does `AS65001` want to push the traffic to the nearest exit point with a route to the destination? Because carrying the traffic along the path to link H, for instance, consumes network resources. `AS65001` is being paid based on the usage of link C, rather than for actually carrying the traffic as close as possible to the destination. Hence, `AS65001` will draw as much traffic as possible off its paying customers but then push the traffic to the nearest exit point.

• `AS65002`, on the other hand, generally wants to control its user’s experience as tightly as possible, because it is selling a service. If the network between the service and the user has poor quality, then the service itself is perceived to be poor quality, and the content provider’s overall business will suffer. The longer the traffic stays in `AS65002`’s network, the more control the content provider has over the Quality of Service delivery. Keeping the customer’s traffic inside the network is essentially bringing the customer’s eyeballs closer to the service itself. This is a form of cold potato routing. Instead of tossing the traffic out of your network as quickly as possible (as you would with a hot potato), you hold on to the traffic as long as possible (like a cold potato). In this case, `AS65002` is going to perceive the closest exit point to the customer as being through `AS65001` at link H because the path through H has the shortest AS path. Although the internal path is longer, `AS65002` will choose the path through link H to control the traffic as long as possible.

• When traffic is received at link H, `AS65001` needs to decide whether to send the traffic to some nearby exit point, say link F, or to carry the traffic along the entire network so it exits at link C. In this case, `AS65001` will almost always decide to carry the traffic along its entire network. Again, the primary selling point `AS65001` has toward `AS65000` is to increase the average utilization along link C. To do this, `AS65001` needs traffic to send toward `AS65000`; the only way to get this traffic is to carry traffic from every entry point into the network to the connection to the customer, if the destination is a customer. This is again cold potato routing.
