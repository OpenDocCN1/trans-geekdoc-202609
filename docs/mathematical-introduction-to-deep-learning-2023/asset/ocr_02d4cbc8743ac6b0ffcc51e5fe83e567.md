# Chapter 13

# Strong generalization error estimates

In Chapter 12 above we reviewed generalization error estimates in the probabilistic sense. Besides such probabilistic generalization error estimates, generalization error estimates in the strong $L^p$-sense are also considered in the literature and in our overall error analysis in Chapter 15 below we employ such strong generalization error estimates. These estimates are precisely the subject of this chapter (cf. Corollary 13.3.3 below).

We refer to the beginning of Chapter 12 for a short list of references in the literature dealing with similar generalization error estimates. The specific material in this chapter mostly consists of slightly modified extracts from Jentzen & Weliti [230, Section 4].

# 13.1 Monte Carlo estimates

**Proposition 13.1.1.** Let $d, M \in \mathbb{N}$, let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $X_j: \Omega \rightarrow \mathbb{R}^d$, $j \in \{1, 2, \dots, M\}$, be independent random variables, and assume $\max_{j \in \{1, 2, \dots, M\}} \mathbb{E}[\|X_j\|_2] < \infty$ (cf. Definition 3.3.4). Then

```
$\begin{align*}
&\left(\mathbb{E}\left[\|\frac{1}{M} \sum_{j=1}^{M} X_j - \mathbb{E}\left[\frac{1}{M} \sum_{j=1}^{M} X_j\right]\right]_2^2\right)^{1/2} \\
&\leq \frac{1}{\sqrt{M}}\left[\max_{j \in \{1, 2, \dots, M\}} \left(\mathbb{E}\left[\|X_j - \mathbb{E}[X_j]\|_2^2\right]\right)^{1/2}\right].
\end{align*} \tag{13.1}$
```

*Proof of Proposition 13.1.1.* Observe that the fact that for all $x \in \mathbb{R}^d$ it holds that $\langle x, x \rangle =$