# Spectral Pattern Discovery

a peak spectrum is expressed as below, where w is an error threshold, which is heterogeneous across a whole spectrum and p is an extracted spectrum,

```
p = s - b - w (5.33)
```

A spectra intensity is thus treated as a peak only when the following condition is satisfied, i.e., p_l > 0. Here, a peak is assumed to correspond to a true signal. Due to any possible variation, it may not be possible for a discovered peak to have an identical spectra analyser value, i.e., the value shown at the horizontal axis of a spectrum, across replicates in a spectra data. However, the spectra analyser values across replicates for a true peak are assumed to have a relatively small variation and this variance is significantly smaller than the distance between true peaks. Therefore, an alignment process is required when discovering peaks for spectra data with multiple replicates. The main purpose of using an alignment process is obvious, i.e., removing false signals and the confusion across replicates. The other assumption for applying an alignment process to the discovered significant peaks in a replicated data set is that a peak corresponding to a potential true signal should occur in most replicates. Instead, a false signal may present in one replicate by a chance.

Unlike analysing a single spectrum, estimating baselines and extracting peak spectrum based on a spectra data with multiple replicates needs some update to the t vector. The new t vector is defined as below,

```
t_i = 1 - r_i = 1 / (1 + exp[-kE_m(s_mi - b_mi - w_m)]) (5.34)
```

Such a t vector is called a global anchor. In the equation, k1 is a large positive number, which was set 100 as default [Lau, et al., 2012], E_m stands for the expectation across replicates and m is used to index the m^th spectrum. The use of such a sigmoid function is to make it differentiable. The derivative of r_i is called an entropy and is shown below,

```
r_i' = r_i(1 - r_i) (5.35)
```

The noise threshold variable w is assumed to follow a Gamma distribution. Therefore the model posterior of replicated spectra is