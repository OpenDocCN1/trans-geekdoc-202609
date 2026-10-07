# 48 | GREEDY INFOMAX

![](bbox=[0.125, 0.096, 0.823, 0.203])

**Figure 5.2:** Groups of 4 image patches (red square) that excite a specific neuron, at 3 levels in the model (rows). Despite unsupervised greedy training, neurons appear to extract increasingly semantic features. Best viewed on screen.

using an autoregressive model $g_{ar}(z_{0:t}) = c_t$. Then, the mutual information between the extracted representations $z_{j+t}$ and $c_t$ of temporally nearby patches is maximized by employing a specifically defined probabilistic loss: Following the principles of Noise Contrastive Estimation (NCE) (Gutmann and Hyvärinen, 2010), CPC takes a bag $X = \{z_{t+k_1}, z_{t+k_2}...z_{t+k_{N-1}}\}$ for each delay k, with one "positive sample" $z_{t+k}$ which is the encoding of the input that follows k-steps after $c_t$, and $N-1$ "negative samples" $z_{j_n}$ which are uniformly drawn from all encoded input sequences.

Each pair of encodings $(z_j, c_i)$ is scored using a function $f(\cdot)$ to predict how likely it is that the given $z_j$ is the positive sample $z_{t+k}$. In practice, Oord et al. (2018b) use a log-bilinear model $f_k(z_j, c_i) = \exp\left(z_j^T W_kc_i\right)$ with a unique weight-matrix $W_k$ for each k-steps-ahead prediction. The scores from $f(\cdot)$ are used to predict which sample in the bag $X$ is correct, leading to the InfoNCE loss:

```
$$\mathcal{L}_N=-\mathbb{E}_k\left[\log \frac{f_k(z_{t+k}, c_t)}{\sum_{z_j\in X} f_k(z_j, c_t)}\right].$ (5.1)$
```

This loss is used to optimize both the encoding model $g_{enc}$ and the autoregressive model $g_{ar}$ to extract features that are consistent over neighboring patches but diverge between random pairs of patches. At the same time, the scoring model $f_k$ learns to use these features to correctly classify the matching pair. In practice, the loss is trained using stochastic gradient descent with minibatches drawn from a large dataset of sequences, and negative samples drawn uniformly from all sequences in the minibatch. Note, that no min-max issues are found in adversarial training.