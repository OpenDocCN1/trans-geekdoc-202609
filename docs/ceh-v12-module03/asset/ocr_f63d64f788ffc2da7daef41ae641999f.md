# LO#04: Demonstrate Various Scanning Techniques for Port and Service Discovery

![](bbox=[0.795, 0.098, 0.86, 0.13])

# Port and Service Discovery

The next step in the network scanning process involves checking the open ports and services in live systems. This discovery of open ports and services can be performed via various port scanning techniques. Administrators often use port scanning techniques to verify the security policies of their networks, whereas attackers use them to identify open ports and running services on a host with the intent of compromising the network. Moreover, sometimes, users unknowingly keep unnecessary open ports on their systems. An attacker takes advantage of such open ports to launch attacks.

This section describes the common ports and corresponding services along with various port scanning techniques and tools used by the attacker to perform port scanning.

# List of Common Ports and Services

The important reserved ports are listed below:

| Name | Port/Protocol | Description |
|---|---|---|
| echo | 7/tcp, udp |  |
| discard | 9/ tcp, udp | sink null |
| systat | 11/tcp | Users |
| daytime | 13/ tcp, udp |  |
| netstat | 15/tcp, udp |  |
| qotd | 17/tcp, udp | Quote |
| chargen | 19/tcp, udp | ttytst source |