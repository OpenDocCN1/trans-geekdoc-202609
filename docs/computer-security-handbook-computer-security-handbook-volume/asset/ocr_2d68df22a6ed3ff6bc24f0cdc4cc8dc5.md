![](bbox=[0.08, 0.07, 0.9, 0.35])

# Exhibit 5.19 Internet Control Message Protocol (ICMP)

process is often called pinging because the most popular program for sending ICMP echo message is called Ping. The echo message is a very important tool for network management. If the network manager suspects a problem, he or she will ping a wide range of host addresses to see which of them are reachable. The pattern of responses can reveal where problems exist within a network.

Attackers also love to ping a wide range of host IP addresses. This can give them a list of hosts that are reachable for attacks. Another popular network management and attack tool is traceroute (or tracert on Windows PCs). Traceroute is similar to ping, but traceroute also lists the routers that lie between the sending host and the host that is the target of the traceroute command. This allows an attacker to map the network. Border firewalls often drop echo reply messages leaving the firm to the outside.

Many ICMP messages are error messages. For instance, if a router cannot deliver the packet, it may send back an ICMP error message to the source host. This error message will provide as much information as possible about the type of error that occurred.

If an attacker cannot ping destination hosts because a firewall stops them, attackers often send IP packets that are malformed and so will be rejected. The ICMP error message is delivered in an IP packet, and the source IP address in this packet will reveal the IP address of the sending router. By analyzing error messages, the attacker can learn how routers are organized in a network. This information can be very useful to attackers.

# 5.8.2 Domain Name System (DNS).

To send a packet to another host, a source host must place the destination host's IP address in the destination address field of the packets. Often, however, the user merely types the host name of the destination host, for instance, cnn.com.

Unfortunately, host names are only nicknames. If the user types a host name, the computer must learn the corresponding IP address. As Exhibit 5.20 shows, the host wishing to send a packet to a target host sends a Domain Name System (DNS) request message to the DNS server. This message contains the host name of the target host. The DNS response message sends back the target host's IP address. To give an analogy, if you know someone's name, you must look up their telephone number in a telephone directory if you want to call them. In DNS, the human name corresponds to the