# 3 SHARPNESS-BASED DISTRIBUTION ROBUST OPTIMIZATION

Particularly, we re-utilize weight perturbation $e^*$ to compute an OOD score:

```
$\omega_i = \max f(\theta; (x_i)) - \max f(\theta + e^*; (x_i)), \quad (3.11)$
```

where $f(\cdot)$ stands for the $c$-dimensional label prediction in the label space, whose maximum value is considered as prediction confidence. Intuitively, the model is much more robust to the clean distribution than the corrupted distribution, the prediction of clean data usually exhibits more stability than scarce noisy data when facing perturbations. Hence, if an example comes from a rarely exposed distribution, its prediction certainty would deviate significantly from the original value, producing a large OOD score, as shown in Section 3.5.1. Note that the major difference is that we target generalization on worst-case data, not OOD detection excludes OOD data.

To this end, we construct our worst-case data as:

```
$Q := \left{\{\sum_{i=1}^M \omega_i \cdot (x_i, y_i) : \omega_i = \frac{\omega_i}{\frac{1}{M}\sum_{i=1}^M \omega_i}}\right\\}, \quad (3.12)$
```

where normalization on $\omega_i$ is performed simultaneously. Then, the learning target of the distribution-agnostic setting becomes

```
$\min_{\theta} \left{\{\max_{\omega_i} \{\sum_{(x_i,y_i) \in Q} [\mathcal{L}(\theta, \omega_i; (x, y))] + \sum_{(x_i,y_i) \in Q} [\mathcal{R}(\theta, \omega_i; (x, y))]\}\right\},\ \quad (3.13)$
```

Therefore, the worst-case data can be selected by focusing on the examples with large OOD scores. In this, our SharpDRO can be successfully deployed into the distribution-agnostic setting to ensure robust generalization, whose effectiveness is demonstrated by quantitative and qualitative results in Sections 3.4.3 and 3.5.1. Next, we give details about implementing SharpDRO.

# 3.3.3 Optimization for SharpDRO

In both distribution-aware and distribution-agnostic scenarios, the worst-case data distribution is identified using the distribution weighting parameter $\omega_s$ and OOD score $\omega$, respectively. Intuitively, their effect is similar: finding the distribution that yields