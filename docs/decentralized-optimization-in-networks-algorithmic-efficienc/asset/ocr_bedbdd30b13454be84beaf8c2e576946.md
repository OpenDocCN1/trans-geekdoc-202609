(3) Comparison: In this simulation, we contrast ET-DSGT against other prevalent methods reported in [14,26,38]. The results of this comparison are visible in Fig. 4.3. It is worth mentioning that we utilize the residual \((1/N)\log_{10}(\sum_{i=1}^N \|x_t^i - x^*\|)\) as our benchmark for comparison. Upon examining Fig. 4.3, it becomes evident that approaches devoid of stochastic gradient exhibit superior convergence precision. Conversely, methods incorporating an event-triggering mechanism demonstrate a convergence accuracy and rate that is on par with real-time methods, yet with reduced communication requirements.

![](bbox=[0.27, 0.282, 0.655, 0.545])

FIGURE 4.3
Comparisons between ET-DSGT and other methods.

# 4.4.2 Energy-based source localization

In this subsection, we present a simulation based on an energy-driven source localization challenge, as referenced in [45], conducted on a randomly linked network structured as follows:

```
\(\min_{x \in \mathbb{R}^2} \frac{1}{N} \sum_{l=1}^N (\frac{1}{n^i} \sum_{h=1}^{n^i} (z^{i,h} - \frac{c}{||x - b^i||^\lambda})^2 ).\)
```

Here, \(b^i \in \mathbb{R}^2\) (where \(i = 1, ..., N\)) represents sensor \(i\), which gathers \(n^i\) data points. The isotropic energy propagation model, represented by \(z^{i,h} = c/(||\hat{x} - b^i||^\lambda) + q^{i,h}\), is employed to gauge the intensity of the \(h\)th signal received by sensor \(i\). Here, \(c\) is a positive constant indicating signal strength, while \(\lambda\) signifies the attenuation characteristic. Additionally, the condition \(||\hat{x} - b^i|| > 1\) holds, and \(q^{i,h}\) denotes an independent and homogeneously distributed sample noise.