
We can even expand the notion of protected subnets to two or more subnets, as shown in [Figure 6-51](#ch06a.html#ch06fig51). The three subnets could be for separate departments or user groups, or they could be allocated geographically. Of course, the more subnets gateway A supports, the more risk if device A fails.

![Image](graphics/06fig51.jpg)

**FIGURE 6-51** Multiple Protected Subnets

***

**Protected subnetworks can separate departments, projects, clients, areas—any subgroup requiring controlled access to data or communication.**

***

Reconfiguring the architecture of a network limits or complicates movement, but it does not address the central security goal of controlled access. To accomplish that goal we depend on a device called a firewall, which we describe next.

### 6.7 Firewalls

Firewalls in buildings, as their name implies, are walls intended to inhibit the spread of fire from one part of a building to another, for example, between one apartment and the next. Firewalls are built of materials that withstand fires of a particular intensity or duration; they deter fire spread but are not guaranteed or intended to stop a particularly intense fire.

As computer security devices, network firewalls are similar, protecting one subnet from harm from another subnet. The primary use of a firewall is to protect an internal subnetwork from the many threats we have already described in the wild Internet. Firewalls can also be used to separate segments of an internal network, for example, to preserve high confidentiality of a sensitive research network within a larger organization.

#### What Is a Firewall?

Firewalls are one of the most important security devices for networks. Firewalls were officially invented in the early 1990s, but the concept really reflects the reference monitor (introduced in [Chapter 2](#ch02.html#ch02)) from two decades earlier. The first reference to a firewall by that name may be by Marcus Ranum [[RAN92](#bib01.html#bib_511)]; other early references to firewalls are the Trusted Information Systems firewall toolkit [[RAN94](#bib01.html#bib_512)] and the 1994 book by Bill Cheswick and Steve Bellovin [updated as CHE02].

A **firewall** is a device that filters all traffic between a protected or “inside” network and a less trustworthy or “outside” network. Usually a firewall runs on a dedicated device; because it is a single point through which traffic is channeled, performance is important, which means that only firewall functions should run on the firewall machine.

In practice, a firewall is a computer with memory, storage devices, interface cards for network access, and other devices. It runs an operating system and executes application programs. Often the hardware, operating system, and applications are sold as a package, so the firewall application (a program) is sometimes also called a firewall.

***

**A firewall is a computer traffic cop that permits or blocks data flow between two parts of a network architecture. It is the only link between parts.**

***

A firewall system typically does not have compilers, linkers, loaders, general text editors, debuggers, programming libraries, or other tools an attacker might use to extend an attack from the firewall computer. Because a firewall is executable code, an attacker could compromise that code and execute from the firewall’s device. For example, Cisco runs a proprietary operating system `IOS` on its switches, routers, and firewalls. In the year from July 2013 to June 2014 Cisco released 27 patches to `IOS` to deal with a range of problems from vulnerabilities that could lead to denial of service, to address translation and routing problems. For a long time proprietary software on network devices was scarcely a target for attackers, but even these devices are now catching hackers’ attention.

The purpose of a firewall is to keep “bad” things outside a protected environment. To accomplish that, firewalls implement a security policy that is specifically designed to address what bad things might happen. For example, the policy might be to prevent any access from outside (while still allowing traffic to pass from the inside to the outside). Alternatively, the policy might permit accesses only from certain places, from certain users, or for certain activities. Part of the challenge of protecting a network with a firewall is determining which security policy meets the needs of the installation.

***

**Firewalls enforce predetermined rules governing what traffic can flow.**

***

People in the firewall community (users, developers, and security experts) disagree about how a firewall should work. In particular, the community is divided about a firewall’s default behavior. We can describe the two schools of thought as “that which is not expressly forbidden is permitted” (**default permit**) and “that which is not expressly permitted is forbidden” (**default deny**). Users, always interested in new features, prefer the former. Security experts, relying on several decades of experience, strongly counsel the latter. An administrator implementing or configuring a firewall must choose one of the two approaches, although the administrator can often broaden the policy by setting the firewall’s parameters.

#### Design of Firewalls

As we have described them, firewalls are simple devices that rigorously and effectively control the flow of data to and from a network. Two qualities lead to that effectiveness: a well-understood traffic flow policy and a trustworthy design and implementation.

##### Policy

A firewall implements a **security policy**, that is, a set of rules that determine what traffic can or cannot pass through the firewall. As with many problems in computer security, we would ideally like a simple policy, such as “good” traffic can pass but “bad” traffic is blocked. Unfortunately, defining “good” and “bad” is neither simple nor algorithmic. Firewalls come with example policies, but each network administrator needs to determine what traffic to allow into a particular network.

An example of a simple firewall configuration is shown in [Table 6-5](#ch06a.html#ch06tab05). The table is processed from the top down, and the first matching rule determines the firewall’s action. The `*` character matches any value in that field. This policy says any inbound traffic to port 25 (mail transfer) or port 69 (so-called trivial file transfer) is allowed to or from any host on the 192.168.1 subnetwork. By rule 3 any inside host is allowed outbound traffic anywhere on port 80 (web page fetches). Furthermore, by rule 4 outside traffic to the internal host at destination address 192.168.1.18 (presumably a web server) is allowed. All other traffic to the 192.168.1 network is denied.

![Image](graphics/06tab05.jpg)

**TABLE 6-5** Example Firewall Configuration

##### Trust

A firewall is an example of the reference monitor, a fundamental computer security concept. Remember from [Chapters 2](#ch02.html#ch02) and [5](#ch05.html#ch05) that a reference monitor has three characteristics:

• always invoked

• tamperproof

• small and simple enough for rigorous analysis

A firewall is a special form of reference monitor. By carefully positioning a firewall in a network’s architecture, we can ensure that all network accesses that we want to control must pass through the firewall. A firewall is positioned as the single physical connection between a protected (internal) network and an uncontrolled (external) one. This placement ensures the “always invoked” condition.
