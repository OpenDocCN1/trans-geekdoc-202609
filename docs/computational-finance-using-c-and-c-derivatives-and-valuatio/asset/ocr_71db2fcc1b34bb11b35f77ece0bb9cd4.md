# Two-asset Options Section | 6.5 183

of the jump and the probability of the jump are the same as the CRR binomial model.
The attractive feature of the BEGKR binomial lattice model is that it can be easily generalized to describe a model consisting of k assets. Here, we will merely quote the results in Kamrad and Ricken (1991). As it is assumed that the asset process follows a multivariate lognormal distribution. Let $\mu_i = r - \sigma_i^2/2$, and $\sigma_i$ be the instantaneous mean and variance respectively $(i=1, 2, \dots, k)$ and let $ho_{ij}$ be the correlation between assets $i$ and $j$. The binomial model now requires $2^k$ possible jumps in the time interval $\Delta t$. Let $m$ denote the state of the process at $\Delta t$ with $p_m$ representing the probability of state $m$ ($m=1, \dots, 2^k$). The probabilities of these jumps are given by

```
$p_m = \left\{1 + \Delta t \sum_{i=1}^k \frac{\mu_i}{\sigma_i} + \sum_{i=1}^k \sum_{j=i+1}^k (x_{ij}^* \rho_{ij})\right\\}, m=1, 2, \dots, 2^k, k \ge 2,$
```

where $x_{im}=1$ if asset $i$ has an up-jump in state $m$, and $x_{im}=-1$ if asset $i$ has a down-jump in state $m$. In addition, $x_{ij}^*=1$ if asset $i$ and asset $j$ jump in the same direction in state $m$, and $x_{ij}^*=-1$ if asset $i$ and asset $j$ jump in the opposite direction in state $m$.

# 6.5 TWO-ASSET OPTIONS

In this section, we consider options based on the underlying prices of two assets, $S_1$ and $S_2$. We give analytic formulae to price European exchange options and those based on the maximum or minimum of two assets. In addition, we show how to construct binomial latices for the valuation of two-asset American style options.

# 6.5.1 European Exchange Options

A European exchange option gives the holder the right to exchange one asset for another at maturity

```
$dS_A^A = S_A^A \mu_A dt + S_A^A \sigma_A dW_A^A$,n$dS_B^B = S_B^B \mu_B dt + S_B^B \sigma_B dW_B^B$.
```

where $S_A^A$ denotes the value of asset $A$ at time $t$ and $S_B^B$ denotes the value of asset $B$ at time $t$ - the other symbols have their obvious meanings.
We will now find the value, at time $t_0$, of an option which gives the holder the right to exchange asset $A$ for asset $B$ at maturity $T$. The payoff of maturity is $H_T = \max(S_B^B - S_A^A, 0)$.
If we use the value of asset $A$ as the numeraire, then from equation (4.2.1), the value of the exchange option at time $t_0$ is

```
$V(t_0) = S_A^A E^Q \left[ \frac{\max(S_B^B - S_A^A, 0)}{S_T^A} \right]$
```