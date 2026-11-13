Goodfellow et al. further proved that global optimality is only reached for \( p_{data} = p_G \), so if the input data distribution matches the distribution learned by the generator. In this case, \( D(x) = \frac{1}{2} \) holds, which results in regression in the training process. [143]

Combining Equation (2.121) and Equation (2.122) results in the following minimax game for GAN optimization:

```
\(\min_G \max_D V(D, G)\)
\(= \mathbb{E}_{x \sim p_{data}(x)} [\log D(x)] + \mathbb{E}_{z \sim p_z(z)} [\log (1 - D(G(z)))] .\)
(2.123)
```

\(\log (1 - D(G(z)))\) gives the cross-entropy between \([0 \ 1]^T\) and \([D(G(z)) \ 1 - D(G(z))]^T\). Proposed by Rubinstein [240] in 1997, the cross-entropy is a measure of the quality of a model for a probability distribution. As the name already implies, it uses the cross entropy or Kullback–Leibler divergence as a measure for the closeness of two sampling distributions [241]. Analogously, \(\log D(x)\) gives the cross-entropy between \([1 \ 0]^T\) and \([D(x) \ 1 - D(x)]^T\). Hence, the value function \(V(G, D)\) is a Binary Cross Entropy (BCE) function, which is commonly used in binary classification problems [238]. In fact, any monotonically increasing function could be used instead of a logarithmic function [242].

After introducing the equations, the training procedure ought to have become evident: The discriminator receives a mini-batch of the generator samples and a mini-batch of the true samples. Then, the stochastic gradient of the discriminator equation is ascended to update the discriminator. The generator receives noise samples and the stochastic gradient of the generator equation is descended, and so on. A corresponding pseudocode can be taken from [143]. Theoretically, the discriminator could be updated \(k\) times and the generator only once per iteration, but in the original paper they use the least expensive and meanwhile most used option with \(k = 1\).