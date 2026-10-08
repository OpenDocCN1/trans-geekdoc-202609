# # Chapter 12

# # Probabilistic generalization error estimates

In Chapter $15$ below we establish a full error analysis for the training of **ANNs** in the specific situation of **GD**-type optimization methods with many independent random initializations (see Corollary $15.2.3$). For this combined error analysis we do not only employ estimates for the approximation error (see Part **II** above) and the optimization error (see Part **III** above) but we also employ suitable generalization error estimates. Such generalization error estimates are the subject of this chapter (cf. Corollary $12.3.10$ below) and the next (cf. Corollary $13.3.3$ below). While in this chapter, we treat probabilistic generalization error estimates, in Chapter we will present generalization error estimates in the strong $L^{p}$-sense.

In the literature, related generalization error estimates can, for instance, be found in the survey articles and books $[25, 35, 36, 87, 373]$ and the references therein. The specific material in Section $12.1$ is inspired by Duchi $[116]$ , the specific material in Section $12.2$ is inspired by Cucker & Smale $[87, \ S e c t i o n$ 6 in Chapter I] and Carl & Stephani $[61,$ Section 1.1], and the specific presentation of Section $12.3$ is strongly based on Beck et al. $[25,$ Section 3.2].

# ## 12.1 Concentration inequalities for random variables

# ### 12.1.1 Markov's inequality

**Lemma 12.1.1** (Markov inequality). *Let $(\Omega,\mathcal{F},\mu)$ be a measure space, let $X: \Omega \rightarrow [0,\infty)$* ***be $\mathcal{F} / \mathcal{B}([0,\infty))$-measurable, and let $\varepsilon \in (0,\infty)$. Then***

```
$$\mu(X \geq \varepsilon) \leq \frac{\int_{\Omega} X d \mu}{\varepsilon} \tag{12.1}$$
```