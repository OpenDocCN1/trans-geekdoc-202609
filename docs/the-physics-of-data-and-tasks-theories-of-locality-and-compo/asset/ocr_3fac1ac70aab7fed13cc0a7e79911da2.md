# A THEORY OF CREATIVITY AND COMPOSITIONALITY

empirical correlation function, we compare the magnitude of correlations with the sampling noise, which has magnitude $(\upsilon mP)^{-1/2}$. Thus, the number of samples required to detect correlations between tuples of first-level latents and visible tokens

```
$P_3 = (1 - m/\upsilon^{\ell-1})^{-1} \upsilon m^4. \quad (87)$
```

EXTENSION TO GENERAL DEPTH $\ell$ The same procedure generalizes to any depth $\ell$. The correlations between tuples of latents at level $\ell-2$ and visible tokens, having lowest common ancestor at level $\ell$, have magnitude

```
$C^{(\ell)} = \sqrt{\frac{1 - m/\upsilon^{\ell+2}}{\upsilon^3 m^{\ell+2}}} \quad (88)$
```

Meanwhile, the sampling noise remains of order $(\upsilon^2 mP)^{-1/2}$. Equating these terms gives the sample complexity required to reconstruct level-$(\ell-1)$ latents

```
$P_{\ell} = (1 - m/\upsilon^{\ell-1})^{-1} \upsilon m^{\ell+1}. \quad (89)$
```

This indicates that rules leveraging correlations at depth $L$ requires a number of samples scaling as $m^{L+1}=md^{\log_L}$, which is polynomial (and not exponential) in the dimension. Knowing the rules, the network can reduce the dimensionality of the score by conditioning the expectation of a value on the latent variables instead of the full input sequence. Remarkably, Equation 80 displays the same scaling observed in our experiments with the U-Net in Section 6.2, confirming Theorem 6.3.1.

# 6.3.3 Clustering and one-step GD

CLUSTERING To validate the hypothesis that synonyms are grouped based on correlations, we consider a simple clustering based on the empirical correlations between (latent) tuples and a visible token. In particular, for a given (visible or latent) patch $h$, we fix it to one of its possible values $\upsilon$ and compute its $mean$ context vector by averaging the one-hot-encoded tokens $x$. Otherwise, we estimate the empirical conditional expectation $v_{\upsilon} = E[x|h = \upsilon]$ for each value $\upsilon$. These context vectors are proportional to the empirical patch-patch correlations in Section 6.3. We then perform k-means clustering on these vectors. When the dataset is sufficiently large, synonymous patches $\upsilon$ will produce similar mean contexts and are consequently grouped together.

As shown in Figure 18, the sample complexity for such an algorithm (black points) closely follows the theoretical prediction $P_L \sim m^{\ell+1}$. We also test a modified algorithm that uses all the tokens in the first visible tuple of just