# Methods of DoS Attacks

There are four main methods attackers follow when carrying out a DoS attack. They can also use hybrid DoS attacks that use elements of each method. The following is not intended to be a comprehensive list of every type of DoS attack. Rather, it is an introduction to DoS methods.

The main DoS attack methods we will look at are (1) direct/indirect, (2) intermediary, (3) reflected, and (4) sending malformed packets. Each method has its own advantages and disadvantages. Simpler attacks may be easier to implement, but they are also easier to stop. On the other hand, attacks that are inherently more complex may be extremely difficult to stop without causing additional harm.

+   **Not a DoS Attack**
+   - Faulty coding
+   - Referrals from large sites
+   **Goals of DoS Attacks**
+   - Stop critical services
+   - Slowly degrade services over time
+   **Direct and Indirect DoS Attacks**
+   - Direct DoS attack—flood the victim directly
+   - Indirect DoS attack—spoof the source address and then flood the victim
+   - Backscatter from spoofed addresses
+   - Multiple types of packets can be sent
+   - SYN flood
+   - Attacker sends a TCP SYN segment to a port
+   - The application program sends back a SYN/ACK segment and sets aside resources
+   - The attacker never sends back an ACK, so the victim keeps the resources reserved
+   - The victim soon runs out of resources and crashes or can no longer serve legitimate traffic
+   **Intermediary**
+   - Botmaster controls bots
+   - Updatable DoS attack programs
+   - Handler can update the software to change the type of attack the bot can do
+   - May sell or lease the botnet to other criminals
+   - Handler can update the bot to fix bugs
+   - Peer-to-peer redirect
+   **Reflected**
+   - DRDoS attack
+   - Smurf flood
+   - Spoofed ICMP echo requests
+   - Incorrectly configured router
+   - Broadcasts to internal hosts
+   **Sending Malformed Packets**
+   - Malformed packet will cause the victim to crash
+   - Ping of death
+   - SMS of death