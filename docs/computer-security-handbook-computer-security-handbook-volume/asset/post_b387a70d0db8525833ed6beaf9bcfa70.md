
## 6.4 LOCAL AREA NETWORK TOPOLOGIES, PROTOCOLS, AND DESIGN

permission to transmit on the medium. There are three common topologies found in LANs: star, ring, and bus.

### 6.2.1 Network Control.

Since LANs are broadcast networks, it is imperative that only a single node be allowed to transmit at any one time. All LANs use a distributed access-control scheme, meaning that all nodes follow the same rules to access the network medium and no one LAN node controls the other nodes’ access. In this way, LAN nodes can come online and offline without bringing the network down.

This description is not meant to suggest that there are no critical elements in a LAN. Indeed, if a central hub, switch, or transmitter fails, the LAN will crash. Distributed control does suggest, however, that all nodes (user stations) follow the same access rules, and failure of a single node will not bring the LAN down. The access-control scheme is defined by the MAC protocol.

### 6.2.2 Star Topology.

In a star topology (see Exhibit 6.1), all devices on the LAN are interconnected through some central device. Since LANs use distributed access-control schemes, all communication is from one node to another, and the central device merely provides a pathway between pairs of devices.

Physical star topologies have a tremendous advantage over other topologies in that they greatly ease network administration, maintenance, reconfiguration, and error recovery. Disadvantages include the single point of failure.

### 6.2.3 Ring Topology.

In a ring topology, the nodes are connected by a set of point-to-point links that are organized in a circle (see Exhibit 6.2). Stations connect to

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_193_0.png)

EXHIBIT 6.1 Star Topology

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_194_0.png)

**EXHIBIT 6.2** Ring Topology

the medium using *active taps* that are actually bit repeaters; a bit is read from the input line, held for a single bit time, then transmitted out to the output line.

A station transmits a message on the network by sending out a bit stream on its outgoing link; thus, rings are unidirectional in nature. Since all of the other stations see the bits one at a time, the intended receiver has no prior warning about an incoming message. For this reason, the transmitter is responsible for removing the message from the ring when the bits come back around. The MAC scheme ensures that multiple stations do not transmit at the same time.

In addition, a ring is a *serial broadcast* network. Because a station sends a message one bit at a time, every other station will see the message as it passes through but each will be receiving a different part of the message at any point in time.

Rings are a common physical LAN topology. However, unlike stars, they have multiple points of failure: if one link or one active tap fails, the integrity of the ring is destroyed. If the probability of failure of a single element is *p* and there are *n* elements, then the probability of failure P{F} of the LAN is

$$P\{F\} = 1 - (1-p)^n$$

As the number of elements rises, the probability of network failure rises exponentially. This problem is of such a critical nature that nearly all ring products use a star-wiring scheme or have some sort of redundancy built in for just this eventuality.

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_195_0.png)

Exhibit 6.3 Bus Topology

### 6.2.4 Bus Topology.

In a *bus topology* (see Exhibit 6.3), all devices are connected to a single electrically continuous medium; for this reason, this topology is also called a common cable or shared medium network. Nodes attach to the medium using a *passive tap*, one that monitors the bit flow without altering it. This is similar to the operation of a voltmeter; it measures the voltage on a power line without changing the available voltage.

Bus networks are analogous to the way appliances are connected to an alternating current (AC) power line. All of the devices draw power from the same source, even if they are on different physical segments of the power distribution network within the building. In addition, the operation of the devices is independent of each other; if the coffeepot breaks, the toaster will still work.

A bus is a *simultaneous broadcast* network, meaning that all stations receive a transmitted message at essentially the same time (ignoring propagation delay through the medium). Most home and business LANs employ a *baseband bus* where direct current (DC) signals are applied directly to the bus by the transmitter without any modification. In addition, transmissions on a baseband bus are broadcast bidirectionally and cannot be altered by the receivers. Bus LAN technologies are employed on cable television systems. For example, they employ a *broadband bus* where the signals are modulated (i.e., frequency shifted) to certain frequencies for transmission in one direction or another.

Buses are the oldest LAN topology and are generally limited in the type of medium that they can use. They do not usually suffer from single-point-of-failure problems.

### 6.2.5 Physical versus Logical Topology.

A distinction was made above between the *physical* and *logical* topology of a LAN. *Physical* topology describes how the stations are physically positioned and attached to each other whereas the *logical* topology describes how the signals propagate and the logical operation of the network.

In all of today’s commonly used LANs, the logical topology differs from the physical topology. The most common LAN configuration today is a *star-wired bus* (see Exhibit 6.4). This type of network has a star topology where all stations are physically attached with point-to-point links to a central device. This central device contains a bus that interconnects all of the I/O ports in such a way that when one station transmits a message, all stations will receive it. Since this acts exactly like a simultaneous broadcast, or bus, network, we categorize this configuration as a physical star, logical bus.

Another common configuration is a *star-wired ring* (see Exhibit 6.5). In this configuration, the bits will travel in logical order from station A to B, C, A, and so forth,

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_196_0.png)

Exhibit 6.4 Star-Wired Bus

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_196_1.png)

Exhibit 6.5 Star-Wired Ring

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_197_0.png)

Exhibit 6.6 Bus-Wired Ring (The station identifier is shown above the station ID of the predecessor and successor stations in the logical ring.)

which matches the serial broadcast operation of a ring. We call this a physical star, logical ring.

Although uncommon today, another hybrid technology is the bus-wired ring (see Exhibit 6.6). In this configuration, nodes are passively attached to a single cable, forming a physical bus. Each station maintains a table specifying the address of predecessor and successor stations, thus forming a logical ring.

## 6.3 MEDIA.

The next paragraphs discuss the three primary types of LAN media currently in use. Due to their relatively high speed, small geographic size, and protected environments, a number of media types can be employed with LANs.

### 6.3.1 Coaxial Cable.

Coaxial cable (coax) is the original LAN medium. It gets its name from the physical composition of the cable itself (see Exhibit 6.7). At the center of the cable is a conductor, usually made of copper, which is surrounded by an insulator that, in turn, is surrounded by another conductor that acts as an electrical shield. Since the shield completely surrounds the central conductor and the two have a common axis, the shield prevents external electrical noise from affecting signals on

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_197_1.png)

Outer Insulation
Outer Conductor
Inner Insulation
Center Conductor

Exhibit 6.7 Coaxial Cable

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_198_0.png)

Exhibit 6.8 Unshielded Twisted Pair

the conductor and prevents signals on the conductor from generating noise that affects other cables.

Coaxial cables vary in size from 1/4–1 inch (6.35–25.4 mm), depending on the thickness of the conductor, shield, and insulation. Applications for coax range from cable television to LANs. Speeds in excess of several hundred Mbps at distances of several hundred to several thousand meters can be achieved. Coaxial cable also has a high immunity from electromagnetic and radio frequency interference. However, it is easy to tap.

Coaxial cable is only seen in physical bus LANs such as Ethernet. The original Ethernet specification, in fact, called for a thin coaxial cable; a later version that employed thin (CATV) coax was dubbed CheaperNet. Coax is not typically found in star or ring networks.

Coaxial cable is easy to wiretap.²

### 6.3.2 Twisted Pair.

The medium enjoying the largest popularity for LAN applications today is twisted pair. Twisted pair cable consists of two insulated copper conductors that are twisted around each other (see Exhibit 6.8). This is typically 22- to 26-gauge (i.e., 0.025"/0.644 mm to 0.016"/0.405 mm) wire, the same as is used for telephone wiring. Twisting the conductors around each other minimizes the effect of external electrical radiation on the signal carried on the wire; if external voltage is applied to one wire of the pair, it will be applied equally to the other wire. The twisting, then, effectively eliminates the effect of the external noise. As the number of twists per inch increases, the noise reduction characteristics improve; unfortunately, so does the overall amount of cable and the cost. Most twisted pair for telephony applications has 10 to 15 twists per foot.

The type of twisted pair cable shown in Exhibit 6.8 is called unshielded twisted pair (UTP) because the wire pair itself is not shielded. The data-carrying capacity of UTP is generally indicated by its category:

- Level 1 (sometimes called Category 1, or Cat 1) cable is older 0.4 MHz cable used for some telephone and modem applications, but is generally unsuited for data applications.
- Level 2 (sometimes called Category 2, or Cat 2) cable is 4 MHz cable used for legacy data terminal systems, such as IBM 3270 BISYNC.
- Category 3 (Cat 3) cable has a maximum bandwidth of 16 MHz and is rated for 10 Mbps over a wire segment of 100 m (although speeds of 100 Mbps can often be achieved). Cat 3 cable is rated up to 16 Mbps and is primarily used today for telephones.
- Category 4 (Cat 4) cable, with a maximum bandwidth of 20 MHz, was used for IBM’s 16 Mbps Token Ring networks. It is not commonly seen today.
