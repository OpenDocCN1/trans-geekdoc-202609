physical layer is *link-to-link encryption*, which encrypts all the data sent from a specific communication device to another specific device. This includes the headers, addresses, and routing information. The primary strength of this type of encryption is that it provides added protection against sniffers and eavesdropping. The disadvantage is that all intermediate devices must have the keys, software, and algorithms necessary to encrypt and decrypt the encrypted packets at each hop along the trip. This adds complexity, consumes time, and requires additional processing power.

# Network Access Control Devices

Security should be implemented in layers to exert multiple barriers against attackers. One good example of a network access control is a firewall. The firewall can act as a choke point to control traffic as it ingresses and egresses the network. Another network access control is a DMZ (demilitarized zone), which establishes a safe zone for internal and external users to work. The sections that follow describe these network security devices and techniques in more detail.

# Firewalls

The term *firewall* has been used since the 1990s to describe hardware or software that guards the entrance to a private network. Firewalls were developed to keep unauthorized traffic out. Firewalls have undergone generations of improvements, and today several different types of firewalls exist, including packet filters, application proxies, circuit proxies, and stateful inspection.

It’s a sad fact that we need firewalls. Just as in the real world, on networks, some individuals enjoy destroying other people’s property. A firewall is a computer, a router, or a software component implemented to control access to a protected network. It enables an organization to protect its network and control traffic. Remember that the models addressed here, such as stateful inspection and proxies, are theoretical, and most vendor products do not match one design perfectly.

# Packet Filters