+   - **docker network rm** Deletes specific networks on a Docker host or swarm.

You also ran some native Linux commands.

+   - **brctl show** prints a list of all kernel bridges on the Docker host and shows if any containers are connected.

+   - **ip link show** prints bridge configuration data. You ran an **ip link show docker0** to see the configuration of the **docker0** bridge on your Docker host.

# Chapter Summary

The Container Network Model (CNM) is the design document for Docker networks and defines the three major constructs — sandboxes, endpoints, and networks.

Libnetwork is the reference implementation of the CMN and is an open-source project maintained by the Moby project. Docker uses it to implement its core networking, including control plane services such as service discovery.

Drivers extend the capabilities of libnetwork by implementing specific network topologies, such as bridge and overlay networks. Docker ships with built-in drivers, but you can also use third-party drivers.