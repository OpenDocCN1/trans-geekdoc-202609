Another aspect to understand is when to use global versus regional load balancers. A global load balancer will manage and distribute traffic coming in from the internet to backends that are distributed across multiple regions. Your users only interact with one application using the same unicast IP address, and a global load balancer can distribute traffic to the closest backend location. Premium Tier is a requirement for global load balancer. Regional load balancers, however, are used when you have a requirement such as regulatory requirements to keep your traffic limited to backends in a particular region. For this type of load balancer, you can use Standard Tier.

![](bbox=[0.148, 0.245, 0.851, 0.638])

# 7.27 – Decision tree for choosing a use type of load balancer

The next important thing to know is which type of load balancer. You can use Figure 7.27 as a decision tree to help you decide.