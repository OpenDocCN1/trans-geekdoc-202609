
For optimization problems where we need to choose across probability distributions where `σ²` is a function of `μ`, we seek the distribution that maximizes $x_{CE} = \\mu - \\frac{a\\sigma^{2}}{2}$. This clearly illustrates the concept of “risk-adjusted-return” because `μ` serves as the “return” and the risk-adjustment $\\frac{a\\sigma^{2}}{2}$ is proportional to the product of risk-aversion `a` and risk (i.e., variance in outcomes) `σ²`.

## 7.6 A PORTFOLIO APPLICATION OF CARA

Let's say we are given $1 to invest and hold for a horizon of 1 year. Let's say our portfolio investment choices are:

*   A risky asset with Annual Return ∼ 𝒩(`μ`, `σ²`), `μ` ∈ ℝ, `σ` ∈ ℝ^+.

*   A riskless asset with Annual Return = `r` ∈ ℝ.

Our task is to determine the allocation `π` (out of the given $1) to invest in the risky asset (so, 1 − `π` is invested in the riskless asset) so as to maximize the Expected Utility of Consumption of Portfolio Wealth in 1 year. Note that we allow `π` to be unconstrained, i.e., `π` can be any real number from −∞ to +∞. So, if `π` > 0, we buy the risky asset and if `π` < 0, we “short-sell” the risky asset. Investing `π` in the risky asset means in 1 year, the risky asset's value will be a normal distribution 𝒩(`π`(1 + `μ`), `π²σ²`). Likewise, if 1 − `π` > 0, we lend 1 − `π` (and will be paid back (1 − `π`)(1 + `r`) in 1 year), and if 1 − `π` < 0, we borrow 1 − `π` (and need to pay back (1 − `π`)(1 + `r`) in 1 year).

Portfolio Wealth `W` in 1 year is given by:

$$
\begin{array}{r}
{\left. W \right.\sim\mathcal{N}(1 + r + \\pi(\\mu - r),\\pi^{2}\\sigma^{2})}
\\\\
\end{array}
$$

We assume CARA Utility with `a` ≠ 0, so:

$$
\begin{array}{r}
{U(W) = \\frac{1 - e^{- aW}}{a}}
\\\\
\end{array}
$$

We know that maximizing 𝔼[`U`(`W`)] is equivalent to maximizing the Certainty-Equivalent Value of Wealth `W`, which in this case (using the formula for `x`[*CE*] in the section on CARA) is given by:

$$
\begin{array}{r}
{1 + r + \\pi(\\mu - r) - \\frac{a\\pi^{2}\\sigma^{2}}{2}}
\\\\
\end{array}
$$

This is a quadratic concave function of `π` for `a` > 0, and so, taking its derivative with respect to `π` and setting it to 0 gives us the optimal investment fraction in the risky asset (`π`^(\*)) as follows:

$$
\begin{array}{r}
{\\pi^{\*} = \\frac{\\mu - r}{a\\sigma^{2}}}
\\\\
\end{array}
$$

## 7.7 CONSTANT RELATIVE RISK-AVERSION (CRRA)

Consider the Utility function `U`:ℝ^+→ℝ, parameterized by `γ` ∈ ℝ, defined as:

$$
\begin{array}{l}
{U(x) = \\left\\{ \\begin{array}{ll}
\\frac{x^{1 - \\gamma} - 1}{1 - \\gamma} & {\\text{~for~}\\gamma \\neq 1} \\\\
{\\log(x)} & {\\text{~for~}\\gamma = 1} \\\\
\\end{array}~ \\right.}
\\\\
\end{array}
$$

Firstly, note that `U`(`x`) is continuous with respect to `γ` for all `x` ∈ ℝ^+ since:

$$
\begin{array}{r}
{\\lim\\limits\\_{\\gamma\\rightarrow 1}\\frac{x^{1 - \\gamma} - 1}{1 - \\gamma} = \\log(x)}
\\\\
\end{array}
$$

Now let us analyze the function `U`(⋅) for any fixed `γ`. We note that for all `γ` ∈ ℝ:

*   `U`(1) = 0

*   `U`^′(`x`) = `x`^(−`γ`) > 0 for all `x` ∈ ℝ^+

*   `U`^(′′)(`x`) = −`γ` ⋅ `x`^(−1 − `γ`)

This means `U`(⋅) is a monotonically increasing function passing through (1, 0), and its curvature has the opposite sign as that of `γ` (note: no curvature when `γ` = 0).

So now we can calculate the Relative Risk-Aversion function:

$$
\begin{array}{r}
{R(x) = \\frac{- U^{\\prime\\prime}(x) \\cdot x}{U^{\\prime}(x)} = \\gamma}
\\\\
\end{array}
$$

So we see that the Relative Risk-Aversion function is the constant value `γ`. Consequently, we say that this Utility function corresponds to *Constant Relative Risk-Aversion (CRRA)*. The parameter `γ` is referred to as the Coefficient of CRRA. The magnitude of positive `γ` signifies the degree of risk-aversion. `γ` = 0 yields the Utility function `U`(`x`) = `x` − 1 and is the case of being Risk-Neutral. Negative values of `γ` mean one is “risk-seeking”, i.e., one will pay to take risk (the opposite of risk-aversion) and the magnitude of negative `γ` signifies the degree of risk-seeking.

If the random outcome `x` is lognormal, with log(`x`) ∼ 𝒩(`μ`, `σ²`), then making a substitution `y` = log(`x`), expressing 𝔼[`U`(`x`)] as 𝔼[`U`(`e`^(`y`))], and using Equation (A.5) in [Appendix A](#appA.xhtml#appA), we get:

$$
\begin{array}{l}
{\\mathbb{E}\\lbrack U(x)\\rbrack = \\left\\{ \\begin{array}{ll}
\\frac{e^{\\mu(1 - \\gamma) + \\frac{\\sigma^{2}}{2}{(1 - \\gamma)}^{2}} - 1}{1 - \\gamma} & {\\text{for~}\\gamma \\neq 1} \\\\
\\mu & {\\text{for~}\\gamma = 1} \\\\
\\end{array}~ \\right.}
\\\\
\end{array}
$$

$$
\begin{array}{r}
{x_{CE} = e^{\\mu + \\frac{\\sigma^{2}}{2}(1 - \\gamma)}}
\\\\
\end{array}
$$

$$
\begin{array}{r}
{\\text{Relative~Risk~Premium~}\\pi_{R} = 1 - \\frac{x_{CE}}{\\overline{x}} = 1 - e^{- \\frac{\\sigma^{2}\\gamma}{2}}}
\\\\
\end{array}
$$

For optimization problems where we need to choose across probability distributions where `σ²` is a function of `μ`, we seek the distribution that maximizes $\\log(x_{CE}) = \\mu + \\frac{\\sigma^{2}}{2}(1 - \\gamma)$. Just like in the case of CARA, this clearly illustrates the concept of “risk-adjusted-return” because $\\mu + \\frac{\\sigma^{2}}{2}$ serves as the “return” and the risk-adjustment $\\frac{\\gamma\\sigma^{2}}{2}$ is proportional to the product of risk-aversion `γ` and risk (i.e., variance in outcomes) `σ²`.

## 7.8 A PORTFOLIO APPLICATION OF CRRA

This application of CRRA is a special case of Merton's Portfolio Problem ([Merton 1969](#bib01.xhtml#refbib_44)) that we shall cover in its full generality in [Chapter 8](#chapter8.xhtml). This section requires us to have some basic familiarity with Stochastic Calculus (covered in [Appendix C](#appC.xhtml#appC)), specifically Ito Processes and Ito's Lemma. Here we consider the single-decision version of Merton's Portfolio Problem where our portfolio investment choices are:

*   A risky asset, evolving in continuous time, with value denoted `S`[*t*] at time `t`, whose movements are defined by the Ito process:

    $$
    \begin{array}{r}
    {dS\\_{t} = \\mu \\cdot S\\_{t} \\cdot dt + \\sigma \\cdot S\\_{t} \\cdot dz\\_{t}}
    \\\\
    \end{array}
    $$

    where `μ` ∈ ℝ, `σ` ∈ ℝ^+ are given constants, and `z`[*t*] is 1-dimensional standard Brownian Motion.

*   A riskless asset, growing continuously in time, with value denoted `R`[*t*] at time `t`, whose growth is defined by the ordinary differential equation:

    $$
    \begin{array}{r}
    {dR\\_{t} = r \\cdot R\\_{t} \\cdot dt}
    \\\\
    \end{array}
    $$

    where `r` ∈ ℝ is a given constant.

We are given $1 to invest over a period of 1 year. We are asked to maintain a constant fraction of investment of wealth (denoted `π` ∈ ℝ) in the risky asset at each time `t` (with 1 − `π` as the fraction of investment in the riskless asset at each time `t`). Note that to maintain a constant fraction of investment in the risky asset, we need to continuously rebalance the portfolio of the risky asset and riskless asset. Our task is to determine the constant `π` that maximizes the Expected Utility of Consumption of Wealth at the end of 1 year. We allow `π` to be unconstrained, i.e., `π` can take any value from −∞ to +∞. Positive `π` means we have a “long” position in the risky asset and negative `π` means we have a “short” position in the risky asset. Likewise, positive 1 − `π` means we are lending money at the riskless interest rate of `r` and negative 1 − `π` means we are borrowing money at the riskless interest rate of `r`.

We denote the Wealth at time `t` as `W`[*t*]. Without loss of generality, assume `W`[0] = 1. Since `W`[*t*] is the portfolio wealth at time `t`, the value of the investment in the risky asset at time `t` would need to be `π` ⋅ `W`[*t*] and the value of the investment in the riskless asset at time `t` would need to be (1 − `π`) ⋅ `W`[*t*]. Therefore, the change in the value of the risky asset investment from time `t` to time `t` + *d**t* is:
