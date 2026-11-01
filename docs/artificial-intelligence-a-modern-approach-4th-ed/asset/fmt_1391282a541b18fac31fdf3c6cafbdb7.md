
## Structural Equations and Interventions

If all the `U-variables` are mutually independent random variables with suitably chosen priors, the joint distribution in [Equation (13.14)](#Chapter13-05.xhtml#eq13-14) can be represented exactly by the structural equations in [Equation (13.15)](#Chapter13-05.xhtml#eq13-15). Thus, a system of stochastic relationships can be captured by a system of deterministic relationships, each of which is affected by an exogenous disturbance. However, the system of structural equations gives us more than that: it allows us to predict how interventions will affect the operation of the system and hence the observable consequences of those interventions. This is not possible given just the joint distribution.

For example, suppose we turn the sprinkler on—that is, if we (who are, by definition, not part of the causal processes described by the model) intervene to impose the condition `Sprinkler=true`. In the notation of the `do-calculus`, which is a key part of the theory of causal networks, this is written as `do(Sprinkler = true)`. Once done, this means that the sprinkler variable is no longer dependent on whether it’s a cloudy day. We therefore delete the equation `S = fS(C, US)` from the system of structural equations and replace it with `S = true`, giving us

> **Do-calculus**

$\\begin{array}{l} {\\,\\, C\\ = \\ f\_{C}(U\_{C})} \\\\ {\\,\\, R\\ = \\ f\_{R}(C,U\_{R})} \\\\ {\\,\\, S\\ = \\ true} \\\\ {W\\ = \\ f\_{W}(R,S,U\_{W})} \\\\ {G\\ = \\ f\_{G}(W,U\_{G}).} \\\\ \\end{array}\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\begin{array}{l} \\\\ \\\\ {\\text{(13}\\text{.16)}} \\\\ \\\\ \\\\ \\end{array}$

From these equations, we obtain the new joint distribution for the remaining variables conditioned on `do(Sprinkler = true)`:

$\\begin{matrix} \\left. P(c,r,w,g \\middle| do(S = true))\\ = \\ P(c)\\ P(r \\middle| c)\\ P(w \\middle| r,\\ s = true)\\ P(g \\middle| w) \\right. & {\\text{(13}\\text{.17)}} \\\\ \\end{matrix}$

This corresponds to the “mutilated” network in [Figure 13.23(b)](#Chapter13-05.xhtml#fig13-23). From [Equation (13.17)](#Chapter13-05.xhtml#eq13-17), we see that the only variables whose probabilities change are `WetGrass` and `GreenerGrass`, that is, the descendants of the manipulated variable `Sprinkler`.

Note the difference between conditioning on the action `do(Sprinkler = true)` in the original network and conditioning on the observation `Sprinkler = true`. The original network tells us that the sprinkler is less likely to be on when the weather is cloudy, so if we observe the sprinkler to be on, that reduces the probability that the weather is cloudy. But common sense tells us that if we (operating from outside the world, so to speak) reach in and turn on the sprinkler, that doesn’t affect the weather or provide new information about what the weather is like that day. As shown in [Figure 13.23(b)](#Chapter13-05.xhtml#fig13-23), intervening breaks the normal causal link between the weather and the sprinkler. This prevents any influence flowing backward from `Sprinkler` to `Cloudy`. Thus, conditioning on `do(Sprinkler = true)` in the original graph is equivalent to conditioning on `Sprinkler = true` in the mutilated graph.

A similar approach can be taken to analyze the effect of `do(Xj = xjk)` in a general causal network with variables `X1,...,Xn`. The network corresponds to a joint distribution defined in the usual way (see [Equation (13.2)](#Chapter13-02.xhtml#eq13-2)):

$\\begin{matrix} {P\\text{(}x\_{1}\\text{,}\\ldots\\text{,}x\_{n}\\text{)~} = {\\prod\\limits\_{i = 1}^{n}\\left. P(x\_{i} \\middle| parents\\text{(}X\_{i}\\text{)}). \\right.}} & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\text{(13}\\text{.18)}} \\\\ \\end{matrix}$

After applying `do(Xj = Xjk)`, the new joint distribution `Pxjk` simply omits the factor for `Xj`:

$\\begin{matrix} {P\_{xjk}\\text{(}x\_{1}\\text{,}\\ldots\\text{,}x\_{n}\\text{)~} = \\left\\{ \\,\\begin{array}{l} {\\prod\_{i \\neq j}\\left. P(x\_{i} \\middle| parents\\text{(}X\_{i}\\text{)}) = \\frac{\\text{P(}x\_{1}\\text{,}\\ldots\\text{,}x\_{n}\\text{)}}{\\left. P(x\_{j} \\middle| parents\\text{(}X\_{j}\\text{)}) \\right.} \\right.} \\\\ 0 \\\\ \\end{array}\\,\\,\\,\\,\\,\\,\\,\\,\\,\\begin{array}{l} {\\text{if~}\\,\\,\\, x\_{j} = x\_{jk}} \\\\ {\\text{if~}\\,\\,\\,\\, x\_{j} \\neq x\_{jk}} \\\\ \\end{array} \\right.} & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\text{(13}\\text{.19)}} \\\\ \\end{matrix}$

This follows from the fact that setting `Xj` to a particular value `Xjk` corresponds to deleting the equation `Xj = fj(Parents(Xj), Uj)` from the system of structural equations and replacing it with `Xj = Xjk`. With a bit more algebraic manipulation, one can derive a formula for the effect of setting variable `Xj` on any other variable `Xi`:

$\\begin{array}{l} \\left. P(X\_{i}\\ = \\ x\_{i} \\middle| do(X\_{j} = x\_{jk})) = \\, P\_{x\\ jk}\\ (X\_{i} = x\_{i}) \\right. \\\\ {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, = \\,{\\sum\\limits\_{parents(X\_{j})}\\left. P(x\_{i} \\middle| x\_{jk},\\ parents(X\_{j}))P(parents(X\_{j})) \\right.}\\,.\\,\\,\\,\\,\\,\\,\\,(13.20)} \\\\ \\end{array}$

The probability terms in the sum are obtained by computation on the original network, by any of the standard inference algorithms. This equation is known as an adjustment formula; it is a probability-weighted average of the influence of `Xj` and its parents on `Xi`, where the weights are the priors on the parent values. The effects of intervening on multiple variables can be computed by imagining that the individual interventions happen in sequence, each one in turn deleting the causal influences on a variable and yielding a new, mutilated model.

> **Adjustment formula**

### 13.5.2 The back-door criterion

The ability to predict the effect of any intervention is a remarkable result, but it does require accurate knowledge of the necessary conditional distributions in the model, particularly `P(xj | parents(Xj))`. In many real-world settings, however, this is too much to ask. For example, we know that “genetic factors” play a role in obesity, but we do not know which genes play a role or the precise nature of their effects. Even in the simple story of Mary’s sprinkler decisions ([Figure 13.15](#Chapter13-03.xhtml#fig13-15), which also applies in [Figure 13.23(a)](#Chapter13-05.xhtml#fig13-23)), we might know that she checks the weather before deciding whether to turn on the sprinkler, but we might not know how she makes her decision.

The specific reason this is problematic in this instance is that we would like to predict the effect of turning on the sprinkler on a downstream variable such as `GreenerGrass`, but the adjustment formula ([Equation (13.20)](#Chapter13-05.xhtml#eq13-20)) must take into account not only the direct route from `Sprinkler`, but also the “back door” route via `Cloudy` and `Rain`. If we knew the value of `Rain`, this back-door path would be blocked—which suggests that there might be a way to write an adjustment formula that conditions on `Rain` instead of `Cloudy`. And indeed this is possible:

$\\begin{matrix} \\left. P\\text{(}g \\middle| do\\text{(}S = true\\text{))} = {\\sum\\limits\_{r}\\left. P(g \\middle| S = true,\\ r)P(r) \\right.} \\right. & {\\text{(13}\\text{.21)}} \\\\ \\end{matrix}$

In general, if we wish to find the effect of `do(Xj = xjk)` on a variable `Xi`, the back-door criterion allows us to write an adjustment formula that conditions on any set of variables `Z` that closes the back door, so to speak. In more technical language, we want a set `Z` such that `Xi` is conditionally independent of `Parents(Xj)` given `Xj` and `Z`. This is a straightforward application of `d-separation` (see [page 437](#Chapter13-02.xhtml#page_437)).

> **Back-door criterion**
