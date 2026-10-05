
# 10: Docker Swarm

Now that you know how to install Docker, pull images, and work with containers, the next logical step is to do it all at scale. That's where Docker Swarm comes into play.

I've split the chapter into the following main parts:

- Docker Swarm – The TLDR
- Swarm primer
- Build a secure Swarm cluster
- Deploy and manage an app on swarm
- Service logs
- The commands

# Docker Swarm – The TLDR

Docker Swarm is two things:

1. An enterprise-grade cluster of Docker nodes
2. An orchestrator of microservices apps

On the clustering front, Swarm groups one or more Docker nodes into a cluster. Out of the box, you get an encrypted distributed cluster store, encrypted networks, mutual TLS, secure cluster join tokens, and a PKI that makes managing and rotating certificates a breeze. You can even add and remove nodes non-disruptively. We call these clusters “swarms”.

On the orchestration front, Swarm makes deploying managing complex microservices apps easy. You define applications declaratively in Compose files and use simple Docker commands to deploy them to the swarm. You can even perform rolling updates, rollbacks, and scaling operations.

Docker Swarm is similar to Kubernetes — both are clusters that run and manage containerized applications. Kubernetes is more popular and has a more active community and ecosystem. However, Swarm is easier to use and is a popular choice for small-to-medium businesses and smaller application deployments. Learning Swarm also prepares you to learn and work with Kubernetes. In fact, if you plan on learning Kubernetes, you should check out my books, Quick Start Kubernetes and The Kubernetes Book.

# Swarm primer

On the clustering front, a swarm is one or more Docker nodes that can be physical servers, VMs, cloud instances, Raspberry Pi’s, and more. The only requirement is that they all run Docker and can communicate over reliable networks.

**Terminology:** When referring to the Docker Swarm technology, we’ll write Swarm with an uppercase “S”. When referring to a swarm as a cluster of nodes, we’ll use a lowercase “s”.

Every node in a swarm is either a manager or a worker:

- Managers run the control plane services that maintain the state of the cluster and schedule user applications to workers
- Workers run user applications

Swarm runs user applications on managers and workers in a default installation. However, you can force user applications to run on worker nodes on important clusters, allowing your managers to focus on cluster management operations.

The swarm stores its state and configuration in an in-memory distributed database that replicates across all manager nodes. Fortunately, it’s automatically configured when you create the swarm and takes care of itself.

Swarm uses TLS to encrypt communications, authenticate nodes, and authorize roles (managers and workers). It also configures and performs automatic key rotation. And with the cluster store, it’s automatically configured when you create the swarm and takes care of itself.

Figure 10.1 shows a high-level view of a swarm with three managers, three workers, and a distributed cluster store replicated across all three managers.

![](img/aae0230bf8529bd80767c4c780dca8d3_249_0.png)

Figure 10.1 High-level swarm

On the orchestration front, Swarm makes it easy to deploy and manage containerized applications. It balances workloads across the cluster and adds cloud-native capabilities such as self-healing, scaling, rollouts, and rollbacks.

That's enough of a primer. Let's build a swarm.

# Build a secure swarm cluster

In this section, you'll build a secure swarm cluster. I'll build the cluster shown in Figure 10.2 with three managers and two workers. You can build a different cluster, but the following rules usually apply:

- Three or five managers are recommended for high-availability
- Enough workers to handle your application requirements

![](img/aae0230bf8529bd80767c4c780dca8d3_250_0.png)

# Pre-reqs

If you’re following along, I recommend using Multipass to create five Docker VMs on your laptop or local machine. Multipass is free and easy to use, and I’ll use it for the examples.

However, running five Multipass VMs requires a lot of system resources as each VM needs 2 CPUs, 40GB of disk space, and 4GB of memory. If your system can handle this, you can create fewer managers and workers or build your lab in [Play with Docker](Play with Docker (PWD) is a free cloud-based service that lets you create up to five nodes in a 4-hour Docker playground. Other Docker environments will also work. All you need is one or more Docker nodes that can communicate over a reliable network. You'll find it easier if you configure name resolution so you can reference nodes by name rather than IP address.

I don't recommend following along on Docker Desktop as it only supports a single node, which isn’t enough for some of the examples later in the book.

# Build your Docker nodes

This section uses Multipass to build the swarm in Figure 10.2.

Search the web for *install multipass* and follow the instructions to install it on your system.

Run the following five `multipass launch` commands to create five VMs running Docker. We’ll refer to each VM as a *node*, and each will require 2 CPUs, 40GB of disk space, and 4GB of RAM. If your machine doesn’t have those resources, go to Play with Docker and build your lab there.

Name three of the nodes as mgr1, mgr2, and mgr3, and name the other two wrk1 and wrk2. Yours will get different IPs, but that doesn't matter. It can take a minute or two to create each VM.

```
$ multipass launch docker --name mgr1
Launched: mgr1

$ multipass launch docker --name mgr2
Launched: mgr2

$ multipass launch docker --name mgr3
Launched: mgr3

$ multipass launch docker --name wrk1
Launched: wrk1

$ multipass launch docker --name wrk2
Launched: wrk2
```

Run the following command and note the node IP addresses. Yours will have different addresses, and you're only interested in the 192.168.x.x address for each.

| Name | State | IPv4 | Image |
| :--- | :--- | :--- | :--- |
| mgr1 | Running | 192.168.64.61 | Ubuntu 22.04 |
| mgr2 | Running | 172.17.0.1, 192.168.64.62 | Ubuntu 22.04 |
| mgr3 | Running | 172.17.0.1, 192.168.64.63 | Ubuntu 22.04 |
| wrk1 | Running | 192.168.64.64, 172.17.0.1 | Ubuntu 22.04 |
| wrk2 | Running | 192.168.64.65, 172.17.0.1 | Ubuntu 22.04 |

Once you've built the nodes, you can log on to them with the multipass shell command, and you can log out by typing exit.

Log on to one of the nodes and check that Docker is installed and running.

```
$ multipass shell mgr1
$ docker --version
Docker version 26.1.1, build 2ae903e
```

Type exit to log out of the node and return to your local shell.

Once you've confirmed your nodes are working, you can move to the next section and build a swarm.

# Initializing a new swarm

The process of building a swarm is called initializing a swarm, and this is the high-level process:

1. Initialize the first manager
2. Join additional managers
3. Join workers.

Before a Docker node joins a swarm, it runs in single-engine mode and can only run regular containers. After joining a swarm, it switches into swarm mode and can run advanced containers called swarm services. More on services later.

When you run a docker swarm init command on a Docker node that's currently in single-engine mode, Docker switches into swarm mode, creates a new swarm, and makes the node the first manager of the swarm. You can then add more nodes as managers and workers, and these nodes also get switched into swarm mode.

You're about to complete all of the following:

1. Initialize a new swarm from mgr1
2. Join wrk1 and wrk2 as worker nodes
3. Join mgr2 and mgr3 as additional managers

After completing the procedure, all five nodes will be in swarm mode and part of the same swarm.

The examples will use the names and IPs from Figure 10.2. Yours will be different, and you should use your own.

1. Log on **mgr1** and initialize a new swarm. Be sure to use the private IP address of **your mgr1** node.

```bash
docker swarm init \
  --advertise-addr 192.168.64.61:2377 \
  --listen-addr 192.168.64.61:2377
```
Swarm initialized: current node (d21lyz...c79qzkx) is now a manager.
<Snip>

```

Let's step through the different parts of the command:

1. **docker swarm init** tells Docker to initialize a new node with this node as the first manager.
2. The **advertise-addr** flag is optional and tells Docker which of the node's IP addresses to advertise as the swarm API endpoint. It's usually one of the node's IP addresses can also be an external load balancer.
3. The **--listen-addr** flag tells Docker which of the node's interfaces to accept swarm traffic on. It defaults to the same value as **--advertise-addr** if you don't specify it.
```