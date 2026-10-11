
# Nodes

Nodes are the objects that are connected to one another by networks and which carry out computations, store data, interface with humans, and interface with the physical world.

The most obvious kinds of nodes are computers, ranging from large, powerful servers down to personal computers. But there are other kinds of nodes that are even more common. For example, most people interact with cyberspace using a phone, which is just a computer of a specialized kind. Increasingly, there are also **Internet of Things (IoT)** devices, nodes that often do not interact directly with humans, but have useful functions: video cameras, light switches, thermostats, motion detectors, and medical devices. Even less obvious are **cyber-physical systems**, such as the robots and machinery that are used in modern production lines, and the devices that control pipelines and electricity grids.

This range of devices, all containing computing capabilities and connected to networks, exist because it's almost always easier to start with a general-purpose computing device and program it to act in a certain way than to build a specialized device to act that way directly. The result is that cyberspace has almost become a monoculture since there are only a handful of computer manufacturers, operating system providers (`Windows`, `Mac`, `Linux`), phone systems (`Android`, `iOS`), and network switch providers (`Ericcson`, `Cisco`, `Huawei`).

This introduces the vulnerabilities associated with any monoculture: an attack on a particular kind of system can be successful against many targets at once. Attackers can rapidly scale their attacks and cause serious havoc. They can also try scattershot attacks on all of the nodes of a particular kind with the expectation of at least some successes.

# Pipes

Pipes are the connectors that join the nodes to one another. They move data which comes in many forms: emails, requests for web pages, contents of the web pages themselves, digitally encoded voice, video, audio, software, many other kinds of data transfer, and control messages that manage the network of pipes itself.

Pipes can be hard-wired to move data between two fixed endpoints. For example, undersea cables connect continents and can carry vast amounts of data; high-capacity networks move data around within a country, and fiber and coaxial cables move data to and from businesses, houses, and apartment buildings.

Other pipes carry data wirelessly. These include the cell network that connects phones with the local cell tower, wifi within a few hundred square meters, Bluetooth and similar systems that connect over short distances of about two meters, and the very short range wireless connections used for RFID tags and Near Field devices over centimeters.

# Management Infrastructure

Management infrastructure manages how nodes and pipes are organized so that data can find its way to where it is intended to go, and so that resources are shared in accordance with agreed rules. Both nodes and pipes come and go from the network as their users move around, or as systems fail or are replaced, so this infrastructure must also deal with a dynamic situation. The size of cyberspace dictates that much of this management must be automated.

# People in Cyberspace

People can also be thought of, in a way, as part of cyberspace for two reasons. First, much of the data moving around cyberspace is doing so because it is heading for a particular individual. So cyberspace must have ways of discovering where and how each individual is connected to the network—people must have addresses or points of presence that make sense looking out from within cyberspace.

Second, individuals act in cyberspace and we would generally prefer them to be accountable for those actions. This is a difficult trade-off: we would sometimes like to be able to act anonymously as we can in the real world, but all countries already have mechanisms to limit anonymity when it makes committing crimes easy, and similar mechanisms need to be migrated to cyberspace. The picture is muddied by the desire of large online businesses to collect lots of data about every individual to build models of them that will improve (supposedly) customized delivery of advertisements. As a result, individuals are wary of being identified when they act in cyberspace because they do not trust governments or multinational businesses not to misuse the information they gain from observing known individuals and their actions.

# 2.3 Nodes

Since cyberspace contains billions of nodes, there must be a way to identify which is which. This issue is more complicated than it seems because the same physical object, say a phone, can appear in multiple places over time, and sometimes at more than one place simultaneously. For example, whenever you move about (sometimes even when you go up in an elevator), your phone connects to different cell towers to maintain its connection to the cell network.

Identifying which device is which relies on each one having a unique identifier. For phones there is a unique number, the **IMEI** (International Mobile Equipment Identity) which is tied to the hardware of the phone itself. Cellular networks can check the `IMEI` when a phone connects to the network and so know with absolute certainty which phone it is.

Other phone identifiers are associated with its **SIM card**. SIM cards are the association between a physical phone and the provider who serves that phone. They can be swapped in and out of most phones, so they don't identify the phone as such but they get closer to being an identifier for the user of the phone, at least for users who want to receive phone calls. The first identifier connected to the SIM card is the **International Mobile Subscriber Identity (IMSI)** which contains details of the country, the provider, and the individual who is associated with it (if it was sold to an explicitly identified individual, which some countries require). The `IMSI` is used, for example, to determine whether a phone has roaming privileges on another company's network.

The second identifier associated with a phone's SIM card is the phone number. With the country and area code each number is unique across the world. This is the primary way that an incoming call is connected with the particular phone being called.

Cell networks must keep track of all of these identifiers for the phones connected to their cell towers so the incoming calls can be sent to the correct place, and correctly billed.

In parallel with the cell-phone system is the much larger Internet which connects computers (of all sizes and complexities) and also phones that are using their wifi connection capability. Each device is identified by a unique address called a **MAC** (Medium Access Control) address, which is six groups of pairs of hexadecimal.

While a MAC address describes what each physical device is, it is convenient, and sometimes necessary, to replace one device by another that does the same job, and to do it seamlessly. So to provide a level of abstraction above the purely physical, Internet-connected devices are all given **IP addresses**. In the original version, called `IPv4`, these are 32-bit addresses written as four groups of numbers between 0 and 255 (each based on 8 bits of the address) such as `64.233.160.1`. However, because of the number of devices connected to the Internet, a new version, `IPv6`, was rolled out in the mid-2000s. It uses 128 bits and addresses are written using 8 groups of hexadecimal numbers.

IP addresses are hierarchical. For example, with `IPv4` the first group of numbers specifies a high-level area of the Internet (usually owned by a single large business or Internet Service Provider), the next group a subregion, the next group an even smaller region, and the final group the addresses of a local set of computers. Thus knowing an IP address provides a natural, hierarchical way to find the particular device that has that address.
