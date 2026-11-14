
## 3.5 Network Hardware and Communication

### 3.5.1 Network Hardware

Data also can be transmitted wirelessly. Wireless transmission uses radio signals that travel through the air as radio waves. All wireless technology relies on some form of hardware to transmit and relay the radio signals. For example, our cell phones connect to cell towers that send and receive wireless data, including phone conversations, Internet surfing, email, and text messages. Our computers and other devices connect to Wi-Fi networks to send and receive wireless signals. Wireless earbuds, mice, and keyboards also send and receive data through the air.

As data travels, it can be intercepted. If the data goes through a cable, securing the cable itself and endpoints from physical access is important to ensure data security. If the data goes through the air, it is potentially accessible to anyone in the vicinity, unless it is secured by encryption.

A switch is a network hardware device that forwards data, but does so automatically, without thinking or processing anything as a router would. Switches are important to relay data over long distances, because otherwise the data signal degrades over the length of the cable and would not reach the destination. Switches also can be a point of compromise for criminals seeking unauthorized access to data.

#### 3.5.1.3 Modem

The modem is a piece of external hardware that sits between the computer and the Internet service provider. Typically, Internet service comes into a home or business through a cable and connects to a modem. The modem acts as a translator. In the early days of the Internet, data was transmitted using telephone lines and analog sounds, and the modem did the translating into computer data protocols. Today, the modem is still needed to translate between different data transmission protocols – those inside your network, and those controlled by the Internet provider.

#### 3.5.1.4 Router

Routers “route” data and information. Routers are needed in the business and home environment to move data among the many computing devices on a network. In the home, the modem and router might be housed within a single hardware unit.

In the common home set-up, the modem connects to the router, which then connects to computing devices either by cable or wirelessly. The router establishes a network and routes data along it, allowing multiple devices to communicate with one another and share resources, especially Internet access. A typical home Wi-Fi router can allow a dozen devices to connect wirelessly, all accessing the Internet simultaneously through a single modem. The router keeps track of every conversation that every device in the home is having with every website or other Internet location, and ensures each conversation can proceed without any of the data getting mixed up. Consider it like a mailroom that sends and receives mail on behalf of many building occupants. The networks of an organization are more complex, so more sophisticated routers are used to keep that data moving properly.

Routers create routing tables to keep track of the various devices in the network, and to keep track of their communications. This function makes routers a potential source of evidence in an investigation, since the tables may contain valuable information about who was using a particular network and what communication occurred. Routers are also susceptible to compromise by cybercriminals. Routers have firmware (an operating system) and, like every application, vulnerabilities are periodically discovered. If this firmware is not updated regularly, an attacker may be able to compromise the router. Routers have administrator portals that are secured with a password, and weak or default passwords also can make routers vulnerable to attack.

Since Wi-Fi networks move data through the air, the data is subject to interception. Well-secured Wi-Fi networks use strong encryption to transmit data, and require a strong password to join the network. An open, or public, Wi-Fi network allows anyone to join it. Data transmitted on these unsecured networks is available for anyone to see.

### 3.5.2 Networking Communication and Internet Protocol (IP) Addresses

The Internet is an enormous network of computers that relay data to, from, and on behalf of other computers. Often, two computers using the network will connect with each other to send and receive data, such as when you visit a website. Each portal to the Internet has a unique Internet Protocol (IP) address. These addresses enable Internet communication by specifying the destination and return address of each device online. For communication through the Internet to work, a device needs to know its own IP address, and the IP address of the other computer with which it is communicating, as depicted in Figure 3.6.

![Figure 3.6 Computer to Website Connection.](images/fig3_7.jpg)

Figure 3.6 Computer to Website Connection.

Data sent between two computers must be broken up into smaller pieces, or “packets”, to allow transmission through the Internet to the ultimate destination. Data moving to and from destinations around the world through the Internet passes through a series of computers along the way. Each packet might take a different route from sender to recipient, where it is then reassembled into the original large chunk. To envision this process, imagine you are at a crowded baseball game and want to buy a hotdog from the roaming vendor, but you are stuck ten seats into the row. To pay the vendor standing in the aisle, you might need to pass your money through the crowd, until it gets to the vendor, he gets the hot dog ready and then sends your hotdog back to you with the change. On the Internet, there is a similar dynamic that relies on intermediary computers to send along the data. Unlike passing money and hotdogs straight along the row, however, data travels through the Internet using many different routes, depending upon which Internet servers are available.

There are two kinds of IP addresses: public and private. Public IP addresses are used on the Internet, and private IP addresses are used for private networks in homes or offices, sometimes known as local area networks (LANs). A computer that communicates with the Internet uses both a `private` IP address on its local network and a public IP address as identification online. This process of translating between a public IP and a private IP is known as network address translation (NAT), and is done by the router. Multiple computers can share the same public IP address. The router gives each computer a private IP address on the local network and routes their traffic through the public IP address to the Internet.

Public IP addresses are set up by the Internet Assigned Numbers Authority (IANA), a multinational organization that helps administer IP addresses and other Internet-related systems. IANA allocates address ranges to each country (while some addresses are reserved for private use). Each country then distributes its set of public IP addresses to the nation’s Internet Service Providers (ISPs), the entities through which users access the Internet. When users go online, they use IP addresses from their ISP (e.g. from Comcast, Verizon, etc.).

On a local network, such as the network established by your home Wi-Fi router, the router assigns a `private` IP address for each device on the local network, including itself. The router uses these private IP addresses to keep track of all the devices on the network, and the data being transmitted into and out of each one. The routing table tracks the MAC address and IP address of each device on the network, and assigns virtual ports (virtual mailboxes) to keep track of each computing device’s conversations with the outside world.
