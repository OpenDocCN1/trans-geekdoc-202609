The protocol analyzer it uses a series of parsers to interpret the data for each protocol in a packet. For example, Figure 23.1 shows a protocol analyzer display of a packet containing an ICMP Echo Request message. On the Ethernet line, the tool has interpreted an Type code from the Ethernet header, indicating that the frames contain IP data. In the same way, the tool has interpreted the IP address's Next Protocol field to indicate that the data contains an ICMP message. Each line is displayed, enabling the technician to examine each protocol in detail.

| Frame Number: 3, Frame Length: 94, MediaType: ETHERNET |
| Ethernet: Destination = 00:00:5E:00:53:66, Source = 00:29:5B-29-D2 |
| IPv4: Src = 10.0.0.11, Dest = 10.0.0.2, Protocol = ICMP, Packet ID = 2823, IP Length = 60 |
| ICMP: Type = Echo Request, Code = 0 |
| Checksum = 3719 (xe4d6) |
| ID = 1 |
| Sequence Number: 0 (0) |
| ImplementationSpecificData: Binary Large Object (32 Bytes)|

FIGURE 23.1 An ICMP packet displayed in a protocol analyzer

# Bandwidth Speed Tester

Many are familiar with web-based Internet speed testing tools that work by performing downloads and uploads to a server belonging to the user's service provider (ISP). By measuring the amount of data sent and received in a specific amount of time, the tool can display the speed of the Internet connection, downstream and upstream.

There are also bandwidth speed testing tools that IT troubleshooters can use to measure the throughput of an internal network connection. The software tool includes both a client and end server, which when installed exchange traffic in the same way as that. The benefit of a tool like this is that it enables technicians to quantify the speed of the network and compare it to readings taken earlier or when users report that the network is slow, it is possible to determine objectively if this is true.

# Port Scanner

A port scanner is a software that sends a series of query messages to a specified server and listens for responses. The messages contain queries targeted at each of the server's ports, and the responses indicate which of the targeted ports are open or blocked by a firewall. except required by its applications, and a port scanner is a convenient method for testing. A port scanner is also a quick and easy way to determine if an application associated with a particular port is functioning.

# iPerf

iPerf is a client/server application that can measure the actual throughput achievable on a particular network connection. The tool is worth mentioning because it is open source and