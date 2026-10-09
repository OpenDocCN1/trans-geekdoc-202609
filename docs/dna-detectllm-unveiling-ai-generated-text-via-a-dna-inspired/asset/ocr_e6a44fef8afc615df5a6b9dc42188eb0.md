![](bbox=[0.17, 0.05, 0.83, 0.19])

Figure 3: Variation of repair scores Across Different Repair Strategies.

# 3.5 Repair Score-Based Detection

We introduce the *repair score* $R(s)$ to quantify the difficulty of the repair process, defined as the average conditional score accumulated throughout the repair trajectory:

```
$$R(s) = \frac{1}{T+1} \sum_{t=0}^{T} \sigma(s_{t}|s) = \frac{\sum_{t=0}^{T} \log \text{PPL}_{M_{t}}(s_{t}|s)}{(T+1) \log X \text{-PPL}_{L, M_{T}}(s)}, \qquad (5)$$
```

where $s_{t}$ is the sequence after $t$ repair steps, and $T$ is the total number of mutated tokens to be corrected.

Human-written texts typically exhibit more substantial mutations, resulting in greater repair difficulty. In contrast, AI-generated texts are generally easier to repair. Accordingly, the detection result for the input sequence is determined as:

```
$$D(s) = \begin{cases} \text{Human-written Text}, & R(s) > \tau \\ \text{AI-generated Text}, & R(s) \leq \tau. \end{cases} \qquad (6)$$
```

# 3.6 Sensitivity to Repair Order and Score Simplification

Figure 3 shows that different repair orders yield varying repair scores for the same input sequence, due to the unequal impact of each mutated token on the conditional score. Mutated tokens can be broadly categorized into high- and low-probability types. Repairing low-probability tokens typically causes larger shifts in the conditional score, while high-probability tokens lead to smaller changes. To systematically analyze the influence of repair order, we identify four types of principal repair strategies as follows:

+   *   **High-to-low:** Repairing high-probability tokens first, followed by low-probability ones, results in a convex “repair curve” with a higher repair score.

*   **Low-to-high:** Repairing low-probability tokens before high-probability ones yields a concave “repair curve” with a lower repair score.

*   **Sequential Repair:** Tokens are repaired in their original order of appearance in the input sequence, regardless of their probability values.

*   **Random Repair:** Tokens are repaired in a randomly chosen order. Averaging the repair scores across multiple random repairs leads to a more stable estimate.

These findings highlight the sensitivity of the repair score to the chosen repair order. Performing multiple random repairs effectively mitigates biases, resulting in a repair score close to the midpoint between the initial and final scores. Consequently, we further derive that the average repair score converges as the number of random repairs $N$ approaches infinity. The derivation is as follows:

Let $\{\delta_{1}, \delta_{2}, \dots, \delta_{T}\}$ be a set of non-negative real numbers satisfying $\sum_{i=1}^{T} \delta_{i} = \sigma(s) - \sigma(s|s)$. Moreover, $\delta_{i} = \sigma(s_{t-1}|s) - \sigma(s_{t}(s)$ quantifies the impact of repairing the current token on the score. Since the influence of each token repair on the conditional log-perplexity is independent and fixed, the set $\{\delta_{1}, \delta_{2}, \dots, \delta_{T}\}$ consists of fixed values for a given input sequence, whose order varies depending on the repair strategy. It further follows:

```
$$\sigma(s_{t}|s) = \sigma(s) - \sum_{i=1}^{t} \delta_{i} \quad \text{for } t = 1, 2, \dots, T, \quad \text{where } \sigma(s) = \sigma(s_{0}|s). \qquad (7)$$
```

5