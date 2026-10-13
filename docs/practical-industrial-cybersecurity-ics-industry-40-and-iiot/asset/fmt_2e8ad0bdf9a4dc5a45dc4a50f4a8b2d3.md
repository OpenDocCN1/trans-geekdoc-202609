
Because it is possible to flood a network with ping requests, ICMP traffic is often blocked. Most firewall devices can be used to block this traffic completely. While it is typically good practice to allow ICMP traffic on public networks, for a variety of reasons it is critical that the firewall block ICMP traffic for the local network. As a matter of fact, for most networks it may be more desirable to set the firewall to not reply to these requests itself.

A number of tools are available to carry out ping flood attacks. One of these is the `Low Orbit Ion Cannon (LOIC)`, GUI-based tool used to launch very effective ping floods at specified targets. This tool is usually blocked at the host by their antivirus utilities and requires exemptions be put in place to install it.

### Smurf Attacks

A **Smurf attack** is a DDoS attack that floods a network with ICMP packets. This attack builds on the ping flood attack by adding a reflective property. This reflective property is created by using more participants, known as **Smurf amplifiers**, in the attack.

An attacker forges a ping request packet by taking the sender's address (which was originally the attacker's address) and establishing it as the victim's address, as shown in [Figure 5.23](#c05.xhtml#c05-fig-0023). Then, the attacker changes the destination address to a broadcast address of the network.

![FIGURE 5.23 Smurf amplification](images/c05f023.png)

[**FIGURE 5.23**](#c05.xhtml#R_c05-fig-0023) Smurf amplification

When the attacker sends the ping request, Smurf amplifiers that are on the network and able to respond to the ping request will reply using the victim's IP address as the destination address. Because many devices are responding to the victim, the victim is flooded with traffic and becomes virtually inoperable.

ICMP tunneling can also be used to deliver malicious packets. The best defense here is to configure network devices not to respond to ICMP echo requests. Another option is to simply block all ICMP traffic, as well as inbound broadcast traffic.

### UDP Flood Attacks

A **UDP flood attack** is a DoS attack that is similar to a ping flood attack that uses **User Datagram Protocol (UDP) packets**. Because UDP is connectionless and lacks an error-checking ability such as TCP, it lacks the three-way handshake process of TCP.

For this attack, an attacker will send massive amounts of UDP packets to a victim on random ports. Since these packets are sent to specific ports, the victim must check to see if an application is really listening on those ports.

When the victim sees that nothing is listening, it will reply with an ICMP Destination Unreachable packet. In this case, the victim will struggle to send back all the ICMP packets, and anything else trying to connect to the victim will be denied access. Also, the attacker is likely to spoof the IP address being used to send the UDP packets to avoid detection.

A **fraggle attack** is similar in concept and mitigation to a Smurf attack except that it uses UDP packets instead of ICMP.

### SYN Flooding

A **SYN flood attack** is a form of a denial-of-service attack where an attacker takes advantage of the TCP handshake that uses SYN and ACK messages to establish a reliable connection between two hosts. Unlike UDP, where packets can be dropped without any sort of error correction, TCP uses a three-way handshake to ensure that messages are being sent properly and reliably, as shown in [Figure 5.24](#c05.xhtml#c05-fig-0024).

![FIGURE 5.24 SYN flooding](images/c05f024.png)

[**FIGURE 5.24**](#c05.xhtml#R_c05-fig-0024) SYN flooding

Here's the way a three-way handshake works:

1.  A client would like to establish a connection between itself and a server. It sends a SYN message to the server.
2.  The server receives the message and sends back a SYN acknowledgment, which is represented as SYN-ACK.
3.  The client then responds to the SYN acknowledgment by sending an ACK message to the server.

In a SYN flood attack, the attacker takes advantage of the three-way handshake. The attacker will send numerous SYN messages to the server, dozens if not hundreds of these per second. The server tries to keep up and send SYN-ACK messages back to the attacker, but the attacker never responds with the ACK message. Then, when a legitimate client wants to connect to the server, they are unable to do so because the server is flooded with SYN messages and unable to reply.

Because this could also look like network congestion, the server will usually wait a short time before responding, in hopes the congestion will settle down. A true malicious attack will continue to use up the server's resources, denying its services to other clients. Some servers may malfunction or even crash at this point.

There are effective countermeasures to SYN flooding depending on the operating system involved. One method of dealing with SYN flooding is to use a **calculated sequence number** rather than a **state table**. Unfortunately, this calculation can be quite CPU intensive, so this technique generally involves implementing specialized load balancers or network appliances specifically designed for handling DoS attacks.

Modern firewalls can also deal with SYN flooding to some extent by discarding half-open connections. However, a high-volume SYN flood will generally still manage to have a noticeable impact on network performance.

### Data Manipulation Attacks

Not all attacks are designed to steal data; some are designed merely to manipulate data to diminish its integrity. Many cybersecurity experts see **data manipulation** as a larger problem than traditional data theft or physical infrastructure attacks. These types of attacks undermine organizational, customer, and governmental confidence in the data they possess. The end result is the inability to make sound business decisions or make military decisions based on situational awareness data.

For example, the main thrust of the Stuxnet attack was based on data manipulation instead of theft. The attack altered the operational speed data of the Iranian centrifuges so that the operators did not know the true speed of their systems. Therefore, they had no idea that the centrifuges were in danger of destruction.

With the IoT and IIoT markets continuing to grow in every facet of life (including industrial processing and utility operations), the windows of opportunity for data manipulation–based attacks have increased exponentially. This includes items such as sensor networks, residential thermostats, insulin pumps, switching gear, etc.

Because data manipulation attacks are silent, targeted attacks that occur over multiple links in the cyber chain described earlier, it is important that organizations orchestrate their cybersecurity tools to detect, investigate, and mitigate attempts to overwrite data in their networks.

### Session Hijacking Attacks

In a TCP session, authentication generally occurs only when the session starts. Often when logging into a website a **session cookie** is given to the user to identify them going forward. If an attacker is able to sniff this connection and obtain the session cookie, they can gain access to that site. This sort of attack is known as **session hijacking**, as shown in [Figure 5.25](#c05.xhtml#c05-fig-0025).

![FIGURE 5.25 Session hijacking](images/c05f025.png)

[**FIGURE 5.25**](#c05.xhtml#R_c05-fig-0025) Session hijacking

A **clickjacking attack** employs deceptive frame techniques to trick the user into clicking on their content rather than the intended content. This is a popular trick deployed on hacked websites, as it is easy to do and can yield high rewards, as shown in [Figure 5.26](#c05.xhtml#c05-fig-0026). The attacker mostly conceals the legitimate frame so the user clicks the attacker's frame. This is often done to social media frames. It is possible for the web page developer to add a little frame-busting code to their web documents, but that can be defeated as well.
