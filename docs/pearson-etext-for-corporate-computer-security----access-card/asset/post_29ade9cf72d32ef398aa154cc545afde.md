
## Methods of DoS Attacks

There are four main methods attackers follow when carrying out a DoS attack. They can also use hybrid DoS attacks that use elements of each method. The following is not intended to be a comprehensive list of every type of DoS attack. Rather, it is an introduction to DoS methods.

The main DoS attack methods we will look at are (1) direct/indirect, (2) intermediary, (3) reflected, and (4) sending malformed packets. Each method has its own advantages and disadvantages. Simpler attacks may be easier to implement, but they are also easier to stop. On the other hand, attacks that are inherently more complex may be extremely difficult to stop without causing additional harm.

### Not a DoS Attack
- Faulty coding
- Referrals from large sites

### Goals of DoS Attacks
- Stop critical services
- Slowly degrade services over time

### Direct and Indirect DoS Attacks
- Direct DoS attack—flood the victim directly
- Indirect DoS attack—spoof the source address and then flood the victim
- Backscatter from spoofed addresses
- Multiple types of packets can be sent
- SYN flood
- Attacker sends a TCP SYN segment to a port
- The application program sends back a SYN/ACK segment and sets aside resources
- The attacker never sends back an ACK, so the victim keeps the resources reserved
- The victim soon runs out of resources and crashes or can no longer serve legitimate traffic

### Intermediary
- Botmaster controls bots
- Updatable DoS attack programs
- Handler can update the software to change the type of attack the bot can do
- May sell or lease the botnet to other criminals
- Handler can update the bot to fix bugs
- Peer-to-peer redirect

### Reflected
- DRDoS attack
- Smurf flood
- Spoofed ICMP echo requests
- Incorrectly configured router
- Broadcasts to internal hosts

### Sending Malformed Packets
- Malformed packet will cause the victim to crash
- Ping of death
- SMS of death

## Figure 4-3 SYN Flood DoS Attack

![](img/073342643701cc54eb7875c41ab92ef2_194_0.png)

### DIRECT AND INDIRECT ATTACKS
The simplest form of a DoS attack is a direct attack, similar to the one shown in Figure 4-3. A **direct attack** occurs when an attacker tries to flood a victim with a stream of packets directly from the attacker’s computer. An **indirect attack** tries to flood the victim computer in the same way, but the attacker’s IP address is *spoofed* (i.e., faked) and the attack appears to come from another computer (Step 1).

### Flooding
Direct or indirect attacks can only succeed if the attacker can flood the victim with more requests than the victim can handle (Step 2). The attacker must have more bandwidth, memory (RAM), and/or CPU power than the victim (Step 3). Given the size of most corporate server farms, it’s unlikely that a single user will be able to generate enough traffic to successfully degrade existing services. Corporate servers can handle more requests than the single attacker can generate.

### Spoofing
Direct attacks are rare. Attackers do not like to directly attack victims because their source IP address is shown on all incoming packets. Rather, attackers prefer to use spoofed IP addresses that hide their IP address.

The downside to spoofing an IP address is that the attacker cannot get direct feedback about the attack. They must rely on indirect means of monitoring the attack, such as sending requests to the victim from another computer to test for availability.

### Backscatter
A side effect of an attacker spoofing an IP address is backscatter. **Backscatter** occurs when a victim sends *responses* to the spoofed IP address used by the attacker, and it inadvertently floods an unintended victim (Step 4). A variation of the backscatter effect is used to specifically target victims in a reflected attack (discussed later).

### Types of Packets Sent
Sometimes DoS attacks are named after the *type* of packet sent during the attack, rather than the attack *method*. Some of the DoS attacks explained in this section can use multiple types of packets (e.g., DDoS). Other attack methods, like a Smurf flood, use a single type of packet. Below are just a few of the types of packets that could be sent in a DoS attack (Figure 4-4).

- *SYN Flood* A victim is flooded with SYN packets in an attempt to make many half-open TCP (Transmission Control Protocol) connections. Memory is allocated for each false connection, causing the victim to run out of memory and crash.

|  | Name | Description |
|---|---|---|
| **TCP** | Transmission Control Protocol | Guarantees delivery of packets over the Internet |
| **SYN** | Synchronize | First part of a three-way TCP handshake to make a network connection |
| **SYN-ACK** | Synchronize-Acknowledge | Second part of a three-way TCP handshake sent in response to a SYN |
| **ICMP** | Internet Control Message Protocol | Supervisory protocol used to send error messages between computers |
| **HTTP** | Hypertext Transfer Protocol | Protocol for sending data over the web |

## Figure 4-4 Common Types of Packets Used in DoS Attacks

- *Ping Flood* A victim is flooded with ICMP (Internet Control Message Protocol) packets (also known as echo requests) that appear to be normal supervisory traffic. Bandwidth and CPU cycles are consumed to the point where the victim crashes.
- *HTTP Flood* A victim, typically a webserver, is flooded with application layer web requests. The webserver crashes due to insufficient memory and CPU power.

### SYN Flood Example
A **SYN flood**, or half-open TCP attack, happens when the attacker sends a large number of TCP SYN segments to the victim server (Figure 4-3) (Step 1). Each SYN begins a TCP session opening process on the server (Step 2). The server sets aside RAM and other resources for the connection. The server then sends back a SYN/ACK segment.

The attacker never completes the connection opening by sending a final ACK. As the attacker sends more SYN segments, the victim host keeps setting aside resources until it crashes or refuses to provide any more connections, even to legitimate users (Step 3). Either way, the attacker wins.

### INTERMEDIARY
The second primary DoS method used by attackers is to use intermediaries to attack the victim. **Intermediaries**, typically referred to as **bots**, are actually compromised hosts running malware controlled by the attacker. The DoS attack begins when the **botmaster**, the attacker who controls the bots, sends a signal for the bots to attack the victim.

An attacker controlling bots in a coordinated attack against a victim, shown in Figure 4-5, is known as a **distributed denial-of-service (DDoS)** attack. DDoS attacks are the most common form of DoS attack for several reasons. First, the attacker’s *identity* can be hidden behind layers of bots (Step 1) which directly attack the victim (Step 2). Second, the ability to control thousands of bots can give the attacker the *resources* needed to overwhelm the victim (Step 3).

### Bots
As Figure 4-5 shows, the botmaster (attacker) is not limited to sending attack commands to installed bots. The botmaster can also send software *updates* to the bots. The simplest updates are sent to fix bugs in the program code. In the past, malware releasers often discovered after the release that the program had unforeseen bugs that prevented it from working as designed. These flaws made it possible for antimalware firms to destroy many of these programs. However, the ability to download updates allows malware writers to fix errors.

Figure 4-5 shows that the botmaster can send updates that give *new functionality* to bots. For instance, many bot armies are originally programmed to send spam. Later, when antispam efforts lock out the IP addresses of these bots, the attacker can send updates to make the bots capable of implementing DoS attacks. The attacker can then use them to make attacks or lease the **botnet** to other criminals for DoS attacks. As of
