model. The end result has you using a model with ten inputs, but in truth 50% of them are junk that is unrelated to your response variable! Such false discoveries are worse than useless: they add noise to your model and reduce the quality of your predictions.

This situation, where a high proportion of “discoveries” are false positives, gets worse with decreasing signal-to-noise ratios. For example, if you have one true signal out of 1000 hypothesis tests with an $\alpha=0.05$ cutoff, then you will have around $0.05 \times 999 \approx 50$ false discoveries. Your false discovery (FD) proportion will be around $50/51 \approx 98\%$. This might sound extreme, but having far fewer than 1/1000 true signals is the norm in applications like digital advertising, where a true signal is the rare existence of a website in browser history that indicates future purchasing intent.

In general, you have

$FD \, Proportion = \frac{\# \, false \, positives}{\# \, tests \, called \, significant}$

as a measure of the amount of spurious noise you have introduced into the model through false discovery. The FD proportion is a property of the fitted model. You can’t know it: either you’ve made mistakes or you haven’t. However, you can control its expectation, the false discovery rate:

$FDR = \mathbb{E}[FDP] = \mathbb{E} \left[ \frac{\# \, false \, positives}{\# \, tests \, called \, significant} \right]$. $

This is the multitest aggregate analog of the probability of a false positive from a single test. Because probability is just expectation for a binary random variable, the FDR for a single test is equal to the probability of a false positive—what we called $\alpha$ earlier.

Just as we used an $\alpha$-cutoff procedure to control false positives in single tests, you can ensure that $FDR \leq q$ for some chosen $q$-cutoffs (e.g., 0.1 is common). The Benjamini–Hochberg (BH) algorithm controls your FDR by defining a cutoff on ranked lists of $p$-values.

# **ALGORITHM 3** Benjamini–Hochberg (BH) FDR Control

For $N$ tests, with $p$-values {$p_{1} \, . . . \, p_{N}$} and target FDR $q$: 

+   * Order your $p$-values from smallest to largest as $p_{(1)} \, . . . \, p_{(N)}$. $