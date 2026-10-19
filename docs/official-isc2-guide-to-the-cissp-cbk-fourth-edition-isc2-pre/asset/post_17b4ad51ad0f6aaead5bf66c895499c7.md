
about bridges: They do not filter broadcasts.

Bridges do not prevent an intruder from intercepting traffic on the local segment. A common type of bridge for many organizations is a wireless bridge based upon one of the IEEE 802.11 standards. While wireless bridges offer compelling efficiencies, they can pose devastating security issues to organizations by effectively making all traffic crossing the bridge visible to anyone connected to the LAN. Wireless bridges must absolutely apply link-layer encryption and any other available native security features, such as access lists, to ensure secure operation.

Switches solve the same issues posed at the beginning of this section, except the solutions are more sophisticated and more expensive. Essentially, a basic switch is a multiport device to which LAN hosts connect. Switches forward frames only to the device specified in the frame’s destination MAC address, which greatly reduces unnecessary traffic. See Figure 4.9.

![](img/3be1e4f35d99b14a974b22ecf8355b5e_718_0.png)

Figure 4.9 – Simple switched network

In this very simple LAN, client A transmits traffic to the server. When the switch receives the traffic, it relays it out of the port to which the server is connected. Client B does not receive any of the traffic. On the other hand, if the switch were a hub, client B would receive the traffic transmitted between client A and the server.

Because client B does not receive the traffic between the other client and server, the likelihood of client B intercepting the traffic is reduced (there are sophisticated attacks that could trick a switch, especially a poorly configured one, into sending traffic to client B).

Switches can perform more sophisticated functions to increase network bandwidth. Due to the increased processing speed of switches, models exist that can make forwarding decisions based on IP address and prioritization of types of network traffic. Like hubs and bridges, switches forward broadcasts.

## Routers

Routers forward packets to other networks. They read the destination layer 3 address (e.g., destination IP address) in received packets, and based on the router’s view of the network, it determines the next device on the network (the next hop) to send the packet. If the destination address is not on a network that is directly connected to the router, it will send the packet to another router.

Routers can be used to interconnect different technologies. For example, connecting a Token Ring and Ethernet networks to the same router would allow IP Ethernet packets to be forwarded to a Token Ring network.

## Transmission Media

### Wired

It is tempting to underestimate the importance of cables in a network. Yet without the cables, there would not be a network, just stand-alone components. One can think of cables as the glue that holds a network together.

Selecting proper cables in a network design is imperative. If inappropriate ones are used, the results can lead to network failures. Cables have to withstand much that threatens the confidentiality, integrity, and availability of the information on the network. Consider the risk of someone tapping into a cable to intercept its signal, electromagnetic interference from nearby devices, or simply the dangers of a cable breaking. This, considered with the technical parameters of cables, shows that the correct cable must be used for each application.

Here are some parameters that should be considered when selecting cables:

- **Throughput** – The rate that data will be transmitted. Certain cables, such as fiber optic, are designed for hauling an incredible amount of data at once.
- **Distance between Devices** – The degradation or loss of a signal (attenuation) in long runs of cable is a perennial problem, especially if the signal is at a high frequency. Also, the time required for a signal to travel (propagation delay) may be a factor. A bus topology that uses collision detection may not operate correctly if the cable is too long.
- **Data Sensitivity** – What is the risk of someone intercepting the data in the cables? Fiber optics, for example, makes data interception more difficult than copper cables.
- **Environment** – It is a cable-unfriendly world. Cables may have to be bent when installing, which contributes to degradation of conduction and signal distortion. The amount of electromagnetic interference is also a factor because cables in an industrial environment with a lot of interference may have to be shielded. Similarly, cables running through areas with wide temperature fluctuations and especially exposure to ultra-violet (sunlight) will degrade faster and be subject to degrading signals.

### Twisted Pair 3.4

Pairs of copper wires are twisted together to reduce electromagnetic interference and cross talk. Each wire is insulated with a fire-resistant material, such as Teflon. The twisted pairs are surrounded by an outer jacket that physically protects the wires. The quality of cable, and therefore its appropriate application, is determined by the number of twists per inch, the type of insulation, and conductive material. To help determine which cables are appropriate for an application or environment, cables are assigned into categories (Table 4.11).

| Category | Speed | Use |
|---|---|---|
| Category 1 | Less than 1 Mbps | Analog voice and basic interface rate (BRI) in Integrated Services Digital Network (ISDN) |
| Category 2 | <4Mbps | 4 Mbps IBM Token Ring LAN |
| Category 3 | 16 Mbps | 10 Base-T Ethernet |
| Category 4 | 20 Mbps | 16 Mbps Token Ring |
| Category 5 | 100 Mbps | 100 Base-TX and Asynchronous Transfer Mode (ATM) |
| Category 5e | 1,000 Mbps | 1000 Base-T Ethernet |
| Category 6 | 10,000 Mbps | 1000 Base-T Ethernet |

Table 4.11 — Cable Categories

### Unshielded Twisted Pair (UTP)

UTP has several drawbacks. Because it does not have shielding like shielded twisted-pair cables, UTP is susceptible to interference from external electrical sources, which could

are connected, network administrators only have to reconnect patch cords. Patch panels and wiring closets must be secured because they offer an excellent place to tap into the network and egress the product. Wiring must be well laid out and neat, and records should be kept in a secure location; otherwise, it is much easier to hide a tap in a mess of wires. Shared wiring closets should be avoided.

### Fiber Optic

A fiber-optic system is similar to the copper wire system that fiber optics may be replacing. The difference is that fiber optics use light pulses to transmit information down fiber lines instead of using electronic pulses to transmit information down copper lines. Looking at the components in a fiber-optic chain will give the security professional a better understanding of how the system works in conjunction with wire based systems.

At one end of the system is a transmitter. This is the place of origin for information coming on to fiber-optic lines. The transmitter accepts coded electronic pulse information coming from copper wire. It then processes and translates that information into equivalently coded light pulses. A light-emitting diode (LED) or an injection-laser diode (ILD) can be used for generating the light pulses. Using a lens, the light pulses are funneled into the fiber-optic medium where they travel down the cable.

Think of a fiber cable in terms of a very long cardboard roll (from the inside roll of paper towels) that is coated with a mirror on the inside. If you shine a flashlight in one end, you can see light come out at the far end - even if it’s been bent around a corner.

Light pulses move easily down the fiber-optic line because of a principle known as total internal reflection. This principle states that when the angle of incidence exceeds a critical value, light cannot get out of the glass; instead, the light bounces back in. When this principle is applied to the construction of the fiber-optic strand, it is possible to transmit information down fiber lines in the form of light pulses. The core must be made from a very clear and pure material. The core can be plastic (used for very short distances), but most are made from glass. Glass optical fibers are almost always made from pure silica, but some other materials, such as fluorozirconate, fluoroaluminate, and chalcogenide glasses, are used for longer-wavelength infrared applications.

There are three types of fiber-optic cable commonly used:

- 1. Single-mode
- 2. Multi-mode
- 3. Plastic Optical Fiber (POF).
