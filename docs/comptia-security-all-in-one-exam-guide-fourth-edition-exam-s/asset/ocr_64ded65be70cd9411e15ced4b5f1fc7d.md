to ACL building, allowed traffic must be explicitly allowed by a permit statement. All of the specific permit commands are followed by a deny all statement in the ruleset. ACL entries are typically evaluated in a top-to-bottom fashion, so any traffic that does not match a “permit” entry will be dropped by a “deny all” statement placed as the last line in the ACL.

# Port Security

Port security is a capability provided by switches that enables you to control which devices and how many of them are allowed to connect via each port on a switch. Port security operates through the use of MAC addresses. Although not perfect—MAC addresses can be spoofed—port security can provide useful network security functionality.

Port security has three variants:

+   - **Static learning** A specific MAC address is assigned to a port. This is useful for fixed, dedicated hardware connections. The disadvantage is that the MAC addresses need to be known and programmed in advance, making this good for defined connections but not good for visiting connections.
+   - **Dynamic learning** Allows the switch to learn MAC addresses when they connect. Dynamic learning is useful when you expect a small, limited number of machines to connect to a port.
+   - **Sticky learning** Also allows multiple devices to a port, but also stores the information in memory that persists through reboots. This prevents the attacker from changing settings through power cycling the switch.

# 802.1x

IEEE 802.1x is an authentication standard that supports communications between a user and an authorization device, such as an edge router. IEEE 802.1x is used by all types of networks, including Ethernet, Token Ring, and wireless. This standard describes methods used to authenticate a user prior to granting access to an authentication server, such as a RADIUS server. 802.1x acts through an intermediate device, such as an edge switch, enabling ports to carry normal traffic if the connection is properly authenticated. This prevents unauthorized clients from accessing the publicly available ports on a switch, keeping unauthorized users out of a LAN. Until a client has successfully authenticated itself to the device, only Extensible Authentication Protocol over LAN (EAPOL) traffic is passed by the switch.

EAPOL is an encapsulated method of passing Extensible Authentication Protocol (EAP) messages over 802 frames. EAP is a general protocol that can support multiple methods of authentication, including one-time passwords, Kerberos, public keys, and security device methods such as smart cards. Once a client successfully authenticates itself to the 802.1x device, the switch opens ports for normal traffic. At this point, the client can communicate with the system’s authentication, authorization, and accounting (AAA) method, such as a RADIUS server, and authenticate itself to the network.