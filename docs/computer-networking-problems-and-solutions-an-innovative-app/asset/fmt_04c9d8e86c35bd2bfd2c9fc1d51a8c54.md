
• The **exploit** takes advantage of the vulnerability using a process or tool, such as manually entering a specific string, running a script or piece of software, etc.

• The **attack** or **threat** is the potential or actual attack performed by the threat actor using the exploit.

• **Vulnerabilities** are potential weak spots in the defense that can be exploited to achieve an objective. For instance, a missing or misconfigured packet filter, someone inside the network with rights to the target system who can be social-engineered to provide access in some way, or a defect in a system’s code allowing a threat actor to attack a system in some way.

• The **attack surface** is the total set of systems, port numbers, applications, etc., the threat actor has access to in some way.

• **Assets** are the network elements and information within the network that the threat actor would either like to access or prevent access to (in the case of a denial of service attack).

• **Risks** are the potential negative results of an attack, such as bad publicity (represented by the microphone), a major business consequence (represented by the breach report), or even a complete failure of the business itself. Risk is often quantified as potential times impact.

## The Problem Space

The security problem space, from a network perspective, can be divided into three broad areas:

• How can users and processes access the data they need to do their jobs?
• How can the information carried over the network and stored on devices connected to the network remain confidential?
• How can the network remain accessible? Many attackers would like to disrupt a business or organization by removing the network as a usable resource; this is called a denial of service (DoS) attack.

The following section will consider a wide scope of possible solutions to each of these problems. After this, some examples of solutions in the security space will be considered, and then a useful model for considering network security, the Observe, Orient, Decide, Act (OODA) loop, will be discussed.

### The Solution Space

Many books, articles, and research papers have been written addressing different elements of security since the first network break-in, which probably happened the day after the first network was operational. The “Further Reading” section will be helpful if you are interested in learning more about security than what is contained in this and later sections in this chapter.

This section will begin by looking at the concept of defense in depth and then consider three broad security solution spaces: access control, data protection, and service availability assurance.

#### Defense in Depth

The first, and most important, solution is more conceptual than tool or method oriented. Defense in depth is the concept of having multiple, overlapping layers of defenses interacting in a way that poses multiple challenges to an attacker. [Figure 21-3](#ch21.xhtml#ch21fig03) illustrates one possible set of lines of defense.

![Image](graphics/21fig03.jpg)

**Figure 21-3** *Defense in depth*

In [Figure 21-3](#ch21.xhtml#ch21fig03), there are a number of lines of defense, including

• Packet filters and access controls at the routed edge to the network; these are “basic” controls that just check to see if a user is authorized to access the network in general, block some basic (obvious) packet flows, and even limit the rate at which hosts outside the network can transfer data.
• Route validation at the routed edge to the network; this will help prevent access from hijacked address space.
• General telemetry throughout the network, which will indicate top talkers, provide information on the most common source/destination pairs, note unusual spikes in utilization, etc.
• Stateful packet filters at the middlebox C, which will only allow traffic into the network on some ports if there is an existing connection.
• Exfiltration monitoring deployed in several locations; this will raise an alert when specific access patterns occur, such as large amounts of data being transferred toward a destination outside the network from a database containing sensitive user information.
• Access control on individual services and/or servers, such as G, which ensures the user at D is authorized to access individual resources.

Although none of these systems will stop an intruder from breaching your network or data, used together they can provide a fairly effective defense system against many different forms of attack. First, the time a threat actor spends moving through one layer gives the network operator an opportunity to discover and counter the attack with more specific controls. Second, the layering of systems and filters forms a kind of “layer of grids” through which traffic must pass to reach important resources. An attack not blocked by the first grid layer may be blocked by the second, etc.

Understanding the in-depth defensive posture of the complete set of systems in a network and using every available resource as a potential defensive system are important skills in the network design space.

#### Access Control

Access control tries to ensure

• Users (or processes) are who they claim to be—to verify identity. This is often called authentication.
• Users (or processes) are able to access the data they are attempting to access, or rather whether or not they are authorized to use a particular service or access a particular piece of data.
• Information about user actions are recorded so they can be used to trace back to failures and breaches. This is generally called accounting.

Access control systems are often called AAA systems, because of the three A’s: authentication, authorization, and accounting. These systems are often specialized applications, interacting with devices through a protocol such as Remote Authentication Dial-In User Service (`RADIUS`) to ensure users are properly logged in and applications have enough information to ensure that only valid and authorized users are accessing information and services.

Access control can be implemented in many different places in a system; for instance:

• Before the user connects to the network, or rather before the user can log on to a device that is able to obtain an Internet Protocol (`IP`) address, connect to an upstream switch, connect to a wireless network, etc.
• After the user connects to the network but before the user can access any service.
• After the user connects to the network and before the user accesses each individual service.

These three different options can be combined; for instance, a user may be asked to provide a username and password before connecting to the network, and again before accessing any service on the network, and then again before accessing particular, more highly restricted, systems or information.

#### Data Protection

Consider the protection around a safe holding classified documents. Is it possible the safe might be breached in some way? What if someone calls in a bomb threat to the building where the safe is housed? Will the occupants of the building gather up any necessary equipment and information, including the contents of the safe, and leave the building? Or what if someone who appears to be authorized calls and asks for the data? The safe being breached is similar to an access control failure, and the bomb threat or request for information that drives the data out into the street is similar to a request pulling the information across the network.

Ultimately, there must be a line of defense to protect data in these sorts of situations; systems and applications will be breached, and data will be requested over the network. Encryption is generally the last line of defense for these situations.

**The Man in the Middle and the Control Plane**
