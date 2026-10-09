```
x <- as.simple_triplet_matrix(we8thereCounts)
tpc <- topics(x,K=10)
```

Here, we’ve fit a ten-topic model. You can also give `topics` a range of $K$ values and let it choose the best number using a *Bayes factor* (BF) criterion that is closely related to the BIC. The BF is proportional to the *posterior model probability* approximated by $\exp[-\mathrm{BIC}]$, so whereas you want to minimize the BIC, you will want to maximize the BF.

```
> tpcs <- topics(x,K=5*(1:5))
Estimating on a 6166 document collection.
Fit and Bayes Factor Estimation for K = 5 ... 25
log BF( 5 ) = 86639.7
log BF( 10 ) = 99317.15
log BF( 15 ) = 13398.18
log BF( 20 ) = -55807.93
> dim(tpcs$omega)
[1] 6166   10
```

Given $K$ of 5, 10, 15, 20, or 25, `topics` chooses$_{10}$ the BF maximizing $K=10$. I have generally advised against putting too much faith in this sort of selection for unsupervised models. However, since topic models are so expensive to fit, it is convenient to have a fast search strategy. In my experience, the BF maximization in `maptpe` finds $K$ that will perform well for a variety of downstream tasks, although it does sometimes tend to select $K$ smaller than we would like for storytelling purposes. If you are going to use the topics as inputs to a lasso regression, analogous to the lasso PCR, then you can use a larger $K$ and let the lasso choose the ones it needs.

Interpretation for topics proceeds the same as for PCA; you work from bottom up and top down to build a narrative. Bottom up, you look at “top” words for each topic. For this to work, you need to take care in how you order words when looking at the “top.” Ordering words by topic probability, $\theta_{ki}$, will yield top words that are common in topic $k$ but, potentially, also common in other topics (especially when you’ve cut only a small set of stop words). Instead, the `summary` function in `maptpe` orders words by *lift*—the probability of word $j$ in topic $k$ divided by its aggregate probability:

$\mathrm{lift}_{jk} = \theta_{jk} / \bar{q}_{j}$