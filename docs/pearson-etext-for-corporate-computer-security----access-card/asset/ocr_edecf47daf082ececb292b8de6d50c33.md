# Figure 4-11 The Difficulty of Stopping DoS Attacks

![](bbox=[0.11, 0.1, 0.72, 0.41])

Even more troubling, once DoS traffic clogs the site’s access line going to the Internet, there is nothing a border firewall can do to alleviate the situation (Figure 4-11). In general, DoS attacks are community problems that can only be stopped with the help of ISPs and organizations whose computers are taken over as bots and used to attack other firms.

# Test Your Understanding

+   5. a. What is black holing?
+      b. Is black holing an effective defense against DoS attacks? Why?
+      c. How can the effects of SYN floods be mitigated?
+      d. What is a false opening?
+      e. Why is rate limiting a good way to reduce the damage of some DoS attacks?
+      f. Why is it limited in effectiveness?
+      g. Why is DoS protection a community problem, not just a problem for individual victim firms to solve?

# 4.3 ARP Poisoning

# 4.3 Explain how ARP poisoning works.

Address Resolution Protocol (ARP) is used to resolve 32-bit IP addresses (e.g., 55.91.56.21) into 48-bit local MAC addresses (e.g., 01-1C-23-0E-1D-41). Hosts on the same network must know each other’s MAC addresses before they can send and receive packets using IP addresses. Hosts build ARP tables, similar to the one shown in Figure 4-12, by sending ARP requests and replies to each other.