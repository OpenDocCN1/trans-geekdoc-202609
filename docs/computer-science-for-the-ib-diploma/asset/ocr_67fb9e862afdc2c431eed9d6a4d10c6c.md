# # Network security

# ## SYLLABUS CONTENT

By the end of this chapter, you should be able to:

+   - A2.4.1 Discuss the effectiveness of firewalls for protecting a network
+   - A2.4.2 Describe common network vulnerabilities (HL)
+   - A2.4.3 Describe common network countermeasures (HL)
+   - A2.4.4 Describe the process of encryption and digital certificates

# ## A2.4.1 Firewalls

Firewalls obviously play a key role in helping protect computer networks, but what exactly do they do?

![](bbox=[0.285, 0.395, 0.89, 0.655])

**Firewall in action**

A firewall inspects the IP packets that pass through it, and filters the incoming and outgoing traffic, based on a set of predefined security rules. In the illustration above, Rule 1 is allowing traffic from PC2 on the internal LAN to access any external IP address that begins with 185.3.??? for destination ports 80 or 443. Rule 2 then denies all other internal requests. Each individual packet is checked against the rules until a rule is encountered that allows or denies passage through the firewall.

Some firewalls are also capable of applying stateful inspection, where the state of active connections is monitored and can be used to determine passage through the firewall, for instance once a connection has been allowed to be established, packets are allowed to continue back and forth through the connection until it closes.