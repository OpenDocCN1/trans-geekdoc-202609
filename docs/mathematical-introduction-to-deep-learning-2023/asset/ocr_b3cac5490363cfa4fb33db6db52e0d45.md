# # Chapter 15

# # Composed error estimates

In Part **II** we have established several estimates for the approximation error, in Part **III** we have established several estimates for the optimization error, and in Part **IV** we have established several estimates for the generalization error. In this chapter we employ the error decomposition from Chapter **14** as well as parts of Parts **II, III**, and **IV** (see Proposition **4.4.12** and Corollaries **11.3.9** and **13.3.3**) to establish estimates for the overall error in the training of **ANNs** in the specific situation of **GD**-type optimization methods with many independent random initializations.

In the literature such overall error analyses can, for instance, be found in [25, 226, 230]. The material in this chapter consist of slightlyly modified extracts from Jentzen & Welti [230, Sections 6.2 and 6.3].

# ## 15.1 Full strong error analysis for the training of ANNs

**Lemma 15.1.1.** *Let* $d, \mathbf{d}, \mathbf{L} \in \mathbb{N}$, $\mathbf{l} = (\mathbf{l}_0, \mathbf{l}_1, \dots, \mathbf{l}_{\mathbf{L}}) \in \mathbb{N}^{\mathbf{L}+1}$, $u \in [-\infty, \infty)$, $v \in (u, \infty]$, *let* $D \subseteq \mathbb{R}^d$, *assume*

$\mathbf{l}_0 = d, \qquad \mathbf{l}_{\mathbf{L}} = 1, \qquad \text{and} \qquad \mathbf{d} \ge \sum_{i=1}^{\mathbf{L}} \mathbf{l}_i (\mathbf{l}_{i-1} + 1), \tag{15.1}$

*let* $\mathcal{E} \colon D \to \mathbb{R}$ *be* $\mathcal{B}(D) / \mathcal{B}(\mathbb{R})$-measurable, *let* $(\Omega, \mathcal{F}, \mathbb{P})$ *be a probability space*, *and let* $X \colon \Omega \to D$, $\mathbf{k} \colon \Omega \to (\mathbb{N}_0)^2$, *and* $\Theta_{k,n} \colon \Omega \to \mathbb{R}^{\mathbf{d}}$, $k, n \in \mathbb{N}_0$, *be random variables. Then*

+   (i) *it holds that* $\mathbb{R}^{\mathbf{d}} \times \mathbb{R}^{\mathbf{d}} \ni (\theta, x) \mapsto \mathcal{N}_{u,v}^{\Theta, \mathbf{l}}(x) \in \mathbb{R}$ *is* $(\mathcal{B}(\mathbb{R}^{\mathbf{d}}) \otimes \mathcal{B}(\mathbb{R}^{\mathbf{d}})) / \mathcal{B}(\mathbb{R})$-measurable,

+   (ii) *it holds for all* $\omega \in \Omega$ *that* $\mathbb{R}^{\mathbf{d}} \ni x \mapsto \mathcal{N}_{u,v}^{\Theta_{k,n}(\omega), \mathbf{l}}(x) \in \mathbb{R}$ *is* $\mathcal{B}(\mathbb{R}^{\mathbf{d}}) / \mathcal{B}(\mathbb{R})$-measurable, *and*

+   (iii) *it holds for all* $p \in [0, \infty)$ *that*

$\Omega \ni \omega \mapsto \int_D |\mathcal{N}_{u,v}^{\Theta_{k,n}(\omega), \mathbf{l}}(x) - \mathcal{E}(x)|^p \, \mathbb{P}_X(\mathrm{d}x) \in [0, \infty[ \tag{15.2}$