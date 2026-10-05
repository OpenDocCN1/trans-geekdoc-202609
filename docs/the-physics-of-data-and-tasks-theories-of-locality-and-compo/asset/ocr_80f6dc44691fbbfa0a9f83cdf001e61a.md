# 1.2 GENERALIZATION IN DEEP LEARNING

from characters to words to phrases in text. This hierarchical composition introduces a natural notion of scale separation: fine-grained features interact locally, coarser features emerge from aggregations over broader contexts. Coarsening operations like pooling in CNNs mimic renormalization-group transformations in physics, progressively integrating information across scales.

In fact, deep neural networks — by virtue of their depth — are naturally suited to modeling such hierarchical functions. Each layer operates at a distinct scale, composing simple features into increasingly abstract ones. Theoretical results support this intuition: compositional functions, e.g.,

```
$f(x1, x2, x3, x4) = g(h1(x1, x2), h2(x3, x4)), (11)
```

can be represented by deep networks with exponentially fewer parameters than shallow ones [MLPF]. This implies an information-theoretic lower bound on sample complexity that is only polynomial in dimension [ShiZa]. However, these theoretical results do not imply that gradient descent will efficiently discover solutions in practice. In fact, efficient representability does not guarantee learnability by gradient descent for hierarchical tasks [Cag+24].

# 1.2.4 Questions

Despite the empirical success of convolutional networks, our theoretical understanding of why they outperform connected networks and how different architectural components contribute to this advantage remains incomplete. A central challenge in machine learning is to quantify how different forms of structure – both in the model and in the data – affect sample complexity.

How much does locality contribute to generalization? Can locality alone change the curve exponent $\beta$, allowing convolutional networks to escape the curse of dimensionality? How do these gains compare to those induced by other structural priors, such as translational invariance and weight sharing?

In the NTK regime, FCNs are biased toward low-frequency functions. What is the spectral bias of convolutional kernels? How do locality and weight sharing reshape the kernel spectrum, and what classes of functions become easier (or harder) to learn as a result? Does it privilege classes of functions – e.g., those with localized or multiscale structure?

For FCNs in the NTK limit, increasing depth is known to have no impact. Yet in practice, deep CNNs substantially outperform shallow ones. Does depth lead to improved generalization in wide CNNs as well? Is this advantage attributable to the presence of hierarchical receptive fields, which mirror the compositional organization of many real-world signals? More broadly, is the sample complexity of learning hierarchical or compositional target functions with gradient-based methods?