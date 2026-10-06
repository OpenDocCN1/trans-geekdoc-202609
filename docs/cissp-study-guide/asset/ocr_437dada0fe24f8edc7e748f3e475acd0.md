VLANs may also add defense-in-depth protection to networks; for example, using VLANs to segment data traffic and management traffic.

# Port Isolation

The concept of port isolation is not new but has been revitalized and more commonly employed with the increasing density of virtualized systems in datacenters. Traditional port isolation focused on using software in a managed switch to isolate a port so that could only communicate with the designated uplink. Port isolation, commonly referred to as a Private VLAN or PVLAN, can be used to ensure that individual systems cannot interact with other resources if logically on the same subnet. From a security standpoint this could severely limit the ability of an adversary to pivot or move laterally within an organization after successfully compromising a system.

Architecture, implementing widespread traditional port isolation/PVLANs has seemed to prove cumbersome for many organizations. However, with heavily virtualized infrastructures, port isolation has found a resurgence. Port isolation can provide tremendously useful in multi-tenant environments to ensure isolation amongst customers being served by the same hypervisor. Likewise, even in internal virtual infrastructures, there are often systems that have no need of direct access to one another but are fronted by a single switch. Port isolation can help to ensure logical segmentation within a single switch (virtual).

# SPAN Ports

Since switches provide traffic isolation, a Network Intrusion Detection System (NIDS) connected to a 24-port switch will not see traffic sent to and from other devices on the same switch. Configuring a Switched Port Analyzer (SPAN) port is one way to solve this problem, by mirroring traffic from multiple switches to one “SPAN.” SPAN is a Cisco term; HP switches use the term “Mirror port.”

One drawback to using a SPAN port is bandwidth overload. A 100-megabit, 24-port switch can mirror twenty-three 100-megabit streams of traffic to a 100-megabit SPAN port. The aggregate traffic could easily exceed 100megabits, meaning the SPAN port (and connected NIDS) will miss traffic.

# Network Taps

A network tap provides a way to “tap” into network traffic and see all traffic (including all connections) to a network. Taps are the preferred way to provide meticulous Network Intrusion Detection System.

Taps can “fail open,” so that network traffic will pass in the event of a failure. Taps can also provide access to all traffic, including malformed Ethernet frames. A switch will often “clean” that traffic and not pass it. Finally, Taps can be purchased with memory buffers, which cache traffic bursts.