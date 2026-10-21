where $e_i$ is the current price of a pure state $i$ security that pays out $1 at maturity date if state $i$ occurs; $s_i$ is the value of the underlying security in state $i$; $c_i$ is the value of a European call option in state $i$; $d_i$ is the state discount factor that is non-increase with respect to wealth; $\pi_i$ is ex ante consensus probabilities that state $i$ occurs; $S_0$ and $B_0$ are current values of the underlying security and a portfolio containing all state securities, respectively.

Ritckhen (1985), Ritckhen and Kuo (1988) propose the application of the single-period linear-programming option model to handle multiple periods. Ritckhen and Kuo (1988) obtain identical upper bounds and tighter lower bounds than Ritckhen (1985). Ritckhen and Kuo (1989) further consider the additional preference restrictions on the investors with third order or above stochastic dominance criteria. They also apply a decreasing absolute risk aversion (DARA) dominance rule in a state preference context. With the two restrictions, the closed form analytical solutions for the option bounds are not obtained, but a simple numerical example are presented.

The behavior of the DARA lower bound for the option price is not wholly explored by Ritckhen and Kuo (1989). Basso and Pianca (1997) analyze the general rule of DARA dominance. They solve the optimization DARA problem in the case of three states of nature, proving that the optimal solution satisfies the nonlinear constraint as equality. This solution is obtained through an exponential-like utility function having constant absolute risk aversion (CARA).

Basso and Pianca (1997) reconsider the following maximization and minimization problem:

Minimize (or Maximize) $C_0 = \sum_{i=1}^n c_i e_i$,
subject to $\sum_{i=1}^n s_i e_i = S_0$ and $\sum_{i=1}^n e_i = B_0$
with $(e_1, e_2, e_3, \dots, e_n) \in D$, (24.17)

where the set $D$ depends on the stochastic dominance rule adopted and is determined by the assumptions made on the utility function. For example, given utility function with decreasing absolute risk-aversion (DARA) character, the set $D$ is constrained by:

+   - $e_i \geq 0$, $i = 1,2,\dots,n$
+   - $e_i \geq e_{i+1}$, $i = 1,2,\dots,n-1$
+   - $e_i e_{i+2} \geq e_{i+1}^2$, $i = 1,2,\dots,n-2$