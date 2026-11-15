For a lower bound (verification), by extending (16.7) to the K > 1 case we have the following lemma.

# Lemma 3. For a K-NN model with odd K, we have the following lower bound for the minimum adversarial perturbation:

```
\epsilon^* \ge s\text{th min}_{j \in [n^+]} \left( s\text{th max}_{i \in [n^+]} \sqrt{2\epsilon^{(i,j)}} \right), \quad \text{(16.9)}
```

where s = (K + 1)/2 is a positive integer, “sth min” and “sth max” select the sth minimum value and the sth maximum value, respectively, and

```
\epsilon^{(i,j)} = \frac{\max(\|z - x_j^-\|^2 - \|z - x_i^+\|^2, 0)^2}{8\|x_j^- - x_i^+\|^2}.
```

This is a simple extension of the 1-NN case. Note that the lower bound (16.9) can be efficiently computed. It requires O(n^2 d) time to compute all ε(i,j), and then the top-s selection can be done in linear time, so the overall complexity is just O(n^2 d), which is independent of K.

# Robustness of KNN vs neural network on simple problems

Using the above-mentioned algorithms implemented by Wang et al. (2019c), we are able to 1) efficiently compute the exact robustness of 1-NN models for a reasonable number of examples (e.g., for MNIST dataset, Wang et al. (2019c) showed that we can conduct evaluation in few seconds) and 2) for K-NN models, compute the certified robustness (verification) efficiently using Lemma 3.

With these algorithms, we can then compare the robustness between K-NN models and neural networks. We compare certified robust errors, defined as the fractions with lower bounds less than the given threshold (if an instance is wrongly classified, then the lower bound is 0), of 1-NN, a simple convolutional network (ConvNet), and a strong ℓ2 certified defense network (RandSmooth) (Cohen et al., 2019) in Fig. 16.2 (see Chapter 13 for more details on randomized smoothing). The results show that 1-NN can achieve better certified robust errors than neural networks on these two datasets. This is partially because the proposed verification algorithm provides very tight certified regions for NN classifiers. Note that this is not saying that K-NN is more robust than neural networks on more complex datasets such as CIFAR and ImageNet. However, this is showing K-NN could obtain better certified robust errors on some simpler tasks.