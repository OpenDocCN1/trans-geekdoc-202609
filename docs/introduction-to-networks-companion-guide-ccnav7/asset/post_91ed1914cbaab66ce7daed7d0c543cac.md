
Table 4-2 shows the UTP cable type, related standards, and typical applications of these cables.

## Table 4-2 Cable Types and Standards

| Cable Type | Standard | Application |
|---|---|---|
| Ethernet straight-through | Both ends T568A or both ends T568B | Connects a network host to a network device such as a switch or hub |
| Ethernet crossover | One end T568A, other end T568B | Connects two network hosts<br>Connects two network intermediary devices (switch to switch or router to router) |
| Rollover | Cisco proprietary | Connects a workstation serial port to a router console port, using an adapter |

## Activity—Cable Pinouts (4.4.4)

For this activity, correctly order the wire colors to a TIA/EIA cable pinout. Select a wire sheath color by clicking it. Then click a wire to apply that sheath to it. Refer to the online course to complete this activity.

![](img/e71dc48d3ae3db3394e5857ab2acae75_194_0.png)

## Fiber-Optic Cabling (4.5)

Networking media selection is being driven by the growing needs for network bandwidth. The distance and performance of fiber-optic cable make it a good media choice for supporting these network needs. This section examines the characteristics of fiber-optic cabling use in data networks.

### Properties of Fiber-Optic Cabling (4.5.1)

As you have learned, fiber-optic cabling is a type of cabling used in many networks today. Because it is expensive, it is not as commonly used as the various types of copper cabling. But fiber-optic cabling has certain properties that make it the best option in certain situations, as discussed in this section.

Optical fiber cable transmits data over longer distances and at higher bandwidths than any other networking media. Fiber-optic cable can transmit signals with less attenuation than copper wire, and it is completely immune to EMI and RFI. Optical fiber is commonly used to interconnect network devices.

Optical fiber contains a flexible but extremely thin, transparent strand of very pure glass, not much bigger than a human hair. Bits are encoded on the fiber as light impulses. The fiber-optic cable acts as a waveguide, or “light pipe,” to transmit light between the two ends with minimal loss of signal.

As an analogy, consider an empty paper towel roll with the inside coated like a mirror. Imagine that it is 1000 meters in length, and a small laser pointer is used to send Morse code signals at the speed of light. Essentially, that is how a fiber-optic cable operates, except that it is smaller in diameter and uses sophisticated light technologies.

### Types of Fiber Media (4.5.2)

Fiber-optic cables are broadly classified into two types: single-mode fiber (SMF) and multimode fiber (MMF).

### Single-Mode Fiber

SMF consists of a very small core and uses expensive laser technology to send a single ray of light, as shown in Figure 4-22. SMF is popular in long-distance situations spanning hundreds of kilometers, such as those required in long-haul telephony and cable TV applications.

![](img/e71dc48d3ae3db3394e5857ab2acae75_195_0.png)

### Multimode Fiber

MMF consists of a larger core and uses LED emitters to send light pulses. Specifically, light from an LED enters the multimode fiber at different angles, as shown in Figure 4-23. It is popular in LANs because they can be powered by low-cost LEDs. It provides bandwidth up to 10 Gbps over link lengths of up to 550 meters.

![](img/e71dc48d3ae3db3394e5857ab2acae75_196_0.png)

Figure 4-23 Multimode Fiber

One of the main differences between MMF and SMF is the amount of dispersion. Dispersion refers to the spreading out of a light pulse over time. Increased dispersion means increased loss of signal strength. MMF has greater dispersion than SMF; this is why MMF can travel only up to 550 meters before signal loss occurs.

### Fiber-Optic Cabling Usage (4.5.3)

Fiber-optic cabling is now being used in four types of industry:

- **Enterprise networks:** Fiber is used for backbone cabling applications and for interconnecting infrastructure devices.
- **Fiber-to-the-home (FTTH):** Fiber is used to provide always-on broadband services to homes and small businesses.
- **Long-haul networks:** Service providers use fiber to connect countries and cities.
- **Submarine cable networks:** Fiber is used to provide reliable high-speed, high-capacity solutions capable of surviving in harsh undersea environments at up to transoceanic distances. Search the internet for “submarine cables telegeography map” to view various maps online.

Our focus in this book is the use of fiber within the enterprise.

### Fiber-Optic Connectors (4.5.4)

A fiber-optic connector terminates the end of an optical fiber. A variety of fiber-optic connectors are available. The main differences among them are their dimensions and the methods of coupling. Businesses decide on the types of connectors that will be used, based on their equipment.

**Note**
Some switches and routers have ports that support fiber-optic connectors through a small form-factor pluggable (SFP) transceiver. Search the internet for various types of SFPs.

The straight-tip (ST) connector (see Figure 4-24) was one of the first connector types used. The connector locks securely with a “twist-on/twist-off” bayonet-style mechanism.

![](img/e71dc48d3ae3db3394e5857ab2acae75_197_0.png)

Figure 4-24 Straight-Tip (ST) Connectors

Subscriber connector (SC) connectors (see Figure 4-25) are sometimes referred to as square connectors or standard connectors. They are widely adopted LAN and WAN connectors that use a push/pull mechanism to ensure positive insertion. This connector type is used with multimode and single-mode fiber.

![](img/e71dc48d3ae3db3394e5857ab2acae75_197_1.png)

Figure 4-25 Subscriber Connector (SC) Connectors

The Lucent Connector (LC) simplex connector (see Figure 4-26) is a smaller version of the SC connector. LC connectors are sometimes called little connectors or local connectors, and their popularity is quickly growing due to their smaller size.

![](img/e71dc48d3ae3db3394e5857ab2acae75_198_0.png)

Figure 4-26 Lucent Connector (LC) Simplex Connector

A duplex multimode LC connector (see Figure 4-27) is similar to an LC simplex connector but uses a duplex connector.

![](img/e71dc48d3ae3db3394e5857ab2acae75_198_1.png)

Figure 4-27 Duplex Multimode LC Connector

Until recently, light could travel in only one direction over optical fiber. Two fibers were required to support full-duplex operation. Therefore, two optical fiber cables needed to be bundled with fiber-optic patch cables and terminated with a pair of standard, single-fiber connectors. Some fiber connectors accept both the transmitting and receiving fibers in a single connector known as a duplex connector (shown in Figure 4-27). BX standards such as 100BASE-BX use different wavelengths for sending and receiving over a single fiber.

### Fiber Patch Cords (4.5.5)

Fiber patch cords are required for interconnecting infrastructure devices. The use of color distinguishes between single-mode and multimode patch cords. A single-mode
fiber cable has a yellow jacket, and a multimode fiber cable has an orange (or aqua) jacket.

Figure 4-28 shows four types of fiber patch cords.

**Note**
A fiber cable should be protected with a small plastic cap when not in use.

![](img/e71dc48d3ae3db3394e5857ab2acae75_199_0.png)

SC-SC Multimode Patch Cord

![](img/e71dc48d3ae3db3394e5857ab2acae75_199_1.png)

LC-LC Single-mode Patch Cord

![](img/e71dc48d3ae3db3394e5857ab2acae75_199_2.png)

ST-LC Multimode Patch Cord

![](img/e71dc48d3ae3db3394e5857ab2acae75_199_3.png)

SC-ST Single-mode Patch Cord

Figure 4-28 Fiber Patch Cords

### Fiber Versus Copper (4.5.6)

There are many advantages to using fiber-optic cable compared to using copper cable. Table 4-3 highlights some of the differences between these cable types.

At present, in most enterprise environments, optical fiber is primarily used as backbone cabling for high-traffic, point-to-point connections between data distribution facilities. It is also used to interconnect buildings in multi-building campuses. Because fiber-optic cables do not conduct electricity and have low signal loss, they are well suited for these uses.

## Table 4-3 UTP and Fiber-Optic Cabling Comparison

| Implementation Issue | UTP Cabling | Fiber-Optic Cabling |
|---|---|---|
| Bandwidth supported | 10 Mbps–10 Gbps | 10 Mbps–100 Gbps |
| Distance | Relatively short (1–100 meters) | Relatively long (1–100,000 meters) |
| Immunity to EMI and RFI | Low | High (completely immune) |
| Immunity to electrical hazards | Low | High (completely immune) |
| Media and connector costs | Lowest | Highest |
| Installation skills required | Lowest | Highest |
| Safety precautions | Lowest | Highest |

## Check Your Understanding—Fiber-Optic Cabling (4.5.7)

Refer to the online course to complete this activity.

![](img/e71dc48d3ae3db3394e5857ab2acae75_200_0.png)

## Wireless Media (4.6)

As more mobile devices are being used, wireless networking is growing in demand. This section explores wireless media characteristic and uses.

### Properties of Wireless Media (4.6.1)

You might be reading this book or taking the accompanying course using a tablet or a smartphone. This is only possible due to the use of wireless media to connect to the physical layer of a network.

Wireless media carry electromagnetic signals that represent the binary digits of data communications using radio wave or microwave frequencies.
