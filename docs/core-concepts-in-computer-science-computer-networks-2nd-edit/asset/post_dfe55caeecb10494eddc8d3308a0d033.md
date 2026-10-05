
## CORE CONCEPT: WIRELESS LAN

A wireless LAN is one in which a mobile user can connect to a local area network (LAN) through a wireless (radio) connection. The IEEE 802.11 group of standards specify the technologies for wireless LANs. 802.11 standards use the Ethernet protocol and CSMA/CA (carrier sense multiple access with collision avoidance) for path sharing and include an encryption method, the Wired Equivalent Privacy algorithm.

Wireless local area network (WLAN or wireless LAN) consists of two or more computers that communicate wirelessly via radio waves. This is contrasted with a wired LAN, in which each computer in the network is physically tethered with an Ethernet cable to the server's network switch or hub.

The basic structure of all networks consists of a main computer or server, with connected machines known as clients. The server typically has two Ethernet network interface cards (NICs) installed and software that can support the network. Microsoft Windows operating systems have featured built-in networking capability since Windows 98 Special Edition (SE), but third-party networking software is also available. In the case of a simple home LAN, a desktop might be the server while a laptop could be the client.

Let's assume that the desktop is a digital subscriber line (DSL) connection — high-speed Internet service. In order to share the Internet connection via a wireless LAN, the desktop will be physically connected to a wireless DSL modem. The wireless DSL modem might also have a built-in network switch or router. These two devices keep data flowing to the proper machine on the network. If they are not built into the modem, they will have to be purchased separately.

The connections from the desktop to the DSL modem, switch and router are made with physical Ethernet cables. The clients, however, do not require cabling. Instead, each machine must have a wireless NIC installed. USB device or even an internal wireless NIC. Many, but not all, wireless NICs feature a small antenna.

Once the wireless LAN has been set up on the server and client, the machines can communicate by sending and receiving data via radio waves. This makes a wireless LAN very convenient because the client can remain mobile anywhere within the broadcasting range of the network. One can work on a laptop in any room in the house — the backyard in most cases — and still share the network connection from the server.

At the office, a wireless LAN provides instant connectivity to mobile personnel. It also avoids the costly expense of running Ethernet cable throughout a building, easy, effortless desktop connectivity between clients. Because there are no wires running to the clients, one of the main advantages of a wireless LAN is easy installation. Wireless LANs also provide more flexibility than wired LANs and are less expensive.

Two disadvantages of the wireless LAN are that it requires a few more steps to secure it from intrusion; it can be slower and, if interference is present, less reliable than a wired network. However, dependency spells are always improving as technology improves. Some configurations of wireless LANs can compete with wired networks.

Standards of wireless technology are indicated by letter designations. The wireless “g” standard delivers speeds of 54 megabit per second (mbps). With augmented technology like the latest varieties of multiple input output (MIMO), rates reach 100 Mbps. This is about the speed of an average DSL connection and hard-wired network. Previous wireless LAN standards “a” and “b” are slower technologies.

Multiple Input Multiple Output (MIMO) is a wireless communication technology that uses multiple antennas at both the transmitter and receiver to improve the performance and reliability of wireless systems.

## Wireless LAN Overview

WLAN technology and the WLAN industry date back to the mid-1980s when the Federal Communications Commission (FCC) first made the RF spectrum available to industry. During the 1980s and early 1990s, growth was relatively slow. Today, however, WLAN technology is experiencing tremendous growth. The key reason for this growth is the increased bandwidth made by the IEEE 802.11 standard. An introduction to the 802.11 WLAN technology, Table 1 provides some key characteristics at a glance.

**Table 1**: Key Characteristics of 802.11 Wireless LANs

| Characteristic | Description |
| --- | --- |
| Physical Layer | Direct Sequence Spread Spectrum (DSSS), Frequency Hopping Spread Spectrum (FHSS), Orthogonal Frequency Division Multiplexing (OFDM), infrared (IR). |
| Frequency Band | 2.4 GHz (ISM band) and 5 GHz. |
| Data Rates | 1 Mbps, 2 Mbps, 5.5 Mbps (11b), 11 Mbps (11g), 54 Mbps (11a) |
| Data and Network Security | RC4-based stream encryption algorithm for confidentiality, authentication, and integrity. Limited key management. (AES is considered for 802.11i.) |
| Operating Range | Up to 150 feet indoors and 1500 feet outdoors. |
| Positive Aspects | Ethernet speeds without wires; many different products from many different companies. Wireless cards and access point are decreasing. |
| Negative Aspects | Poor security in native mode; throughput decrease with distance and load. |

## Frequency and Data Rates

IEEE developed the 802.11 standards to provide wireless networking technology like the wired Ethernet that has been available for many years. The IEEE 802.11a standard is the most widely adopted member of the 802.11 WLAN family. It operates in the licensed 5 GHz band using OFDM. The popular 802.11b standard operates in the unlicensed 2.4 GHz–2.5 GHz Industrial, Scientific, and Medical (ISM) frequency band using a direct sequence-spectrum technology. The ISM band has become popular for wireless communications because it is available worldwide. The 802.11b WLAN technology permits transmission speeds of up to 11 Mbps per second. This makes it considerably faster than the original IEEE 802.11 standard (that sends data up to 2 Mbps) and slightly faster than standard Ethernet.

## 802.11 Architecture

The 802.11 standard defines two kinds of services: the Basic Service Set (BSS) and the Extended Service Set (ESS) [1, 6]. The BSS is the basic building block of a wireless LAN. A BSS consists of stationary or mobile wireless stations and possibly a central base station (e.g., an AP). When a station is in the BSS, it can communicate with the other members of the BSS.

![](img/f7819d05465fc14719b3ebbba980271a_215_0.png)

Figure 1: Independent and Infrastructure Basic Service Sets.

The BSS without an AP is a stand-alone network and cannot send data to other BSSs. Such BSSs are called Independent BSSs. See Figure 1 (a). Typically, IBSSs involve a small number of stations set up for a specific purpose and for a short period of time (e.g., creating a meeting in a conference room). IBSSs are also referred to as ad hoc networks.

Infrastructure BSSs are distinguished from ad hoc networks by the use of an AP. Figure 1 (b). APs are used for all communications in an infrastructure BSS, including communication between mobile nodes in the service set. An infrastructure BSS is bounded by the coverage distance from the AP. The coverage area of a single AP is called a cell. All mobile stations are required to be within reach of the AP 802.11 allows wireless networks of arbitrarily large size to be created by linking BSSs into an ESS. An ESS is created by chaining BSSs with a backbone network. All APs in an ESS are given the same Service Set Identifier (SSID), which serves as a network name for its users. APs in an ESS operate in a manner such that the outside world can use the station's MAC address to talk to a station without worrying about its location in the ESS.

Figure 4 shows three BSSs corresponding to three APs. There is an equal level of overlap between BSS 1 and BSS 2, and between BSS 2 and BSS 3. Such overlap is necessary to provide stations with seamless connectivity if they move from one BSS to another. In the figure, the router uses the station's MAC address as the destination to deliver frames to a station; only the AP with which is associated delivers the frame.

![](img/f7819d05465fc14719b3ebbba980271a_216_0.png)

**Figure 2**: Extended service set.

Usually, mobility support is the primary motivation for deploying 802.11 network. 802.11 allows mobility between BSSs at the link layer. However, it is not aware of anything that happens above the link layer. When stations move between BSSs, they will find and attempt to associate with an AP with the strongest signal and the least network traffic. This event is often referred to as roaming.

## Wireless LAN Network

A WLAN comprises two types of equipment: a wireless station and an access point. A station, or client, is typically a laptop or
