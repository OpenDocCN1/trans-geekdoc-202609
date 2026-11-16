FTP and Telnet are very vulnerable to session hijacking because all communication is sent in plaintext. Secure Shell (SSH) is a good alternative. SSH establishes an encrypted channel between the local and remote hosts. Detection can be improved by using IDSs or IPSs. You can make session hijacking more difficult for an attacker by using switches, protocols like SSH, and software that uses more random initial sequence numbers (ISNs).

# Sniffing

A *sniffer* is a packet-capturing program that captures network traffic and can decode the captured frames. Sniffers work by placing the hosting system’s network card in *promiscuous mode*, which means the network card can receive all the data it can see and not just packets addressed to it.

When sniffing is performed on a switched network, it is known as *active sniffing*. There can be exceptions to this rule, however, because some switches can have one port configured to receive copies of all the packets in the broadcast domain. In such a case, passive sniffing can be performed.

When attackers do not have physical access to a switch, they might use techniques like Address Resolutions Protocol (ARP) poisoning and Media Access Control (MAC) address flooding to bypass the functionality of a switch.

Sniffers operate at the data link layer (Layer 2) of the OSI model. Sniffers can intercept whatever they see on the wire and record it for later review. They allow the user or attacker to see all the data contained in a packet—even information that should remain hidden. For sniffers to be successfully used by an attacker, the attacker must be on your local network or on a prominent intermediary point, such as a border router through which traffic passes.

Plaintext protocols are particularly at risk to sniffing. Figure 7.4 shows an example of a plaintext FTP session, which an attacker could use to steal password information. To reduce the threat of sniffing, you should use protocols like IPsec, SSL, and SSHv2 to pass usernames, passwords, and data.