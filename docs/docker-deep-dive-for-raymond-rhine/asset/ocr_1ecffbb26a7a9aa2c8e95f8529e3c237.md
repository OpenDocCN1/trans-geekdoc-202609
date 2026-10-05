# Building and testing Docker overlay networks

You’ll need at least two Docker nodes configured in a swarm to follow along. The examples in the book show the two nodes on different networks connected by a router, but yours can be on the same network. You can follow along with two Multipass VMs on the same laptop or computer, but any Docker configuration will work as long as the nodes can communicate. I don’t recommend using Docker Desktop as you only get a single node and won’t get the full experience.

Figure 14.1 shows the initial lab configuration. Remember, your nodes can be on the same network, this will just mean your underlay network is simpler. We’ll explain underlay networks later.

![](bbox=[0.178, 0.623, 0.822, 0.848])

Figure 14.1