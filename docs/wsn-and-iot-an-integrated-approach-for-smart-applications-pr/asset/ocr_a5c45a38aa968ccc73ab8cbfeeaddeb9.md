![](bbox=[0.118, 0.096, 0.881, 0.423])

**Figure 12.5** Components and functionalities of serverless computing.

# 12.4.4 CONTAINER-BASED COMPUTING

Virtualization is a critical technology that enables the deployment of cloud environments in a distributed context. Virtualization allows service providers to assign multiple VM instances to tasks or applications without the user's knowledge, improving resource efficiency and reducing energy consumption. In the past, cloud providers offered resources to users in the form of VM instances, which virtualized resources at the hardware level. Based on bare-metal or hypervisor technology, each VM instance has its own operating system (OS) and shares the processing resources of a host. A hypervisor is a piece of software or hardware that provides the ability to deploy and operate VM instances. The major benefit of VM instances is that they allow for the utilization of server resources and increased parallelism of tasks. This improves the utilization of resources, as shown in Figure 12.6. For example, a single physical server could host multiple VM instances, each running a different application or workload, thereby maximizing the utilization of the server’s resources.

# 12.4.5 MULT-ACCESS EDGE COMPUTING

MEC is a network architecture that enables computing resources and services to be delivered to the edge of a network closer to the end-user. MEC aims to reduce latency, improve network efficiency, and enhance the user experience by providing applications and services closer to the end-user. MEC works by deploying small data centers (edge nodes or servers) at the network’s edge, typically within the mobile operator’s radio access network (RAN) [53]. These edge nodes are equipped with