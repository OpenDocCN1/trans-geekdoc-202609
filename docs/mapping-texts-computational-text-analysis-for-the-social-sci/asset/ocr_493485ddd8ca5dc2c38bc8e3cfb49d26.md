percentile, for instance, and a “1” otherwise. We can also take a statistical approach by finding the *network backbone*.

The backbone is a subset of the network created by the “significant” ties. For a weighted network, it is an unweighted network “preserv[ing] only those [ties] whose weights are sufficiently large” (Neal 2014:84). Finding the backbone for a weighted network that is the one-mode projection of a bipartite graph (such as a DTM) is tricky. The backbone algorithms tailored to “native” one-mode weighted networks do not account for the bipartite nature when deciding to retain a tie (Neal 2014:84). Though backbone algorithms for weighted bipartite graphs exist (e.g., Neal 2017), DTMs tend to make convergence difficult (if not impossible, in some cases). So, we’ll use a document-similarity matrix (DSM) created as the document-level projection of a DTM.

We’ll do so with the *disparity filter* (Serrano et al. 2009). This filtering mechanism draws on a “statistical significance” test. So, we must choose a significance level, or “alpha” ($\alpha$).$^{37}$ For us, the null hypothesis is that any tie weight between two documents is as good as random.

$^{37}$ Alpha is the probability below which we are willing to reject a null hypothesis when, in fact, it is true.

Let $i$ and $j$ be any two documents in the corpus and $D$ be a document in the DSM. For each document $i$, we normalize its tie weights so the sum of its tie weights equals 1. We then create a simulation of $D_i$ (call it $D'_i$) where (1) $i$’s degree and neighborhood (i.e., set of alters) are the same as in $D_i$, and (2) the tie weights are pulled from a uniform distribution and normalized so that each tie weight has the same probability. The distribution of these tie weights for $D'_i$ reflects a null hypothesis that any given weight attached to one of $i$’s ties is random.$^{38}$

$^{38}$ Specifically, the probability of the weight for the $ij$ tie is no different from the probability of the weight attached to any of $i$’s other ties.

$^{39}$ That is, “statistically significant.”

We then find the probability of getting a tie weight *at least as large* as the one we observe between $i$ and $j$ if the null hypothesis were true. This is known as a right-tailed $p$-value. If the $p$-value is smaller than our significance level,$^{39}$ then it is unlikely we would observe the $ij$ tie weight if it was just as likely as any other tie weight in $i$’s neighborhood. This also means the tie gets a “1” in the unweighted backbone network, and otherwise a “0.” We repeat this process for every tie in the network.

$^{40}$ We’ll preprocess our text by transliterating to Basic Latin, removing URLs, HTML, punctuation, and excess whitespace, and then replacing contractions and ordinal numbers.

We’ll use a sample from news articles mentioning “immigration” in the All the News (ATN) corpus. For expediency, let’s also limit ourselves to 400 articles.$^{40}$

```
data("corpus_atn_immigr", package = "textmap.corpora")
set.seed(2063)
df_atn <- corpus_atn_immigr |> sample_n(size = 400)
```