# Single asset American options

and for vanilla put options:

$f_{n_i,j} = \max(E - j\Delta S, 0), \quad j = 0, \dots, n_s - 1$

This is illustrated in Fig. 5.5 for a vanilla put option with current asset value $S_0 = 20$, strike, $E = 25$, and maturity $	au = 2$. The grid asset price spacing $\Delta S = 5$, and the time increment is $\Delta t = 0.2$. At option maturity, corresponding to time index $i = 10$, the value of the put option is zero for all asset indices $i \geq 5$.

# Computation of the options at a given time instant

Having found the option boundary we are now in a position to solve Eq. (5.4.14) at time instant $t_i = i\Delta t$.

First we note that $f_{i,0} = f_{BL}$ and $f_{i,n_s-1} = f_{BU}$ Eq. (5.4.14) only needs to be solved for values of the asset index $j$ in the range $1$ to $j = n_s - 2$. We now deal with the following situations:

+   * Case 1: $j = 1$, the asset line just above the lower boundary
* Case 2: $j = n_s - 2$, the asset line just below the upper boundary
* Case 3: all other asset grid lines not included in Case 1 or Case 2

and consider the form that Eq. (5.4.14) takes under each condition.

Case 1: $j = 1$
Substituting $j = 1$ into Eq. (5.4.14) we obtain:

$a_{1,0} + b_1f_{1,1} + c_1f_{1,2} = \tilde{a}_1f_{1,0} + \tilde{b}_1f_{1,1} + \tilde{c}_1f_{1,2}$

Now, since $f_{1,0} = f_{BL}$, this becomes:

$b_{1,1} + c_1f_{1,2} = (\tilde{a}_1 - a_1)f_{BL} + \tilde{b}_1f_{1,1} + \tilde{c}_1f_{1,2}$

or equivalently:

$b_{1,1} + c_1f_{1,2} = R_{1,1}$ (5.4.22)

where

$R_{1,1} = (\tilde{a}_1 - a_1)f_{BL} + \tilde{b}_1f_{1,1} + \tilde{c}_1f_{1,2}$ (5.4.23)

Case 2: $j = n_s - 2$
Substituting $j = n_s - 1$ into Eq. (5.4.14) we obtain:

$a_{n_s-2}f_{n_s,n_s-3} + b_{n_s-2}f_{n_s,n_s-2} + c_{n_s-2}f_{n_s,n_s-1}$
$= \tilde{a}_{n_s-2}f_{1,n_s-3} + \tilde{b}_{n_s-2}f_{1,n_s-2} + \tilde{c}_{n_s-2}f_{1,n_s-1}$

Since $f_{n_i,-1} = f_{BU}$ this gives us:

$a_{n_s-2}f_{n_s,n_s-3} + b_{n_s-2}f_{n_s,n_s-2}$
$= \tilde{a}_{n_s-2}f_{1,n_s-3} + \tilde{b}_{n_s-2}f_{1,n_s-2} + (\tilde{c}_{n_s-2} - c_{n_s-2})fBU$