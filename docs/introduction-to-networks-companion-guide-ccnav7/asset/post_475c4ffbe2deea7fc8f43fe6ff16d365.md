
![](img/e71dc48d3ae3db3394e5857ab2acae75_448_0.png)

## Figure 12-10 IPv6 Link-Local Communications

Figure 12-11 shows some of the uses for IPv6 LLAs:

![](img/e71dc48d3ae3db3394e5857ab2acae75_448_1.png)

## Figure 12-11 Example of Using IPv6 LLAs

- 1. Routers use the LLAs of neighbor routers to send routing updates.
- 2. Hosts use the LLA of a local router as the default gateway.

Note
Typically, it is the LLA of the router, and not the GUA, that is used as the default gateway for other devices on the link.

There are two ways that a device can obtain an LLA:

- **Statically:** This means the device is manually configured.
- **Dynamically:** This means the device creates its own interface ID by using randomly generated values or using the Extended Unique Identifier (EUI) method, which uses the client MAC address along with additional bits.

## Interactive Graphic

## Check Your Understanding—IPv6 Address Types (12.3.8)

Refer to the online course to complete this activity.

## GUA and LLA Static Configuration (12.4)

This section discusses the static configuration of IPv6 global unicast (GUA) and link-local addresses.

### Static GUA Configuration on a Router (12.4.1)

IPv6 GUAs are the same as public IPv4 addresses. They are globally unique and routable on the IPv6 internet. An IPv6 LLA makes it possible for two IPv6-enabled devices to communicate with each other on the same link (subnet). It is easy to statically configure IPv6 GUAs and LLAs on routers to aid in creating an IPv6 network. This section teaches you how to do just that.

Most IPv6 configuration and verification commands in Cisco IOS are similar to their IPv4 counterparts. In many cases, the only difference is the use of ipv6 in place of ip within the commands.

For example, the Cisco IOS command to configure an IPv4 address on an interface is ip address ip-address subnet-mask. In contrast, the command to configure an IPv6 GUA on an interface is ipv6 address ipv6-address/prefix-length. Notice that there is no space between ipv6-address and prefix-length.

Figure 12-12 shows the topology used in the configuration example in this section. The topology includes these IPv6 subnets:

- 2001:db8:acad:1::/64
- 2001:db8:acad:2::/64
- 2001:db8:acad:3::/64

![](img/e71dc48d3ae3db3394e5857ab2acae75_449_0.png)

## Figure 12-12 IPv6 Addressing Topology

Example 12-2 shows the commands required to configure the IPv6 GUA on the GigabitEthernet 0/0/0, GigabitEthernet 0/0/1, and Serial 0/1/0 interfaces of R1.

## Example 12-2 IPv6 GUA Configuration on Router R1

```
R1(config)# interface gigabitethernet 0/0/0
R1(config-if)# ipv6 address 2001:db8:acad:1::1/64
R1(config-if)# no shutdown
R1(config-if)# exit
R1(config)# interface gigabitethernet 0/0/1
R1(config-if)# ipv6 address 2001:db8:acad:2::1/64
R1(config-if)# no shutdown
R1(config-if)# exit
R1(config)# interface serial 0/1/0
R1(config-if)# ipv6 address 2001:db8:acad:3::1/64
R1(config-if)# no shutdown
```

### Static GUA Configuration on a Windows Host (12.4.2)

Manually configuring the IPv6 address on a host is similar to configuring an IPv4 address.

As shown in Figure 12-13, the default gateway address configured for PC1 is 2001:db8:acad:1::1. This is the GUA of the R1 GigabitEthernet interface on the same network. Alternatively, the default gateway address can be configured to match the LLA of the GigabitEthernet interface. Using the LLA of the router as the default gateway address is considered best practice, but either configuration will work.

Just as with IPv4, with IPv6, statically configuring addresses on clients does not scale to larger environments. For this reason, most network administrators enable dynamic assignment of IPv6 addresses.

There are two ways in which a device can obtain an IPv6 GUA automatically:

- Stateless address autoconfiguration (SLAAC)
- Stateful DHCPv6

SLAAC and DHCPv6 are covered in the next section.

![](img/e71dc48d3ae3db3394e5857ab2acae75_451_0.png)

## Figure 12-13 Manually Configuring IPv6 Addressing on a Windows Host

Note
When DHCPv6 or SLAAC is used, the LLA of the router is automatically specified as the default gateway address.

### Static Configuration of a Link-Local Unicast Address (12.4.3)

By configuring the LLA manually, you can create an address that is recognizable and easier to remember. Typically, it is only necessary to create recognizable LLAs on routers. Recognizability is beneficial because router LLAs are used as default gateway addresses and in routing advertisement messages.

LLAs can be configured manually using the ipv6 address ipv6-link-local-address link-local command. When an address begins with a hextet in the range fe80 to febf, the link-local parameter must follow the address.

Figure 12-14 shows an example of a topology with an LLA on each interface.

![](img/e71dc48d3ae3db3394e5857ab2acae75_452_0.png)

## Figure 12-14 IPv6 Addressing Topology with LLAs

Example 12-3 shows the configuration of an LLA on router R1.

## Example 12-3 R1 Static LLA Configuration

```
R1(config)# interface gigabitethernet 0/0/0
R1(config-if)# ipv6 address fe80::1:1 link-local
R1(config-if)# exit
R1(config)# interface gigabitethernet 0/0/1
R1(config-if)# ipv6 address fe80::1:2 link-local
R1(config-if)# exit
R1(config)# interface serial 0/1/0
R1(config-if)# ipv6 address fe80::1:3 link-local
R1(config-if)# exit
```

LLAs may be statically configured to be more easily recognizable as belonging to router R1. In Example 12-3, each of the interfaces of router R1 has been configured with an LLA that begins with fe80::1:n and a unique rightmost digit n. The 1 represents router R1.

If the topology included router R2 and you wanted to follow the same naming convention as for router R1, you would configure R2's three interfaces with the LLAs fe80::2:1, fe80::2:2, and fe80::2:3.

Note
Exactly the same LLA could be configured on each link, as long as it is unique on that link. This is because an LLA only has to be unique on its link. However, common practice is to create a different LLA on each interface of the router to make it easy to identify the router and the specific interface.

### Syntax Checker—GUA and LLA Static Configuration (12.4.4)

Refer to the online course to complete this activity.

## Interactive Graphic

## Dynamic Addressing for IPv6 GUAs (12.5)

This section discusses the different ways a device can automatically create or receive an IPv6 GUA.

### RS and RA Messages (12.5.1)

If you do not want to statically configure IPv6 GUAs, don’t worry. Most devices obtain their IPv6 GUAs dynamically. This section explains how this process works when using Router Advertisement (RA) messages and Router Solicitation (RS) messages. This section gets rather technical, but when you understand the difference between the three methods that a router advertisement can use, as well as how the EUI-64 process for creating an interface ID differs from a randomly generated process, you will have made a huge leap in your IPv6 expertise!

For the GUA, a device obtains the address dynamically through Internet Control Message Protocol version 6 (ICMPv6) messages. IPv6 routers send out ICMPv6 RA messages every 200 seconds to all IPv6-enabled devices on the network. An RA message is also sent in response to a host sending an ICMPv6 RS message, which is a request for an RA message. As shown in Figure 12-15, these messages work as follows:

![](img/e71dc48d3ae3db3394e5857ab2acae75_453_0.png)

## Figure 12-15 ICMPv6 RS and RA Messages

- 1. RS messages are sent to all IPv6 routers by hosts requesting addressing information.
- 2. RA messages are sent to all IPv6 nodes. If Method 1 (SLAAC only) is used—as described in the next section—the RA includes network prefix, prefix length, and default gateway information.

RA messages are on IPv6 router Ethernet interfaces. A router must be enabled for IPv6 routing, which is not enabled by default. To enable a router as an IPv6 router, the ipv6 unicast-routing global configuration command must be used.

The ICMPv6 RA message is a suggestion to a device on how to obtain an IPv6 GUA. The ultimate decision is up to the device operating system. The ICMPv6 RA message includes the following:

- **Network prefix and prefix length:** This tells the device which network it belongs to.
- **Default gateway address:** This is an IPv6 LLA, the source IPv6 address of the RA message.
- **DNS addresses and domain name:** These are the addresses of DNS servers and a domain name.

There are three methods for RA messages:

- **Method 1: SLAAC:** “I have everything you need, including the prefix, prefix length, and default gateway address.”
- **Method 2: SLAAC with a stateless DHCPv6 server:** “Here is my information, but you need to get other information, such as DNS addresses, from a stateless DHCPv6 server.”
- **Method 3: Stateful DHCPv6 (no SLAAC):** “I can give you your default gateway address. You need to ask a stateful DHCPv6 server for all your other information.”

### Method 1: SLAAC (12.5.2)

With stateless address autoconfiguration (SLAAC), a device creates its own GUA without the services of DHCPv6. Using SLAAC, devices rely on the ICMPv6 RA messages of the local router to obtain the necessary information.

By default, the RA message suggests that the receiving device use the information in the RA message to create its own IPv6 GUA and all other necessary information. The services of a DHCPv6 server are not required.

SLAAC is stateless, which means there is no central server (for example, a stateful DHCPv6 server) allocating GUAs and keeping a list of devices and their addresses. With SLAAC, the client device uses the information in the RA message to create its own GUA. As shown in Figure 12-16, the two parts of the address are created:

- **Prefix:** The prefix is advertised in the RA message.
- **Interface ID:** The interface ID uses the EUI-64 process or generates a random 64-bit number, depending on the device operating system.
