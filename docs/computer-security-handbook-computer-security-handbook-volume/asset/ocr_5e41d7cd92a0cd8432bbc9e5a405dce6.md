![](bbox=[0.087, 0.071, 0.849, 0.528])

# **EXHIBIT 6.2**  Ring Topology

the medium using *active taps* that are actually bit repeaters; a bit is read from the input line, held for a single bit time, then transmitted out to the output line.

A station transmits a message on the network by sending out a bit stream on its outgoing link; thus, rings are unidirectional in nature. Since all of the other stations see the bits one at a time, the intended receiver has no prior warning about an incoming message. For this reason, the transmitter is responsible for removing the message from the ring when the bits come back around. The MAC scheme ensures that multiple stations do not transmit at the same time.

In addition, a ring is a *serial broadcast* network. Because a station sends a message one bit at a time, every other station will see the message as it passes through but each will be receiving a different part of the message at any point in time.

Rings are a common physical LAN topology. However, unlike stars, they have multiple points of failure: if one link or one active tap fails, the integrity of the ring is destroyed. If the probability of failure of a single element is *p* and there are *n* elements, then the probability of failure P{F} of the LAN is

$$P\{F\} = 1 - (1-p)^n$$

As the number of elements rises, the probability of network failure rises exponentially. This problem is of such a critical nature that nearly all ring products use a star-wiring scheme or have some sort of redundancy built in for just this eventuality.