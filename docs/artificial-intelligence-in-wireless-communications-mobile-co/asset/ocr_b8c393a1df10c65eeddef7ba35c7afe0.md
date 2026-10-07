![](bbox=[0.136, 0.095, 0.863, 0.283])

(a) Actual versus estimated
(b) Percent error

# Figure 4.1 Comparison of the exact erf fc function to the estimation.

is calculated from the bandwidth of the waveform and the noise floor. The BER formulas are presented using $E_b/N_0$, or the ratio of the energy per bit to the noise power spectral density, as the standard representation of the signal quality. If $S$ is the signal power, the energy per symbol is $S/R_s$, since the symbol rate is the inverse of the symbol time. The energy per bit is the energy per symbol divided by the number of bits per symbol, $\log_2(M)$. The waveform sets the transmitted signal power, so the received signal strength is approximated by (4.5), where $P_T$ is the transmitted power and $L$ is the path loss.

```
$S = P_T - L \quad\ (dBm)$
```

The noise power spectral density is the noise per Hz, calculated in (4.6), where $k_B$ is Boltzmann’s constant $(1.38 	imes 10^{-23}$ J/K) and $T$ is the system noise temperature (K). The noise power in the channel is the noise power spectral density multiplied by the channel bandwidth, $B$.

```
$N_0 = k_B T \quad\ (J)\nN = 10\log_{10}(B N_0) + 30 \quad\ (dBm)$
```

The $E_b/N_0$ is a measurement independent of the signal bandwidth as given in (4.7), where $S - N$ is the SNR.

```
$E_b/N_0 = \gamma = 10\log_{10} \left(\frac{B}{R_s \log_2(M)}ight) + (S - N) \quad\ (dB) \quad\ (4.7)$
```