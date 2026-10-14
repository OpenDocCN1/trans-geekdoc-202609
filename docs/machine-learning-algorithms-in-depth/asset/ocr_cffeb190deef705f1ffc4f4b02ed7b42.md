Here, the expectations under q of log θ and log β are as follows.

E_q[log θ_dk] = Ψ(γ_dk) − Ψ(∑_{i=1}^K γ_di)

E_q[log β_kw] = Ψ(λ_kw) − Ψ(∑_{i=1}^W λ_ki)      (9.9)

The variational parameter updates can be used in an online setting that does not require a full pass through the entire corpus at each iteration. An online update of variational parameters enables topic analysis for very large datasets, including streaming data. Online variational Bayes (VB) for LDA is described in the algorithm in figure 9.2.

+   1: Define ρ_t = (τ₀ + t)^{-κ}
+   2: Initialize λ randomly
+   3: for t = 1 to ∞ do
+   4: E step:
+   5: Initialize γ_ik = 1
+   6: repeat
+   7: Set φ_{twk} ∝ exp{E_q[log θ_{tk}] + E_q[log β_{kw}]} ← Topic assignments
+   8: Set γ_{ik} = α + Σ_{w} φ_{twk} n_{tw} ← Topic proportions
+   9: until 1/K Σ_k |Δγ_{ik}| < ε
+   10: M step:
+   11: Compute 	ilde λ_{kw} = η + D n_{tw} φ_{twk}
+   12: Set λ = (1 − ρ_t) λ + ρ_t 	ilde λ
+   13: end for

# Figure 9.2 LDA algorithm pseudo-code

As the t-th vector of word counts n_t is observed, we perform an E step to find locally optimal values of γ_t and φ_t, holding λ fixed. We then compute the 	ilde λ that would be optimal if our entire corpus consisted of the single document n repeated D times. We then update λ as a weighted average of its previous value and 	ilde λ, where the weight is given by the learning parameter ρ_t for κ ∈ (0.5, 1], controlling the rate at which old values of 	ilde λ are forgotten. We are now ready to implement variational Bayes for LDA from scratch in the following listing!

# Listing 9.1 Variational Bayes for latent Dirichlet allocation

```
import numpy as np
import matplotlib.pyplot as plt
from sklearn.datasets import fetch_20newsgroups
from sklearn.feature_extraction.text import TfidfVectorizer
from wordcloud import WordCloud
from scipy.special import digamma, gammaln
```