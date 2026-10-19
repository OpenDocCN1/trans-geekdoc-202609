any point, the sensors and capturing devices can be exploited along with the underlying communication network and the data can be forged. The IoT environment usually works in open, unattended and hostile environments. This ease-of-access to data can lead to increase the chances of attacks like DoS, Masquerade, and selective forwarding attacks [12]. In addition, if the fog node manages sensitive data and is lacking in better access control mechanisms, it might suffer from information leakage due to account hijacking, unauthorized access, and other vulnerable points of entry [13]. The attacks in the healthcare system can be broadly categorized into three types, which are depicted in Figure 15.2.

![](bbox=[0.219, 0.261, 0.775, 0.331])

**Figure 15.2**  Categorization of attacks in healthcare system.

# 15.3.1  Jamming Attack

In a jamming attack, the antagonist tampers with the content of the original message by transporting radio frequency signals inside the network or by blocking the message and, as a result, it cannot reach the intended receiver. Radio interference attacks are very difficult to be addressed by conventional security methods. An attacker can cause the attack simply by disregarding the medium access protocol and continually sending on a wireless network. A jamming attack can happen in two ways. Either it could be an external threat model in which jammer is not part of network; or it could be an internal threat model in which jammer belongs to the underlying network. A jamming attack may happen in healthcare applications by interference of the attacker’s radio signal with frequencies of the BAN (body area networks) [14].

# 15.3.2  Data Collision Attack

A data collision attack takes place when two or more nodes attempt to transmit simultaneously. It is a form of jamming attack where an intruder may strategically produce extra collisions by sending repeated messages on the channel [15, 16]. When the frame header is changed due to a collision, the error checking mechanism at the receiving end detects an error and rejects the received data. Thus, a change in the data frame header is a threat to data availability in the BAN [17].

# 15.3.3  Desynchronization Attack

In this type of attack, the attacker tampers with the message transmitted between sensor nodes by copying it many times by imposing a fake sequence number to one or both endpoints in an active connection; which leads to WBAN (wireless body area networks) overwhelming the network resources and energy, thereby causing the sensor nodes to transfer the message repeatedly [15, 18].