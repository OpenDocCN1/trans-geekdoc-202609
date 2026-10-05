
# A PHASE TRANSITION IN THE DIFFUSION PROCESS

![](img/86150bd6d44cb578b97e3eba954b7be2_83_0.png)

**Figure 8:** Probability that the latent has not changed the denoising process, corresponding to the largest marginal probability computed by BP, for each leaf, for inversion times of the diffusion process $t$. For the RHM with $v = 32, m = 8, s = 2, L = 10$. Each level of the tree, indicated in the legend, is represented with a different color. We observe the behavior of the correct class for ImageNet in Figure 5: the probability of the correct class has a sharp transition at a characteristic time scale, the probabilities corresponding to latent variables in the lower levels change smoothly.

## 4.5 MEAN-FIELD THEORY OF DENOISING DIFFUSION

In this section, we are making a simplifying assumption for the initial noise acting on the input and adopt a mean-field approximation to justify the existence of a phase transition. Remarkably, this approximation turns out to be of excellent quality for describing the dynamics. Specifically, consider a reference configuration at the leaves variables $X_i^{(0)} = \bar{X}_i$, which we would like to reconstruct, given a noisy observation of it. We assume that for each leaf variable, the noise is uniformly spread among the other symbols. In our words, our belief in the correct class is corrupted by $e \in [0, 1]$:

> $$\begin{aligned} X_i^{(0)} &= \bar{X}_i, \quad \text{with belief } 1-e, \ X_i^{(0)} &= \text{uniform over alphabet with belief } e. \end{aligned} \quad (71)$$

Hence, the initialization condition of the upward BP messages at a leaf node $X_i^{(0)}$ becomes

> $$\begin{aligned} v_i^{\uparrow}(\bar{X}_i) &= 1-e+e/v, \ v_i^{\uparrow}(X_i \neq \bar{X}_i) &= e/v, \ \end, \end{aligned} \quad (72)$$

where $v$ is the alphabet cardinality, and since the production rules are known, if $e = 0 - i.e.$, in the noiseless case – BP can reconstruct all values of the latent variables. Conversely, if $e = 1 - i.e.$, when the input is completely corrupted and the leaves variables are uniform — the reconstruction is impossible. In general, for a value of $e$, one is interested in computing the probability of recovering the latent structure of the tree at each layer $\ell$ and, as $L \to \infty$, to decide whether the probability of recovering the correct class of the input remains larger than $1/v$.

![](img/86150bd6d44cb578b97e3eba954b7be2_84_0.png)

**Figure 9:** Phase diagram for inferring the correct class using the upward iteration of BP. When $sf < f$, BP can infer the class if $e < e^*(sf)$. This transition is very well predicted by our theory. The inference region in the figure corresponds to the phase wherein the probability of the correct class is larger than the initialization belief in the correct values of the leaves, that is $1 - e + f$. Experimental data are for a single realization of the RHM with $v = 32, s = 2, L = 10$.

UPWARD PROCESS

We begin by studying the upward process from the leaves. A true input tuple $\tilde{x}_1, \dots, \tilde{x}_n$ which is associated with the higher-level feature $\tilde{y}$. Given the randomness of the production, rules are random variables depending on the specific realization of rules. We adopt a *mean-field* or *annealed* approximation that neglects the fluctuations from the random choice of rules. Specifically, we approximate the upward message by the average upward message using the corresponding factor message $\langle \psi^{(1)}(y_i) \rangle_\psi$ over the possible realizations of $\psi$. In Section C.2, we show that $(\psi^{(1)}(y_i))_\psi$ can take only two values: one for $y = \tilde{y}$ and one for $y \neq \tilde{y}$, expected by symmetry considerations. Furthermore, means-$e'$. Introducing the probability of reconstructions $p = 1 - e + \epsilon/v$ and $p' = 1 - e' + \epsilon'/v$, we have

```
$p' = \frac{p^s + f\frac{m-1}{m}}{p^s + f(1-p^s)} = F(p).
```

Iterating this procedure across all the levels of the tree, we can compute the probability of recovering the correct class of the input. In particular, for large $L$, we are interested in studying the fixed $p^* = F(p^*)$ of the iteration map in Equation 73. As derived in Section C.2.1.1, when $sf > 1$, this map has a repulsive fixed point $p^* = 1$, which corresponds to $\epsilon = 0$, and an attractive fixed point $p^* = 1/v$, corresponding to $\epsilon = 1$. Thus, in this regime, referring the class from the noisy observation of the input is impossible. In contrast, when $sf < 1$, $p^* = 1$ and $p^* = 1/v$ are both attractive points, and a new repulsive fixed point emerges. Therefore, in this regime, referring the class from the noisy observation of the input is impossible.

DOWNWARD PROCESS

We begin by studying the upward process from the leaves. A true input tuple $\tilde{x}_1, \dots, \tilde{x}_n$ which is associated with the higher-level feature $\tilde{y}$. Given the randomness of the production, rules are random variables depending on the specific realization of rules. We adopt a *mean-field* or *annealed* approximation that neglects the fluctuations from the random choice of rules. Specifically, we approximate the upward message by the average upward message using the corresponding factor message $\langle \psi^{(1)}(y_i) \rangle_\psi$ over the possible realizations of $\psi$. In Section C.2, we show that $(\psi^{(1)}(y_i))_\psi$ can take only two values: one for $y = \tilde{y}$ and one for $y \neq \tilde{y}$, expected by symmetry considerations. Furthermore, means-$e'$. Introducing the probability of reconstructions $p = 1 - e + \epsilon/v$ and $p' = 1 - e' + \epsilon'/v$, we have

```
$p' = \frac{p^s + f\frac{m-1}{m}}{p^s + f(1-p^s)} = F(p).
```

Iterating this procedure across all the levels of the tree, we can compute the probability of recovering the correct class of the input. In particular, for large $L$, we are interested in studying the fixed $p^* = F(p^*)$ of the iteration map in Equation 73. As derived in Section C.2.1.1, when $sf > 1$, this map has a repulsive fixed point $p^* = 1$, which corresponds to $\epsilon = 0$, and an attractive fixed point $p^* = 1/v$, corresponding to $\epsilon = 1$. Thus, in this regime, referring the class from the noisy observation of the input is impossible.

PROBABILITIES OF RECONSTRUCTION

We begin by studying the upward process from the leaves. A true input tuple $\tilde{x}_1, \dots, \tilde{x}_n$ which is associated with the higher-level feature $\tilde{y}$. Given the randomness of the production, rules are random variables depending on the specific realization of rules. We adopt a *mean-field* or *annealed* approximation that neglects the fluctuations from the random choice of rules. Specifically, we approximate the upward message by the average upward message using the corresponding factor message $\langle \psi^{(1)}(y_i) \rangle_\psi$ over the possible realizations of $\psi$. In Section C.2, we show that $(\psi^{(1)}(y_i))_\psi$ can take only two values: one for $y = \tilde{y}$ and one for $y \neq \tilde{y}$, expected by symmetry considerations. Furthermore, means-$e'$. Introducing the probability of reconstructions $p = 1 - e + \epsilon/v$ and $p' = 1 - e' + \epsilon'/v$, we have

$p' = \frac{p^s + f\frac{m-1}{m}}{p^s + f(1-p^s)} = F(p)$.

Downward PROCESS

We begin by studying the upward process from the leaves. A true input tuple $\tilde{x}_1, \dots, \tilde{x}_n$ which is associated with the higher-level feature $\tilde{y}$. Given the randomness of the production, rules are random variables depending on the specific realization of rules. We adopt a *mean-field* or *annealed* approximation that neglects the fluctuations from the random choice of rules. Specifically, we approximate the upward message by the average upward message using the corresponding factor message $\langle \psi^{(1)}(y_i) \rangle_\psi$ over the possible realizations of $\psi$. In Section C.2, we show that $(\psi^{(1)}(y_i))_\psi$ can take only two values: one for $y = \tilde{y}$ and one for $y \neq \tilde{y}$, expected by symmetry considerations. Furthermore, means-$e'$. Introducing the probability of reconstructions $p = 1 - e + \epsilon/v$ and $p' = 1 - e' + \epsilon'/v$, we have

conditioning on the sampled class, and one latent variable $L-1$. We iterate this procedure node-by-node, descending the tree until we obtain a sampled configuration at the bottom layer.

EXPERIMENT ON CNN'S ACTIVATIONS

Similarly to experiment in 4.2, we investigate how the hidden representation of a model changes when input is denoised starting from corruption noise $\epsilon$. We consider the RHM with $v=32, s=2, L=10$. First, we train a convolutional neural network with $L=7$ layers, with 300k training examples. To sample new data from noisy observations, we start by sampling the root using the marginal probability computed with BP. Then, we update the beliefs and the marginals

## 4.6 CONCLUSIONS

![](img/86150bd6d44cb578b97e3eba954b7be2_86_0.png)

**Figure 10:** Probability that the latent has not changed the denoising process, corresponding to the largest marginal probability computed by BP, for each leaf, for inversion times of the diffusion process $t$. For the RHM with $v = 32, m = 8, s = 2, L = 10$. Each level of the tree, indicated in the legend, is represented with a different color. We observe the behavior of the correct class for ImageNet in Figure 5: the probability of the correct class has a sharp transition at a characteristic time scale, the probabilities corresponding to latent variables in the lower levels change smoothly.

We have argued that reversing in denoising diffusion models opens a window on the compositional nature of data. For synthetic hierarchical generative models of data, where the Bayes optimal denoising can be exactly computed, low-level features can change at small times, but the class remains often the same. At larger times, a phase transition is found where the probability of remaining in the same class suddenly drops to random chance. Strikingly, this theoretical analysis characterizes the results well with ImageNet, where the denoising is performed by a trained U-Net.
