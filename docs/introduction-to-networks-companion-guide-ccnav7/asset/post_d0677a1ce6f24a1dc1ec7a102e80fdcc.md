
![](img/e71dc48d3ae3db3394e5857ab2acae75_341_0.png)

## Video—ARP Operation—ARP Reply (9.2.4)

Only the device with the target IPv4 address associated with the ARP request responds with an ARP reply. The ARP reply is encapsulated in an Ethernet frame using the following header fields:

- **Destination MAC Address:** This is the MAC address of the sender of the ARP request.
- **Source MAC Address:** This is the MAC address of the sender of the ARP reply.
- **Type:** ARP messages have a Type field setting of 0x806. This informs the receiving NIC that the data portion of the frame needs to be passed to the ARP process.

Only the device that originally sent an ARP request receives a unicast ARP reply. After the ARP reply is received, the device adds the IPv4 address and the corresponding MAC address to its ARP table. Packets destined for that IPv4 address can then be encapsulated in frames using the corresponding MAC address.

If no device responds to an ARP request, the packet is dropped because a frame cannot be created.

Entries in the ARP table are timestamped. If a device does not receive a frame from a particular device before the timestamp expires, the entry for this device is removed from the ARP table.

In addition, static map entries can be entered in an ARP table, but this is rarely done. Static ARP table entries do not expire over time and must be manually removed.

**Note:** Whereas IPv4 uses ARP, IPv6 uses a similar process, known as ICMPv6 Neighbor Discovery (ND). IPv6 uses neighbor solicitation and neighbor advertisement messages, which are similar to IPv4 ARP requests and ARP replies.

Refer to the online course to view this video.

![](img/e71dc48d3ae3db3394e5857ab2acae75_341_1.png)

## Video—ARP Role in Remote Communications (9.2.5)

When the destination IPv4 address is not on the same network as the source IPv4 address, the source device needs to send the frame to its default gateway. This is the interface of the local router. Whenever a source device has a packet with an IPv4 address on another network, it encapsulates that packet in a frame, using the destination MAC address of the router.

The IPv4 address of the default gateway is stored in the IPv4 configuration of the hosts. When a host creates a packet for a destination, it compares the destination IPv4 address and its own IPv4 address to determine if the two IPv4 addresses are located on the same Layer 3 network. If the destination host is not on its same network, the source checks its ARP table for an entry with the IPv4 address of the default gateway. If there is not an entry in the ARP table, the source uses the ARP process to determine the MAC address of the default gateway.

Refer to the online course to view this video.

## Removing Entries from an ARP Table (9.2.6)

For each device, an ARP cache timer removes ARP entries that have not been used for a specified period of time. The times differ depending on the operating system of the device. For example, newer Windows operating systems store ARP table entries for 15 to 45 seconds, as illustrated in Figure 9-8.

Commands may also be used to manually remove some or all of the entries in the ARP table. After an entry has been removed, the process for sending an ARP request and receiving an ARP reply must occur again in order to once again enter the map in the ARP table.

![](img/e71dc48d3ae3db3394e5857ab2acae75_342_0.png)

MAC addresses are shortened for demonstration purposes.

Figure 9-8 Removing MAC-to-IP Address Mappings

## ARP Tables on Networking Devices (9.2.7)

On a Cisco router, the show ip arp command is used to display the ARP table, as shown in Example 9-1.

### Example 9-1 Cisco Router ARP Table

```
R1# show ip arp
Protocol Address Age (min) Hardware Addr Type Interface
Internet 192.168.10.1 - a0e0.af0d.e140 ARPA GigabitEthernet0/0/0
Internet 209.165.200.225 - a0e0.af0d.e141 ARPA GigabitEthernet0/0/1
Internet 209.165.200.226 1 a03d.6fe1.9d91 ARPA GigabitEthernet0/0/1
R1#
```

On a Windows 10 PC, the arp -a command is used to display the ARP table, as shown in Example 9-2.

### Example 9-2 Windows 10 PC ARP Table

```
C:\Users\PC> arp -a
Interface: 192.168.1.124 --- 0x10
Internet Address Physical Address Type
192.168.1.1 c8-d7-19-cc-a0-86 dynamic
192.168.1.101 08-3e-0c-f5-f7-77 dynamic
192.168.1.110 08-3e-0c-f5-f7-56 dynamic
192.168.1.112 ac-b3-13-4a-bd-d0 dynamic
192.168.1.117 08-3e-0c-f5-f7-5c dynamic
192.168.1.126 24-77-03-45-5d-c4 dynamic
192.168.1.146 94-57-a5-0c-5b-02 dynamic
192.168.1.255 ff-ff-ff-ff-ff-ff static
224.0.0.22 01-00-5e-00-00-16 static
224.0.0.251 01-00-5e-00-00-fb static
239.255.255.250 01-00-5e-7f-ff-fa static
255.255.255.255 ff-ff-ff-ff-ff-ff static
C:\Users\PC>
```

## ARP Issues—ARP Broadcasts and ARP Spoofing (9.2.8)

As a broadcast frame, an ARP request is received and processed by every device on the local network. On a typical business network, these broadcasts would probably have minimal impact on network performance. However, if a large number of devices were to be powered up and all start accessing network services at the same time, there could be some reduction in performance for a short period of time, as shown in Figure 9-9. After the devices send out the initial ARP broadcasts and have learned the necessary MAC addresses, any impact on the network will be minimized.

### All devices powered on at the same time

Shared Media (multiple access)

![](img/e71dc48d3ae3db3394e5857ab2acae75_344_0.png)

ARP broadcasts can flood the local media.

### Figure 9-9 ARP Broadcasts Flooding a Network

In some cases, the use of ARP can lead to a potential security risk. A threat actor can use ARP spoofing to perform an ARP poisoning attack. This is a technique used by a threat actor to reply to an ARP request for an IPv4 address belonging to another device, such as the default gateway, as shown in Figure 9-10. The threat actor sends an ARP reply with its own MAC address. The receiver of the ARP reply adds the wrong MAC address to its ARP table and sends these packets to the threat actor.

![](img/e71dc48d3ae3db3394e5857ab2acae75_344_1.png)

Note: MAC addresses are shortened for demonstration purposes.

### Figure 9-10 Threat Actor Spoofing an ARP Reply

Enterprise-level switches can use mitigation techniques such as dynamic ARP inspection (DAI). DAI is beyond the scope of this course.

![](img/e71dc48d3ae3db3394e5857ab2acae75_345_0.png)

## Packet Tracer—Examine the ARP Table (9.2.9)

In this Packet Tracer activity, you will complete the following objectives:

- Examine an ARP Request
- Examine a Switch MAC Address Table
- Examine the ARP Process in Remote Communications

This activity is optimized for viewing PDUs. The devices are already configured. You will gather PDU information in simulation mode and answer a series of questions about the data you collect.

![](img/e71dc48d3ae3db3394e5857ab2acae75_345_1.png)

## Check Your Understanding—ARP (9.2.10)

Refer to the online course to complete this activity.

## IPv6 Neighbor Discovery (9.3)

This section discusses the relationship between MAC addresses and IPv6 addresses and how the Neighbor Discovery (ND) protocol is used to map the two addresses.

![](img/e71dc48d3ae3db3394e5857ab2acae75_345_2.png)

## Video—IPv6 Neighbor Discovery (9.3.1)

If your network is using the IPv6 communications protocol, the Neighbor Discovery protocol (ND) is what matches IPv6 addresses to MAC addresses. This section explains how ND works.

Refer to the online course to view this video.

## IPv6 Neighbor Discovery Messages (9.3.2)

IPv6 Neighbor Discovery protocol is sometimes referred to as ND or NDP. In this book, we refer to it as ND. ND provides address resolution, router discovery, and redirection services for IPv6 using ICMPv6. ICMPv6 ND uses five ICMPv6 messages to perform these services:

- Neighbor Solicitation messages
- Neighbor Advertisement messages
- Router Solicitation messages
- Router Advertisement messages
- Redirect message

Neighbor Solicitation and Neighbor Advertisement messages are used for device-to-device messaging such as address resolution (similar to ARP for IPv4). Devices include both host computers and routers, as shown in Figure 9-11.

![](img/e71dc48d3ae3db3394e5857ab2acae75_346_0.png)

Figure 9-11 Device-to-Device Messaging

Router Solicitation and Router Advertisement messages are for messaging between devices and routers. Router discovery is typically used for dynamic address allocation and stateless address autoconfiguration (SLAAC).

![](img/e71dc48d3ae3db3394e5857ab2acae75_346_1.png)

Figure 9-12 Device–Router Messaging

> **Note**
The fifth ICMPv6 ND message is a redirect message that is used for better next hop selection. This is beyond the scope of this book.

IPv6 ND is defined in IETF RFC 4861.
