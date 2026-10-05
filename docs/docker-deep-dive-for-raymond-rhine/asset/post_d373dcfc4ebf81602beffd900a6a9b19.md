
Fortunately, Docker already works with Wasm, and Docker Desktop ships with lots of popular Wasm runtimes. This means you can use industry-standard tools such as `docker build` and `docker run` to containerize and run Wasm apps. You can even push them to OCI registries such as Docker Hub.

# 13: Docker Networking

It’s always the network!

Any time we experience infrastructure issues, we always blame the network. One of the reasons we do this is that networks are at the center of everything. With this in mind, it’s important you have a strong understanding of Docker networking.

In the early days of Docker, networking was hard. Fortunately, these days it’s almost a pleasure ;)

This chapter will get you up to speed with the fundamentals of Docker networking. You’ll learn all the theory behind the Container Network Model (CNM) and libnetwork, and you’ll get your hands dirty with lots of examples. You’ll learn about overlay networks in the next chapter.

I’ve divided the chapter into the following sections:

- Docker networking – the TLDR
- Docker networking theory
- Single-host bridge networks via port mappings
- Connecting to existing networks and VLANs
- Service Discovery
- Ingress load balancing

A few quick things before we start.

Everything we'll cover relates to Linux containers, and I recommend you follow along using something like Multipass or Play with Docker, as they give you easy access to some of the Linux commands we'll use. I don't recommend following along on Docker Desktop as it runs everything inside a Linux VM and you won't have access to the Linux commands.

Some of the examples explain how networking works on a swarm. You'll only be able to follow these if you're following along with a Swarm cluster.

# Docker Networking – The TLDR

Docker runs microservices applications comprised of many containers that work together to form the overall app. These containers need to be able to communicate, and some will have to connect with external services, such as physical servers, virtual machines, or something else.

Fortunately, Docker has solutions for both of these requirements.

Docker networking is based on libnetwork, which is the reference implementation of an open-source architecture called the Container Network Model (CNM).

For a smooth out-of-the-box experience, Docker ships with everything you need for the most common networking requirements, including multi-host container-to-container networks and options for plugging into existing VLANs. However, the model is pluggable, and the ecosystem can extend Docker's networking capabilities via drivers that plug into libnetwork.

Last but not least, libnetwork also provides native service discovery and basic load balancing.

That's the big picture. Let's get into the detail.

# Docker networking theory

At the highest level, Docker networking is based on the following three components:

- The Container Network Model (CNM)
- Libnetwork
- Drivers

The CNM is the design specification and outlines the fundamental building blocks of a Docker network.

Libnetwork is a real-world implementation of the CNM. It’s open-sourced as part of the Moby project and used by Docker and other platforms.

Drivers extend the model by implementing specific network topologies such as VXLAN overlay networks.

Figure 13.1 shows all three.

![](img/aae0230bf8529bd80767c4c780dca8d3_338_0.png)

Figure 13.1

Let's take a closer look at each.

# The Container Network Model (CNM)

Everything starts with a design.

The design guide for Docker networking is the CNM that outlines the fundamental building blocks of a Docker network.

I recommend you read the [specification document], but at a high level, it defines three building blocks:

- Sandboxes
- Endpoints
- Networks

A sandbox is an isolated network stack inside a container. It includes Ethernet interfaces, ports, routing tables, DNS configuration, and everything else you’d expect from a network stack.

Endpoints are virtual network interfaces that look, smell, and feel like regular network interfaces. They connect sandboxes to networks.

Networks are virtual switches (usually software implementations of an 802.1d bridge). As such, they group together and isolate one or more endpoints that need to communicate.

Figure 13.2 shows how all three connect and relate to familiar infrastructure components. Using CNM terminology, endpoints connect sandboxes to networks. Every container you create will have a sandbox with at least one endpoint connecting it to a network.

![](img/aae0230bf8529bd80767c4c780dca8d3_340_0.png)

As the name suggests, the Container Network Model is all about providing networking for containers. Figure 13.3 shows how CNM components relate to containers — each container gets its own sandbox which hosts the container's entire network stack, including one or more endpoints that act as Ethernet interfaces and can be connected to networks.

![](img/aae0230bf8529bd80767c4c780dca8d3_341_0.png)

Figure 13.3

Container A has a single interface (endpoint) and is only connected to Network A. However, Container B has two interfaces connected to Network A and Network B. The containers can communicate with each other because they are both connected to Network A. However, the two endpoints inside of Container B cannot communicate with each other as they're on different networks.

It’s also important to understand that endpoints behave exactly like regular network adapters, meaning you can only connect them to a single network. This is why Container B needs two endpoints if it wants to connect to both networks.

Figure 13.4 extends the diagram further by adding the Docker host. Even though both containers are running on the same host time, their network stacks are completely isolated and can only communicate via a network.

![](img/aae0230bf8529bd80767c4c780dca8d3_342_0.png)

Figure 13.4

# Libnetwork

Libnetwork is the reference implementation of the CNM. It’s open-source, cross-platform (Linux and Windows), maintained by the Moby project, and used by Docker.

Before Docker created libnetwork, it implemented all of its networking code inside the daemon. However, over time, the daemon became bloated and difficult for other projects to use. As a result, Docker removed the networking code from the daemon and refactored it as an external library called libnetwork based on the CNM design. Today, Docker implements all of its core networking in libnetwork.

As well as implementing the core components of the CNM, libnetwork also implements the network control plane, including management APIs, service discovery, and ingress-based container load balancing.

# Drivers

Libnetwork implements the control plane, but it relies on drivers to implement the data plane. For example, drivers are responsible for creating networks and ensuring isolation and connectivity.

Docker ships with several built-in drivers that we sometimes call native drivers or local drivers. These include bridge, overlay, and macvlan, and they build the most common network topologies. Third parties can also write network drivers to implement other network topologies and more advanced configurations.

Figure 13.5 shows the roles of libnetwork and drivers and how they relate to control plane and data place responsibilities.

![](img/aae0230bf8529bd80767c4c780dca8d3_344_0.png)

Every network you create is owned by a driver, and the driver creates and manages everything about the network. For example, if you create an overlay network called prod-fe-cuda, Docker will invoke the overlay driver to create the network and its resources.

To meet the demands of complex, highly fluid environments, a single Docker host or Swarm cluster can have multiple heterogeneous networks managed by different drivers.

Let's look at single-host bridge networks and connecting to existing networks. You'll learn about overlay networks in the next chapter.

# Single-host bridge networks
