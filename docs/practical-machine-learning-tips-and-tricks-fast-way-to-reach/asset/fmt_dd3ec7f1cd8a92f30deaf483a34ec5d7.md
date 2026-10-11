
# 3.2.2 Prior

The earlier is chosen by human, not machines, so it is abstract. The subjectivity of the earlier is disputable. For instance, that a youngster and a number related teacher will reach dif Since the probability term relies dramatically upon `N`, and the earlier stays steady, as we get an ever increasing number of information, the MAP gauge combines towards the most extreme probability gauge or MLE:

```
hMLE ≜ arg max_h p(D|h) = arg max_h log p(D|h)  (3.6)
```

At the end of the day, assuming we have sufficient information, we see that the information overpowers the prior.

14 http://en.wikipedia.org/wiki/Occam%27s_razor

# 3.2.4 Posterior predictive distribution

The idea of back prescient distribution15 is ordinarily utilized in a Bayesian setting, where it utilizes the whole back appropriation of the boundaries given the noticed information to yield a likelihood circulation over a span rather than basically a point estimate.

```
p(x̃|D) = E_{h|D}[p(x̃|h)] = ∑_h p(x̃|h)p(h|D)  (3.7)
       = ∫ p(x̃|h)p(h|D)dh
```

This is only a weighted normal of the forecasts of every individual speculation and is called Bayes model averaging (Hoeting et al. 1999).

```
p(θ|Da,Db) = p(θ,Db|Da) / p(Da) ∝ p(θ,Db|Da)
           = p(Db,θ|Da)
           = p(Db|θ)p(θ|Da)
           = Bin(Nb1|θ, Nb1+Nb0) Beta(θ|Na1+a, Na0+b)
           = Beta(θ|Na1+Nb1+a, Na0+Nb0+b)  (3.10 and 2.19 combined)
```

This makes Bayesian surmising especially appropriate to internet learning, as we will see later.

# 3.3 The beta-binomial model

## 3.3.1 Likelihood

Given `X ~ Bin(θ)`, the probability of `D` is given by

```
p(D|θ) = Bin(N1|N,θ)  (3.8)
```

If we utilize a uniform earlier, then, at that point, the MAP gauge decreases to the MLE:

```
θ_MAP ∝ θ_MLE = N1/N  (3.13)
```

## 3.3.2 Prior

```
Beta(θ|a,b) ∝ θ^{a-1}(1-θ)^{b-1}  (3.9)
```

The boundaries of the earlier are called hyperparameters.

We will presently show that the back mean is curved blend of the earlier mean and the MLE, which catches the thought that the back is a trade off between what we recently accepted and what the information is telling us.

## 3.3.3 Posterior

```
p(θ|D) ∝ Bin(N1|N1+N0,θ) Beta(θ|a,b)
       = Beta(θ|N1+a, N0+b)  (3.10)
```

Note that refreshing the back consecutively is comparable to refreshing in a solitary cluster. To see this, assume we have two information sets `Da` and `Db` with adequate measurements `Na1, Na0` and `Nb1, Nb0`. Let `N1 = Na1+Nb1` and `N0 = Na0+Nb0` be the adequate measurements of the joined datasets. In clump mode we have

### 3.3.3.1 Posterior mean and mode

From Table 2.7, the back mean is given by

```
θ̄ = (a+N1) / (a+b+N)  (3.11)
```

The mode is given by

```
θ̂_MODE = (a+N1-1) / (a+b+N-2)  (3.12)
```

### 3.3.3.2 Posterior fluctuation

The mean and mode are point gauges, however it is helpful to know the amount we can trust them. The fluctuation of the back is one method for estimating this.

The difference of the Beta back is given by

```
var(θ|D) = (a+N1)(b+N0) / [(a+N1+b+N0)^2 (a+N1+b+N0+1)]  (3.14)
```

We can work on this imposing articulation for the situation that `N ≫ a,b`, to get

```
var(θ|D) ≈ N1 N0 / N^3 = θ̂_MLE (1 - θ̂_MLE) / N  (3.15)
```

15 http://en.wikipedia.org/wiki/Posterior_predictive_distribution

## 3.3.4 Posterior predictive distribution

```
Bb(x̃ | M, a, b) = B(x̃+a, M-x̃+b) / B(a,b)  (3.21)
```

So far, we have been zeroing in on induction of the obscure parameter(s). Let us presently direct our concentration toward expectation of future noticeable data. Consider foreseeing the likelihood of heads in a solitary future preliminary under a `Beta(a,b)` posterior. We have

```
p(x̃|D) = ∫_0^1 p(x̃|θ)p(θ|D)dθ
       = ∫_0^1 θ Beta(θ|a,b)dθ
       = E[θ|D] = a / (a+b)  (3.16)
```

This appropriation has the accompanying mean and fluctuation

```
mean = M a / (a+b)
var  = M a b (a+b+M) / [(a+b)^2 (a+b+1)]  (3.22)
```

This interaction is shown in Figure 3.1. We start with a `Beta(2,2)` earlier, and plot the back prescient thickness in the wake of seeing `N1 = 3` heads and `N0 = 17` tails. Figure 3.1(b) plots a module guess utilizing a MAP gauge. We see that the Bayesian expectation has longer tails, spreading its likelihood mass all the more broadly, and is thusly less inclined to overfitting and blackswan type paradoxes.

![Figure 3.1(a)](image_rsrc1R5.jpg)
![Figure 3.1(b)](image_rsrc1R6.jpg)

**Fig. 3.1:** (a) Posterior prescient dispersions in the wake of seeing `N1 = 3, N0 = 17`. (b) MAP estimation.

We perceive the necessary as the standardization consistent for a `Beta(x̃+a, M-x̃+b)` appropriation. Hence

```
∫_0^1 θ^{x̃}(1-θ)^{M-x̃} θ^{a-1}(1-θ)^{b-1} dθ = B(x̃+a, M-x̃+b)  (3.20)
```

Thus we find that the back prescient is given by the accompanying, known as the (compound) beta-binomial distribution:

### 3.3.4.1 Overfitting and the dark swan paradox

Let us presently infer a straightforward Bayesian answer for the issue. We will utilize a uniform earlier, so `a = b = 1`. For this situation, connecting the back mean gives Laplaces rule of succession

```
p(x̃|D) = (N1 + 1) / (N0 + N1 + 1)  (3.17)
```

This legitimizes the normal act of adding 1 to the experimental counts, normalizing and afterward connecting them, a method known as add-one smoothing. (Note that connecting the MAP boundaries would not have this smoothing impact, since the mode turns into the MLE if `a = b = 1`, see Section 3.3.3.1.)

### 3.3.4.2 Predicting the result of numerous future trials

Suppose now we were keen on foreseeing the quantity of heads, `x̃`, in `M` future preliminaries. This is given by

```
p(x̃|D) = ∫_0^1 Bin(x̃ | M,θ) Beta(θ|a,b) dθ  (3.18)
       = (M choose x̃) / B(a,b) ∫_0^1 θ^{x̃+a-1} (1-θ)^{M-x̃+b-1} dθ  (3.19)
```

# 3.4 The Dirichlet-multinomial model

In the past segment, we talked about how to derive the likelihood that a coin comes up heads. In this segment, we sum up these outcomes to induce the likelihood that a dice with `K` sides comes up as face `k`.

## 3.4.1 Likelihood

Suppose we notice `N` dice rolls, `D = {x1, x2, ..., xN}`, where `xi ∈ {1, 2, ..., K}`. The probability has the form

```
p(D|θ) = (N! / (N1! ... NK!)) ∏_{k=1}^K θ_k^{Nk}  (3.23)
```

where `Nk = ∑_{i=1}^N I(yi = k)` practically as old as 2.21.

## 3.4.2 Prior

```
Dir(θ|α) = (1/B(α)) ∏_{k=1}^K θ_k^{αk-1} I(θ ∈ S_K)  (3.24)
```

## 3.4.3 Posterior

```
p(θ|D) ∝ p(D|θ)p(θ)
       ∝ ∏_{k=1}^K θ_k^{Nk} ∏_{k=1}^K θ_k^{αk-1}
       = Dir(θ|α1+N1, ..., αK+NK)  (3.27)
```

From Equation 2.38, the MAP gauge is given by

```
θ̂_k = (Nk + αk - 1) / (N + α0 - K)  (3.28)
```

If we utilize a uniform earlier, `αk = 1`, we recuperate the MLE:

```
θ̂_k = Nk / N  (3.29)
```

## 3.4.4 Posterior predictive distribution

The back prescient conveyance for a solitary multinoulli preliminary is given by the accompanying expression:

```
p(X = j|D) = ∫ p(X = j|θ)p(θ|D)dθ  (3.30)
           = ∫ [∫ p(X = j|θj) p(θ_{-j}, θj|D) dθ_{-j}] dθj  (3.31)
           = ∫ θj p(θ|D) dθj = E[θj|D] = (αj + Nj) / (α0 + N)  (3.32)
```

where `θ_{-j}` are generally the parts of `θ` aside from `θj`. The above articulation evades the zero-include problem.

Truth be told, this type of Bayesian smoothing is significantly more significant in the multinomial case than the twofold case, since the probability of information sparsity increments once we begin apportioning the information into numerous categories.

# 3.5 Naive Bayes classifiers

Assume the elements are restrictively independent given the class name, then, at that point, the class contingent thickness has the accompanying form

```
p(x|y=c, θ) = ∏_{j=1}^D p(xj|y=c, θ_{jc})  (3.33)
```

The subsequent model is known as a guileless Bayes classifier (NBC). The type of the class-restrictive thickness relies upon the kind of each component. We give a few prospects below:

*   For the situation of genuine esteemed elements, we can utilize the Gaussian conveyance:
    `p(x|y,θ) = ∏_{j=1}^D N(xj | µ_{jc}, σ^2_{jc})`, where `µ_{jc}` is the mean of highlight `j` in objects of class `c`, and `σ^2_{jc}` is its variance.
*   For the situation of double elements, `xj ∈ {0,1}`, we can utilize the Bernoulli dissemination:
    `p(x|y,θ) = ∏_{j=1}^D Ber(xj | µ_{jc})`, where `µ_{jc}` is the likelihood that include `j` happens in class `c`. This is at times called the multivariate Bernoulli innocent Bayes model. We will see a utilization of this below.
