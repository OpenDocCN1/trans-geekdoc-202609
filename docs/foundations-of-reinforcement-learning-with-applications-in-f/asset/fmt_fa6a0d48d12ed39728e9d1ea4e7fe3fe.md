
We note that the sale price demand for the call option is quite low (6.31) when the risk-aversion is low at `a = 0.3` (relative to the complete market price of 11.43) but the sale price demand for the call option rises sharply to 32.32 and 44.24 for `a = 0.6` and `a = 0.9`, respectively. This makes sense since if you are more risk-averse (high `a`), then you'd be less willing to take the risk of selling a call option and hence, would want to charge more for the sale of the call option. Note how the risky asset hedge units are less (52% – 53%) compared to the risky asset hedge units (60%) in the case of a complete market. The varying riskless borrowing amounts (as a function of the risk-aversion `a`) essentially account for the variation in option prices (as a function of `a`). [Figure 9.2](#chapter9.xhtml#fig9_2) provides the visual intuition on how the hedges work for the 3 choices of risk-aversion parameters (along with the hedges for the complete market, for reference).

![Figure 9.2 Hedges When Selling a Call Option](images/fig9_2.jpg)

[Figure 9.2](#chapter9.xhtml#b9fig9_2) Hedges When Selling a Call Option

Note that each buyer and each seller might have a different level of risk-aversion, meaning each of them would have a different buy price bid/different sale price ask. A transaction can occur between a buyer and a seller (with potentially different risk-aversion levels) if the buyer's bid matches the seller's ask.

### 9.6.3 Derivatives Pricing When Market Has Arbitrage

Finally, we arrive at the case where the market has arbitrage. This is the case where there is no risk-neutral probability measure and there can be multiple replicating portfolios (which can lead to arbitrage). So this is the case where we are unable to price derivatives. To provide intuition for the case of a market with arbitrage, we consider the special case of 2 risky assets (`m = 2`) and 2 random outcomes (`n = 2`), which we will show is a Market with Arbitrage. Without loss of generality, we assume `S[1]^((1)) < S[1]^((2))` and `S[2]^((1)) < S[2]^((2))`. Let us try to determine a risk-neutral probability measure `π`:

```
\begin{array}{r} {S_{1}^{(0)} = e^{- r} \cdot (\pi(\omega_{1}) \cdot S_{1}^{(1)} + \pi(\omega_{2}) \cdot S_{1}^{(2)})} \\ \end{array}
```

```
\begin{array}{r} {S_{2}^{(0)} = e^{- r} \cdot (\pi(\omega_{1}) \cdot S_{2}^{(1)} + \pi(\omega_{2}) \cdot S_{2}^{(2)})} \\ \end{array}
```

```
\begin{array}{r} {\pi(\omega_{1}) + \pi(\omega_{2}) = 1} \\ \end{array}
```

3 equations and 2 variables implies that there is no risk-neutral probability measure `π` for various sets of values of `S[1]^((1))`, `S[1]^((2))`, `S[2]^((1))`, `S[2]^((2))`. Let's try to form a replicating portfolio (`θ[0]`, `θ[1]`, `θ[2]`) for a derivative `D`:

```
\begin{array}{r} {V_{D}^{(1)} = \theta_{0} \cdot e^{r} + \theta_{1} \cdot S_{1}^{(1)} + \theta_{2} \cdot S_{2}^{(1)}} \\ \end{array}
```

```
\begin{array}{r} {V_{D}^{(2)} = \theta_{0} \cdot e^{r} + \theta_{1} \cdot S_{1}^{(2)} + \theta_{2} \cdot S_{2}^{(2)}} \\ \end{array}
```

2 equations and 3 variables implies that there are multiple replicating portfolios. Each such replicating portfolio yields a price for `D` as:

```
\begin{array}{r} {V_{D}^{(0)} = \theta_{0} + \theta_{1} \cdot S_{1}^{(0)} + \theta_{2} \cdot S_{2}^{(0)}} \\ \end{array}
```

Select two such replicating portfolios with different `V[D]^((0))`. The combination of one of these replicating portfolios with the negative of the other replicating portfolio is an Arbitrage Portfolio because:

*   They cancel off each other's portfolio value in each `t = 1` states.

*   The combined portfolio value can be made to be negative at `t = 0` (by appropriately choosing the replicating portfolio to negate).

So this is a market that admits arbitrage (no risk-neutral probability measure).

## 9.7 DERIVATIVES PRICING IN MULTI-PERIOD/CONTINUOUS-TIME

Now that we have understood the key concepts of derivatives pricing/hedging for the simple setting of discrete-time with a single-period, it's time to do an overview of derivatives pricing/hedging theory in the full-blown setting of multiple time-periods and in continuous-time. While an adequate coverage of this theory is beyond the scope of this book, we will sketch an overview in this section. Along the way, we will cover two derivatives pricing applications that can be modeled as MDPs (and hence, tackled with Dynamic Programming or Reinforcement Learning Algorithms).

The good news is that much of the concepts we learnt for the single-period setting carry over to multi-period and continuous-time settings. The key difference in going over from single-period to multi-period is that we need to adjust the replicating portfolio (i.e., adjust `θ`) at each time step. Other than this difference, the concepts of arbitrage, risk-neutral probability measures, complete market etc. carry over. In fact, the two fundamental theorems of asset pricing also carry over. It is indeed true that in the multi-period setting, no-arbitrage is equivalent to the existence of a risk-neutral probability measure and market completeness (i.e., replication of derivatives) is equivalent to having a unique risk-neutral probability measure.

### 9.7.1 Multi-Period Complete-Market Setting

We learnt in the single-period setting that if the market is complete, there are two equivalent ways to conceptualize derivatives pricing:

*   Solve for the replicating portfolio (i.e., solve for the units in the fundamental assets that would replicate the derivative payoff), and then calculate the derivative price as the value of this replicating portfolio at `t = 0`.

*   Calculate the probabilities of random-outcomes for the unique risk-neutral probability measure, and then calculate the derivative price as the riskless rate-discounted expectation (under this risk-neutral probability measure) of the derivative payoff.

It turns out that even in the multi-period setting, when the market is complete, we can calculate the derivative price (not just at `t = 0`, but at any random outcome at any future time) with either of the above two (equivalent) methods, as long as we appropriately adjust the fundamental assets' units in the replicating portfolio (depending on the random outcome) as we move from one time step to the next. It is important to note that when we alter the fundamental assets' units in the replicating portfolio at each time step, we need to respect the constraint that money cannot enter or leave the replicating portfolio (i.e., it is a `self-financing replicating portfolio` with the replicating portfolio value remaining unchanged in the process of altering the units in the fundamental assets). It is also important to note that the alteration in units in the fundamental assets is dependent on the prices of the fundamental assets (which are random outcomes as we move forward from one time step to the next). Hence, the fundamental assets' units in the replicating portfolio evolve as random variables, while respecting the self-financing constraint. Therefore, the replicating portfolio in a multi-period setting in often referred to as a `Dynamic Self-Financing Replicating Portfolio` to reflect the fact that the replicating portfolio is adapting to the changing prices of the fundamental assets. The negatives of the fundamental assets' units in the replicating portfolio form the hedges for the derivative.
