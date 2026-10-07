
## Artificial Intelligence in Wireless Communications

Table 3.1
Knobs and Meters Available to the GNU Radio Simulation

| Knob Name | Knob Settings |
| --- | --- |
| Modulation | (D)BPSK, (D)QPSK, (D)8PSK, KMSK |
| Transmit power | 0 – 20 (dBm) |
| Symbol rate | 0.125, 0.25, 0.5, 1 (normalized sps) |
| Shaping filter roll-off | 0.1 – 1.0, steps of 0.01 |
| Normalized frequency | -1.0 – 1.0, steps of 0.01 |
| Frame size | 100 – 1500, steps of 1 |
| Meters | |
| Received signal strength (dBm) | |
| Noise power (dBm) | |
| Bit error rate | |
| Packet error rate | |
| Path loss | |
| Signal-to-noise ratio | |

to the average magnitude squared calculation when the mean of the signal 0.

```python
def variance(data):
    count = 0
    mean = 0
    sum = 0
    for x in data:
        count += 1
        delta = x - mean
        mean = mean + delta/count
        sum += delta*(x - mean)
    variance = sum/(count - 1)
```

In the GNU block for calculating variance, the number of items available for processing is a variable. The loop is calculated over all items, then the variance is calculated before the block exits. The received signal strength is first calculated by taking the average magnitude squared of the samples when the transmitter is known. However, this estimation is biased by the noise power, especially at low SNRs, so the final signal strength estimation shown in (3.1), by subtracting the noise power, provides a good estimation of the signal.

## Overview and Basics of Software Radios

```
$P = 10 \log_{10} \left( \frac{1}{K} \sum_{i=0}^{K-1} |x_i|^2 - n \right) \text{ dB}$
```

Here $x_i$ are time samples in millwatts and $n$ is the estimated power in millwatts. The GNU Radio block that implements average magnitude squared simply calculates the norm of each signal. Path loss and the energy per bit to noise ratio ($E_b/N_0$) are easy to estimate since the radios know the transmitted power and received power. Both of these values are converted into energy per bit ($E_b$) and noise density ($N_0$). The simulation calculates $E_b$ from the signal power by dividing it by the bit rate $R_b$, where $k$ is the number of bits per symbol and $R_s$ is the symbol rate. The calculation of noise comes from dividing the received power by the bandwidth, represented by the number of samples.

In our simulation, the BER calculation is more complicated. Figure 3.5 shows a BER calculation block (gr_ber_calc) with an input from the transmit path and one from the receive path. The BER is not simply a comparison of the transmitted and received bits because of the delay introduced by the blocks in the flow graph. The received bits are therefore delayed some amount from the transmitted bits. Furthermore, the delay is different for different types of modulations, changes with the symbol rate, and for some types of modulations, the delay is not consistent (GMSK, for instance, would have a delay of 7 or 8 samples during any run). Consequently, the BER calculation block calculates and compensates for the delay. To do this, it waits to see a particular code from both the transmitter and receiver and calculates the delay between corresponding samples. To avoid the problem of losing the code in noise, the packet is always transmitted with a much higher SNR (infinite in the simulation by setting the noise to 0).

The BER estimation works well in the simulation, though the over-air procedure has not been developed. For performing the analysis over the air, more synchronization is required between the transmitter and receiver and a procedure is required to know the actual transmitted bits for proper comparison, which is usually done using a pseudorandom sequence generator with known seeds. The transmitted bits could be known at the beginning, but synchronization is required if a packet is lost. The bits could be calculated using a seed passed in the packet, which could be corrupted itself, or a secondary transmit path such as Ethernet could be used with guaranteed fidelity, although this still requires synchronization. When a packet is lost, it is due to either corruption in the access code or the header, and the BER calculation needs to account for the lost bits without assuming all in the packet were lost.

There are many ways to solve the problem of over-the-air BER testing, and many implement tests, but the problem has not been solved in GNU Radio. Because we can get the performance analysis in the simulation, we do not solve this problem here and rely on packet errors as a performance measure during our over-the-air experiments. The packet error rate is an easy calculation because the packet numbers are included with the packets. The PER is calculated by knowing the number of packets transmitted from the packet number (or by being told) as well as the number of good packets received, which is determined by a 32-bit cyclic redundancy check (CRC).

Finally, the interference power is measured using a simple energy detector. The receiver opens up its bandwidth to sample the entire band of interest, and knowing the noise power from above, finds the frequencies where the signals exceed a certain threshold (e.g., 5 or 10 dB) above the noise floor and where the signals fall below the threshold. These frequencies are stored along with the average power between them to build an interference “map” of the channel. The cognitive radio can then use the map to understand the interference potential in a given bandwidth. Chapter 2 discussed the use of these meters in the cognitive engine and presented the XML format used to represent the information.

## 3.5 Conclusions

This chapter provides both a basic review of software radio technology and introduces the SDR system used later in the experiments. The GNU Radio platform solves a number of problems in working with SDR. First, it provides an affordable platform (free software, inexpensive hardware) that is open and therefore transparent to analysis as well as upgrades.

One of the authors, Rondeau, developed large portions of the digital communications capabilities in the current GNU Radio distribution. These were developed because of the need to perform research which also led to the SDR community. From a research point of view, the available GNU Radio platform enables the use of SDR. Anyone can use the next chapter to test.
