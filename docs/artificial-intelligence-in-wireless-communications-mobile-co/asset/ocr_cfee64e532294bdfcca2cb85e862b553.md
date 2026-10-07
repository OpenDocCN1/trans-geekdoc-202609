# DQPSK:

```
$P_e = Q_M(a,b) - rac{1}{2}I_0(ab) \exp\left(-rac{a^2+b^2}{2}\right)\nna = \sqrt{2\gamma}\left(1-\sqrt{\frac{1}{2}}\right)\nb = \sqrt{2\gamma}\left(1+\sqrt{\frac{1}{2}}\right) \quad (4.12)
```

Where $Q_M(a,b)$ is the Marcum-function of the first kind and $I_0(ab)$ is the modified Bessel function of the first kind and order zero [10].

Unfortunately, there is no formula for the performance of D8PSK. In the objective analysis of this modulation, we assume it will perform like 8PSK with a 2-dB loss in the SNR.

# 4.2.2 Bandwidth (Hz)

Dependencies

Knobs: modulation type, symbol rate, pulse shape filter

Meters: none

Objectives: none

Definitions

+   $k$ = number of bits per symbol\n$R_s$ = symbol rate (sps)\n$r$ = property of the pulse shape filter (roll-off factor in RRC and bandwidth-time product in a Gaussian filter)

Bandwidth is an objective that is also used in many other objective calculations. It appears in the bit error rate, interference power, spectral efficiency, and throughput. It is a direct measurement of how much spectrum is occupied by the radios. This objective offers a good indication of the spectral resources occupied and therefore measures the trade-offs we have been discussing.

In calculating the bandwidth, instead of using the raised cosine (RC) Nyquist pulse shaping, an RRC filter in both the transmitter and receiver provides a more practical implementation. Over the air, the pulse is shaped by a single RRC filter while the second RRC filter in the receiver shapes