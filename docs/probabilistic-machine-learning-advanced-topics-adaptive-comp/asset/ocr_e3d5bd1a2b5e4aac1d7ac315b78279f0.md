where $\mathbf{N}_j = (N_{j1}, \dots, N_{jK})$ are the counts for leaving state $j$ and $B(\boldsymbol{\alpha})$ is the generalized beta function.

We can fit this using the methods discussed in [Min00c]. However, we can also use the following approximation [MP95, p12]:

```
$m_k \propto |\{j : N_{jk} > 0\}|$
```

This says that the prior probability of word $k$ is given by the number of different contexts in which it occurs, rather than the number of times it occurs. To justify the reasonableness of this result, MacKay and Peto [MP95] give the following example.

> Imagine, you see, that the language, you see, has, you see, a frequently occurring couplet 'you see', you see, in which the second word of the couplet, see, follows the first word, you, with very high probability, you see. Then the marginal statistics, you see, are going to become hugely dominated, you see, by the words you and see, with equal frequency, you see.

If we use the standard smoothing formula, Equation (3.270), then P(you|novel) and P(see|novel), for some novel context word not seen before, would turn out to be the same, since the marginal frequencies of 'you' and 'see' are the same (11 times each). However, this seems unreasonable. 'You' appears in many contexts, so P(you|novel) should be high, but 'see' only follows 'you', so P(see|novel) should be low. If we use the Bayesian formula Equation (3.273), we will get this effect for free, since we back off to $m_k$ not $f_k$, and $m_k$ will be large for 'you' and small for 'see' by Equation (3.276).

Although elegant, this Bayesian model does not beat the state-of-the-art language model, known as interpolated Kneser-Ney [KN95; CG98]. By using ideas from nonparametric Bayes, one can create a language model that outperforms such heuristics, as discussed in [Teh06; Woo+09]. However, one can get even better results using recurrent neural nets (Section 16.3.4); the key to their success is that they don't treat each symbol "atomically", but instead learn a distributed embedding representation, which encodes the assumption that some symbols are more similar to each other than others.

# 3.7.4 EB for non-conjugate models

For more complex models, we cannot compute the EB estimate exactly. However, we can use the variational EM method to compute an approximate EB estimate, as we explain in Section 10.1.3.2.

# 3.8 Model selection

> All models are wrong, but some are useful. — George Box [BD87, p424].

In this section, we assume we have a set of different models $\mathcal{M}$, each of which may fit the data to different degrees, and each of which may make different assumptions. We discuss how to pick the best model from this set, or to average over all of them.

We assume the "true" model is in the set $\mathcal{M}$; this is known as the $\mathcal{M}$-**complete** assumption [BS94]. Of course, in reality, none of the models may be adequate; this is known as the $\mathcal{M}$-**open** scenario

9. George Box is a retired statistics professor at the University of Wisconsin.