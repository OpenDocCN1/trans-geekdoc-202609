+   86.7 Derivation of Sensitivity for Stock Options with Respect to Exercise Price . . . . . . . . . . . . . . . . . . . . . . . 2989
+   86.8 Relationship Between Delta, Theta, and Gamma . . . . . . 2991
+   86.9 Empirical Examples of Delta, Theta, Gamma, Vega, and Rho 2992
+   86.10 Summary and Concluding Remarks . . . . . . . . . . . . . 2993
+   Bibliography . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2993
+   Appendix 86A: Convexity and Bond Price Change . . . . . . . . 2994
+   Appendix 86B: Greek Letter Estimates in Terms of Johnson & Johnson Stock Price and Option Information . . . . 2997

# Abstract

Based on comparative analysis, we first discuss different kinds of Greek letters in terms of Black-Scholes option pricing model, then we show how these Greek letters can be applied to perform hedging and risk management. The relationship between delta, theta, and gamma is also explored in detail.

# Keywords

Delta (Δ) • Theta (Θ) • Gamma (Γ) • Vega (ν) • Rho (ρ) • Hedging.

# 86.1 Introduction

It is well known that the call option value can be affected by stock price per share, exercise price per share, the contract period of the option, the risk-free rate, and the volatility of the stock return. In this chapter, we will mathematically analyze these kinds of relationships. Parts of these mathematical relationships are called “Greek letters” by finance professionals. Here, we specifically derive Greek letters for call (put) options on non-dividend stock and dividends-paying stock. Some examples will be provided to explain applications of these Greek letters. Sections 86.2–86.6 discuss the derivations and applications of Delta, Theta, Gamma, Vega, and Rho, respectively. Section 86.7 derives the partial derivative of stock options with respect to their exercise prices. Section 86.8 describes the relationship between Delta, Theta, and Gamma, and their implication in delta-neutral portfolio. In Section 86.9, we summarize and conclude this chapter. Appendix 86A discusses the relationship between convexity and bond price change. Finally, Appendix 86B discusses Greek letter estimates in terms of Johnson & Johnson stock price and option information.