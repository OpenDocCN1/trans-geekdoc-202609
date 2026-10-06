
## CHAPTER 5 | Single Asset American Options

When the LHS of the above equation is substituted into equation (5.2.20), we obtain the equation for $S^*$:

```
$S^* - E = c(S^*, E, \tau) + \frac{S^*}{\gamma_2}\{1 - \exp(-q\tau)N_1(d_1(S^*))}. \quad (5.2.24)
```

This equation can be solved for $S^*$ using standard iterative methods (the section on the numerical solution of critical asset values). Where $S^*$ has been found, equation (5.2.23) gives

```
$ha_2 = A_2S^{*\gamma_2}.
```

where

```
$A_2 = \frac{S^*}{\gamma_2}\{1 - \exp(-q\tau)N_1(d_1(S^*))\}$.
```

From (5.2.19), the value of an American call is thus of the

```
$C(S,E, \tau) = c(S,E, \tau) + A_2(\frac{S}{S^*})^{\gamma_2} \quad \text{when } S < S^*, \quad (5.2.25)
```

```
$C(S,E, \tau) = S - E \quad \text{when } S \geq S^*. \quad (5.2.26)
```

## American Put Options

For an American put, we proceed in a similar manner to that of the American call. We now use fact that both the value and early exercise premium $(y_p(S,E,\tau) = h_p(S,E,\tau))$ of an American put tend to zero as the asset price $S \to \infty$. So $q_p(S,E,\tau) \to 0$ as $S \to \infty$. Since $\gamma_2 > 0$, the only way this can be achieved by equation (5.2.18) is if $a_2 = a_1S^{*\gamma_1}$ and the value of an American put is

```
$P(S,E,\tau) = p(S,E,\tau) + ha_1S^{*\gamma_1}. \quad (5.2.27)
```

An expression for $a_1$ can be found by considering the critical asset price, $S^*$, below which the American option will be exercised. For $S > S^*$, the value of the American put is given by equation (5.2.27), and for $S < S^*$, we have $P(S,E,\tau) = S - E$.

Continuity of the option value at the critical asset price gives

```
$E - S^* = p(S,E,\tau) + ha_1S^{*\gamma_1}. \quad (5.2.28)
```

and continuity of the option value's gradient at the critical asset price yields

```
$\frac{\partial(E - S^*)}{\partial S^*} = \frac{\partial}{\partial S^*}\{p(S^*,E,\tau) + ha_1S^{*\gamma_1}\}. \quad (5.2.29)
```

which can be simplified to

```
$-1 = -N_1(d_1(S^*))\exp(-q\tau) + \gamma_1 a_1. \quad (5.2.30)
```

where we have used value of hedge $\Delta_p$ for a European put,

```
$\frac{\partial\Delta_p(S^*,\tau)}{\partial S^*} = \{N_1(d_1(S^*)) - 1\}\exp(-q\tau).
```

## Approximations for American Options

Equation (5.2.30) can therefore be written as

```
$ha_1S^{\gamma_1} = \frac{S^{**}}{\gamma_1}\{1 - N_1(d_1(S^{**}))\}\exp(-q\tau). \quad (5.2.31)
```

When the LHS of the above is substituted into equation (5.2.28), we obtain the following equation for $S^{**}$:

```
$E - S^{**} = p(S^{**}, \tau) + \{1 - \exp(-q\tau)N_1(d_1(S^{**}))\}\frac{S^{**}}{\gamma_1}. \quad (5.2.32)
```

which can be solved iteratively to yield $S^*$ (see the section on critical asset values). When $S^{**}$ has been found, equation (5.2.31) gives

```
$ha_1 = A_1S^{**\gamma_1},
```

where

```
$A_1 = -\frac{S^{**}}{\gamma_1}\{1 - \exp(-q\tau)N_1(d_1(S^{**}))\}$. 
```

We note here that $A_1 > 0, since $\gamma_1 < 0$, $S^{**} > 0$, and $N_1(d_1(S^{**}))\exp(-q\tau) < 1$.

From (5.2.27), the value of an American put is

```
$P(S, \tau) = p(S, \tau) + A_1\frac{S^{\gamma_2}}{S^{**}} \quad \text{when } S > S^{**},
```

```
$P(S, \tau) = E - S \quad \text{when } S \le S^{**}.
```

## Numerical Solution of Critical Values

We provide details on how to iteratively solve for the critical price in equation (5.2.24) and equation (5.2.32).

## American Call Options

For American call options, we need to solve equation (5.2.24), which is

```
$S^* - E = c(S^*, \tau) + \frac{S^*}{\gamma_2}\{1 - \exp(-q\tau)N_1(d_1(S^*))\}$.
```

We denote the $i$th approximation to the critical asset value $S^*_i$ and represent the LHS of the $i$th

```
$LHS(S^*_i, \tau) = S^*_i - E,
```

and the right-hand side of the equation by

```
$RHS(S^*_i, \tau) = c(S^*_i, \tau) + \frac{S^*_i}{\gamma_2}\{1 - \exp(-q\tau)N_1(d_1(S^*_i))\}$.
```

If we let $K(S^*_i, \tau) = RHS(S^*_i, \tau) - LHS(S^*_i, \tau)$, then we want to find the value of $S^*_i$ (which to a specified tolerance) gives $K(S^*_i, \tau) \sim 0$. This can be achieved with Newton's root finding method, in which a better approximation, $S_{i+1}^*$, can be found using

```
$S_{i+1}^* = S^*_i - \frac{K(S^*_i, E, \tau)}{K'(S^*_i, E, \tau)}, \quad (5.2.33)
```

where

```
$K'(S^*_i, E, \tau) = \frac{\partial}{\partial S^*_i}\{RHS(S^*_i, E, \tau) - LHS(S^*_i, \tau)\}$
= \frac{\partial}{\partial S^*_i}\{RHS(S^*_i, E, \tau)\} - \frac{\partial}{\partial S^*_i}\{LHS(S^*_i, E, \tau)\}$
= b_i - 1.
```

Here, we have used $b_i = \frac{\partial}{\partial S^*_i}\{RHS(S^*_i, E, \tau)\}$, and the expression for $b_i$ is given by equation (5.2.35), which is derived at the end of this section.

Substituting $K(S^*_i, E, \tau)$ and $K'(S^*_i, E, \tau)$ into equation (5.2.32), we obtain

```
$S_{i+1}^* = S^*_i - \frac{RHS(S^*_i, E, \tau) - LHS(S^*_i, E, \tau)}{b_i - 1} = S^*_i - \frac{RHS(S^*_i, E, \tau) - (S^*_i - E)}{b_i - 1} = \frac{b_i S^*_i - RHS(S^*_i, E, \tau) + E}{b_i - 1}$
```

The final iterative algorithm for the American call is

```
$S_{i+1}^* = \frac{E + RHS(S^*_i, E, \tau) - b_i S^*_i}{1 - b_i}, \quad (5.2.34)
```

where we can use $S^*_i = E$ for the initial estimate of the critical value, computer code below:

## The Expression for $b_i$

Here, we derive the term $b_i$ which is used in equation (5.2.34),

```
$b_i = \frac{\partial(S^*_i, E, \tau)}{\partial S^*_i} + \frac{1}{\gamma_2}\{1 - \exp(-q\tau)N_1(d_1(S^*_i))\}$.
```

We will now quote the following results are derived in Appendix A:

- Appendix A, equation (A.1.3): $n(d_1(S^*_i)) = \frac{\partial d_1(S^*_i)}{\partial S^*_i}$
- Appendix A, equation (A.1.6): $\frac{\partial d_1(S^*_i)}{\partial S^*_i} = \frac{1}{\sigma\sqrt{\tau}}$
- Appendix A, equation (A.3.2): $\Delta_c = \frac{\partial c(S^*_i, E, \tau)}{\partial S^*_i} = \exp(-q\tau)N_1(d_1(S^*_i))$.

Substituting these results into the above expression, we obtain

```
$b_i = \exp(-q\tau)N_1(d_1(S^*_i)) + \frac{1}{\gamma_2} \frac{\exp(-q\tau)N_1(d_1(S^*_i))}{\gamma_2} - \frac{\exp(-q\tau)n(d_1(S^*_i))}{\gamma_2\sqrt{\tau}}$
```

which can be rearranged to yield

```
$b_i = \exp(-q\tau)N_1(d_1(S^*_i)) \left\{ 1 - \frac{1}{\gamma_2} \right\} + \frac{1}{\gamma_2} \left\{ 1 - \frac{\exp(-q\tau)n(d_1(S^*_i))}{\sqrt{\tau}} \right\} \quad (5.2.35)
```

## American Put Options

For put options, we need to solve (5.2.32) which is

```
$E - S_i^{**} = p(S_i^{**}, E, \tau) - \frac{S_i^{**}}{\gamma_1} \{ 1 - N_1(d_1(S_i^{**}))\}\exp(-q\tau)$
```

If we let $S_i^{**}$ denote the hit approximation to the critical asset value $S^{**}$, then we can represent the LHS of the equation by

```
$LHS(S_i^{**}, E, \tau) = E - S_i^{**}$
```

and the right-hand side of the equation by

```
$RHS(S_i^{**}, E, \tau) = p(S_i^{**}, \tau) - \frac{S_i^{**}}{\gamma_1} \{ 1 - N_1(-d_1(S_i^{**}))\}\exp(-q\tau)$
= p(S_i^{**}, E, \tau) - \frac{S_i^{**}}{\gamma_1} \{ 1 - N_1(d_1(S_i^{**}))\}\exp(-q\tau)$
= p(S_i^{**}, E, \tau) - \frac{S_i^{**}}{\gamma_1} \{ 1 - \exp(-q\tau) + N_1(d_1(S_i^{**}))\}\exp(-q\tau)$
```

We denote $K(S_i^{**}, E, \tau) = RHS(S_i^{**}, E, \tau)$ and using Newton's method, we obtain

```
$S_{i+1}^{**} = S_i^{**} - \frac{K(S_i^{**}, E, \tau)}{K'(S_i^{**}, E, \tau)} \quad (5.2.36)
```

where before

```
$K'(S_i^{**}, E, \tau) = \frac{\partial}{\partial S_i^{**}} RHS(S_i^{**}, E, \tau)\}$
```

So $K'(S_i^{**}, E, \tau) = 1 + b_i$, where $b_i = [\partial(RHS(S_i^{**}, E, \tau))]/\partial S_i^{**}$, and the expression for $b_i$ is given by equation (5.2.38), which is derived at the end of this section.

Equation (5.2.36) can therefore be written as

```
$S_{i+1}^{**} = S_i^{**} - \frac{(RHS(S_i^{**}, E, \tau) - LHS(S_i^{**}, E, \tau))}{1 + b_i}$
= \frac{S_i^{**}(1 + b_i) - RHS(S_i^{**}, E, \tau) + E - S_i^{**}}{1 + b_i}$
```
