we have used similar notation to that used in Eq. (7.2.12), with

$FLT_1(t) = P_1(DF_1(t, t_k) - DF_1(t, t_n)) \quad (7.2.22)$

and

$FLT_2(t) = P_2(DF_2(t, t_k) - DF_2(t, t_n)) \quad (7.2.23)$

InEqs. (7.2.22) and (7.2.23) $P_1$ is the principal for leg 1 and $P_2$ is the principal for leg 2. The time of the next coupon payment for leg 1 is $t_{k_1}$, while for leg 2 is $t_{k_2}$; in addition we have used the fact that $t_{n_1} = t_{n_2}$.

We will now consider the case in which the basis swap has been traded at time $t$, and will also assume that $C_1 = C_2 = 0$ and $t_{k_1} = t_{k_2}$. In addition, we will specify that principal exchange occurs at the start (time) and end (time) of the swap.

The cash flows associated with principal exchange at the start of the swap are in the opposite direction to those for the remainder of the swap; Hull (2003).

$FLT_1(t) = P_1 - P_1DF_1(t, t_n) + \{-P_1 + P_1DF_1(t, t_n)\} \quad (7.2.24)$

and

$FLT_2(t) = P_2 - P_2DF_2(t, t_n) + \{-P_2 + P_2DF_2(t, t_n)\} \quad (7.2.25)$

where the principal exchange terms are in the curly brackets, and use discount factors $DF_1(t, T)$ from the *main currency yield curve* (in this GBP) rather than $DF_1(t, T)$ or $DF_2(t, T)$.

It can be seen from Eq. (7.2.21) that principal exchange at the start of the swap causes leg 2 to contribute the *positive* $P_2$ to the value of the swap, while leg 1 contributes the *negative* $P_2$ to the value. In contrast, principal exchange at the end of the swap results in leg 2 contributing the *negative* $-P_2DF(t, t_n)$ to the swap value, while leg 1 contributes the *positive* $P_1DF(t, t_n)$. If $P_1 = P_2$ then principal exchange does not affect the value of the basis swap. It can also be seen from Eq. (7.2.24) that if leg 1 used the *main GBP* yield curve instead of the main LIBOR curve, then $DF_1(t, t_n) = DF(t, t_n)$ which would result in $FLT_1(t) = 0$. Similarly $DF_2(t, t_n) = DF(t, t_n)$ would mean $FLT_2(t) = 0$.

If the valuation time $t$ is after the date has started, Eq. (7.2.21) can be used to price the basis swap, but Eqs. (7.2.24) and (7.2.25) need to be modified as follows:

$FLT_1(t) = P_1DF_1(t, t_k) - P_1DF_1(t, t_n) + \{P_1DF_1(t, t_n)\} \quad (7.2.26)$

and

$FLT_2(t) = P_2DF_2(t, t_k) - P_2DF_2(t, t_n) \quad (7.2.27)$

We will now consider how the timing of the coupon payment in relation to its associated forward rate affects the *present value*, $V_0$, of the coupon.