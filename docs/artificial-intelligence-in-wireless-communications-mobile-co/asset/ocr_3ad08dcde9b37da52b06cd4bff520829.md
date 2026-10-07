curves even more difficult to follow.

# 8.2.2 BER and Power (1)

For a more interesting example than the results just presented, in this simulation, we add the power minimization objective to the algorithm and lower the BER objective weight as represented in Table 8.3. The algorithm should now produce a waveform that produces a low BER while driving the power to the maximum, and indeed, Table 8.4 shows this exact trend. The BER is higher than in the previous example and the power is reduced.

# Table 8.3

| BER | SINR | Thr. | BW | Spec. Eff. | Int. | Pwr. | Comp. |
|---|---|---|---|---|---|---|--|
| 0.75 | N/A | N/A | N/A | N/A | N/A | 0.50 | N/A |

Objectives: BER and Power Test (1)

# Table 8.4

Waveform Settings and Results BER and Power Test (1)

| Knob | Settings |
|---|--|
| Modulation | BPSK |
| Transmit power (dBm) | 12.88 |
| Symbol rate (sps) | 0.250 |
| Pulse shaping | RRC, 0.22 |
| Normalized frequency | -0.807 |
| Packet size | 101 |

| | Sim. Result |
|---|--|
| BER | 3.28 × 10⁻² |
| SINR (dB) | N/A |
| Spec. Eff. (bps/Hz) | N/A |
| BW (Hz) | N/A |
| Throughput (bps) | N/A |
| Interference (dBm) | N/A |
| Power (dBm) | 12.88 |
| Computation (ticks) | N/A |

| Obs. BER | 0 |

One of the more telling aspects of this result is the value of the BER result of the cognitive engine versus the observed result of using the waveform on the radio. The simulated BER looks a bit large and suggests that the algorithm did not perform well as expected; from the objective function