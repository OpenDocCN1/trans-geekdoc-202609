
$$\\begin{array}{r} {SP = {\\sum\\limits\_{j = 0}^{m}\\theta\_{j}^{\*}} \\cdot S\_{j}^{(0)} = \\sup\\limits\_{\\lambda}L(\\lambda) = \\sup\\limits\_{\\lambda}\\inf\\limits\_{\\theta}J(\\theta,\\lambda)} \\\\ \\end{array}$$  

Complementary Slackness and some linear algebra over the space of risk-neutral probability measures `π`:`Ω`→\[0,1\] enables us to argue that:

$$\\begin{array}{r} {SP = \\sup\\limits\_{\\pi}{\\sum\\limits\_{i = 1}^{n}\\frac{\\pi(\\omega\_{i})}{1 + r}} \\cdot V\_{D}^{(i)}} \\\\ \\end{array}$$  

This means the Superhedging Price is the least upper-bound of the riskless rate-discounted expectation of derivative payoff across each of the risk-neutral probability measures in the incomplete market, which is quite an intuitive thing to do amidst multiple risk-neutral probability measures.

Likewise, the `Subhedging` price `SB` is defined as:

$$\\begin{array}{r} {\\max\_{\\theta}{\\sum\\limits\_{j = 0}^{m}\\theta\_{j}} \\cdot S\_{j}^{(0)}\\text{~such~that~}{\\sum\\limits\_{j = 0}^{m}\\theta\_{j}} \\cdot S\_{j}^{(i)} \\leq V\_{D}^{(i)}\\text{~for~all~}i = 1,\\ldots,n} \\\\ \\end{array}$$  

Likewise arguments enable us to establish:

$$\\begin{array}{r} {SB = \\inf\\limits\_{\\pi}{\\sum\\limits\_{i = 1}^{n}\\frac{\\pi(\\omega\_{i})}{1 + r}} \\cdot V\_{D}^{(i)}} \\\\ \\end{array}$$  

This means the Subhedging Price is the highest lower-bound of the riskless rate-discounted expectation of derivative payoff across each of the risk-neutral probability measures in the incomplete market, which is quite an intuitive thing to do amidst multiple risk-neutral probability measures.

So this technique provides an lower bound (`SB`) and an upper bound (`SP`) for the derivative price, meaning:

*   A price outside these bounds leads to an arbitrage

*   Valid prices must be established within these bounds

But often these bounds are not tight and so, not useful in practice.

The alternative approach is to identify hedges that maximize Expected Utility of the combination of the derivative along with its hedges, for an appropriately chosen market/trader Utility Function (as covered in [Chapter 7](#chapter7.xhtml)). The Utility function is a specification of reward-versus-risk preference that effectively chooses the risk-neutral probability measure (and hence, Price).

Consider a concave Utility function `U`:ℝ→ℝ applied to the Value in each random outcome `ω`[*i*], `i` = 1, …`n`, at `t` = 1 (e.g., $U(x) = \\frac{1 - e^{- ax}}{a}$ where `a` ∈ ℝ is the degree of risk-aversion). Let the real-world probabilities be given by `μ`:`Ω`→\[0,1\]. Denote `V`[*D*] = (`V`[*D*]^((1)), …, `V`[*D*]^((`n`))) as the payoff of Derivative `D` at `t` = 1. Let us say that you buy the derivative `D` at `t` = 0 and will receive the random outcome-contingent payoff `V`[*D*] at `t` = 1. Let `x` be the candidate derivative price for `D`, which means you will pay a cash quantity of `x` at `t` = 0 for the privilege of receiving the payoff `V`[*D*] at `t` = 1. We refer to the candidate hedge as Portfolio `θ` = (`θ`[0], `θ`[1], …, `θ`[*m*]), representing the units held in the fundamental assets.

Note that at `t` = 0, the cash quantity `x` you'd be paying to buy the derivative and the cash quantity you'd be paying to buy the Portfolio `θ` should sum to 0 (note: either of these cash quantities can be positive or negative, but they need to sum to 0 since “money can't just appear or disappear”). Formally,

$$\\begin{array}{r} {x + {\\sum\\limits\_{j = 0}^{m}\\theta\_{j}} \\cdot S\_{j}^{(0)} = 0} \\\\ \\end{array}$$  

(9.16)

Our goal is to solve for the appropriate values of `x` and `θ` based on an `Expected Utility` consideration (that we are about to explain). Consider the Utility of the position consisting of derivative `D` together with portfolio `θ` in random outcome `ω`[*i*] at `t` = 1:

$$\\begin{array}{r} {U(V\_{D}^{(i)} + {\\sum\\limits\_{j = 0}^{m}\\theta\_{j}} \\cdot S\_{j}^{(i)})} \\\\ \\end{array}$$  

So, the Expected Utility of this position at `t` = 1 is given by:

$$\\begin{array}{r} {{\\sum\\limits\_{i = 1}^{n}\\mu}(\\omega\_{i}) \\cdot U(V\_{D}^{(i)} + {\\sum\\limits\_{j = 0}^{m}\\theta\_{j}} \\cdot S\_{j}^{(i)})} \\\\ \\end{array}$$  

(9.17)

Noting that `S`[0]^((0)) = 1, `S`[0]^((`i`)) = 1 + `r` for all `i` = 1, …, `n`, we can substitute for the value of $\\theta\_{0} = - (x + {\\sum\\limits\_{j = 1}^{m}\\theta\_{j}} \\cdot S\_{j}^{(0)})$ (obtained from Equation (9.16)) in the above Expected Utility expression (9.17), so as to rewrite this Expected Utility expression in terms of just (`θ`[1], …, `θ`[*m*]) (call it `θ`[1 : *m*]) as:

$$\\begin{array}{r} {g(V\_{D},x,\\theta\_{1:m}) = {\\sum\\limits\_{i = 1}^{n}\\mu}(\\omega\_{i}) \\cdot U(V\_{D}^{(i)} - (1 + r) \\cdot x + {\\sum\\limits\_{j = 1}^{m}\\theta\_{j}} \\cdot (S\_{j}^{(i)} - (1 + r) \\cdot S\_{j}^{(0)}))} \\\\ \\end{array}$$  

We define the `Price` of `D` as the “breakeven value” `x`^(\*) such that:

$$\\begin{array}{r} {\\max\_{\\theta\_{1:m}}g(V\_{D},x^{\*},\\theta\_{1:m}) = \\max\_{\\theta\_{1:m}}g(0,0,\\theta\_{1:m})} \\\\ \\end{array}$$  

The core principle here (known as `Expected-Utility-Indifference Pricing`) is that introducing a `t` = 1 payoff of `V`[*D*] together with a derivative price payment of `x`^(\*) at `t` = 0 keeps the Maximum Expected Utility unchanged.

The (`θ`[1]^(\*), …, `θ`[*m*]^(\*)) that achieve max[`θ`[1 : *m*]]*g*(*V*[*D*], `x`^(\*), `θ`[1 : *m*]) and $\\theta\_{0}^{\*} = - (x^{\*} + {\\sum\\limits\_{j = 1}^{m}\\theta\_{j}^{\*}} \\cdot S\_{j}^{(0)})$ are the requisite hedges associated with the derivative price `x`^(\*). Note that the Price of `V`[*D*] will NOT be the negative of the Price of −`V`[*D*], hence these prices simply serve as bid prices or ask prices, depending on whether one pays or receives the random outcomes-contingent payoff `V`[*D*].

To develop some intuition for what this solution looks like, let us now write some code for the case of 1 risky asset (i.e., `m` = 1). To make things interesting, we will write code for the case where the risky asset price at `t` = 1 (denoted `S`) follows a normal distribution `S` ∼ 𝒩(`μ`, `σ`²). This means we have a continuous (rather than discrete) set of values for the risky asset price at `t` = 1. Since there are more than 2 random outcomes at time `t` = 1, this is the case of an Incomplete Market. Moreover, we assume the CARA utility function:

$$\\begin{array}{r} {U(y) = \\frac{1 - e^{- a \\cdot y}}{a}} \\\\ \\end{array}$$  

where `a` is the CARA coefficient of risk-aversion.

We refer to the units of investment in the risky asset as `α` and the units of investment in the riskless asset as `β`. Let `S`[0] be the spot (`t` = 0) value of the risky asset (riskless asset value at `t` = 0 is 1). Let `f`(`S`) be the payoff of the derivative `D` at `t` = 1. So, the price of derivative `D` is the breakeven value `x`^(\*) such that:

$$\\begin{array}{r} {\\max\_{\\alpha}\\mathbb{E}\_{S\\sim\\mathcal{N}(\\mu,\\sigma^{2})}\\lbrack\\frac{1 - e^{- a \\cdot (f(S) - (1 + r) \\cdot x^{\*} + \\alpha \\cdot (S - (1 + r) \\cdot S\_{0}))}}{a}\\rbrack} \\\\ {= \\max\_{\\alpha}\\mathbb{E}\_{S\\sim\\mathcal{N}(\\mu,\\sigma^{2})}\\lbrack\\frac{1 - e^{- a \\cdot (\\alpha \\cdot (S - (1 + r) \\cdot S\_{0}))}}{a}\\rbrack} \\\\ \\end{array}$$  

(9.18)

The maximizing value of `α` (call it `α`^(\*)) on the left-hand-side of Equation (9.18) along with `β`^(\*) = −(`x`^(\*) + `α`^(\*) ⋅ `S`[0]) are the requisite hedges associated with the derivative price `x`^(\*).

We set up a `@dataclass` `MaxExpUtility` with attributes to represent the risky asset spot price `S`[0] (`risky_spot`), the riskless rate `r` (`riskless_rate`), mean `μ` of `S` (`risky_mean`), standard deviation `σ` of `S` (`risky_stdev`), and the payoff function `f`(⋅) of the derivative (`payoff_func`).

![](images/comp09_1.jpg)
