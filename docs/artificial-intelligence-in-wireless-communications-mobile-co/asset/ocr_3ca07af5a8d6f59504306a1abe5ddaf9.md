# Artificial Intelligence in Wireless Communications

![](bbox=[0.115, 0.096, 0.865, 0.246])

(a) BER

(b) Power

![](bbox=[0.315, 0.306, 0.665, 0.442])

(c) Throughput

**Figure 8.5** Performance curves for throughput test. The (c) throughput objective is more directly dependent on the modulation and can increase with less pressure from (a) BER as the (b) power increases.

In none of these problems did the cognitive engine find a waveform that uses differential modulation. This is actually good, because under no circumstances in the system provided does a differential modulation make more sense than a nondifferential modulation. The differential modulations have about a 2-db loss in the BER performance, and they do not offer any benefit in throughput or bandwidth. Their use in real communication systems is derived from the simpler design requirements for the receiver. However, in the GNU Radio system, as discussed in Appendix C, the differential modulators only add blocks to the flow graph and increase the complexity of the system. Therefore, given the current radio platform, there are no situations that will allow a differential modulation an advantage over a nondifferential form, but it is important to point out that this only holds true for the radio platform used. Another platform that implements a simpler differential receiver might show some benefits under certain conditions of low battery capacity.