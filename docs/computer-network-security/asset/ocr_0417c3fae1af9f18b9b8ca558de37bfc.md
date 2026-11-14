# Figure 9.1. The IPsec framework

# 9.1.4. The IPsec security association

- An IPsec Security Association (SA) makes it possible to specify the security settings associated with a communication.

+   - Each SA is identified uniquely by:
+     - the destination address of the packets;
+     - the basic IPsec protocol (AH or ESP);
+     - the SA identifier: the SPI.

- An SA is unidirectional. We thus need two SAs to protect communications in both directions.

All SAs together make up the Security Policy Database (SPD).

# 9.1.5. IPsec modes

There are two modes in which IPsec can be used: transport mode and tunnel mode.

+   - Transport mode:
+     - protects data within a packet. However, the original IP headers remain intact;
+     - is used for communications between two hosts that support IPsec;
+     - is generally combined with the GRE protocol to protect traffic.