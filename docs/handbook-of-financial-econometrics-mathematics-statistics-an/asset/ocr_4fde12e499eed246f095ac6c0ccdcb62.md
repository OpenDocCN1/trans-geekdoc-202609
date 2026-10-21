pricing formula as given in equation (102.23) includes the Black-Scholes option pricing formula as a limiting case.

Lyapunov’s condition requires that X1, X2, … are independent and uniformly bounded with E(Xi)=0, Yn=X1+⋯+Xn, and s²=E(Yn²)=Var(Yn). However, rates of return are generally not independent over time and not necessarily uniformly bounded by the condition required. This is the potential limitation of proof by Cox et al. (1979). We found that the derivation methods proposed by Rendleman and Bartter (1979), which will be discussed in next section, are not so restrictive as the proof discussed in this section.

# 102.4.2 Rendleman and Bartter method

In Rendleman and Bartter (1979), a stock price can either advance or decline during the next period. Let H_T^+ and H_T^- represent the returns per dollar invested in the stock if the price rises (the + state) or falls (the − state), respectively, from time T − 1 to time T (maturity of the option). V_T^+ and V_T^- the corresponding end-of-period values of the option.

Let R be the riskless interest rate, they showed that the price of the option can be represented as a recursive form as:

W_{T-1} = \frac{W_T^+ (1 + R - H_T^-) + W_T^- (H_T^+ - 1 - R)}{(H_T^+ - H_T^-)(1 + R)} . (102.38)

Equation (102.37) can be applied at any time T − 1 to determine the price of the option as a function of its value at time T.⁷ By using recursive substitution as discussed in Section 102.2.1, they derived the binomial option pricing model as defined in equation (102.38)⁸:

W_0 = S_0 B_1(a; T, φ) - \frac{X}{(1 + R)^T} B_2(a; T, φ), (102.39)

where pseudo probabilities φ and φ are defined as

φ = \frac{(1 + R - H^-) H^+}{(1 + R)(H^+ - H^-)}, (102.40)

φ = \frac{(1 + R - H^-)}{(H^+ - H^-)}, (102.41)

⁷Note that notation T used here is the number of periods rather than calendar time.
⁸Note that some of the variables used in this section are different from those used in Section 102.2.1 and Section 102.4.1.