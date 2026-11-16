
the meaning of a particular word. This is illustrated in Figure 28.4, where a subset of the words are annotated with the topic to which they were assigned (i.e., we show \(\text{argmax}_k p(c_{nl} = k | x_n)\). In the first document, the word “music” makes it clear that the musical topic (number 77) is present in the document, which in turn makes it more likely that \(c_{nl} = 77\) where \(l\) is the index corresponding to the word “play”.

### 28.1.1.3 Posterior inference

Many algorithms have been proposed to perform approximate posterior inference in the LDA model. In the original LDA paper, [BNJ03], they use variational mean field inference (see **??**), and in [HBB10], they use stochastic VI (see Section 28.1.6). In Section 28.1.5 we discuss the collapsed Gibbs sampler, which marginalizes out the discrete latents. In [MB16; SS17] they discuss how to learn amortized inference networks to perform VI for the collapsed model.

Recently, there has been considerable interest in spectral methods for fitting LDA-like models which are fast and which come with provable guarantees about the quality of the solution they obtain (unlike MCMC and variational methods, where the solution is just an approximation of unknown quality). These methods make certain (reasonable) assumptions beyond the basic model, such as the existence of some anchor words, which uniquely the topic for a document. See [Aro+13] for details.

### 28.1.1.4 Determining the number of topics

Choosing \(N_z\), the number of topics, is a standard model selection problem. Here are some approaches that have been taken:

- Use annealed importance sampling (**??**) to approximate the evidence [Wal+09].
- Cross validation, using the log likelihood on a test set.
- Use the variational lower bound as a proxy for \(\log p(\mathcal{D}|N_z)\).
- Use non-parametric Bayesian methods [Teh+06].

### 28.1.2 Correlated topic model

One weakness of LDA is that it cannot capture correlation between topics. For example, if a document has the “business” topic, it is reasonable to expect the “finance” topic to co-occur. The source of the problem is the use of a Dirichlet prior for \(z_n\). The problem with the Dirichlet is that it is characterized by just a mean vector \(\alpha\), but its covariance is fixed (\(\Sigma_{ij} = -\alpha_i\alpha_j\)), rather than being a free parameter.

One way around this is to replace the Dirichlet prior with the **logistic normal distribution**, which is defined as follows:

```
\(p(z) = \int \text{Cat}(z|\mathcal{S}(\epsilon))\mathcal{N}(\epsilon|\mu, \Sigma)d\epsilon\) (28.3)
```

This is known as the **correlated topic model** [BL07]:

The difference from categorical PCA discussed in **??** is that CTM uses a logistic normal to model the mean parameters, so \(z_n\) is sparse and non-negative, whereas CatPCA uses a normal to model the natural parameters, so \(z_n\) is dense and can be negative. More precisely, the CTM defines \(x_{nl} \sim \text{Cat}(\mathbf{W}\mathcal{S}(\epsilon_n))\), but CatPCA defines \(x_{nd} \sim \text{Cat}(\mathcal{S}(\mathbf{W}_d z_n))\).

Fitting the CTM model is tricky, since the prior for \(\epsilon_n\) is no longer conjugate to the multinomial likelihood for \(c_{nl}\). However, we can derive a variational mean field approximation, as described in [BL07].

Having fit the model, one can then convert \(\hat{\Sigma}\) to a sparse precision matrix \(\hat{\Sigma}^{-1}\) by pruning low-strength edges, to get a sparse Gaussian graphical model. This allows you to visualize the correlation between topics. Figure 28.5 shows the result of applying this procedure to articles from *Science* magazine, from 1990-1999.

### 28.1.3 Dynamic topic model

In LDA, the topics (distributions over words) are assumed to be static. In some cases, it makes sense to allow these distributions to evolve smoothly over time. For example, an article might use the topic “neuroscience”, but if it was written in the 1900s, it is more likely to use words like “nerve”, whereas if it was written in the

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_146_0.png)

Figure 28.5: Output of the correlated topic model (with K = 50 topics) when applied to articles from Science. Nodes represent topics, with the 5 most probable phrases from each topic shown inside. Font size reflects overall prevalence of the topic. See http://www.cs.cmu.edu/~lemur/science/ for an interactive version of this model with 100 topics. Used with kind permission of Figure 2 of [BL07]. Used with kind permission of David Blei.

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_146_1.png)

Figure 28.6: The dynamic topic model as a PGM-D.

2000s, it is more likely to use words like “calcium receptor” (this reflects the general trend of neuroscience towards molecular biology).

One way to model this is to assume the topic distributions evolve according to a Gaussian random walk, as in a state space model (see ??). We can map these Gaussian vectors to probabilities via the softmax function, resulting in the following model:

```
$$\begin{aligned} w_k^t | w_k^{t-1} \sim \mathcal{N}(w_{t-1,k}, \sigma^2 1_{N_w}) \quad (28.4) \\ z_k^t \sim \text{Dir}(\alpha 1_{N_z}) \quad (28.5) \\ c_{nl}^t | z_n^t \sim \text{Cat}(z_n^t) \quad (28.6) \\ x_{nl}^t | c_{nl}^t = k, W^t \sim \text{Cat}(S(w_k^t)) \quad (28.7) \end{aligned}$$
```

This is known as a **dynamic topic model** [BL06a]. See Figure 28.6 for the PGM-D.

One can perform approximate inference in this model using a structured mean field method (**??**), that exploits the Kalman smoothing algorithm (**??**) to perform exact inference on the linear-Gaussian chain between the $w_k^t$ nodes (see [BL06a] for details). See the main text for an example of this model applied to 100 years of articles from Science.

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_147_0.png)

Figure 28.7: LDA-HMM model as a PGM-D.

It is also possible to use amortized inference, and to learn embeddings for each word, which works much better with rare words. This is called the **dynamic embedded topic model** [DRB19].

### 28.1.4 LDA-HMM

The Latent Dirichlet Allocation (LDA) model of Section 28.1.1 assumes words are exchangeable, and thus ignores word order. A simple way to model sequential dependence between words is to use an HMM. The trouble with HMMs is that they can only model short-range dependencies, so they cannot capture the overall gist of a document. Hence they can generate syntactically correct sentences, but not semantically plausible ones.

It is possible to combine LDA with HMM to create a model called **LDA-HMM** [Gri+04]. This model uses the HMM states to model function or syntactic words, such as “and” or “however”, and uses the LDA to model content or semantic words, which are harder to predict. There is a distinguished HMM state which specifies when the LDA model should be used to generate the word; the rest of the time, the HMM generates the word.

More formally, for each document n, the model defines an HMM with states $h_{nl} \in \{0, \dots, H\}$. In addition, each document has an LDA model associated with it. If $h_{nl} = 0$, we generate word $x_{nl}$ from the semantic LDA model, with topic specified by $c_{nl}$; otherwise we generate word $x_{nl}$ from the syntactic HMM model. The PGM-D is shown in Figure 28.7. The CPDs are as follows:

$p(\mathbf{z}_n) = \text{Dir}(\mathbf{z}_n|\alpha\mathbf{1}_{N_z}) \quad (28.8)$
$p(c_{nl} = k|\mathbf{z}_n) = z_{nk} \quad (28.9)$
$p(h_{n,l} = j|h_{n,l-1} = i) = A_{ij} \quad (28.10)$
$p(x_{nl} = d|c_{nl} = k, h_{nl} = j) = \begin{cases} W_{kd} & \text{if } j = 0 \\ B_{jd} & \text{if } j > 0 \end{cases} \quad (28.11)$

where **W** is the usual topic-word matrix, **B** is the state-word HMM emission matrix and **A** is the state-state HMM transition matrix.

Inference in this model can be done with collapsed Gibbs sampling, analytically integrating out all the continuous quantities. See [Gri+04] for the details.

The results of applying this model (with $N_z = 200$ LDA topics and $H = 20$ HMM states) to the combined Brown and TASA corpora^2 are shown in Table 28.1. We see that the HMM generally is responsible for

2The Brown corpus consists of 500 documents and 1,137,466 word tokens, with part-of-speech tags for each token. The TASA corpus is an untagged collection of educational materials consisting of 37,651 documents and 12,190,931 word tokens. Words appearing in fewer than 5 documents were replaced with an asterisk, but punctuation was included. The combined vocabulary was of size 37,202 unique words.
