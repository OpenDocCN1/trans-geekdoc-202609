
# Network Topologies

## Star Network

The star-shaped network has one peculiarity compared to the others: it has a centralized control. In the event of a fault, the whole system is not compromised; in addition, there is better network management and ease of control as everything is managed "centrally". The disadvantage of this mode is that it can create overload on the central system and does not allow sharing.

## Mesh Network

The mesh network allows all hosts to connect directly with others; it is certainly advantageous but has a greater complexity of management and control.

# Network Devices

The main network devices are:

## Repeater

All it does is regenerate the signal. It is not a smart device.

## Hub

It is a repeater with multiple ports that receives the signal on one port and forwards it to all the others.

## Switch

It allows you to connect multiple hosts to each other using a `MAC table` (in the table each host is identified with its own `MAC address`). The received data is delivered to the recipient and not to all hosts as it was in the hub. The switch can work on 2 Layers, i.e. on two levels of the `OSI model`:

### Layer 2 (Data Link)

### Layer 3 (Network Layer)

If it works on both levels it works as both a `ROUTER` and a `SWITCH`.

## Router

`ROUTER`s connect networks to each other. Unlike the `SWITCH`, it does not use `MAC addresses` but uses `IP addresses`. Most `ROUTER`s work both as a `firewall` and `ACL` (access control). There are particular `ROUTER`s that are called `border routers` because they operate between the `LAN` and the `WAN`. `ROUTER`s can also be connected to other `ROUTER`s by creating autonomous zones. Internal networks are usually divided into sub-networks to make them easily manageable; all `ROUTER`s contain information, saved in tables, about destinations. Routing paths, i.e. sending data along a communication channel, can be:

### Static Routing

Fixed routes are chosen.

### Dynamic Routing

`ROUTER`s learn information from other `ROUTER`s to build the routing table. The standards used for communication are: `RIP` (Routing Information Protocol) and `BGP` (Border Gateway Protocol).

## Proxy

The `PROXY` is a device that acts on behalf of others. For security, all user operations with the Internet should be controlled via `PROXY`. The `PROXY` server blocks known malicious sites and stores frequently accessed sites. Usually the `PROXY` is used as a `forward proxy` and the main use is to retrieve data on behalf of a client. The `Reverse Proxy`, known as a surrogate, is an internal server that controls access to a server on a private network. The usage activities are:

- **Authentication**
- **De-encryption**
- **Caching**
- **Load balancing** (`load balancer`)

## Load Balancer

It is nothing more than moving the load from one device to another. Often the device is a server but may well refer to the `CPU` or other devices. It is commonly associated with a device such as a `ROUTER`, `firewall`, `NAT` and so on. The main purpose is to split the traffic to a website into multiple requests that go to redundant servers as soon as they are available. There are two different management methods:

### Round Robin

In the `round robin`, the first request is sent to the first group of servers, the second request to the second group and so on.

### Affinity

The `affinity` instead foresees the sending of similar services to similar servers. You can also use a `virtual IP` (`VIP`); this method offers more flexibility than other `DNS`-based methods. The main disadvantage is that it is a connection-based solution instead of a load-based solution (the assumption is that the load is similar for all connections).

## Access Point

Create a `WLAN` (bridge between wired and wireless network). They consist mainly of a transmitter and a receiver. In addition to functioning as a `bridge` connecting wired network to wireless devices, it can function as a `ROUTER` that retransmits data from one access point to another. The access point works at `Layer 2` of the `OSI model` (data link). `AP`s have many ports to expand the network; some also offer `firewall` and `DHCP` (Dynamic Host Configuration Protocol) functions. They provide private `IP` clients so that Internet traffic cannot access the systems. Basically a `SWITCH` is a `DHCP Server`, a `ROUTER` and a `firewall`. `AP`s can be further classified as follows:

### Fat AP

They must be configured manually with network and security settings.

### Thin AP

They allow remote configuration. They can be easily reconfigured in real time.

### Stand Alone AP

These `AP` types do not require a controller.

### Controller Based AP

They use a controller for centralized management, updates and various functions. Obviously `fat stand alone AP`s are used in small distributions and `thin controller based AP`s in large distributions.

## Modem

The `MODEM` (modulator/demodulator) is nothing more than an analog/digital signal converter and vice versa. `MODEM`s are classified according to their bit/s speed. The current speed is cica 56000 bit/s.

# SOHO Devices

In small networks or small offices there are particular devices that perform all functions; these devices are easy to manage and are called `SOHO` (Small Office Home Office). This device uses a protocol known as `CSMA/CD` (Carrier Sense Multiple Access with Collision Detection) or multiple access via carrier detection with collision detection. The protocol implements the directive: listen before transmitting and while transmitting and if you detect stopped collisions, report the collision to all stations and try again later.

# Network Card

The network card, also called `NIC` (Network Interface Card) uses a unique 48-bit `MAC address`. For physical connections to the network there are two types of connectors: `RJ11` (telephone and fax) and `RJ45` (Internet cable).

# Cable Types

The cable usually used is the `UTP` (Unshielded Twisted Pair) cable consisting of 4 pairs of copper wires coated with a coloured sheath. This type of cable is easy to install and uses the `RJ45` connector, has a diameter of 0.43 cm and a maximum length of 100 meters. `UTP` cables are very sensitive to interference and are vulnerable to tapping. There are various categories of `UTP`:

- `CAT1` (telephone cable)
- `CAT2` (old networks)
- `CAT3` (10 Mbps)
- `CAT4` (16 Mbps)
- `CAT5` (100 Mbps)
- `CAT6` (10 Gbps)

Obviously these types of cables are evolving and over time new types will be introduced that will allow a greater transmission of data.

The `STP` (Shielded Twisted Pair) cable is similar to the `UTP` cable but each pair of wires has its own coating. This cable has a higher shielding and requires grounding. The fiber, unlike copper cables, is not vulnerable to tapping since it has a shielding for each pair of wires in addition to the external shielding even if there are techniques that allow optical tapping even with the fiber; in fact, through the overlapping and splitting of fiber cables, you can access data.

# Transmission

The transmission can be of type:

## Baseband

One signal is transmitted at a time.

## Broadband

Multiple signals are transmitted on different frequencies. The data travels simultaneously.

Wireless transmission can take place via infrared and Bluetooth, creating a point-to-point connection that gives life to `PAN` (Personal Area Network) networks. The standard used is `802.11` which allows data transmission over medium distances and is vulnerable to interception. The standard can be classified as:

### 802.11b

Used in Europe, it uses 13 channels and 3 do not overlap. It has a speed of 11 Mbps with a frequency of 2.4 GHz.

### 802.11g

Used in America and has the same features as `802.11b` but with a speed of 54 Mbps.

### 802.11n

It creates additional channels on the 5 GHz frequency and is much faster with a greater possibility of interference.

### 802.11ac

Comes up to 1300 Mbps on the 5 GHz.
