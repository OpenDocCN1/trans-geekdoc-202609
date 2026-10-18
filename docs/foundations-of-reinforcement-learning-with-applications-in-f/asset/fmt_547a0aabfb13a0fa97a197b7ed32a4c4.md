
Certainty-Equivalent Value represents the certain amount we'd pay to consume an uncertain outcome. This is the amount of $180 you were willing to pay to play the casino game of the previous section.

[Figure 7.2](#chapter7.xhtml#fig7_2) illustrates this concept of Certainty-Equivalent Value in graphical terms. Next, we define Risk-Premium in two different conventions:

*   `Absolute Risk-Premium` `π[A]`:

    $$\\begin{array}{r} {\\pi\_{A} = \\mathbb{E}\\lbrack x\\rbrack - x\_{CE}} \\\\ \\end{array}$$  

*   `Relative Risk-Premium` `π[R]`:

    $$\\begin{array}{r} {\\pi\_{R} = \\frac{\\pi\_{A}}{\\mathbb{E}\\lbrack x\\rbrack} = \\frac{\\mathbb{E}\\lbrack x\\rbrack - x\_{CE}}{\\mathbb{E}\\lbrack x\\rbrack} = 1 - \\frac{x\_{CE}}{\\mathbb{E}\\lbrack x\\rbrack}} \\\\ \\end{array}$$  

![Figure 7.2 Certainty-Equivalent Value](images/fig7_2.jpg)

[Figure 7.2](#chapter7.xhtml#b7fig7_2) Certainty-Equivalent Value

Now we develop mathematical formalism to derive formulas for Risk-Premia `π[A]` and `π[R]` in terms of the extent of Risk-Aversion and the extent of Risk itself. To lighten notation, we refer to `𝔼[x]` as `x̄` and Variance of `x` as `σ[x]²`. We write `U(x)` as the Taylor series expansion around `x̄` and ignore terms beyond quadratic in the expansion, as follows:

$$\\begin{array}{r} {U(x) \\approx U(\\overline{x}) + U^{\\prime}(\\overline{x}) \\cdot (x - \\overline{x}) + \\frac{1}{2}U^{\\prime\\prime}(\\overline{x}) \\cdot {(x - \\overline{x})}^{2}} \\\\ \\end{array}$$  

Taking the expectation of `U(x)` in the above formula, we get:

$$\\begin{array}{r} {\\mathbb{E}\\lbrack U(x)\\rbrack \\approx U(\\overline{x}) + \\frac{1}{2} \\cdot U^{\\prime\\prime}(\\overline{x}) \\cdot \\sigma\_{x}^{2}} \\\\ \\end{array}$$  

Next, we write the Taylor-series expansion for `U(x[CE])` around `x̄` and ignore terms beyond linear in the expansion, as follows:

$$\\begin{array}{r} {U(x\_{CE}) \\approx U(\\overline{x}) + U^{\\prime}(\\overline{x}) \\cdot (x\_{CE} - \\overline{x})} \\\\ \\end{array}$$  

Since `𝔼[U(x)] = U(x[CE])` (by definition of `x[CE]`), the above two expressions are approximately the same. Hence,

$$\\begin{array}{r} {U^{\\prime}(\\overline{x}) \\cdot (x\_{CE} - \\overline{x}) \\approx \\frac{1}{2} \\cdot U^{\\prime\\prime}(\\overline{x}) \\cdot \\sigma\_{x}^{2}} \\\\ \\end{array}$$  

(7.1)

From Equation (7.1), Absolute Risk-Premium

$$\\begin{array}{r} {\\pi\_{A} = \\overline{x} - x\_{CE} \\approx - \\frac{1}{2} \\cdot \\frac{U^{\\prime\\prime}(\\overline{x})}{U^{\\prime}(\\overline{x})} \\cdot \\sigma\_{x}^{2}} \\\\ \\end{array}$$  

We refer to the function:

$$\\begin{array}{r} {A(x) = - \\frac{U^{\\prime\\prime}(x)}{U^{\\prime}(x)}} \\\\ \\end{array}$$  

as the `Absolute Risk-Aversion` function. Therefore,

$$\\begin{array}{r} {\\pi\_{A} \\approx \\frac{1}{2} \\cdot A(\\overline{x}) \\cdot \\sigma\_{x}^{2}} \\\\ \\end{array}$$  

In multiplicative uncertainty settings, we focus on the variance `σ_{x/x̄}²` of `x/x̄`. So in multiplicative settings, we focus on the Relative Risk-Premium:

$$\\begin{array}{r} {\\pi\_{R} = \\frac{\\pi\_{A}}{\\overline{x}} \\approx - \\frac{1}{2} \\cdot \\frac{U^{\\prime\\prime}(\\overline{x}) \\cdot \\overline{x}}{U^{\\prime}(\\overline{x})} \\cdot \\frac{\\sigma\_{x}^{2}}{{\\overline{x}}^{2}} = - \\frac{1}{2} \\cdot \\frac{U^{\\prime\\prime}(\\overline{x}) \\cdot \\overline{x}}{U^{\\prime}(\\overline{x})} \\cdot \\sigma\_{\\frac{x}{\\overline{x}}}^{2}} \\\\ \\end{array}$$  

We refer to the function

$$\\begin{array}{r} {R(x) = - \\frac{U^{\\prime\\prime}(x) \\cdot x}{U^{\\prime}(x)}} \\\\ \\end{array}$$  

as the `Relative Risk-Aversion` function. Therefore,

$$\\begin{array}{r} {\\pi\_{R} \\approx \\frac{1}{2} \\cdot R(\\overline{x}) \\cdot \\sigma\_{\\frac{x}{\\overline{x}}}^{2}} \\\\ \\end{array}$$  

Now let's take stock of what we've learning here. We've shown that Risk-Premium is proportional to the product of:

*   Extent of Risk-Aversion: either `A(x̄)` or `R(x̄)`

*   Extent of uncertainty of outcome (i.e., Risk): either `σ[x]²` or `σ_{x/x̄}²`

We've expressed the extent of Risk-Aversion to be proportional to the negative ratio of:

*   Concavity of the Utility function (at `x̄`): `- U''(x̄)`

*   Slope of the Utility function (at `x̄`): `U'(x̄)`

So for typical optimization problems in financial applications, we maximize `𝔼[U(x)]` (not `𝔼[x]`), which in turn amounts to maximization of `x[CE] = 𝔼[x] − π[A]`. If we refer to `𝔼[x]` as our “Expected Return on Investment” (or simply “Return” for short) and `π[A]` as the “risk-adjustment” due to risk-aversion and uncertainty of outcomes, then `x[CE]` can be conceptualized as “risk-adjusted-return”. Thus, in financial applications, we seek to maximize risk-adjusted-return `x[CE]` rather than just the return `𝔼[x]`. It pays to emphasize here that the idea of maximizing risk-adjusted-return is essentially the idea of maximizing expected utility, and that the utility function is a representation of an individual's risk-aversion.

Note that Linear Utility function `U(x) = a + b*x` implies `Risk-Neutrality` (i.e., when one doesn't demand any compensation for taking risk). Next, we look at typically-used Utility functions `U(⋅)` with:

*   Constant Absolute Risk-Aversion (CARA)

*   Constant Relative Risk-Aversion (CRRA)

## 7.5 CONSTANT ABSOLUTE RISK-AVERSION (CARA)

Consider the Utility function `U`:ℝ→ℝ, parameterized by `a` ∈ ℝ, defined as:

$$\\begin{array}{l} {U(x) = \\left\\{ \\begin{array}{ll} \\frac{1 - e^{- ax}}{a} & {\\text{~for~}a \\neq 0} \\\\ x & {\\text{~for~}a = 0} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  

Firstly, note that `U(x)` is continuous with respect to `a` for all `x` ∈ ℝ since:

$$\\begin{array}{r} {\\lim\\limits\_{a\\rightarrow 0}\\frac{1 - e^{- ax}}{a} = x} \\\\ \\end{array}$$  

Now let us analyze the function `U(⋅)` for any fixed `a`. We note that for all `a` ∈ ℝ:

*   `U(0) = 0`

*   `U'(x) = e^(−a*x) > 0` for all `x` ∈ ℝ

*   `U''(x) = −a ⋅ e^(−a*x)`

This means `U(⋅)` is a monotonically increasing function passing through the origin, and its curvature has the opposite sign as that of `a` (note: no curvature when `a` = 0).

So now we can calculate the Absolute Risk-Aversion function:

$$\\begin{array}{r} {A(x) = \\frac{- U^{\\prime\\prime}(x)}{U^{\\prime}(x)} = a} \\\\ \\end{array}$$  

So we see that the Absolute Risk-Aversion function is the constant value `a`. Consequently, we say that this Utility function corresponds to `Constant Absolute Risk-Aversion (CARA)`. The parameter `a` is referred to as the Coefficient of CARA. The magnitude of positive `a` signifies the degree of risk-aversion. `a` = 0 is the case of being Risk-Neutral. Negative values of `a` mean one is “risk-seeking”, i.e., one will pay to take risk (the opposite of risk-aversion) and the magnitude of negative `a` signifies the degree of risk-seeking.

If the random outcome `x` ∼ `𝒩(μ, σ²)`, then using Equation (A.5) from [Appendix A](#appA.xhtml#appA), we get:

$$\\begin{array}{l} {\\mathbb{E}\\lbrack U(x)\\rbrack = \\left\\{ \\begin{array}{ll} \\frac{1 - e^{- a\\mu + \\frac{a^{2}\\sigma^{2}}{2}}}{a} & {\\text{for~}a \\neq 0} \\\\ \\mu & {\\text{for~}a = 0} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  

$$\\begin{array}{r} {x\_{CE} = \\mu - \\frac{a\\sigma^{2}}{2}} \\\\ \\end{array}$$  

$$\\begin{array}{r} {\\text{Absolute~Risk~Premium~}\\pi\_{A} = \\mu - x\_{CE} = \\frac{a\\sigma^{2}}{2}} \\\\ \\end{array}$$  
