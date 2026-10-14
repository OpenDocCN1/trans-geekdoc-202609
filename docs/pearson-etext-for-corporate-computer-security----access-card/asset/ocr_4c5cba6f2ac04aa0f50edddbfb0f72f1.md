**RADIUS AND EAP** The RADIUS protocol provides *authentication*, but it goes beyond that. It also provides *authorization*, meaning that it can specify limits on such matters as what servers the authenticated supplicant may connect to, what directories the supplicant may access on those servers, and what users can do in these directories (read files, modify files, etc.). RADIUS also provides optional auditing of connections so that a company can check later what workgroup switches a particular computer connected to and how long it was connected.

Although RADIUS has its own methods for authentication communication, Figure 4-20 shows that EAP over RADIUS specifies how to use EAP instead for native RADIUS authentication when RADIUS governs communication between an authenticator and the central authentication server. In other words, EAP is only used in the first A (Authentication) in AAA (Authentication, Authorization, and Auditing, discussed more thoroughly in Chapter 5).

# Test Your Understanding

+   13.  
+      a. What standard do most central authentication servers follow?  
+      b. How are EAP and RADIUS related in terms of functionality?  
+      c. What authentication method does RADIUS use?

# 4.6 Wireless Security

**4.6** **Describe wireless (WLAN) security standards and potential attacks.**

As noted at the start of this chapter, Ethernet LANs aren’t the only type of networks that require security. In fact, wireless LANs (WLAN) have more security issues to consider than wired LANs. Wireless networks, for example, can be attacked by drive-by hackers who don’t even have to enter the building to gain access to the LAN. They can sit across the street or in an adjacent building and easily access an internal network without raising suspicions.

Wireless networks have become nearly ubiquitous because they are quicker, easier, and less expensive to set up than traditional wired networks. They also offer greater mobility, productivity, and functionality. The benefits of wireless networks have encouraged widespread adoption within corporations.

Unfortunately, the ability to secure wireless networks has not kept pace with its rapid growth. Network administrators have seen new types of attacks against their wireless networks. They also had to implement new wireless authentication methods, security standards, and security policies.

# Wireless Attacks

As shown in Figure 4-21, users connect via radio waves to a wireless **access point (AP)** using the **802.11 standards**, developed by the **IEEE 802.11 Working Group** (1). The AP then connects to the local Ethernet (802.3) network with a wired connection (2). The AP acts as a relay point between the wireless and wired networks.

Wireless attacks focus on the access point. Wireless 802.11 networks typically have a range of 30 to 200 meters extending in all directions from the AP. This allows the attacker to attack the AP, and the internal network, while staying outside the physical boundaries of the corporate site.

The three types of wireless network attacks we will look at are (1) unauthorized network access, (2) a man-in-the-middle attack using an evil twin, and (3) wireless denial-of-service attacks.