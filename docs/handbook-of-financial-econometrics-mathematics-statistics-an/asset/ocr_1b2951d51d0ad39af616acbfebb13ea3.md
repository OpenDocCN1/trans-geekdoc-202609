# 7.2.2 Stochastic dominance

There are two ways to derive option bounds in stochastic dominance: one is to utilize second degree stochastic dominance (SSD), and the other one is to use SSD with the consideration of a riskless asset (called second degree stochastic dominance with riskless asset, SSDR). These two methods are introduced in detail in the following two sections.

# 7.2.2.1 Second degree stochastic dominance (SSD)

The concept to obtain the option bounds of Perrakis and Ryan (1984) is looking for the second degree stochastic dominance relationship between different portfolios. Second degree stochastic dominance (SSD) allows the universal ranking of distributions among risk-averse individuals. The criterion is stated as follows:

> *Let X and Y be two random variables whose cumulative distributions are F_X and F_Y, respectively. Then F_X dominates F_Y by second degree stochastic dominance if and only if ∫_{-∞}^{z}[F_Y(t) − F_X(t)]dt ≥ 0 for all z.*

Any risk-averse expected-utility investor prefers a second degree stochastic dominant investment to a dominated alternative.

Based on Rubinstein's (1976) equation of the valuation of uncertain income streams, Perrakis and Ryan (1984) assume that the normalized conditional expected marginal utility of the consumptions is a non-increasing function of price change (Y). The option bounds can be obtained by comparing the values of three portfolios. Assume an investor has wealth endowment S_0 that can only be invested in one of these portfolios:

+   - **Portfolio A.** One share of stock at price S₀
+   - **Portfolio B.** One call option on the stock at price C₀ with strike price K, and S₀ − C₀ invested in the riskless asset with risk free rate, r
+   - **Portfolio C.** S₀/C₀ call options on the stock at price C₀ with strike price K

The values of these three different portfolios are represented as function of Y as:

Value of Portfolio A = S₀ + Y
Value of Portfolio B = (S₀ − C₀)(1 + r) + Max(S₀ + Y − K, 0)
Value of Portfolio C = S₀/C₀ (Max(S₀ + Y − K, 0)).