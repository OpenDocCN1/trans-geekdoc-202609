+   C. Sticky method
+   D. LIFO method

14. Your company has a policy to not allow any connection from overseas addresses to its network. Which security mechanism is best to employ to accomplish this goal?

+   A. VLAN management
+   B. Access control lists
+   C. Implicit deny
+   D. Network separation

15. During your investigation of a security breach, you discover the corporate fileserver is connected to a VLAN that is accessible to systems in the development environment. This violates which security principle?

+   A. VLAN management
+   B. Least privilege
+   C. Network separation
+   D. Loop protection

# Answers

+   1. A. Flood guard functionality is designed to protect against ping floods, port floods, and distributed denial-of-service attacks. A Smurf attack is a denial-of-service attack where an attacker sends ICMP packets with the victim’s spoofed source IP address to a network broadcast address. The result is a flood of ICMP response packets targeted at the victim.

+   2. C. When using an “explicit deny” approach to ACL building, allowed traffic must be explicitly allowed by a permit statement. As ACL entries are typically evaluated in a top-to-bottom fashion, any traffic that does not match a “permit” entry will be dropped by a “deny all” statement placed as the last line in the ACL.

+   3. D. Open Shortest Path First (OSPF) is a link-state routing protocol that is commonly used between gateways in a single autonomous system.

+   4. B. In the context of 802.1x, EAP stands for the Extensible Authentication Protocol (EAP).

+   5. A. A management VLAN is configured to allow remote access to the switch through Telnet, SSH, or a web interface built into the switch.

+   6. B. In access control lists, an implicit deny is the “catch-all” rule at the end of the access list entries. All traffic will match the implicit deny rule, so any traffic that is not permitted by a previous line in the ACL will reach the end of the ACL and be denied. In certain firewalls and routers, the implicit deny rule is automatically enforced by the system at the end of every ACL.