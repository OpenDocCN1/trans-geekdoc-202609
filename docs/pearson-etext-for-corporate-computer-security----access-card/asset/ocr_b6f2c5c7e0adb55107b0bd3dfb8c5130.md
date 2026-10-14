# Figure A-20 Internet Control Message Protocol (ICMP)

![](bbox=[0.11, 0.11, 0.68, 0.33])

If an attacker cannot ping destination hosts because a firewall stops echo replies, the attacker often sends IP packets that are malformed and so will be rejected. The ICMP error message is delivered in an IP packet, and the source IP address in this packet will reveal the IP address of the sending router. By analyzing error messages, the attacker can learn how routers are organized in a network. This information can be very useful to attackers. Border firewalls often drop all outgoing error messages. In fact, they usually drop all outgoing ICMP messages except for echo messages.

# Test Your Understanding

+   29. a. What is the TCP/IP internet layer supervisory protocol?
+      b. Describe ping.
+      c. Describe ICMP error messages.
+      d. What information does ping give an attacker?
+      e. What information does tracert give an attacker?
+      f. What information does an ICMP error message give an attacker?

# The Domain Name System

To send a packet to another host, a source host must place the destination host’s IP address in the destination address field of the packets. Often, however, the user merely types the host name of the destination host, for instance, cnn.com.

Unfortunately, host names are only nicknames. If the user types a host name, the computer must learn the corresponding IP address. As Figure A-21 shows, a resolver program on the host wishing to send a packet to a target host sends a Domain Name System (DNS) request message to the DNS server. This message contains the host name of the target host. The DNS response message sends back the target host’s IP address. To give an analogy, if you know someone’s name, you must look up their telephone number in a telephone directory. In DNS, the human name corresponds to the host name, the telephone number corresponds to the IP address, and the DNS server corresponds to the telephone directory.