# The Limits of Mathematical Modeling in the Social Sciences

We restrict our analysis to the so-called weakly efficient markets. Since one adds the condition that there is a time-polynomial algorithmic procedure to spread the data about the market, we name those markets Maymin-efficient markets, where (we stress) $v(\sigma_k)$ is computed by a time-polynomial Turing machine (or poly-machine).

So the existence of general poly procedures characterizes the market as Maymin efficient. Now, we have the following Maymin's theorem.

# **Proposition H.2.** Markets are (Maymin) efficient if and only if $P = NP$.

Now we put: markets are almost Maymin-efficient if and only if there is an O'Donnell algorithm to determine its successful policies (see da Costa and Doria, 2016). Then, we have the following proposition.

# **Proposition H.3.** If $P < NP$ isn't proved by primitive recursive arithmetic then there are almost Maymin-efficient markets.

# **Appendix I. Details

The main motive is very simple: we are going to code Maymin-efficient markets as Boolean expressions. We use a result by E. Post. The $2^k$ binary sequences naturally code integers from 0 to $2^k - 1$; more precisely, from

```
$000 \dots 00, k \text{ digits},$
```

to:

```
$111 \dots 11, k \text{ digits}$.
```

Fix one such coding: a $k$-digit binary sequence is as sequence of truth values for a Boolean expression $\Xi_k$.

# **Proposition I.1.** Let $\xi_k$ be a binary sequence of length $2^k$. Then there is a Boolean expression $\Xi_k$ on $k$ Boolean variables so that $\xi_k$ is its truth table.