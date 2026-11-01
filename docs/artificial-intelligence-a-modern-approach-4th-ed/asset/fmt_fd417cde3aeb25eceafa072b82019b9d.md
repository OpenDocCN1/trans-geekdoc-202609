
$\\begin{matrix} \\left. P(y \\middle| x) = \\frac{1}{\\sigma\\sqrt{2\\pi}}e^{- \\frac{{(y - (\\theta\_{1}x + \\theta\_{2}))}^{2}}{2\\sigma\_{2}}}. \\right. & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,(12.5)} \\\\ \\end{matrix}$

Here, the parameters are `θ1`, `θ2`, and `σ`. The data are a collection of (`xj`, `yj`) pairs, as illustrated in [Figure 21.4](#Chapter21-02.xhtml#fig21-4). Using the usual methods (Exercise 21.LINR), we can find the maximum-likelihood values of the parameters. The point here is different. If we consider just the parameters `θ1` and `θ2` that define the linear relationship between x and y, it becomes clear that maximizing the log likelihood with respect to these parameters is the same as minimizing the numerator (`y` – (`θ1`x + `θ2`))2 in the exponent of [Equation (21.5)](#Chapter21-02.xhtml#eq21-5). This is the L2 loss, the squared error between the actual value `y` and the prediction `θ1`x + `θ2`.

Description
Seven rectangular nodes from left to right are labeled 5, 6, 6, 2, 5, 6, and 5. Three circular nodes are present. Arrows labeled plus 1, minus 1, and plus 1 from blocks 1, 2, and 3 point to the first circular node. The output of the first circular node is 5. Arrows labeled plus 1, minus 1, and plus 1 from blocks 3, 4, and 5 point to the second circular node. The output of the second circular node is 9. Arrows labeled plus 1, minus 1, and plus 1 from blocks 5, 6, and 7 point to the third circular node. The output of the third circular node is 4.

×![](images/Fig-308.jpg)

Figure 21.4(a) A linear–Gaussian model described as y = `θ1`x + `θ2` plus Gaussian noise with fixed variance. (b) A set of 50 data points generated from this model and the best-fit line.

This is the quantity minimized by the standard linear regression procedure described in [Section 19.6](#Chapter19-06.xhtml#sec19-6). Now we can understand why: minimizing the sum of squared errors gives the maximum-likelihood straight-line model, provided that the data are generated with Gaussian noise of fixed variance.

## 21.2.5 Bayesian parameter learning

Maximum-likelihood learning gives rise to simple procedures, but it has serious deficiencies with small data sets. For example, after seeing one cherry candy, the maximum-likelihood hypothesis is that the bag is 100% cherry (i.e., `θ` = 1.0). Unless one’s hypothesis prior is that bags must be either all cherry or all lime, this is not a reasonable conclusion. It is more likely that the bag is a mixture of lime and cherry. The Bayesian approach to parameter learning starts with a hypothesis prior and updates the distribution as data arrive.

The candy example in [Figure 21.2(a)](#Chapter21-02.xhtml#fig21-2) has one parameter, `θ`: the probability that a randomly selected piece of candy is cherry-flavored. In the Bayesian view, `θ` is the (unknown) value of a random variable `Θ` that defines the hypothesis space; the hypothesis prior is the prior distribution over `P(Θ)`. Thus, `P(Θ=θ)` is the prior probability that the bag has a fraction `θ` of cherry candies.

If the parameter `θ` can be any value between 0 and 1, then `P(Θ)` is a continuous probability density function (see [Section A.3](#Appendix-A-03.xhtml#secA-3)). If we don’t know anything about the possible values of `θ` we can use the uniform density function `P(θ) = Uniform(θ;0,1)`, which says all values are equally likely.

A more flexible family of probability density functions is known as the beta distributions. Each beta distribution is defined by two hyperparameters[3](#Chapter21-05.xhtml#sup21-3) `a` and `b` such that

<p class="sidebar">Beta distribution</p> <p class="sidebar">Hyperparameter</p>

$\\begin{matrix} {Beta(\\theta;a,b)\\ = \\alpha\\,\\theta^{a - 1}{(1 - \\theta)}^{b - 1},} & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\text{(21}\\text{.6)}} \\\\ \\end{matrix}$

for `θ` in the range \[0, 1\]. The normalization constant `α`, which makes the distribution integrate to 1, depends on `a` and `b`. [Figure 21.5](#Chapter21-02.xhtml#fig21-5) shows what the distribution looks like for various values of `a` and `b`. The mean value of the beta distribution is `a/ (a + b)`, so larger values of `a` suggest a belief that `Θ` is closer to 1 than to 0. Larger values of `a + b` make the distribution more peaked, suggesting greater certainty about the value of `Θ`. It turns out that the uniform density function is the same as `Beta(1, 1)`: the mean is 1/2, and the distribution is flat.

Description
Three rows of nodes are shown. The bottom row contains nine rectangular nodes. One rectangular node on each side is faded. The second and eighth rectangular nodes are blue-colored. The remaining five rectangular nodes are red-colored. The middle row contains nine circular nodes. One circular node on each side is faded. The second, third, seventh, and eighth circular nodes are blue-colored. The remaining three circular nodes are red-colored. The top row contains seven circular nodes. The fourth circular node is red-colored. The remaining six circular nodes are blue-colored. Three arrows from each red-colored rectangular node, two arrows from each blue-colored rectangular node, and one arrow from each faded rectangular node point to the nodes in the middle row. Three arrows from each of the middle five circular nodes, two arrows from the second and seventh nodes, and one arrow from the faded nodes point to the top row. The arrows from red-colored nodes to red-colored nodes are colored red.

×![](images/Fig-309.jpg)

Figure 21.5Examples of the Beta(a, b) distribution for different values of (a, b).

Besides its flexibility, the beta family has another wonderful property: if `Θ` has a prior `Beta(a, b)`, then, after a data point is observed, the posterior distribution for `Θ` is also a beta distribution. In other words, `Beta` is closed under update. The beta family is called the conjugate prior for the family of distributions for a Boolean variable.[4](#Chapter21-05.xhtml#sup21-4) Let’s see how this works. Suppose we observe a cherry candy; then we have

<p class="sidebar">Conjugate prior</p>

$\\begin{array}{l} \\left. P(\\theta \\middle| D\_{1} = cherry) \\right. \\\\ \\\\ \\\\ \\end{array}\\,\\,\\begin{array}{l} = \\\\ = \\\\ = \\\\ \\end{array}\\,\\,\\begin{array}{l} \\left. \\alpha\\, P(D\_{1} = cherry \\middle| \\theta)P(\\theta) \\right. \\\\ {\\alpha'\\theta \\cdot Beta\\,(\\theta;a,b) = \\alpha'\\theta \\cdot \\theta^{a - 1}{(1 - \\theta)}^{b - 1}} \\\\ {\\alpha'\\theta^{a}{(1 - \\theta)}^{b - 1} = \\alpha'Beta(\\theta;a + 1,b).} \\\\ \\end{array}$

<p class="sidebar">Virtual count</p>

Thus, after seeing a cherry candy, we simply increment the `a` parameter to get the posterior; similarly, after seeing a lime candy, we increment the `b` parameter. Thus, we can view the `a` and `b` hyperparameters as virtual counts, in the sense that a prior `Beta(a, b)` behaves exactly as if we had started out with a uniform prior `Beta(1, 1)` and seen `a – 1` actual cherry candies and `b – 1` actual lime candies.

By examining a sequence of beta distributions for increasing values of `a` and `b`, keeping the proportions fixed, we can see vividly how the posterior distribution over the parameter `Θ` changes as data arrive. For example, suppose the actual bag of candy is 75% cherry. [Figure 21.5(b)](#Chapter21-02.xhtml#fig21-5) shows the sequence `Beta(3, 1)`, `Beta(6, 2)`, `Beta(30, 10)`. Clearly, the distribution is converging to a narrow peak around the true value of `Θ`. For large data sets, then, Bayesian learning (at least in this case) converges to the same answer as maximum-likelihood learning.

Now let us consider a more complicated case. The network in [Figure 21.2(b)](#Chapter21-02.xhtml#fig21-2) has three parameters, `θ`, `θ1`, and `θ2`, where `θ1` is the probability of a red wrapper on a cherry candy and `θ2` is the probability of a red wrapper on a lime candy. The Bayesian hypothesis prior must cover all three parameters—that is, we need to specify `P(Θ, Θ1, Θ2)`. Usually, we assume parameter independence:
