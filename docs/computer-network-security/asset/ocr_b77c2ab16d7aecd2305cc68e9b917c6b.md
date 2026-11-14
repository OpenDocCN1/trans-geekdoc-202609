# 5.1. Introducing firewalls

A firewall is a software or hardware system put in place between a reliable network and an unreliable one. The main purpose of putting in place a firewall is to filter out and prevent unwanted traffic from crossing the firewall barrier. In order to do this, a firewall must comply with the following recommendations:

+   - it must be resistant to attacks;
+   - it must be the only transit point between two networks;
+   - it must ensure that the organization’s access control strategy is applied.

# 5.2. Types of firewalls

There are different kinds of firewalls. Some of these are:

+   - NAT firewall: this hides a private IP address by translating it into a public IP address;
+   - packet-filtering firewall: this makes it possible to filter packets from Layers 3 or 4 of the OSI model. This kind of firewall is simple to configure but is also vulnerable to identity-theft attacks;
+   - stateful firewall: this carries out the same function as a packet-filtering firewall and also keeps track of the state of network connections (i.e. the TCP and UDP sequence numbers), thereby making it more secure;
+   - application firewall (proxy firewall): This is usually a server that carries out this type of filtering of information located in layers 3, 4, 5 and 7.

# 5.3. Setting up a firewall

The best practices for setting up a firewall include:

+   - place the firewall at the security boundaries to separate different domains of communication;
+   - only allow the traffic of necessary services;
+   - monitor firewall logs;
+   - put in place a variety of firewall technologies in order to provide comprehensive multilayer access control;