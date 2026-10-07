
# 138 Artificial Intelligence in Wireless Communications

![](img/7780d97a7979a9fac4a1941139511cc9_152_0.png)

(a) BER

![](img/7780d97a7979a9fac4a1941139511cc9_152_1.png)

(b) Power

![](img/7780d97a7979a9fac4a1941139511cc9_152_2.png)

(c) Bandwidth

![](img/7780d97a7979a9fac4a1941139511cc9_152_3.png)

(d) Spectral Efficiency

![](img/7780d97a7979a9fac4a1941139511cc9_152_4.png)

(e) Throughput

![](img/7780d97a7979a9fac4a1941139511cc9_152_5.png)

(f) Computational complexity

**Figure 8.6** Performance for waveform efficiency test with plots for (a) BER, (b) power, (c) bandwidth, (d) spectral efficiency, (e) throughput, and (f) computational complexity. The GA searches through a large number of solutions with different objectives dominating at different times before converging to compromised solutions by the final generations.

## 8.3.1 Interference (1): Simple BER Tests

The first, simplest test under these conditions is to ask the cognitive engine to build a waveform that avoids the interferers and minimizes the BER as represented by the objective weights in Table 8.11. Table 8.12 shows that the BER objective was met and Figure 8.7 shows the frequency domain of the simulation to demonstrate that the interferers were avoided properly. In the frequency plots, we show the signal seen by the receiver as the combination of the transmitter and interferers and the transmitted signal is shown as the dotted black line that has been adjusted for path loss. Figure 8.8 shows that the objectives in this case were easily met. The SINR increased to its maximum quickly, and the interference power was always very low. This figure indicates that very good solutions were found early and dominated the population. The figure also shows two plots of the interference objective. The plot in Figure 8.8(c) shows the same axis as all other interference plots while the plot in Figure 8.8(d) shows the same plot zoomed in to better show the objectives performance.

### Table 8.11
Objectives: Interference Test (1)

| BER | SINR | Thr. | BW | Spec. Eff. | Int. | Pwr. | Comp. |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1.00 | 0.00 | 0.00 | 0.00 | 0.00 | 1.00 | 0.00 | 0.00 |

### Table 8.12
Waveform Settings and Results: Interference Test (1)

| Knob | Settings |
| :--- | :--- |
| Modulation | BPSK |
| Transmit power (dBm) | 20.00 |
| Symbol rate (sps) | 0.750 |
| Pulse shaping | RRC, 0.17 |
| Normalized frequency | -0.90 |
| Packet size | 580 |

| Meters | Sim. Result |
| :--- | :--- |
| BER | $1.21 \times 10^{-6} |
| SINR (ratio) | 7.12 |
| Spec. Eff. (bps/Hz) | 1.71 |
| BW (Hz) | 0.439 |
| Throughput (bps) | 0.75 |
| Interference (mW) | $8.63 \times 10^{-5} |
| Power (dBm) | 20.00 |
| Computation (ticks) | 31094.10 |
| Obs. BER | $4.5 \times 10^{-6} |

# Artificial Intelligence in Wireless Communications

![](img/7780d97a7979a9fac4a1941139511cc9_154_0.png)

**Figure 8.7** Frequency domain plot of interference test (1) where the cognitive engine found a solution that avoids the other users.

## 8.3.2 Interference (2): Sensor Problems

In the next set of experiments, we use a more interesting set of objectives from Table 8.13 to balance the wavelet properties and create waveforms that are bandwidth efficient but have high throughput, low BER, and avoid the interferers. In this first test, the cognitive engine used the information retrieved from the PSD sensor to know to avoid the interference. Table 8.14 and Figure 8.9 show, the waveform designed by the cognitive engine has 0 BER and the minimum interference power possible, where $1 \times 10^{-12}$ is used as the minimum power to avoid errors when converting to dBm. However, the observed BER was much higher, and Figure 8.10 shows that the waveform was placed directly on top of one of the interfering signals.

A look at the results returned by the PSD sensor shows why the cognitive engine selected an improper frequency. According to the PSD sensor as seen in Table 8.15, there are only four bands to start and end where the previous signal from about 0.5 to 1.0 Hz (normalized frequency) cannot be detected. The cognitive engine, working with this data, did not understand the presence of the signal and therefore could not avoid it. It turns out that PSD sensor had a small logic error that caused this representation, it was easily corrected. We show this because we want to illustrate this to indicate the impact of incorrect information on the cognitive engine; otherwise, under the conditions presented, the waveform optimization looks correct.

# Example Cognitive Engine

![](img/7780d97a7979a9fac4a1941139511cc9_155_0.png)

(a) BER

![](img/7780d97a7979a9fac4a1941139511cc9_155_1.png)

(b) SINR

![](img/7780d97a7979a9fac4a1941139511cc9_155_2.png)

(c) Interference power

![](img/7780d97a7979a9fac4a1941139511cc9_155_3.png)

(d) Interference power (zoomed)

**Figure 8.8** Performance curves for interference test (1) showing objective plots for (a) BER, (b) SINR, and (c) interference power. Plot (d) is a zoomed in of (c) for a closer look at the variations over the generations.

### Table 8.13
Objectives: Interference Test (2)

| BER | SINR | Thr. | BW | Spec. Eff. | Int. | Pwr. | Comp. |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1.00 | 0.75 | 0.60 | 0.20 | 1.00 | 0.25 | 0.00 | 0.00 |

## 8.3.3 Interference (3): Correcting for Sensors

While the mistake in the last example related to a logic error in the sensors, other measurements and uncertainties can also have effect on the cognitive engine’s performance. The designed for use with Radio measure the received power and noise power, and as Appendix shows, the measurements are fairly accurate, increasing as the SNR decreases.

### Table 8.14
Waveform Settings and Results: Interference Test (2)

| Knob | Settings |
| :--- | :--- |
| Modulation | BPSK |
| Transmit power (dBm) | 10.02 |
| Symbol rate (sps) | 0.750 |
| Pulse shaping | RRC, 0.10 |
| Normalized frequency | 0.777 |
| Packet size | 383 |

| Meters | Sim. Result |
| :--- | :--- |
| BER | 0 |
| SINR (ratio) | 47.092 |
| Spec. Eff. (bps/Hz) | 5.45 |
| BW (Hz) | 0.4125 |
| Throughput (bps) | 2.25 |
| Interference (mW) | $1 \times 10^{-12}$ |
| Power (dBm) | 10.02 |
| Computation (ticks) | 33430.09 |
| Obs. BER | $4.5 \times 10^{-6}$ |

### Table 8.15
PSD Sensor Results in Interference (2)

| Signal | Amplitude (dBm) | $f_{min}$ (Hz) | $f_{max}$ (Hz) |
| :--- | :--- | :--- | :--- |
| 1 | -12.12 | -1 | -0.975 |
| 2 | -11.45 | -0.909 | -0.705 |
| 3 | -1.28 | -0.332001 | 0.493 |
| 4 | -23.02 | 0.493 | 0.493 |

When interference is present, the interference signal is added to the received signal. Because the SNR calculation was not designed properly to measure the SINR, the resulting information is skewed when interference is received through the channel filter, specifically by raising the measured signal power and disproportionately affecting the measurements of the path loss and SNR. This information propagates to the cognitive engine and optimization process. When designing waveforms, the cognitive engine's estimation of the path loss affects the BER measurement, which will then affect what power levels provide acceptable values. In this case, because the path loss estimation is significantly decreased due to the increased measurement of the received power, the BER calculation assumes that lower transmit power provides lower BER than it should.

# Example Cognitive Engine

![](img/7780d97a7979a9fac4a1941139511cc9_157_0.png)

(a) BER (b) SINR

![](img/7780d97a7979a9fac4a1941139511cc9_157_1.png)

(c) Interference power

**Figure 8.9** Performance curves for interference test (2) showing objective plots for (a) BER, (b) SINR, and (c) interference power. The SINR objective plot (b) shows the mistake where the later generations calculated a very small SINR at the solution chosen.

We used the parameters in Table 8.16 to run the next test. The cognitive engine found that a BPSK signal with a 10.72-dBm transmit power will produce a 0 BER (in other words, a value too small to be represented), which indicates a very large SINR (see Figure A.1 to confirm this). However, with the use of the multiobjective search space, different objectives can produce a more acceptable solution. In this case, we use the SINR objective as the pressing agent in the optimization. When the SINR objective is not used, the power is minimized to 0.1 mW.
