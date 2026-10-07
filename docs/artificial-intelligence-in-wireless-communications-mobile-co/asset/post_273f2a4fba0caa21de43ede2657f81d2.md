
optimization and radio framework are currently supported at a time. The cognitive engine can also describe the policy engine interface, if one exists, and it configures the user interface. Currently, the decision maker and case-based systems are integrated with the cognitive controller, but these should be separated to allow different implementations. When this happens, the decision maker, too, will associate with the cognitive controller in this standard way.

When a component is associated, the cognitive controller requests the XML and DTD files used by the component to describe its information. These files are used to build the representation in the case base and store the results of each component, like the optimization results or the sensor data. It is exchange of information that necessitates the instantiation of the components before the controller.

Below, we show a simple Python script that acts as the user interface to control the cognitive engine. The command structure is simple:

```
<component>:[name]:<command> [extra parameters]
```

The component is one of the major components, such as "sensor" or "optimizer." The name is only required for the sensors to describe which sensor command is to be passed, such as "meters" or "objectives." The command describes action requested from the component, such as "collect" to request data from the sensor or "optimize" to tell the optimization process to run. The final optional extra parameters can be additional information to a component for its processing, as a frequency range for the PSD sensor to scan.

The control script performs the actions listed here:

- 1. Run the radio system;
- 2. Collect the meters and PSD;
- 3. Collect the objectives;
- 4. Search for previous solutions in the case base;
- 5. Run the optimization process given the problem definition, the chromosome definition, the GA parameters, the radio environment map and meters, and the previous solutions;
- 6. Receive the optimized waveform and simulated results and store these in the case base;
- 7. Run the new waveform on the radio in the environment;
- 8. Collect the new meters and compare the performance.

## 8.2 Simple Simulations

The simple simulation environment uses an AWGN channel with a free-space path loss shown in (8.1) where $n=2, GT=GR=0, c$ is the speed of light in meters per second, $d$ is the distance between transmitter and receiver, $P_T$ is the transmitted power in dBm, and $P_R$ is the received signal power in dBm. The path loss is implemented by using a frequency of 780 MHz. We chose this frequency because of the significant interest in this spectrum and the FCC 700 MHz spectrum auction that took place in early 2008. The distance was set for this frequency to provide path loss of about -22 dB, or about 1 wavelength.

```
$P_R = P_T + G_T + G_R - n10\log_{10}\left(\frac{4\pi df}{c}\right)\quad(8.1)$
```

The simulation ran 100 KB, or $8 \times 10^5$, bits through the transmit-receive chain, which will provide adequate representation of the BER where $1 \times10^{-6}$ is considered the lowest threshold and most of the simulations were designed for higher BER than this. The objective function calculation was designed the simple lin-log of (5.2).

### 8.2.1 BER-only

In the following tables, we abbreviate the columns for bit error rate (BER), signal to interference plus noise ratio (SINR), throughput (Thr.), bandwidth (BW), spectral efficiency (Spec. Eff.), interference power (Int.), power consumption (Pwr.), and computational power (Comp.). Table 8.1 shows these values for the BER-only test. The results of the test are listed in Table 8.2.

## Table 8.1
Objectives: BER-Only Test

| BER | SINR | Thr. | BW | Spec. Eff. | Int. | Pwr. | Comp. |
|---|---|---|---|---|---|---|---|
| 1.00 | N/A | N/A | N/A | N/A | N/A | 0.00 | N/A |

Figure 8.2 shows the performance of the BER and power objectives over the generations of the genetic algorithm. These plots show the expected behavior of the objectives as the BER objective is optimized. The power objective, while calculated, had a weight of 0, so it did not factor into the preference of the algorithm. We use the calculation here to show how the two objectives are traded off under the performance criteria. The BER curve has a steady negative slope for the best performing individuals while the power increases as a direct result of minimizing the BER.

## Table 8.2
Waveform Settings and Results: BER-Only Test

| Knob | Settings |
|---|---|
| Modulation | BPSK |
| Transmit power (dBm) | 19.08 |
| Symbol rate (sps) | 0.250 |
| Pulse shaping | RRC, 0.86 |
| Normalized frequency | -0.620 |
| Packet size | 171 |
| Meters | Sim. Result |
| BER | $1.18 \times 10^{-7}$ |
| SINR (dB) | N/A |
| Spec. Eff. (bps/Hz) | N/A |
| BW (Hz) | N/A |
| Throughput (bps) | N/A |
| Interference (dBm) | N/A |
| Power (dBm) | 19.08 |
| Computation (ticks) | N/A |
| Obs. BER | 0 |

![](img/7780d97a7979a9fac4a1941139511cc9_144_0.png)

**Figure 8.2** Performance curves for BER-only test with plots for objectives (a) BER and (b) power.

The graphs in Figure 8.2 are simple representations of the graphs we will be discussing in more complicated, multiobjective scenarios. Even in this simple simulation, the graphs show the random behavior of the genetic algorithm that make them difficult to read. The BER plot shows that even in later generations, some individuals exhibit large BER due to mutations or bad crossover. As we introduce more objectives into the experiments, different optimization forces will cause more complex responses by the GA that make curves even more difficult to follow.

### 8.2.2 BER and Power (1)

For a more interesting example than the results just presented, in this simulation, we add the power minimization objective to the algorithm and lower the BER objective weight as represented in Table 8.3. The algorithm should now produce a waveform that produces a low BER while driving the power to the maximum, and indeed, Table 8.4 shows this exact trend. The BER is higher than in the previous example and the power is reduced.

## Table 8.3

| BER | SINR | Thr. | BW | Spec. Eff. | Int. | Pwr. | Comp. |
|---|---|---|---|---|---|---|---|
| 0.75 | N/A | N/A | N/A | N/A | N/A | 0.50 | N/A |

Objectives: BER and Power Test (1)

## Table 8.4
Waveform Settings and Results BER and Power Test (1)

| Knob | Settings |
|---|---|
| Modulation | BPSK |
| Transmit power (dBm) | 12.88 |
| Symbol rate (sps) | 0.250 |
| Pulse shaping | RRC, 0.22 |
| Normalized frequency | -0.807 |
| Packet size | 101 |

| | Sim. Result |
|---|---|
| BER | $3.28 \times 10^{-2}$ |
| SINR (dB) | N/A |
| Spec. Eff. (bps/Hz) | N/A |
| BW (Hz) | N/A |
| Throughput (bps) | N/A |
| Interference (dBm) | N/A |
| Power (dBm) | 12.88 |
| Computation (ticks) | N/A |
| Obs. BER | 0 |

![](img/7780d97a7979a9fac4a1941139511cc9_146_0.png)

**Figure 8.3** Performance curves for BER and power test (1). As (a) and (b) power are competing objectives, the algorithm must balance them.

One of the more telling aspects of this result is the value of the BER result of the cognitive engine versus the observed result of using the waveform on the radio. The simulated BER looks a bit large and suggests that the algorithm did not perform well as expected; from the objective settings, the waveform should heavily weigh minimizing the BER to minimizing the power. However, the actual result of using the waveform showed a much better BER than the simulated performance, indicating that this was a good waveform choice produced the proper balance of power to BER. Furthermore, this indicates a robustness under uncertainty in the system performance.

It does not matter in this case that the information received from the sensor was incorrect; the algorithm found the proper balance. We previously discussed the concept of overoptimization. An error in the meter's representation could lead to an artificially increased transmit power to the detriment of nearby radios as well as its own power consumption.

### 8.2.3 BER and Power (2)

To study the behavior a further, an interesting question to address is the effect changes in the weights on the performance of the cognitive engine. Using Table 8.5, we dropped the BER to 0.5 so that the optimization process has no preference. Of course, only the relative
