To connect two switches, plug a standard patch cable into the uplink port on one switch and a standard port on the other. Connecting an uplink to an uplink would negate the crossover.

# **Auto-Medium-Dependent Interface Crossover (MDI-X)** Some newer switches can automatically sense the Transmit and Receive in the connected cables and enable or disable the crossover for the port as needed.

# Switching Loops

Large enterprises have dozens or even hundreds of switches, and it is common practice to create redundant links between them, for fault tolerance purposes. When a host transmits a packet, it travels over its connected switch. if switch has redundant connections to two other switches, each of the other switches will receive an identical copy of the packet. The other switches then forward the packets over their own redundant connections, so more copies of the packet starting around the network. This is called a *switching loop*, and it can monopolize large amounts of bandwidth and cause corruption of the switch MAC addresses.

There is no Time-to-Live field in data layer switching, as there is in network routing, packets do not expire; they circulate endlessly. The situation only occurs when a host generates broadcast transmissions, which the switches forward out through all of their ports, flooding the network with hundreds or thousands of copies. This is called a *broadcast storm*.

To avoid loops and broadcast storms, switches typically use a protocol called the *Spanning Tree Protocol* (STP). STP is a protocol that allows switches to communicate and organize the switching fabric of the network.

Using bridge protocol data units (BPDUs), one switch is elected to the role of *root bridge*, and every root bridge has a designated *root port*. These selected elements work to elect one port on each network segment as its *designated port*. The designated port is the one that forwards traffic to other switches.

All of the other ports—the designated ports—are blocked to data traffic by switches to prevent looping but continuing to receive STP communications from other switches. This communication allows the switches to self-adjust when a link goes down and a designated port becomes unavailable. In that case, one of the nondesignated ports is elected to take over and transitions through several operational phases to becoming the designated port for the segment.

The convergence period of the original STP—published by the IEEE 802.1 working group in 1990—is fifty seconds. Convergence is the time needed to configure all of the ports in a switch with its STP roles. Each time there is a change in the switching fabric of the network, such as a link to a designated port goes down, there is a 50-second convergence delay as the switches readjust.

In 2001, the working group published a revised version of the STP technology called Rapid Spanning Tree Protocol (RSTP), which modifies some of the port designations and