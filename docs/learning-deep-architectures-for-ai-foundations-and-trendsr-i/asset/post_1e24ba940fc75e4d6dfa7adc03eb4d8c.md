
## 5.4 Contrastive Divergence

is therefore a special case of product of experts model: the $i$-th term $\log \sum_{\mathbf{h}} e^{(c_i;W,\mathbf{x})h_i}$ in Equation (5.21) corresponds to an expert, i.e., there is one expert per hidden neuron and one for the input offset. With that special, a very efficient Gibbs sampling can be performed. For $k$ Gibbs steps, starting from a training example (i.e., sampling from $\hat{P}$):

$$\mathbf{x}_1 \sim \hat{P}(\mathbf{x})$$
$$\mathbf{h}_1 \sim P(\mathbf{x}_1)$$
$$\mathbf{x}_2 \sim P(\mathbf{h}_1)$$
$$\mathbf{h}_{k+1} \sim P(\mathbf{h}_k). \quad (5.26)$$

It makes sense to start the chain from a training example because the model becomes better at capturing the structure in the training data, the model distribution $P$ and the training distribution $\hat{P}$ become more similar (having similar statistics). Note that if we started the chain from $\hat{P}$ itself, it would have converged in one step, so starting from $\hat{P}$ is a good way to ensure that only a few steps are necessary for convergence.

Contrastive Divergence is an approximation of the log-likelihood gradient that has found to be a successful update rule for training RBMs [31]. A pseudo-code is shown in Algorithm 1, with the particular equations for the conditional distributions for the case of binary input and hidden units.

### 5.4.1 Justifying Contrastive Divergence

To obtain this algorithm, the **first approximation** we are going to make replace the average over all possible inputs (in the second term of Equation (5.10)) by a single sample. Since we update the parameters often (e.g., with stochastic or mini-batch gradient updates after one or a few training examples), there is some averaging going on across updates (which we know to well [105]), and the extra variance introduced by taking one or a few MCMC samples...

#### Algorithm 1: RBMUpdate(x1, $\epsilon$, W, b, c)

This is the RBM update procedure for binomial units. It can easily adapted to other types of units.

- $x_1$ is a sample from the training distribution for the RBM
- $\epsilon$ is a learning rate for the stochastic gradient descent in Contrastive Divergence
- $W$ is the RBM weight matrix, of dimension (number of hidden units, number of inputs)
- $b$ is the RBM offset vector for input units
- $c$ is the RBM offset vector for hidden units
- Notation: $Q(h_2=1|x_2)$ is the vector with elements $Q(h_2=1|x_1)$

- for hidden units $i$ do:
  - compute $Q(h_{1i}=1|x_1)$ (for binomial units, $\sigma(c_i+\sum_j W_{ij}x_{1j}))$
  - sample $h_{1i} \in \{0,1\}$ from $Q(h_{1i}|x_1)$
- end
- for visible units $j$ do:
  - compute $P(x_{2j}=1|h_1)$ (for binomial units, $\sigma(b_j+\sum_i W_{ij}h_{1i}))$
  - sample $x_{2j} \in \{0,1\}$ from $P(x_2=1|h_1)$
- end
- for hidden units $i$ do:
  - compute $Q(h_{2i}=1|x_2)$ (for binomial units, $\sigma(c_i+\sum_j W_{ij}x_{2j}))$
- $W \leftarrow W + \epsilon(h_1x_1' - Q(h_2=1|x_2)x_2')$
- $b \leftarrow b + \epsilon(x_1 - x_2)$
- $c \leftarrow c + \epsilon(h_1 - Q(h_2=1|x_2))$

Running a long MCMC chain is very expensive. The idea of k-step Contrastive Divergence (CD-$k$) [69, 70] is simple, and involves a **second approximation**, which introduces some bias in the gradient: run the MCMC chain $x_1, x_2, \dots, x_{k+1}$ for $k$ steps starting from the observed example $x_1 = x$. The CD-$k$ update (i.e., the log-likelihood gradient) after sampling $\tilde{x}$, is,

$$\Delta \theta = \frac{\partial FreeEnergy(x)}{\partial \theta} - \frac{\partial FreeEnergy(\tilde{x})}{\partial \theta} \quad (5.27)$$

where $\tilde{x} = x_{k+1}$ is the last sample from our Markov chain, obtained after $k$ steps. We know that when $k \to \infty$, the bias goes away. We also know when the model distribution is very close to the empirical distribution, i.e., $P \approx \hat{P}$, then we start the chain from $x$ (a sample from $P$) MCMC has already converged, and we need only one step to obtain an unbiased sample from $P$ (although it would still be correlated with $x$).

The surprising empirical result is that even $k=1$ (CD-1) often gives good results. An extensive numerical comparison of training with CD-$k$ versus log-likelihood gradient has been presented in [31]. In these experiments, taking $k$ larger than 1 gives more results, although very good approximations of the solution can be obtained with $k=1$. Theoretical results [12] discussed in Section 5.4.3 help to understand why small values of $k$ can work: CD-$k$ corresponds to a series that converges to the log-likelihood gradient.

One way to interpret Contrastive Divergence is that it is approximating the log-likelihood gradient *locally* around the training point $x_1$. The stochastic reconstruction $\tilde{x} = x_{k+1}$ has a distribution centered around $x_1$ and becomes more spread out as $k$ increases. The CD-$k$ update will decrease the free energy of the training point $x_1$ (which would increase its likelihood if all were constant), and increase the free energy of $\tilde{x}$, which is that $\tilde{x}$ is in the neighborhood of $x_1$, but at the same time more likely to be in regions of high probability under the model (especially for larger $k$). As argued by [106], what is mostly needed from the training algorithm for an energy-based model is that it makes the energy (free energy, here marginalizing hidden variables) of observed inputs smaller, pushing “energy” elsewhere, and most importantly in areas of low energy. The Contrastive Divergence algorithm is fueled by the contrast between the statistics collected when the input is a real training example and when the input is a chain sample. As argued in the next section, one can think of the unsupervised learning problem as discovering a surface that can roughly separate the regions of high probability (where there are many training examples) from the rest. Therefore, we want to penalize the model when it generates examples on the wrong side, and a good way to identify where it should be moved is to compare training examples with samples from the model.

### 5.4.2 Alternatives to Contrastive Divergence

Exciting recent development in the research on learning algorithms for RBMs is use of persistent MCMC for the negative phase [161, 187], following an approach already introduced in [135]. The idea is simple: keep a MCMC chain $x_t \rightarrow h_t \rightarrow x_{t+1} \rightarrow h_{t+1} \dots$ to obtain the negative phase samples (which should be from the model). Instead of running a short chain as in CD-$k$, the approximation is made to ignore the fact that parameters are changing as we move along the chain, i.e., we do not run a separate chain for each value of the parameters (as in the traditional Boltzmann learning algorithm). Maybe because the parameters move slowly, the approximation works well, usually giving rise to better log-likelihood than CD-k (experiments against $k=1$). The trade-off with CD-1 is that the variance is larger but the bias is smaller. Something also happens [185]: the model systematically moves away from the samples obtained in the negative phase, and this interacts with the chain itself, preventing it from staying in the same region long, substantially improving the mixing rate of the chain. This is a very desirable and unforeseen effect, which helps explore more quickly the space of RBM configurations.

Another alternative to Contrastive Divergence [84, 85, 86] is a general approach to train energy-based models in which the energy can be computed tractably, but not the normalization constant $Z$. The score function of the density $p(x)=q(x)/Z$ is $\psi=\nabla \log p(x)$, and we exploit the fact that the score function of our model does not depend on its normalization constant, i.e., $\psi=\nabla \log q(x)$. The basic idea is to match the score function of the model with the score function of the empirical density. The average (under the empirical density) of the square norm of the difference between the two functions can be written in squares of the model score function and second derivatives $(\partial^2 q(\mathbf{x}))/\partial\mathbf{x}$. Score matching has been shown to be locally consistent [84], converging if the model family matches the data generating process, and it has been used for unsupervised models of image and audio data [94].

### 5.4.3 Truncations of the Log-Likelihood Gradient in Gibbs-Chain Models

Here, we approach the Contrastive Divergence update rule from a different perspective, which gives rise to possible generalizations of it and links it to the reconstruction error often used to monitor its performance and that is used to optimize autoencoders (Equation (4.7)). The inspiration for this derivation comes from [73]; first from the idea (explained in Section 8.1) the Gibbs chain can be associated with an infinite directed graphical model (where we associate with an expansion of the log-likelihood gradient), and second that the convergence of the chain justifies Contrastive Divergence (since the expected value of Equation (5.27) becomes equivalent to Equation (5.9) when the chain sample $\mathbf{x}$ comes from the model). In particular, we are interested in clarifying and understanding the bias in the Contrastive Divergence update rule, compared to using the true (intractable) gradient of the log-likelihood.

Consider a converging Markov chain $\mathbf{x}_t \Rightarrow \mathbf{h}_t \Rightarrow \mathbf{x}_{t+1} \Rightarrow \dots$ defined by conditional distributions $P(\mathbf{h}_t|\mathbf{x}_t)$ and $P(\mathbf{x}_{t+1}|\mathbf{h}_t)$, with $\mathbf{x}_1$ sampled from the training data empirical distribution. The following theorem,
