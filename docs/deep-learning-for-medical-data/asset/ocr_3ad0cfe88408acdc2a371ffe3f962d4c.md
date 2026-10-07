# 6.2 RELATED WORK | 75

stress W'' the proposed method differs from work that leverages the Gumbel-Softmax trick to model categorical latent variables: our proposals consider continuous scalar latent variables by quantizing their domain and modeling belief with a multinomial distribution. Categorical latent variable models would incur a much larger polynomial complexity penalty of $O(C^2)$.

The method is easily integrated into deep neural network architectures, and SQUAD layer implementations are provided at github.com/anonymized.

In the natural image domain, we anticipate a need for a high amount of information per variable, for which a small number of bins does not suffice. To improve the tractability of using a large number of quantization bins, we propose a variant of SQUAD that uses a factorization scheme to improve the parameter efficiency. Formally, equation 6.2 becomes:

```
$p(s_k = c(x)) = \text{softmax}(W_{k}^{u}(\mathbf{x}) + b_{k}^{u})$
```

with full weights $W''$ and $W'$ respectively of shape $(K, B, C)$ and $(|X|, K, B)$, where $K$ denotes the number of neurons, $B$ the number of factorization inputs, $C$ number of quantization bins and $|X|$ the input dimensionality. To improve the parameter efficiency, we can learn $W'$ per layer as well, resulting in shape $(|X|, 1, B)$, which is found to be beneficial for large $C$ by the hyper-parameter searched in section 6.3. We depict this alternative model on the right of figure 6.2 and will refer to it as SQUAD-factorized. We leave further extensions such as Network-in-Network (Lin et al., 2013) for future work.

# 6.2 RELATED WORK

Outside the realm of DLVMs, other methods have been explored for predictive uncertainty. Lakshminarayanan et al. (2017) propose deep ensembles: straight-forward averaging of predictions from a small set of separately adversially trained DNNs. Although highly scalable, this method requires retraining a model up to 10 times, which can be prohibitively expensive for large datasets.

Gal and Ghahramani (2015b) propose the use of dropout (Srivastava et al., 2014) at test time (Monte Carlo Dropout, or MC-Dropout) and present a Bayesian neural network interpretation of this method. A follow-up work by Gal et al.