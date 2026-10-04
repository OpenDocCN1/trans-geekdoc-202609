
The numbers in Figure 4-13 identify some key features of STP cable:
- 1. Outer jacket
- 2. Braided or foil shield
- 3. Foil shields
- 4. Twisted pairs

## Coaxial Cable (4.3.5)

*Coaxial cable*, or coax for short, gets its name from the fact that there are two conductors that share the same axis. As shown in Figure 4-14, coaxial cable consists of the following:
- 1. The entire cable is covered with a cable jacket to prevent minor physical damage.
- 2. The insulating material is surrounded by a woven copper braid, or metallic foil, that acts as the second wire in the circuit and as a shield for the inner conductor. This second layer, or shield, also reduces the amount of outside electromagnetic interference.
- 3. A layer of flexible plastic insulation surrounds a copper conductor.
- 4. A copper conductor is used to transmit the electronic signals.

Different types of connectors are used with coax cable. Figure 4-14 shows the Bayonet Neill–Concelman (BNC), N type, and F type connectors.

![](img/e71dc48d3ae3db3394e5857ab2acae75_187_0.png)

![](img/e71dc48d3ae3db3394e5857ab2acae75_187_1.png)

![](img/e71dc48d3ae3db3394e5857ab2acae75_187_2.png)

Figure 4-14 Coaxial Cable and Connectors

The numbers in Figure 4-14 identify some key features of coaxial cable:
- 1. Outer jacket
- 2. Braided copper shielding
- 3. Plastic insulation
- 4. Copper conductor

Although UTP cable has essentially replaced coaxial cable in modern Ethernet installations, the coaxial cable design is used in the following situations:
- **Wireless installations:** Coaxial cables attach antennas to wireless devices. The coaxial cable carries radio frequency (RF) energy between the antennas and the radio equipment.
- **Cable internet installations:** Cable service providers provide internet connectivity to their customers by replacing portions of the coaxial cable and supporting amplification elements with *fiber-optic cable*. However, the wiring inside the customer’s premises is still coax cable.

Interactive Graphic

## Check Your Understanding—Copper Cabling (4.3.6)

Refer to the online course to complete this activity.

## UTP Cabling (4.4)

Copper media has some inherent issues. Twisting the internal pairs of the copper media, as is done in UTP, is a low-cost solution to improve cabling performance. This section further explores UTP cabling.

### Properties of UTP Cabling (4.4.1)

In the previous section, you learned a bit about unshielded twisted-pair (UTP) copper cabling. Because UTP cabling is the standard for use in LANs, this section goes into detail about its advantages and limitations, as well as what can be done to avoid problems.

When used as a networking medium, UTP cabling consists of four pairs of color-coded copper wires that have been twisted together and then encased in a flexible plastic sheath. Its small size can be advantageous during installation.

UTP cable does not use shielding to counter the effects of EMI and RFI. Instead, cable designers have discovered other ways to limit the negative effect of crosstalk:
- **Cancellation:** Designers now pair wires in a circuit. When two wires with magnetic fields exactly opposite each other are placed close together in an electrical circuit, the two magnetic fields cancel each other out and also cancel out any outside EMI and RFI signals.
- **Varying the number of twists per wire pair:** To further enhance the cancellation effect of paired circuit wires, designers vary the number of twists of each wire pair in a cable. UTP cable must follow precise specifications governing how many twists or braids are permitted per meter (3.28 feet) of cable. Notice in Figure 4-15 that the bottom pair (which is orange/orange white, though you can't see that in this book) is twisted less than the pair just above it (which is a blue/blue white pair). Each colored pair is twisted a different number of times.

![](img/e71dc48d3ae3db3394e5857ab2acae75_189_0.png)

Figure 4-15 Different Number of Twists in Each UTP Pair

UTP cable relies solely on the cancellation effect produced by the twisted wire pairs to limit signal degradation and effectively provide self-shielding for wire pairs within the network media.

### UTP Cabling Standards and Connectors (4.4.2)

UTP cabling conforms to the standards established jointly by the TIA/EIA. Specifically, TIA/EIA-568 stipulates the commercial cabling standards for LAN installations and is the standard most commonly used in LAN cabling environments. Some of the elements defined are as follows:
- Cable types
- Cable lengths
- Connectors
- Cable termination
- Methods of testing cable

The electrical characteristics of copper cabling are defined by the Institute of Electrical and Electronics Engineers (IEEE). IEEE rates UTP cabling according to its performance. Cables are placed into categories based on their ability to carry various bandwidth rates. For example, Category 5 cable is used commonly in 100BASE-TX Fast Ethernet installations. Other categories include Enhanced Category 5 cable, Category 6, and Category 6a.

Cables in higher categories are designed and constructed to support higher data rates. As new gigabit speed Ethernet technologies are being developed and adopted, Category 5e is now the minimally acceptable cable type, with Category 6 being the recommended type for new building installations.

Figure 4-16 shows three categories of UTP cable:
- Category 3 was originally used for voice communication over voice lines but later began to be used for data transmission.
- Category 5 and 5e are used for data transmission. Category 5 supports 100 Mbps, and Category 5e supports 1000 Mbps.
- Category 6 has an added separator between each wire pair to support higher speeds. Category 6 supports up to 10 Gbps.
- Category 6a is similar to Category 6 with improved crosstalk characteristics to allow for longer distances.
- Category 7 also supports 10 Gbps.
- Category 8 supports 40 Gbps.

Some manufacturers are making cables exceeding the TIA/EIA Category 6a specifications and refer to these as Category 7.

UTP cable is usually terminated with RJ-45 connectors. The TIA/EIA-568 standard describes the wire color codes and pin assignments (pinouts) for Ethernet cables.

As shown in Figure 4-17, the RJ-45 connector is the male component, crimped at the end of the cable.

The socket, shown in Figure 4-18, is the female component of a network device, wall, cubicle partition outlet, or patch panel.

When terminated improperly, a cable is a potential source of physical layer performance degradation. Figure 4-19 shows an example of a badly terminated UTP cable. This bad connector has wires that are exposed, untwisted, and not entirely covered by the sheath.

![](img/e71dc48d3ae3db3394e5857ab2acae75_191_0.png)

Category 3 Cable (UTP)

![](img/e71dc48d3ae3db3394e5857ab2acae75_191_1.png)

Category 5 and 5e Cable (UTP)

![](img/e71dc48d3ae3db3394e5857ab2acae75_191_2.png)

Category 6 Cable (UTP)

Figure 4-16 Categories of UTP

![](img/e71dc48d3ae3db3394e5857ab2acae75_191_3.png)

![](img/e71dc48d3ae3db3394e5857ab2acae75_191_4.png)

Figure 4-17 RJ-45 UTP Plugs

![](img/e71dc48d3ae3db3394e5857ab2acae75_192_0.png)

![](img/e71dc48d3ae3db3394e5857ab2acae75_192_1.png)

Figure 4-18 RJ-45 UTP Sockets

![](img/e71dc48d3ae3db3394e5857ab2acae75_192_2.png)

Figure 4-19 Poorly Terminated UTP Cable

Figure 4-20 shows a properly terminated UTP cable. It is a good connector with wires that are untwisted only to the extent necessary to attach the connector.

![](img/e71dc48d3ae3db3394e5857ab2acae75_192_3.png)

Figure 4-20 Properly Terminated UTP Cable

> Note
Improper cable termination can impact transmission performance.

### Straight-Through and Crossover UTP Cables (4.4.3)

Different situations may require UTP cables to be wired according to different wiring conventions. This means that the individual wires in the cable have to be connected in different orders to different sets of pins in the RJ-45 connectors.

The following are the main cable types that are created by using specific wiring conventions:
- **Ethernet straight-through:** This is the most common type of networking cable, commonly used to interconnect a host to a switch and a switch to a router.
- **Ethernet crossover:** This cable is used to interconnect similar devices—for example, to connect a switch to a switch, a host to a host, or a router to a router. However, crossover cables are now considered legacy as NICs use medium-dependent interface crossover (auto-MDIX) to automatically detect the cable type and make the internal connection.

Note

Another type of cable is a rollover cable, which is a Cisco-proprietary cable. It is used to connect a workstation to a router or switch console port.

Incorrectly using a crossover or straight-through cable between devices may not damage the devices, but connectivity and communication between the devices will not take place. This is a common error, and checking that the device connections are correct should be the first troubleshooting action if connectivity is not achieved.

Figure 4-21 identifies the individual wire pairs for the T568A and T568B standards.

![](img/e71dc48d3ae3db3394e5857ab2acae75_193_0.png)

Figure 4-21 T568A and T568B Standards
