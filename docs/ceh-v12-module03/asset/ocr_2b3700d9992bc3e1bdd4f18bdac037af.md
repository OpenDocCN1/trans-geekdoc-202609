# IP Spoofing Detection Techniques: TCP Flow Control Method

+   - Attackers sending spoofed TCP packets will not receive the **target's SYN-ACK packets**
+   - Therefore, attackers cannot respond to a change in the congestion window size
+   - When received traffic continues after a window size is exhausted, the **packets are most likely spoofed**

![](bbox=[0.15, 0.245, 0.85, 0.395])

# IP Spoofing Detection Techniques

# Direct TTL Probes

In this technique, you initially send a packet (ping request) to the legitimate host and wait for a reply. Check whether the TTL value in the reply matches with that of the packet you are checking. Both will have the same TTL if they are using the same protocol. Although the initial TTL values vary according to the protocol used, a few initial TTL values are commonly used. For TCP/UDP, the values are 64 and 128; for ICMP, they are 128 and 255.

![](bbox=[0.2, 0.58, 0.8, 0.75])

Figure 3.106: IP Spoofing detection technique: Direct TTL Probes

If the reply is from a different protocol, then you should check the actual hop count to detect the spoofed packets. Deduct the TTL value in the reply from the initial TTL value to determine the hop count. The packet is a spoofed packet if the reply TTL does not match the TTL of the packet. It will be very easy to launch an attack if the attacker knows the hop count between the source and the host. In this case, the test result is a false negative.