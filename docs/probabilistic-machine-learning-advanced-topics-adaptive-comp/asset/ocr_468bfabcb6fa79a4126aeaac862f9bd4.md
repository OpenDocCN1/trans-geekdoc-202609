# 4.4.3.2 General case

In the general case, a CRF can be written as follows:

```
p(\boldsymbol{y}|\boldsymbol{x};\boldsymbol{\theta}) = \frac{\exp(f(\boldsymbol{x}, \boldsymbol{y};\boldsymbol{\theta}))}{Z(\boldsymbol{x}; \boldsymbol{\theta})} = \frac{\exp(f(\boldsymbol{x}, \boldsymbol{y};\boldsymbol{\theta}))}{\sum_{\boldsymbol{y}'} \exp(f(\boldsymbol{x}, \boldsymbol{y}';\boldsymbol{\theta}))} \tag{4.147}
```

where \(f(\boldsymbol{x}, \boldsymbol{y};\boldsymbol{\theta})\) is a scoring (negative energy) function, where high scores correspond to probable configurations. The gradient of the log likelihood is

```
\(\nabla_\theta \ell(\boldsymbol{\theta}) = \frac{1}{N} \sum_{n=1}^N \nabla_\theta f(\boldsymbol{x}_n, \boldsymbol{y}_n; \boldsymbol{\theta}) - \nabla_\theta \log Z(\boldsymbol{x}_n; \boldsymbol{\theta}) \tag{4.148}\)
```

Computing derivatives of the log partition function is intractable provided we can compute the corresponding expectations, as we discuss in Section 4.3.9.2. Note, however, that we need to compute these derivatives for every training example, which is slower than the MRF case, where the log partition function is a constant independent of the observed data (but dependent on the model parameters).

# 4.4.4 Other approaches to structured prediction

Many other approaches to structured prediction have been proposed, going beyond CRFs. For example, **max margin Markov networks** [TGK03], and the closely relied **structural support vector machine** [Tso+05], can be seen as non-probabilistic alternatives to CRFs. More recently, [BYM17] proposed **structured prediction energy networks**, which are a form of energy based model (Chapter 24), where we predict using an optimization procedure, \(\hat{\boldsymbol{y}}(\boldsymbol{x}) = \text{argmin}_\boldsymbol{y} \mathcal{E}(\boldsymbol{x}, \boldsymbol{y})\). In addition, it is common to use graph neural networks (Section 16.3.6) and sequence-to-sequence models such as transformers (Section 16.3.5) for this task.

# 4.5 Comparing directed and undirected PGMs

In this section, we compare DPGMs and UPGMs in terms of their modeling power, we discuss how to convert from one to the other, and we and present a unified representation.

# 4.5.1 CI properties

Which model has more “expressive power”, a DPGM or a UPGM? To formalize the question, recall from Section 4.2.4 that \(G\) is an I-map of a distribution \(p\) if \(I(G) \subseteq I(p)\), meaning that all the CI statements encoded by the graph \(G\) are true of the distribution \(p\). Now define \(G\) to be **perfect map** of \(p\) if \(I(G) = I(p)\), in other words, the graph can represent all (and only) the CI properties of the distribution. It turns out that DPGMs and UPGMs are perfect maps for different sets of distributions (see Figure 4.36). In this sense, neither is more powerful than the other as a representation language.

As an example of some CI relationships that can be perfectly modeled by a DPGM but not a UPGM, consider a v-structure \(A \rightarrow C \leftarrow B\). This asserts that \(A \perp B\), and \(A \not\perp B | C\). If we drop the arrows, we get \(A - C - B\), which asserts \(A \perp B | C\) and \(A \not\perp B\), which is not consistent with the independence statements encoded by the DPGM. In fact, there is no UPGM that can precisely