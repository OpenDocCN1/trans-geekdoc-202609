
Before we write code to solve the derivatives pricing and hedging problem for an incomplete market, let us write code to solve the problem for a complete market (as this will serve as a good comparison against the incomplete market solution). For a complete market, the risky asset has two random prices at `t = 1`: prices `μ + σ` and `μ − σ`, with probabilities of 0.5 each. As we've seen in [Section 9.6.1](#chapter9.xhtml#sec9_6_1), we can perfectly replicate a derivative payoff in this complete market situation as it amounts to solving 2 linear equations in 2 unknowns (solution shown in Equation (9.14)). The number of units of the requisite hedges are simply the negatives of the replicating portfolio units. The method `complete_mkt_price_and_hedges` (of the `MaxExpUtility` class) shown below implements this solution, producing a dictionary comprising of the derivative price (`price`) and the hedge units `α` (alpha) and `β` (beta).

![](images/comp09_2.jpg)

Next, we write a helper method `max_exp_util_for_zero` (to handle the right-hand-side of Equation (9.18)) that calculates the maximum expected utility for the special case of a derivative with payoff equal to 0 in all random outcomes at `t = 1`, i.e., it calculates:

$$\\begin{array}{r} {\\max_{\\alpha}\\mathbb{E}_{S\\sim\\mathcal{N}(\\mu,\\sigma^{2})}\\lbrack\\frac{1 - e^{- a \\cdot ( - (1 + r) \\cdot c + \\alpha \\cdot (S - (1 + r) \\cdot S_{0}))}}{a}\\rbrack} \\\\ \\end{array}$$  

where `c` is cash paid at `t = 0` (so, `c = −(α ⋅ S[0] + β)`).

The method `max_exp_util_for_zero` accepts as input `c: float` (representing the cash `c` paid at `t = 0`) and `risk_aversion_param: float` (representing the CARA coefficient of risk aversion `a`). Refering to [Section A.4.1](#appA.xhtml#secA_4_1) in [Appendix A](#appA.xhtml#appA), we have a closed-form solution to this maximization problem:

$$\\begin{array}{r} {\\alpha^{*} = \\frac{\\mu - (1 + r) \\cdot S_{0}}{a \\cdot \\sigma^{2}}} \\\\ \\end{array}$$  

$$\\begin{array}{r} {\\beta^{*} = - (c + \\alpha^{*} \\cdot S_{0})} \\\\ \\end{array}$$  

Substituting `α*` in the Expected Utility expression above gives the following maximum value for the Expected Utility for this special case:

$$\\begin{array}{r} {\\frac{1 - e^{- a \\cdot ( - (1 + r) \\cdot c + \\alpha^{*} \\cdot (\\mu - (1 + r) \\cdot S_{0})) + \\frac{{(a \\cdot \\alpha^{*} \\cdot \\sigma)}^{2}}{2}}}{a} = \\frac{1 - e^{a \\cdot (1 + r) \\cdot c - \\frac{{(\\mu - (1 + r) \\cdot S_{0})}^{2}}{2\\sigma^{2}}}}{a}} \\\\ \\end{array}$$  

![](images/comp09_3.jpg)

Next, we write a method `max_exp_util` that calculates the maximum expected utility for the general case of a derivative with an arbitrary payoff `f(⋅)` at `t = 1` (provided as input `pf: Callable[[float, float]]` below), i.e., it calculates:

$$\\begin{array}{r} {\\max_{\\alpha}\\mathbb{E}_{S\\sim\\mathcal{N}(\\mu,\\sigma^{2})}\\lbrack\\frac{1 - e^{- a \\cdot (f(S) - (1 + r) \\cdot c + \\alpha \\cdot (S - (1 + r) \\cdot S_{0}))}}{a}\\rbrack} \\\\ \\end{array}$$  

Clearly, this has no closed-form solution since `f(⋅)` is an arbitary payoff. The method `max_exp_util` uses the `scipy.integrate.quad` function to calculate the expectation as an integral of the CARA utility function of `f(S) − (1 + r) ⋅ c + α ⋅ (S − (1 + r) ⋅ S[0])` multiplied by the probability density of `𝒩(μ, σ²)`, and then uses the `scipy.optimize.minimize_scalar` function to perform the maximization over values of `α`.

![](images/comp09_4.jpg)

Finally, it's time to put it all together—the method `max_exp_util_price_and_hedge` below calculates the maximizing `x*` in Equation (9.18). First, we call `max_exp_util_for_zero` (with `c` set to 0) to calculate the right-hand-side of Equation (9.18). Next, we create a wrapper function `prep_func` around `max_exp_util`, which is provided as input to `scipy.optimize.root_scalar` to solve for `x*` in the right-hand-side of Equation (9.18). Plugging `x*` (`opt_price` in the code below) in `max_exp_util` provides the hedges `α*` and `β*` (`alpha` and `beta` in the code below).

![](images/comp09_5.jpg)

The above code for the class `MaxExpUtility` is in the file `rl/chapter8/max_exp_utility.py`. As ever, we encourage you to play with various choices of `S[0]`, `r`, `μ`, `σ`, `f` to create instances of `MaxExpUtility`, analyze the obtained prices/hedges, and plot some graphs to develop intuition on how the results change as a function of the various inputs.

Running this code for `S[0] = 100`, `r = 5%`, `μ = 110`, `σ = 25` when buying a call option (European since we have only one time period) with strike price `= 105`, the method `complete_mkt_price_and_hedges` gives an option price of 11.43, risky asset hedge units of `−0.6` (i.e., we hedge the risk of owning the call option by short-selling 60% of the risky asset) and riskless asset hedge units of 48.57 (i.e., we take the $60 proceeds of short-sale less the $11.43 option price payment = $48.57 of cash and invest in a riskless bank account earning 5% interest). As mentioned earlier, this is the perfect hedge if we had a complete market (i.e., two random outcomes). Running this code for the same inputs for an incomplete market (calling the method `max_exp_util_price_and_hedge` for risk-aversion parameter values of `a = 0.3`, `0.6`, `0.9` gives us the following results:

![](images/comp09_6.jpg)

We note that the call option price is quite high (23.28) when the risk-aversion is low at `a = 0.3` (relative to the complete market price of 11.43) but the call option price drops to 12.67 and 8.87 for `a = 0.6` and `a = 0.9`, respectively. This makes sense since if you are more risk-averse (high `a`), then you'd be less willing to take the risk of buying a call option and hence, would want to pay less to buy the call option. Note how the risky asset short-sale is significantly less (~47% – ~49%) compared the to the risky asset short-sale of 60% in the case of a complete market. The varying investments in the riskless asset (as a function of the risk-aversion `a`) essentially account for the variation in option prices (as a function of `a`). [Figure 9.1](#chapter9.xhtml#fig9_1) provides tremendous intuition on how the hedges work for the case of a complete market and for the cases of an incomplete market with the 3 choices of risk-aversion parameters. Note that we have plotted the negatives of the hedge portfolio values at `t = 1` so as to visualize them appropriately relative to the payoff of the call option. Note that the hedge portfolio value is a linear function of the risky asset price at `t = 1`. Notice how the slope and intercept of the hedge portfolio value changes for the 3 risk-aversion scenarios and how they compare against the complete market hedge portfolio value.

![Figure 9.1 Hedges When Buying a Call Option](images/fig9_1.jpg)

[Figure 9.1](#chapter9.xhtml#b9fig9_1) Hedges When Buying a Call Option

Now let us consider the case of selling the same call option. In our code, the only change we make is to make the payoff function `lambda x: - max(x - 105.0, 0)` instead of `lambda x: max(x - 105.0, 0)` to reflect the fact that we are now selling the call option and so, our payoff will be the negative of that of an owner of the call option.

With the same inputs of `S[0] = 100`, `r = 5%`, `μ = 110`, `σ = 25`, and for the same risk-aversion parameter values of `a = 0.3`, `0.6`, `0.9`, we get the following results:

![](images/comp09_7.jpg)
