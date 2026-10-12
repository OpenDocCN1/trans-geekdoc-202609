
![Figure 18.4 Marginal distributions. a) Given an initial density Pr(x) (top row), the diffusion process gradually blurs the distribution as it passes through the latent variables zt and moves it toward a standard normal distribution. Each subsequent horizontal line of heatmap represents a marginal distribution q(zt). b) The top graph shows the initial distribution Pr(x). The other two graphs show the marginal distributions q(z20) and q(z60), respectively.](images/c18-fig-0004.jpg)

[Figure 18.4](#c018.xhtml#c18-fig-0004a) Marginal distributions. a) Given an initial density `Pr(x)` (top row), the diffusion process gradually blurs the distribution as it passes through the latent variables `z[t]` and moves it toward a standard normal distribution. Each subsequent horizontal line of heatmap represents a marginal distribution `q(z[t])`. b) The top graph shows the initial distribution `Pr(x)`. The other two graphs show the marginal distributions `q(z[20])` and `q(z[60])`, respectively.

However, since we now have an expression for the diffusion kernel `q(z[t]|x)` that "skips" the intervening variables, we can equivalently write:

![c18-fig-5012.jpg](images/c18-fig-5012.jpg)

 (18.10)

Hence, if we repeatedly sample from the data distribution `Pr(x)` and superimpose the diffusion kernel `q(z[t]|x)` on each sample, the result is the marginal distribution `q(z[t])` ([figure 18.4](#c018.xhtml#c18-fig-0004)). However, the marginal distribution cannot be written in closed form because we don't know the original data distribution `Pr(x)`.

***

Notebook 18.1

Diffusion encoder

***

### 18.2.3 Conditional distribution `q(z[t−1]|z[t])`

We defined the conditional probability `q(z[t]|z[t−1])` as the mixing process (equation 18.2). To reverse this process, we apply Bayes' rule:

![c18-fig-5013.jpg](images/c18-fig-5013.jpg)

 (18.11)

***

Appendix C.1.4

Bayes' rule

***

This is intractable since we cannot compute the marginal distribution `q(z[t−1])`.

For this simple 1D example, it's possible to evaluate `q(z[t−1]|z[t])` numerically ([figure 18.5](#c018.xhtml#c18-fig-0005)). In general, their form is complex, but in many cases, they are well-approximated by a normal distribution. This is important because when we build the decoder, we will approximate the reverse process using a normal distribution.

![Figure 18.5 Conditional distribution q(zt−1|zt). a) The marginal densities q(zt) with three points c18-fig-5014.jpg highlighted. b) The probability c18-fig-5015.jpg (cyan curves) is computed via Bayes' rule and is proportional to c18-fig-5016.jpg. In general, it is not normally distributed (top graph), although often the normal is a good approximation (bottom two graphs). The first likelihood term c18-fig-5017.jpg is normal in zt−1 (equation 18.2) with a mean that is slightly further from zero than c18-fig-5018.jpg (brown curves). The second term is the marginal density q(zt−1) (gray curves).](images/c18-fig-0005.jpg)

[Figure 18.5](#c018.xhtml#c18-fig-0005a) Conditional distribution `q(z[t−1]|z[t])`. a) The marginal densities `q(z[t])` with three points ![c18-fig-5014.jpg](images/c18-fig-5014.jpg) highlighted. b) The probability ![c18-fig-5015.jpg](images/c18-fig-5015.jpg) (cyan curves) is computed via Bayes' rule and is proportional to ![c18-fig-5016.jpg](images/c18-fig-5016.jpg). In general, it is not normally distributed (top graph), although often the normal is a good approximation (bottom two graphs). The first likelihood term ![c18-fig-5017.jpg](images/c18-fig-5017.jpg) is normal in `z[t−1]` (equation 18.2) with a mean that is slightly further from zero than ![c18-fig-5018.jpg](images/c18-fig-5018.jpg) (brown curves). The second term is the marginal density `q(z[t−1])` (gray curves).

### 18.2.4 Conditional diffusion distribution `q(z[t−1]|z[t], x)`

There is one final distribution related to the encoder to consider. We noted above that we could not find the conditional distribution `q(z[t−1]|z[t])` because we do not know the marginal distribution `q(z[t−1])`. However, if we know the starting variable `x`, then we *do* know the distribution `q(z[t−1]|x)` at the time before. This is just the diffusion kernel ([figure 18.3](#c018.xhtml#c18-fig-0003)), and it is normally distributed.

Hence, it is possible to compute the conditional diffusion distribution `q(z[t−1]|z[t], x)` in closed form ([figure 18.6](#c018.xhtml#c18-fig-0006)). This distribution is used to train the decoder. It is the distribution over `z[t−1]` when we know the current latent variable `z[t]` and the training data example `x` (which, of course, we do when training). To compute an expression for `q(z[t−1]|z[t], x)` we start with Bayes' rule:

![c18-fig-5024.jpg](images/c18-fig-5024.jpg)

 (18.12)

where between the first two lines, we have used the fact that `q(z[t]|z[t−1], x) = q(z[t]|z[t−1])` because the diffusion process is Markov, and all information about `z[t]` is captured by `z[t−1]`. Between lines three and four, we use the Gaussian change of variables identity:

![c18-fig-5025.jpg](images/c18-fig-5025.jpg)

 (18.13)

***

Appendix C.3.4

Gaussian change of variables

***

to rewrite the first distribution in terms of `z[t−1]`. We then use a second Gaussian identity:

![c18-fig-5026.jpg](images/c18-fig-5026.jpg)

 (18.14)

***

Problems 18.4–18.5

***

to combine the two normal distributions in `z[t−1]`, which gives:

![c18-fig-5027.jpg](images/c18-fig-5027.jpg)

 (18.15)

***

Problem 18.6

***

Note that the constants of proportionality in equations 18.12, 18.13, and 18.14 must cancel out since the final result is already a correctly normalized probability distribution.

![Figure 18.6 Conditional distribution q(zt−1|zt, x). a) Diffusion kernel for x\* = −2.1 with three points c18-fig-5019.jpg highlighted. b) The probability c18-fig-5020.jpg is computed via Bayes' rule and is proportional to c18-fig-5021.jpg. This is normally distributed and can be computed in closed form. The first likelihood term c18-fig-5022.jpg is normal in zt−1 (equation 18.2) with a mean that is slightly further from zero than c18-fig-5023.jpg (brown curves). The second term is the diffusion kernel q(zt−1|x\*) (gray curves).](images/c18-fig-0006.jpg)

[Figure 18.6](#c018.xhtml#c18-fig-0006a) Conditional distribution `q(z[t−1]|z[t], x)`. a) Diffusion kernel for `x* = −2.1` with three points ![c18-fig-5019.jpg](images/c18-fig-5019.jpg) highlighted. b) The probability ![c18-fig-5020.jpg](images/c18-fig-5020.jpg) is computed via Bayes' rule and is proportional to ![c18-fig-5021.jpg](images/c18-fig-5021.jpg). This *is* normally distributed and can be computed in closed form. The first likelihood term ![c18-fig-5022.jpg](images/c18-fig-5022.jpg) is normal in `z[t−1]` (equation 18.2) with a mean that is slightly further from zero than ![c18-fig-5023.jpg](images/c18-fig-5023.jpg) (brown curves). The second term is the diffusion kernel `q(z[t−1]|x*)` (gray curves).

## 18.3 Decoder model (reverse process)

When we learn a diffusion model, we learn the *reverse process*. In other words, we learn a series of probabilistic mappings back from latent variable `z[T]` to `z[T−1]`, from `z[T−1]` to `z[T−2]`, and so on, until we reach the data `x`. The true reverse distributions `q(z[t−1]|z[t])` of the diffusion process are complex multi-modal distributions ([figure 18.5](#c018.xhtml#c18-fig-0005)) that depend on the data distribution `Pr(x)`. We approximate these as normal distributions:

![c18-fig-5028.jpg](images/c18-fig-5028.jpg)

 (18.16)
