where x(t) represents the unprocessed data

Furthermore, as shown previously, the CWT method includes a complex conjugate term denoted by $\psi_{a,b}$, where $\phi(t)$ means wavelet [37] (Equation (2)).

```
$$\psi_{a,b}(t) = \frac{1}{\sqrt{|a|}} \phi(\frac{t-b}{a}).$$
```

# 3.3. Continuous Entropy (FEAT_ENT)

The continuous or differential entropy is another feature used in this work. It is a concept in data theory to represent the measurement of the average rate of a random variable; it is also understood as a measure to measure the quality or class diversity of datasets. On continuous probability distributions, it is based on the expansion from Shannon entropy, defined by Equation (3),

```
$h(X) = - \int^{N(S)} f(x)\log f(x)dx.$
```

where X represents a random variable defined by a probability density function of a subset.

# 3.4. Sample Average Interval Range (FEAT_RNG)

The range of a sample was used as a feature. It is defined as the absolute difference between the values compared to the last f(t) and the first position ($t-\Delta t$) of a sample

```
$R(t) = |f(t) - f(t-\Delta t)|.$
```

# 3.5. Poincaré Plots (FEAT_SD1, FEAT_SD2, FEAT_CT, FEAT_SAR)

The Poincaré plots of RR intervals is one of the methods used in Heart Rate Variability (HRV) analysis. It returns a useful visual map (or cloud), which is capable to summarize the dynamics of an entire RR time series regarding to actual and next one values. It is also a quantitative method to provide information over long- and short-term HRV [40,41].

![](bbox=[0.195, 0.693, 0.755, 0.853])

Figure 5. Poincaré plot demonstration on the flight dataset RC2.