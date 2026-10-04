
high-speed uplinks. Routers can be used to connect different types of networks. Care must be taken to select the appropriate modules and interfaces for the specific media.

## Operating System Features and Services

Network devices must have operating systems that can support the organization's requirements, such as the following:

- Layer 3 switching
- Network Address Translation (NAT)
- Dynamic Host Configuration Protocol (DHCP)
- Security
- Quality of service (QoS)
- Voice over IP (VoIP)

## IP Addressing for a Small Network (17.1.3)

When implementing a network, it is important to create an IP addressing scheme and use it. Every host or device in an internetwork must have a unique address.

Devices that factor into the IP addressing scheme include the following:

- End-user devices, including the number of devices and the connection types (i.e., wired, wireless, remote access)
- Servers and peripheral devices (for example, printers and security cameras)
- Intermediary devices, including switches and access points

It is recommended that you plan, document, and maintain an IP addressing scheme based on device type. The use of a planned IP addressing scheme makes it easier to identify a type of device and to troubleshoot problems, as, for instance, when troubleshooting network traffic issues with a protocol analyzer.

For example, consider the topology of a small to medium-sized organization in Figure 17-2.

The organization requires three user LANs (that is, 192.168.1.0/24, 192.168.2.0/24, 192.168.3.0/24). The organization has decided to implement a consistent IP addressing scheme for each 192.168.x.0/24 LAN, using the plan shown in Table 17-1.

![](img/e71dc48d3ae3db3394e5857ab2acae75_611_0.png)

Figure 17-2 Small to Medium-Sized Organization Topology

### Table 17-1 Example of a Consistent IPv4 Addressing Scheme

| Device Type | Assignable IP Address Range | Summarized As |
|---|---|---|
| Default gateway (router) | 192.168.x.1–192.168.x.2 | 192.168.x.0/30 |
| Switches (max 2) | 192.168.x.5–192.168.x.6 | 192.168.x.4/30 |
| Access points (max 6) | 192.168.x.9–192.168.x.14 | 192.168.x.8/29 |
| Servers (max 6) | 192.168.x.17–192.168.x.22 | 192.168.x.16/29 |
| Printers (max 6) | 192.168.x.25–192.168.x.30 | 192.168.x.24/29 |
| IP phones (max 6) | 192.168.x.33–192.168.x.38 | 192.168.x.32/29 |
| Wired devices (max 62) | 192.168.x.65–192.168.x.126 | 192.168.x.64/26 |
| Wireless devices (max 62) | 192.168.x.193–192.168.x.254 | 192.168.x.192/26 |

Figure 17-3 shows an example of the 192.168.2.0/24 network devices with assigned IP addresses using the predefined IP addressing scheme.

![](img/e71dc48d3ae3db3394e5857ab2acae75_612_0.png)

Figure 17-3 Small Business Topology with Addressing Assigned

For instance, the default gateway IP address is 192.168.2.1/24, the switch IP address is 192.168.2.5/24, the server IP address is 192.168.2.17/24, and so on.

Notice that the assignable IP address ranges were deliberately allocated on subnet boundaries to simplify summarization of the group type. For instance, assume that another switch with IP address 192.168.2.6 is added to the network. To identify all switches in a network policy, the administrator could specify the summarized network address 192.168.x.4/30.

## Redundancy in a Small Network (17.1.4)

An important part of network design is reliability. Even a small business often relies heavily on its network for business operation. A network failure can be very costly.

To maintain a high degree of reliability, redundancy is required in the network design. Redundancy helps to eliminate single points of failure. There are many ways to accomplish redundancy in a network. Redundancy can be accomplished by installing duplicate equipment, and it can also be accomplished by supplying duplicate network links for critical areas, as shown in Figure 17-4.

![](img/e71dc48d3ae3db3394e5857ab2acae75_613_0.png)

Redundant servers are available in case of server failure.

Redundant links are present to provide alternate paths in case of a link failure.

Redundant switches are present in case of switch failure.

Redundant routers are available in case of router or route failure.

Figure 17-4 Small Network with Redundant Devices and Links

A small network typically provides a single exit point toward the internet through one or more default gateways. If the router fails, the entire network loses connectivity to the internet. For this reason, it may be advisable for a small business to pay for a second service provider as backup.

## Traffic Management (17.1.5)

The goal for a good network design—even in a small network—is to enhance the productivity of the employees and minimize network downtime. The network administrator should consider the various types of traffic and their treatment in the network design.

The routers and switches in a small network should be configured to support real-time traffic, such as voice and video, in an appropriate manner relative to other data traffic. In fact, a good network design implements quality of service (QoS) to classify traffic carefully according to priority during times of congestion, as shown in Figure 17-5.

![](img/e71dc48d3ae3db3394e5857ab2acae75_614_0.png)

Figure 17-5 QoS Priority Queuing

Interactive Graphic

## Check Your Understanding—Devices in a Small Network (17.1.6)

Refer to the online course to complete this activity.

## Small Network Applications and Protocols (17.2)

Along with considering the network devices in a small network, it is important to examine the applications and services that it must support.

## Common Applications (17.2.1)

The previous section discusses the components of a small network, as well as some of the design considerations. These considerations are necessary when you are just setting up a network. After you have set it up, the network still needs certain types of applications and protocols in order to work.

A network is only as useful as the applications that are on it. There are two forms of software programs or processes that provide access to the network: network applications and application layer services.

### Network Applications

Applications are the software programs used to communicate over a network. Some end-user applications are network aware, meaning that they implement application layer protocols and are able to communicate directly with the lower layers of the protocol stack. Email clients and web browsers are examples of this type of application.

### Application Layer Services

Other programs may need the assistance of application layer services to use network resources such as file transfer or network print spooling. Although they are transparent to an employee, these services are the programs that interface with the network and prepare the data for transfer. Different types of data—whether text, graphics, or video—require different network services to ensure that they are properly prepared for processing by the functions occurring at the lower layers of the OSI model.

Each application or network service uses protocols, which define the standards and data formats to be used. Without protocols, the data network would not have a common way to format and direct data. In order to understand the function of various network services, it is necessary to become familiar with the underlying protocols that govern their operation.

On a Windows PC, you use Task Manager to view the currently running applications, processes, and services, as shown in Figure 17-6.

![](img/e71dc48d3ae3db3394e5857ab2acae75_615_0.png)

Figure 17-6 Windows Task Manager

## Common Protocols (17.2.2)

Most of a technician's work, in either a small network or a large network, is in some way involved with network protocols. Network protocols support the applications and services used by employees in a small network.

Network administrators commonly require access to network devices and servers.
The two most common remote access solutions are Telnet and Secure Shell (SSH).
SSH is a secure alternative to Telnet. When connected, administrators can access the SSH server device as though they were logged in locally.

SSH is used to establish a secure remote access connection between an SSH client and other SSH-enabled devices:

- **Network device:** The network device (for example, router, switch, access point) must support SSH to provide remote access SSH server services to clients.
- **Server:** The server (for example, web server, email server) must support remote access SSH server services to clients.

Network administrators must also support common network servers and their required related network protocols, as shown in Figure 17-7 and described in the list that follows:

![](img/e71dc48d3ae3db3394e5857ab2acae75_616_0.png)

Figure 17-7 Common Network Servers

- **Web server:**
  - Web clients and web servers exchange web traffic by using Hypertext Transfer Protocol (HTTP).
  - Web clients and web servers exchange secure web communication by using Hypertext Transfer Protocol Secure (HTTPS).
