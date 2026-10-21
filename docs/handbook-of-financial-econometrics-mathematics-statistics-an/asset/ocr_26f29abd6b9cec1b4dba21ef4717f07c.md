# Alternative Methods for Determining Option Bounds: A Review and Comparison 925

we must set \( p_c > p_S \). Therefore, one can solve for a European call option price, \( C_0 \), that equates this condition, and then conclude that the market price of a European call option must be great than such value. Using this line of reasoning, it can be shown that

```
\[ C_0 \ge C^E_{min} = S_0 - \frac{K}{r} + \frac{1}{r p_C} \int_0^K (K - S_T) f(S_T) dS_T, \quad (24.9) \]
```

where \( C_0 \) denotes current price of a European call option; \( S_0 \) denotes current price of the underlying asset, \( S_T \) is the future price of the underlying asset at expiration day, \( T \); \( K \) and \( r \) represent the strike price and risk free rate, respectively; \( p_c \) is the value that solves \( \int_0^{p_c} [Q_{F_c}(w) - r] dw = 0 \) and \( F_c \) is the cumulative distribution of the return of a European call option.

Similarly, the upper bound of a European call option, \( C^E_{max} \), can be obtained by considering the dominance of the price of the underlying asset over the price of a European call option in SSDR. By using Levy (1985)’s dominance theory and setting \( p_S > p_c \), the upper bound of a European call option, \( C^E_{max} \), can be shown as¹

```
\[ C_0 \le C^E_{max} = \frac{S_0}{E(S_T)} \int_K^\infty (S_T - K) f(S_T) dS_T, \quad (24.10) \]
```

where \( S_T \) is the future price of the underlying asset at expiration day, \( T \); \( E(S_T) \) is the expected value of the underlying asset at expiration day; \( C_0 \) denotes current price of a European call option; \( S_0 \) denotes current price of the underlying asset; \( K \) and \( r \) represent the strike price and risk free rate, respectively.

Some classic puts on debt instruments can be viewed as calls with a concave payoff of the underlying interest rate since the bond price is a decreasing convex function of the interest rate. It is essential to understand the option bond of a call on bond. Hence, Henin and Pistre (1998) use second order stochastic dominance arguments to study calls where the payoff is a concave function of the underlying asset. They derive bounds on option prices, whose exercise payoff is a concave function of the difference between the underlying asset and strike price. Later, Constantinides and Perrakis (2002) derive the tighter option bounds of European options by using stochastic dominance arguments. They utilize the zero-net cost portfolio which consists of a riskless bond, a stock, and European call (or put) options and assume the concave utility function for investor preference to derive the

> ¹ The detailed derivation process can be found in Levy’s (1985) paper.