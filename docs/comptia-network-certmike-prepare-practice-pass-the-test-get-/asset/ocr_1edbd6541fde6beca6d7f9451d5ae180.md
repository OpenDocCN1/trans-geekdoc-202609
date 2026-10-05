In addition to servers and storage, other network devices can have built-in redundancies, including the following:

**Switches** As noted in Chapter 11, "Switching," designing a network with redundant switching paths is relatively common in enterprise networking. However, when the switches run in active-active mode, there is a tendency for packets to circulate around the network in switching loops. Switches use the Spanning Tree Protocol (STP) to put individual switching paths into passive mode to prevent switches from repeatedly processing the packets.

**Routers** Unlike switches, which are invisible to the average network user, workstations must have a default gateway address configured, which specifies the router the device will use to access outside networks. Because each has its own IP address, and there is no mechanism to dynamically change a workstation's default gateway address as network conditions change, administrators use specialized protocols called high redundancy protocols (FHRPs), which create a virtual router with its own IP and MAC addresses that stands for the redundant physical routers. By using the virtual router's IP address for a workstation's default gateway, the physical routers can change their active and passive roles without affecting the workstation.

**Firewalls** For load balancing or fault tolerance reasons, an enterprise network can use redundant firewalls that operate as a cluster, as servers do, with a single IP address representing the cluster. This splits the packet processing load among the nodes, ensures high availability, and enables administrators to add and remove them from the cluster as needed. Duplicate firewalls might also be required for a network with connections to multiple Internet service providers.

# FACILITIES AND INFRASTRUCTURE SUPPORT

High availability applies not just to the devices that make up the network, but also to the environment in which those devices run. To run efficiently, the network equipment in a data center or server closet requires a stable power source and an atmosphere with controlled temperature, humidity, and other factors. The data center should also have some measures of protection against disasters, such as fire suppression equipment and sensors to detect flood conditions and toxic gases, as carbon monoxide and radon.

This section describes some of the devices needed to maintain an environmental infrastructure.

# Uninterruptible Power Supply (UPS)

An uninterruptible power supply (UPS) is a battery-based backup power source and power conditioner. The UPS protects the devices connected to it from damage due to power lags