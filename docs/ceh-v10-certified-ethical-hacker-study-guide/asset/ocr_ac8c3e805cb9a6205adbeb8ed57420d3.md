+   10. C. The RFC 1918 address blocks are 10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16. The only address listed that fits into one of those address blocks is 172.20.128.240. The address block is 172.16.0.0–172.31.255.255.

+   11. A. Manual pages provide documentation for commands and programs. IEEE is the Institute for Electrical and Electronics Engineers, which does manage some protocols but isn’t documentation itself. Standards on the Internet are actually uncommon and only happen after a very long period of time. The best place to find definitive documentation about protocols seen on the Internet is in the Request for Comments (RFC) documents.

+   12. D. At the Network layer, the PDU is a packet. The Network layer is IP. At the Data Link layer, the PDU is a frame. Commonly, the protocol would be Ethernet there. UDP uses datagram as the PDU. TCP uses segment for the PDU.

+   13. B. The source address is used as the address to send back to on the response, making it the destination address. The don’t fragment bit is used to tell network devices not to fragment the packet. The acknowledgment field is part of the TCP header and not the IP header. The IP identification field is used to identify fragments of the same packet, as they would all have the same IP identification number.

+   14. C. The traceroute program uses UDP messages with the time to live field starting at 1. This is incremented for each hop in the network until the destination is reached. Each device would send an ICMP time exceeded in transit message back to indicate the TTL had expired. The source of that message indicates the address of the network hop. On Windows systems, tracert uses ICMP echo request messages, also incrementing the time to live value. Because of these two factors, traceroute requires ICMP to work.

+   15. D. Systems over a VPN may use a MAC address but they may also use IP addresses. The same would be true for a tunnel. Using TCP, we would use ports for addressing. On the local network, the MAC address is used.

# Chapter 3: Security Foundations

+   1. C. Packet filters are used to make block/allow decisions based on header data like source and destination address and port. Stateful firewalls add in the ability to factor in the state of the connection—new, related, established. An Application layer gateway knows about Application layer protocols. A unified threat management appliance adds additional capabilities on top of firewall functions, including antivirus.

+   2. D. Confidentiality is about making sure secrets are kept secret. Integrity makes sure that data isn’t altered accidentally or by an unauthorized agent. Non-repudiation makes sure someone can’t say a message didn’t originate with them if it came from their identity. Availability means making sure data is where it needs to be when it should be there. This includes services as well.

+   3. A. Risk is the probability of the occurrence of an event multiplied by the dollar value of loss. There is no mitigation factor that is quantified, so it could be put into a risk calculation.