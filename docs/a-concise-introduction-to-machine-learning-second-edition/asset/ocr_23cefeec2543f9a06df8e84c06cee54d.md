-. Differentiating with respect to $\alpha_1$ gives

```
$$\frac{dE(C_1)}{d\alpha_1} = \sum_{c_i \neq k_1(v_i)} \exp(\alpha_1) - \sum_{c_i = k_1(v_i)} \exp(-\alpha_1).$$
```

Let $N$ be the number of samples and $N_C$ be number of correctly classified samples. We then have

```
$$\frac{dE}{d\alpha_1} = (N - N_C) \exp(\alpha_1) - N_C \exp(-\alpha_1).$$
```

To find the extremum, we set this to zero and solve for $\alpha_1:

```
$$\exp(2\alpha_1) = \frac{N_C}{N - N_C}$\n\alpha_1 = \frac{1}{2} \log \frac{N_C}{N - N_C}$
```

Thus $\alpha_1$ is half the logarithm of the ratio of the number of correctly classified samples over the number of misclassified samples. If $N_C=N/2$, then $\alpha_1=0$, which means we have no confidence in the classification, it is equal to random guessing. Note that $N_C$ cannot be less than $N/2$, because the weak classifiers need to be better than random guessing *ie.* they need to classify at least more than $N/2$ samples correctly. The larger $N_C$, the higher the confidence.

In the $m^{th}$ iteration we generate $c_m = c_{m-1} + \alpha_m k_m$. The total error is

```
$$\E(C_m) = \sum_{i=1}^N \exp(-\alpha_m c_{m-1}(v_i) + \alpha_m k_m(v_i))\n= \sum_{i=1}^N \exp(-\alpha_m c_{m-1}(v_i)) - \exp(-\alpha_m k_m(v_i))\n= \exp(-\alpha_m) \sum_{c_i=k_{m-1}(v_i)} w_{i,m} + \exp(\alpha_m) \sum_{c_i \neq k_m(v_i)} w_{i,m}, \quad (5.7)$
```

where we defined the weights $w_{i,m} = \exp(-\alpha_m c_{m-1}(v_i))$. Hence the weight $w_{i,m}$ is the exponential error the current classifier makes classifying sample $v_i$. The first sum is over all samples $k_m$ classifies correctly, while the second sum is over all incorrectly classified samples. The total error can be rewritten as

```
$$\E(C_m) = \sum_{i=1}^N \exp(-\alpha_m) w_{i,m} + \exp(\alpha_m) \sum_{c_i \neq k_m(v_i)} w_{i,m}.
```

Only the last sum depends on the weak classifier $k_m$. To find $E(C_m)$ small, the weak classifier where the sum of weights over the misclassified elements is