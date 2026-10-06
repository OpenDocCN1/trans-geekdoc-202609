# 258 CHAPTER 5 Domain 4: Communication and Network Security

noted above. E1s are dedicated 2.048-megabit circuits that carry 30 channels, and 16
e1s form an E3, at 34.368 megabits.

> Note
T1 and T3 speeds are often rounded off to 1.5 and 45 megabits, respectively. This book will use those
numbers (and they are also shorthand for the exam). Beyond the scope of the exam is the small
amount of bandwidth required for circuit overhead. The reason is 28 T1s 1.544
megabits 43.232 megabits, a bit lower than the T3 speed of 44.736 megabits. The same is true for
E1—E3 math.

SONET (Synchronous Optical Networking) carries multiple T-carrier circuits via
fiber optic cable. SONET uses a physical fiber ring for redundancy.

# Frame Relay

Frame Relay is a packet-switched Layer 2 WAN protocol that provides no error
recovery and focuses on speed. Higher layer protocols carried by Frame Relay, such
as TCP/IP can be used to provide reliability.

Frame Relay multiplexes logical connections over a single physical con-
ection create Virtual Circuits; this shared bandwidth model is an alternative to
ededicated circuits as T1, a PVC (Permanent Virtual Circuit) is always con-
ected to a real dedicated circuit like a T1. A Switched Virtual Circuit
(SVC) sets up "call," transfers data, and terminates the connection after an idle
timeout. Frame Relay is addressed locally via Data Connection Identifiers
(DLCI), pronounced "delce".

# X.25

X.25 is an older packet-switched WAN protocol. X.25 provided a cost-effective way
to transmit data over long distances in the 1970s through the early 1990s, when the
most common option was a direct call via analog modem. X.25's popularity has
faded as the Internet has become ubiquitous.

The global packet-switched X.25 network is separate from the global IP-based
Internet. X.25 performs error correction which can add latency on long links. It can
carry other protocols such as TCP/IP, but since TCP/IP contains its own reliability,
there is no need to take the extra performance by also providing reliability at
t X.25 layer. Other protocols such as frame relay are usually used to carry
TCP/IP.

# ATM

Asynchronous Transfer Mode (ATM) is a WAN technology that uses fixed
length cells. ATM cells are 53 bytes long, with a 5-byte header and 48-byte data
portion.

ATM allows reliable network throughput compared to Ethernet. The answer to
"How many Ethernet frames can I send per second" is "It depends." Normal Ethernet