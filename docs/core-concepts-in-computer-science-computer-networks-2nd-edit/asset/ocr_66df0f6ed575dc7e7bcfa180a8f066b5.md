# 262

Core Concepts in Computer Science: Computer Networks

![](bbox=[0.407, 0.053, 0.793, 0.442])

That's beautiful, but it seems that you're using a simple error correction code over a network

Well, there's a reason you feel this way. What network coding does is very similar to an error-correcting code. However, the properties of the network code are fairly different from your traditional error-correcting code.

Point-to-point communication, also known as P2P communication, is a type of communication where data is exchanged directly between two specific endpoints or nodes without involving any intermediate devices or additional participants.

Keep in mind that error-correcting codes are designed for point-to-point communications (check this video if the above does not ring a bell). They do not care at all about the network. Data is encoded at the source, replayed at intermediate nodes, and decoded at the destination. Parity bits are added to the original data stream to allow for recovering any bit flips or erasures (see the illustration below).

![](bbox=[0.417, 0.735, 0.863, 0.796])

Message Bits Parity Bits 1 0 1 0 1 1 1???

![](bbox=[0.763, 0.873, 0.863, 0.923])