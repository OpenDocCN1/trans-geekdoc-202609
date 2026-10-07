# Artificial Intelligence in Wireless Communications

![](bbox=[0.135, 0.09, 0.865, 0.34])

**Figure 8.10** Frequency domain plot of interference test (2). A mistake in the interference sensor lead the algorithm to incorrectly believe the spectrum was unoccupied.

# Table 8.16
Objectives: Interference Test (3)

| BER | SINR | Thr. | BW | Spec. | Eff. | Int. | Pwr. | Comp. |
|---|---|---|---|---|---|---|---||
| 1.00 | 0.75 | 0.00 | 0.20 | 0.00 | 1.00 | 0.25 | 0.00 |

underlying calculations were set up to measure these values accurately without the presence of an interferer, but when an interferer is present in the received channel, the signal power calculation incorrectly computes the received signal power as much higher than it really is. We find the behavior and capabilities of the cognitive engine interesting and a valuable experience to enhance the overall understanding of the radio, we want to address how this error can be corrected. The other examples and results in this chapter show that, proper information about signal and noise power, the cognitive engine properly optimizes and finds waveforms that fit the objectives. Therefore, the cognitive engine needs a sensor capable of properly measuring the signal to interference ratio (SIR) or SINR.

One method of calculating the SINR is through the use of known symbols such as a sequence of training symbols or a known preamble. The GNU Radio implementation uses a known access code, or unique word, that the nodes correlate against to know the start of a packet. This known access code can also provide the required information to calculate SINR. The SINR meter probe is given the modulated access code and correlates against