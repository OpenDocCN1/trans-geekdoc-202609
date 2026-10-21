bounds of European option price. Their option bounds can be viewed as a generalization of single-period model to a multi-period economy since they are independent of the trading frequency.

Constantinides et al. (2009) utilized the theoretical stochastic dominance method to test whether S&P 500 index options market is rational or not. In stochastic dominance framework, the investors are risk averse and their preference is to maximize their expected utility that is concave and increasing function of the wealth and the wealth is monotone increasing in the stock return.

# 24.2.3 Linear programming

The development of linear programming is driven by its applications in economics and management. The standard form of a linear programming problem can be written as

Maximize c^T x subject to A x ≤ b and x ≥ 0. (24.11)

In other words, linear programming is a technique for optimization of a linear objective function, subject to linear equality and linear inequality constraints. Any vector x satisfying the constraints of the linear programming problem is called a feasible solution of the problem. Linear programming is an important branch of applied mathematics that solves a wide variety of optimization problems. The biggest advantage of linear programming is that it always achieves the optimal solution if one exists.

Ritchken (1985) proposes using linear programming that places constraints on the time preference, risk aversion, and state probabilities. Under some specific set of assumptions, the price of a European call option can be viewed as the objective function to be optimized and formulated by a linear program. Then the lower and upper bounds of a European call option can be obtained by minimization and maximization of the objective function in linear programming problem.

In an incomplete market, the prices of the state securities are not unique. To replicate Merton (1973)'s result, Ritchken (1985) assumes investors always prefer more to less, which implies the positive value of the current price of the specific pure state security that pays out $1 at maturity day if this specific state occurs. The option bounds are, therefore, obtained by solving the following linear programming problem

Minimize (or Maximize) C0 = Σ_{i=1}^n c_i e_i, (24.12)