![](bbox=[0.15, 0.13, 0.48, 0.21])

![](bbox=[0.52, 0.13, 0.83, 0.21])

![](bbox=[0.15, 0.22, 0.48, 0.29])

![](bbox=[0.52, 0.22, 0.83, 0.29])

# Fig. 3. Results of the benchmarks when testing for directed influences \(\mathcal{F}_{u \to y}\)

| Signal | Result |
|---|---|
| \(u_{wn}\) | X |
| \(u_{sin}\) | ✓ |
| \(u_{st}\) | X |
| \(u_{imp}\) | ✓ |
| \(u_{rw}\) | X |

| Signal | Result |
|---|---|
| \(u_{wn}\) | X |
| \(u_{sin}\) | ✓ |
| \(u_{st}\) | X |
| \(u_{imp}\) | X |
| \(u_{rw}\) | X |

| Signal | Result |
|---|---|
| \(u_{wn}\) | X |
| \(u_{sin}\) | X |
| \(u_{st}\) | X |
| \(u_{imp}\) | X |
| \(u_{rw}\) | ✓ |

| Signal | Result |
|---|---|
| \(u_{wn}\) | ✓ |
| \(u_{sin}\) | X |
| \(u_{st}\) | ✓ |
| \(u_{imp}\) | X |
| \(u_{rw}\) | ✓ |

# Fig. 4. Results of the benchmarks when testing for directed influences \(\mathcal{F}_{y \to u}\)

**Low-pass filter:** Regarding the low pass filter, \(u_{wn}, u_{sin}\) and \(u_{imp}\) detect the correct directed connectivity. The saw tooth and random walk, both having a similar power spectrum (see figure 1) are not detected. The reason is that the low-pass filter has to too much attenuation, resulting in an output signal which has already too much information about itself in past values. Hence, in terms of Granger Causality, this results in a non-significant information gain for \(u_{rw}\). The only excitation signal leading to a connectivity from \(y \to u\) is the sinusoid. Like for the dead time benchmark, the reason is that the sinusoid is cyclic.

**Nonlinear system:** Adding an additional sinusoid as a non-linearity to the low-pass filter in the prior benchmark changes the results of the detected directed influences significantly. \(u_{wn}\) does no longer detect the connectivity \(u \to y\), while the \(u_{rw}\) is detecting it. The two excitation signals \(u_{sin}\) and \(u_{imp}\) behave like without non-linearity. Regarding the directed, causal wrong influence \(y \to u\) the excitation signals \(u_{wn}, u_{st}\) and \(u_{rw}\) detect this influence. Only the \(u_{sin}\) and \(u_{imp}\) correctly define the influence as not significant.