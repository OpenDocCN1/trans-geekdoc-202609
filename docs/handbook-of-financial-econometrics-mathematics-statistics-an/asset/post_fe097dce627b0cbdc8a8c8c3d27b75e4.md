
be an arbitrage opportunity. By the same way, portfolio C should be always worth as much as portfolio D. Hence, we can obtain the relations as follows:

$$C_0 + K e^{-rT} \ge S_0 \quad \text{and} \quad P_0 + S_0 \ge K e^{-rT'}$$

or

$$C_0 \ge S_0 - K e^{-rT} \quad \text{and} \quad P_0 \ge K e^{-rT} - S_0. \quad (24.5)$$

Then, the lower bounds of European options are derived. Since American call options are never early exercised if the underlying asset is without dividend payment, therefore the upper and lower bounds for American call options are the same as the bounds of European call options. However, an American put option should be larger than $K - S_0$ since it can be exercised at any time. Handley (2005) investigates the extension of Merton's (1973) approach to the options with dividends. The tightened upper bounds for European and American call options with dividends under the arbitrage opportunity framework are determined by the comparison between dividend payment and strike price.

## 24.2.2 Stochastic dominance

There are two ways to derive option bounds in stochastic dominance: one is to utilize second degree stochastic dominance (SSD), and the other one is to use SSD with the consideration of a riskless asset (called second degree stochastic dominance with riskless asset, SSDR). Two methods are introduced in detail in this section.

### 24.2.2.1 Second degree stochastic dominance (SSD)

The concept to obtain the option bounds of Perrakis and Ryan (1984) is looking for the second degree stochastic dominance relationship between different portfolios. Second degree stochastic dominance (SSD) allows the universal ranking of distributions among risk-averse individuals. The criterion is stated as follows:

> Let X and Y be two random variables whose cumulative distributions are F_X and F_Y, respectively. Then F_X dominates F_Y by second degree stochastic dominance if and only if $\int_{-\infty}^{z} [F_Y(t) - F_X(t)] dt \ge 0$ for all z.

Any risk-averse expected-utility investor prefers a second degree stochastic dominant investment to a dominated alternative.

Based on Rubinstein's (1976) equation of the valuation of uncertain income streams, Perrakis and Ryan (1984) assume that the normalized conditional expected marginal utility of the consumptions is a non-increasing function of price change (Y). The option bounds can be obtained by comparing the values of three portfolios. Assume an investor has wealth endowment S0 that can only be invested in one of these portfolios:

- *Portfolio A:* One share of stock at price S0
- *Portfolio B:* One call option on the stock at price C0 with strike price K, and S0 − C0 invested in the riskless asset with risk free rate, r
- *Portfolio C:* S0/C0 call options on the stock at price C0 with strike price K

The values of these three different portfolios are represented as function of Y as:

- *Value of Portfolio A* = S0 + Y.
- *Value of Portfolio B* = (S0 − C0)(1 + r) + Max(S0 + Y − K, 0).
- *Value of Portfolio C* = S0/C0 (Max(S0 + Y − K, 0)).

By comparing portfolios A and B to derive the lower bound and comparing portfolio A and portfolio C to derive upper bound, the bounds of an European call option for a single-period can be shown as

$$C_{\min}^E = \max\left(0, S_0 + \frac{1}{1+r}\left[-K + \int_0^K F_Y(w - S_0) dw\right]\right), \quad (24.6)$$

$$C_{\max}^E = S_0 + \frac{S_0}{S_0 + E[Y]} \left[-K + \int_0^K F_Y(w - S_0) dw\right], \quad (24.7)$$

where $F_Y(w - S_0)$ is the cumulative probability distribution of price change $Y$ for $Y \in [-S_0, \infty)$. The option bounds are functions of the initial stock price $S_0$, the exercise price $K$, the riskless rate of interest, $r$, and the distribution of stock price change, $F_Y(Y)$.

In the following, Perrakis (1986) extends the results of Perrakis and Ryan (1984) by tightening the bounds with the restrictions that the one-period return (of per dollar investing in the underlying stock) is finite and has a strictly positive lower limit. In addition, the bounds for American put option are also developed within the framework of Perrakis and Ryan (1984).

### 24.2.2.2 Second degree stochastic dominance with riskless asset (SSDR)

Distinct from Perrakis and Ryan's (1984) option bounds, which are obtainable by applying second degree stochastic dominance method, Levy (1985) applies the concept of second degree stochastic dominance with the riskless asset (SSDR) to derive the upper and lower bounds for European options. Levy (1985) assumes that the investors' preferences belong to the set of all non-decreasing concave utility functions and the underlying assets are those with non-negative consumption beta. Let $F_c$ and $F_s$ be the cumulative distributions of the terminal wealth investing in an European call option and its underlying asset. If borrowing and lending at the risk free rate are allowed, which is a crucial assumption to derive relatively narrower bounds, then an investor may find that any combination of the underlying asset with the riskless asset is dominated by some combination of European call option with the riskless asset even though neither $F_c$ nor $F_s$ dominates the other without the riskless asset. That is, in the presence of a riskless asset, if every risk-averse investor prefers to hold the investment $F_c$ rather than the investment $F_s$, then $F_c$ is said to dominate $F_s$ by SSDR.

Therefore, the European call option bounds can be obtained by using the intuition that the lower (upper) bound of an European call option is derived in such a way that $F_c$ ($F_s$) exactly does not dominate $F_s$ ($F_c$). The criterion of SSDR is stated as follows:

> Let $F_c$ and $F_s$ be the two cumulative distributions with the $p^{th}$ quantile, $Q_{F_C}(p)$ and $Q_{F_S}(p)$, respectively. Then $F_c$ dominates $F_s$ in the SSDR if and only if
>
> $$\inf_{0\le p<p_C}\frac{\int_0^p[Q_{F_S}(w)-r]dw}{\int_0^p[Q_{F_C}(w)-r]dw}\ge\sup_{p_C<p\le1}\frac{\int_0^p[Q_{F_S}(w)-r]dw}{\int_0^p[Q_{F_C}(w)-r]dw}$$
>
> where $p_C$ is the value which solves $\int_0^{p_C}[Q_{F_C}(w)-r]dw=0$.

Levy (1985) proves that the cumulative distribution of the return of a European call option, $F_c$, dominates the cumulative distribution of the return of its underlying asset, $F_s$, in the SSDR if and only if $p_c \le p_s$, where $p_c$ and $p_s$ are the values that solve

$$\int_0^{p_c}[Q_{F_C}(w)-r]dw=0\quad\text{and}\quad\int_0^{p_S}[Q_{F_S}(w)-r]dw=0.\tag{24.8}$$

The lower bounds of a European call option, $C_{\min}^E$, then can be solved by using Levy (1985)'s dominance theory. In order to avoid such dominance, we must set $p_c > p_S$. Therefore, one can solve for a European call option price, $C_0$, that equates this condition, and then conclude that the market price of a European call option must be greater than such value. Using this line of reasoning, it can be shown that

$$C_0 \ge C_{\min}^E = S_0 - \frac{K}{r} + \frac{1}{r p_C} \int_0^K (K - S_T) f(S_T) dS_T, \quad (24.9)$$

where $C_0$ denotes current price of a European call option; $S_0$ denotes current price of the underlying asset, $S_T$ is the future price of the underlying asset at expiration day, $T$; $K$ and $r$ represent the strike price and risk free rate, respectively; $p_c$ is the value that solves $\int_0^{p_c} [Q_{F_c}(w) - r] dw = 0$ and $F_c$ is the cumulative distribution of the return of a European call option.

Similarly, the upper bound of a European call option, $C_{\max}^E$, can be obtained by considering the dominance of the price of the underlying asset over the price of a European call option in SSDR. By using Levy (1985)'s dominance theory and setting $p_S > p_c$, the upper bound of a European call option, $C_{\max}^E$, can be shown as¹

$$C_0 \le C_{\max}^E = \frac{S_0}{E(S_T)} \int_K^\infty (S_T - K) f(S_T) dS_T, \quad (24.10)$$

where $S_T$ is the future price of the underlying asset at expiration day, $T$; $E(S_T)$ is the expected value of the underlying asset at expiration day; $C_0$ denotes current price of a European call option; $S_0$ denotes current price of the underlying asset; $K$ and $r$ represent the strike price and risk free rate, respectively.

Some classic puts on debt instruments can be viewed as calls with a concave payoff of the underlying interest rate since the bond price is a decreasing convex function of the interest rate. It is essential to understand the option bound of a call on bond. Hence, Henin and Pistre (1998) use second order stochastic dominance arguments to study calls where the payoff is a concave function of the underlying asset. They derive bounds on option prices, whose exercise payoff is a concave function of the difference between the underlying asset and strike price. Later, Constantinides and Perrakis (2002) derive the tighter option bounds of European options by using stochastic dominance arguments. They utilize the zero-net cost portfolio which consists of a riskless bond, a stock, and European call (or put) options and assume the concave utility function for investor preference to derive the

> ¹ The detailed derivation process can be found in Levy's (1985) paper.
