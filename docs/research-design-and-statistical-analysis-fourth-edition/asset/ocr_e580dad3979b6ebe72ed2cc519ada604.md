338 Research Design and Statistical Analysis

# 13.2 The Additive Model in the One-Factor Repeated-Measures Design

# 13.2.1 The Structural Model

We assume that the $n$ participants are a random sample from an infinitely large population of participants. We view $Y_{ij}$, the score of the $j$th participant in the $i$th condition, or on the $j$th trial, as being composed of a true score, $\mu_{ij}$ and measurement error, $\epsilon_{ij}$ that is,

```
$Y_{ij} = \mu_{ij} + \epsilon_{ij} \quad (13.1)$
```

If the different treatment levels have the same effect on the scores and if all participants in the population have the same scores, the true scores will equal the grand mean of the population. However, different treatments may have different effects and different participants will score differently because of differences in ability, experience, or motivation. Therefore, the parameter $\mu$ in Equation 13.1 can be viewed as being equal to the population mean plus the effects due to the treatment and the $j$th participant. Acknowledging this, Equation 13.1 is rewritten as

```
$Y_{ij} = \mu + (\mu_i - \mu) + (\mu_j - \mu) + \epsilon_{ij} \quad (13.2)\n= \mu + \alpha_i + \epsilon_{ij}$
```

The parameters of this structural equation are defined in the upper panel of Box 13.1, and related assumptions are in the lower panel. The model of the data represented by Equation 13.2 is referred to as *additive* because scores are reflecting the summing of participant $(\eta$; $\eta$-sub-i) and treatment ($\alpha$) effects; no interaction is assumed to contribute to the data.

**Box 13.1 Definitions and Assumptions for Parameters of the Additive Model**
| Parameter | Definition |
|---|---|
| $\mu_i$ | $\sum \mu_i / a$ |
| $\mu_j$ | $E(\mu_j)$ |
| $\mu$ | $\sum \mu / a$ |
| $\eta_i$ | $\mu_i - \mu$ |
| $\alpha_j$ | $\mu_j - \mu$ |

The following conditions hold for $\alpha_j$, $\eta_i$, and $\epsilon_{ij}$:

+   1. The $\alpha_j$, $\eta_i$, and $\epsilon_{ij}$ are distributed independently of each other.
2. If $A$ is a fixed-effect variable,

+   2.1 $\sum \alpha_j = \sum (\mu_j - \mu) = 0$.
2.2 The variance of the treatment effects is $\sigma_A^2 = \sum \alpha_j^2 / a$.
2.3 The null hypothesis about the effects of treatments is $H_0: \alpha_1 = \alpha_2 = \dots = \alpha_j = \dots = \alpha_k = 0$ or, equivalently, $\sigma_A^2 = 0$.