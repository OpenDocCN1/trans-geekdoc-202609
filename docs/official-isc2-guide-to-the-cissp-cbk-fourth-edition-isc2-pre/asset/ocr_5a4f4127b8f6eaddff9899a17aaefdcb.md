messages between hosts and gateways and is used for diagnostic tools such as ping and traceroute. ICMP can be leveraged for malicious behavior, including man-in-the-middle and denial-of-service attacks.

# Ping of Death 13

Ping is a diagnostic program used to determine if a specified host is on the network and can be reached by the pinging host. It sends an ICMP echo packet to the target host and waits for the target to return an ICMP echo reply. Amazingly, an enormous number of operating systems would crash or become unstable upon receiving an ICMP echo greater than the legal packet limit of 65,536 bytes. Before the ping of death became famous, the source of the attack was difficult to find because many system administrators would ignore a seemingly harmless ping in their logs.

# ICMP Redirect Attacks 14

A router may send an ICMP redirect to a host to tell it to use a different, more effective default route. However, an attacker can send an ICMP redirect to a host telling it to use the attacker’s machine as a default route. The attacker will forward all of the redirected traffic to a router so that the victim will not know that his or her traffic has been intercepted. This is a good example of a man-in-the-middle attack. Some operating systems will crash if they receive a storm of ICMP redirects. The security practitioner should have several tools in his or her toolbox to be able to model and interact with attacks such as the ICMP redirect attack in order to better understand them. One such tool that will be very effective is called Scapy.

Scapy is a powerful interactive packet manipulation program. It is able to forge or decode packets of a wide number of protocols, send them on the wire, capture them, match requests and replies, and much more. It can easily handle most classical tasks like scanning, tracerouting, probing, unit tests, attacks, or network discovery (it can replace hping, 85% of nmap, arpspoof, arp-sk, arping, tcpdump, tethereal, p0f, etc.). It also performs very well at a lot of other specific tasks that most other tools cannot handle, like sending invalid frames, injecting your own 802.11 frames, combining technics (VLAN hopping+ARP cache poisoning, VOIP decoding on WEP encrypted channel, etc.)

You can find Scapy here: http://www.secdev.org/projects/scapy/

# Ping Scanning

Ping scanning is a basic network mapping technique that helps narrow the scope of an attack. An attacker can use one of many tools such as Very Simple Network Scanner for Windows based platforms and NMAP for Linux and Windows based platforms to ping all of