
* `Unsecured Wi-Fi connections` can be used by hackers to distribute malware. If the user allows file sharing when using an unsecure Wi-Fi connection, the hacker can easily plant malware on the victim’s computer.

* In some cases, a hacker may create a rogue hotspot and name it with a well-known store or location, hope to trick users into signing on with their devices.

How can users remain safe?

Some preventive measures when using a public Wi-Fi connection are:

* Set up a `VPN`, which can provide protection against man-in-the-middle attacks.

* Use a strong password along with two-factor authentication (`2FA`), requiring an additional step to log into an account, like a passcode text to a mobile phone or a physical key inserted into a computer.

* Disable the auto-connect functionality for Wi-Fi.

* Visit the safest websites using Hypertext Transfer Protocol Secure (`HTTPS`).

* Beware of phishing scams when using a public Wi-Fi connection.

[Figure 6.18](#c6.xhtml#f6.18) demonstrates the evolution of the most significant cyberattacks from the early 2000s until the present. From early 2000 to 2004 we’ve seen mainly worms; from 2005 to 2012 we’ve seen the rise of modern malware, and from 2013 to the present we’ve experienced ransomware and APT attacks associated with nation-state criminal organizations. These nation-state actors target government and commercial networks containing sensitive data, such as research for COVID-19 vaccines, and critical infrastructure.

![FIGURE 6.18 The evolution of the most important attacks.](images/fig6.18.jpg)

**FIGURE 6.18** The evolution of the most important attacks.

## [6.4 Prevention Mechanisms](#contents.xhtml#re_h-6-15)

### [6.4.1 If You Connect It, Protect It](#contents.xhtml#re_h-6-16)

A `firewall` is a piece of hardware, sometimes a standalone system or part of a router, or software application, or a combination of both, that screens incoming and outcoming traffic to or from a network, according to a defined set of rules.

Along with firewalls, other systems such as `IDS` and `IPS` are part of the network security environment.

* The firewall is the first line of defense, like a fence between a trusted internal network, called the subnet, and the unsafe Internet. The firewall makes sure only specific types of traffic are allowed into and out of a network.

* The IDS system detects the attack, identifies it using a database of attack types, registers the attack, and sends an alert to an IT administrator if it is malicious.

* The IPS inspects traffic flowing in the network, looking for anything suspicious, and prevents or blocks a connection that is suspect, provides alerts, and cleans up malicious network traffic to keep it from getting to the rest of the network. Like the IDS, the IPS resides between the firewall and the rest of the network.

> The best example of the difference between security gates in IDS and IPS is that an IDS security gate works like a patrol car within the borders of its neighborhood, monitoring activities and looking for abnormal situations. An IPS security gate operates like a security guard at the gate, allowing and denying access based on credentials and a predefined rule set, or policy. No matter how strong the security at the gate is, the patrols continue to operate in a system that provides its own checks.^([^(331)](#fn331))

The separation between a computing device on an internal network and the Internet, or the outside world, is referred to as the `Demilitarized Zone (DMZ)` or `perimeter network`. This area sits between the internal network and external network. The Internet cannot establish connections directly to the internal network, but it can establish connections with the DMZ. If you think of network security as an onion, the DMZ is the peel, or the first layer of the onion.

There are several ways to implement a DMZ in a network. One way is to use the `single firewall model` ([Figure 6.19](#c6.xhtml#f6.19)), which requires three network interfaces (devices) or a three-legged firewall. In this case the DMZ will be positioned inside of this firewall. The first network interface, considered Untrusted, is connected to the external public Internet connection. The second interface, considered trusted, is connected to the internal network or LAN. The third interface is connected directly to the DMZ. Normally, inside the DMZ you will find the email server, File Transfer Protocol (`FTP`) server, DNS server, Web server, domain controller, database servers, and HTTPS traffic.

![FIGURE 6.19 The single firewall model.](images/fig6.19.jpg)

**FIGURE 6.19** The single firewall model.

The `dual firewall model` utilizes two separate firewalls. One faces the Internet, called the `front-end firewall`, and the other faces the trusted internal network, or subnet, and is called the `back-end firewall`. The `front-end firewall` is configured to allow only traffic destined for the DMZ. The `back-end firewall` is responsible for regulating network traffic on the trusted internal network or traffic from the DMZ to the internal network.

Cloud computing has changed the role of the DMZ by allowing secure access between the local or on-premises network and cloud-based networks through the use of a VPN service to connect the networks. Most companies use cloud service providers and deploy SaaS applications. DMZs are an important part of network security restricting remote access and guard against unauthorized access to internal servers. [Figure 6.20](#c6.xhtml#f6.20) demonstrates the dual firewall model.

![FIGURE 6.20 The dual firewall model.](images/fig6.20.jpg)

**FIGURE 6.20** The dual firewall model.

How does the firewall perform its job of monitoring services and blocking malicious or unwanted traffic? What does it block?

A firewall does the following:

* On the device interface, the firewall filters source and destination ports, including OSI model, Layer 2 traffic.

* Regarding packet headers, the firewall filters traffic on the source and destination IP addresses, including OSI model, Layer 3 routed interface IPv4 and IPv6 interfaces. It provides different levels of protection based on parameters within the packet header information, including protocols such as TCP, UDP, and ICMP.

* The firewall rejects or accepts network traffic packet by packet, with or without notification, to the sender.

* The firewall records packet information.

* The firewall enforces security policies such as the setting of alarms, filtering rules and modifying packets, and detects, blocks, and rejects malicious requests when hackers scan public IP addresses for open ports.

On most operating systems the server includes a built-in firewall along with its wireless routers. For example, a firewall is built into Mac OS. It is found under System Preferences, Security & Privacy, Firewall. A firewall is included on Linux and on the Windows OS, where it is called Windows Defender. Additional firewall solutions for personal use are available from security companies such as Bitdefender, Kaspersky, Norton, and McAfee, and from ISPs. On an enterprise-level, network firewalls must be able to secure more complex networks such as cloud environments, data center deployments, and remote sites. Some of the leading companies providing enterprise-level firewalls are Barracuda Networks, Check Point, Cisco systems, Juniper, Palo Alto Networks, and SonicWall. [Figure 6.21](#c6.xhtml#f6.21) displays a typical firewall setup on a network.

![FIGURE 6.21 A typical firewall setup on a network.](images/fig6.21.jpg)

**FIGURE 6.21** A typical firewall setup on a network.

### [6.4.2 Types of Firewalls](#contents.xhtml#re_h-6-17)
