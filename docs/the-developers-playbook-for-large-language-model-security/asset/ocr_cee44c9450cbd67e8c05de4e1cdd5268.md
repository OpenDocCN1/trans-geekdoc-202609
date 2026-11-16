utilize a network of infected devices, known as a *botnet*, to generate a flood of traffic that overwhelms the target from numerous points across the internet.

# # Protocol Attacks

Protocol attacks target the network layer or transport layer of a network connection. They exploit weaknesses in the protocols that run the internet. By manipulating the flaws in these protocols, attackers can send a relatively small amount of traffic to create a disproportionately large load on the target, effectively disrupting its ability to communicate. Examples include *SYN floods*, *ping of death*, and *Smurf attacks*:

# ## SYN floods

This attack exploits the TCP handshake process, which is the initial negotiation between the client and the server to establish a connection. In a SYN flood, the attacker sends a rapid succession of SYN requests (a signal to start a connection) to a target server, but intentionally fails to complete the handshake by not sending the final acknowledgment.

# ## Ping of death

This attack involves sending malicious pings to a system. In a ping of death scenario, the attacker sends larger pings than the IP protocol allows (65,535 bytes). Older systems often couldn't handle these oversized packets, causing them to freeze, crash, or reboot.

# ## Smurf attack

The attacker sends ICMP requests (usually pings) to a network's broadcast address, spoofing the return address with the target's IP. All devices on the broadcast network respond to this ping, sending replies to the victim's IP address. This amplifies the volume of traffic directed at the target, overwhelming its resources.

Each of these attacks represents a different approach to overwhelming a target with unwanted traffic or requests, resulting in a denial of service. Protection against such attacks often involves a combination of traffic filtering, rate limiting, and network configuration adjustments to reduce vulnerability.

# # Application Layer Attacks

Application layer attacks are more sophisticated attacks that target the application layer, where web pages are generated and delivered in response to HTTP requests. The attacker requests so many resources from the server that it cannot serve legitimate user requests. Such attacks often require fewer resources than volume-based or protocol attacks but can be highly effective due to their targeted nature. Examples of this kind of attack include *HTTP flood* and *Slowloris*: