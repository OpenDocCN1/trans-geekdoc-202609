# 5.4 Contrastive Divergence 65

So CD-1 corresponds to truncating the chain after two samples (one from $\mathbf{h}_1$, and one from $\mathbf{x}_2|\mathbf{h}_1$). What about stopping after the first (i.e., $\mathbf{h}_1|\mathbf{x}_1$)? It can be analyzed from the following log-likelihood gradient expansion [12]:

```
$$\frac{\partial \log P(\mathbf{x}_1|\mathbf{h}_1)}{\partial \theta} = E [$\frac{\partial \log P(\mathbf{x}_1|\mathbf{h}_1)}{\partial \theta}] - E [$\frac{\partial \log P(\mathbf{h}_1)}{\partial \theta}]$\$. (5.29)
```

Let us consider a mean-field approximation of the first expectation, and where instead of the average over all $\mathbf{h}_1$ configurations according to $P(\mathbf{h}_1|\mathbf{x}_1)$ by its average configuration $\mathbf{h}_1 = E[\mathbf{h}_1|\mathbf{x}_1]$, yielding:

```
$$\frac{\partial \log P(\mathbf{x}_1|\mathbf{h}_1)}{\partial \theta} \approx E$\frac{\partial \log P(\mathbf{x}_1|\mathbf{h}_1)}{\partial \theta}$\$. (5.30)
```

If, as CD, we then ignore the expectation in Equation (5.29) (incurring an additional bias in the estimation of the log-likelihood gradient), we then obtain the right-hand side of Equation (5.30) as an update direction, which is minus the gradient of the *reconstruction* error,

```
$-\log P(\mathbf{x}_1|\mathbf{h}_1)$
```

typically to train auto-encoders (see Equation (4.7) with $\mathbf{c} = E[\mathbf{h}_1]$^4.

So we have found that the truncation of the Gibbs chain gives rise to first approximation (one sample) to reconstruction error (through a biased mean-field approximation), with slightly better approximation (two samples) to CD-1 (approximating the expectation by a sample), and with more terms to CD-k (still approximating expectations by samples). Note that reconstruction error is deterministically computed and correlated with log-likelihood, which is why it has been used to track progress when training RBMs with CD.

> ^4It is debatable whether or not one would take into account the fact that $\mathbf{h}_1$ depends on $\theta$ when computing the gradient in the mean-field approximation of Equation (5.30), but it must be the case to draw a direct link with auto-encoders.