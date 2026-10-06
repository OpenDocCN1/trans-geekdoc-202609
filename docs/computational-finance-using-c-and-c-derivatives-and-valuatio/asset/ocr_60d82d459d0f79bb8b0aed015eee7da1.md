# Lattice Methods for Vanilla Options Section | 5.3 111

where the change in asset price over the time interval $\Delta t$ is denoted by $\Delta S = S_{t+\Delta t} - S_t$. This elementary result sometimes is used without proof, see, for example, Hull (1997) page 344. The proof is simple,

$$Var[S_{t+\Delta t}] = Var[S_t + \Delta S] = Var[\Delta S].$$

where we have used

$$Var[a + bG] = b^2Var[G]$, this time with $a=0$ and $b=1.$$$

To expressions for the mean and variance of $S_{t+\Delta t}$, we simply substitute equation (5.3.5) into equation (5.3.6) and obtain

$$E[S_{t+\Delta t}] = S_t \exp(r\Delta t).$$ (5.3.9)

and substituting equation (5.3.4) into equation (5.3.7) gives

$$Var[S_{t+\Delta t}] = S_t^2 \exp(2r\Delta t)\{\exp(r^2\Delta t) - 1\}.$$ (5.3.10)

Since we are modelling asset price movements with a binomial lattice, the asset price, $S_t$, at any given node is only permitted to jump-up or jump-down in value over the next step $\Delta t$. We will assume that the new asset price, $S_{t+\Delta t}$, is $S_tu$ for an up-jump and $S_td$ for a down-jump; where $u$ and $d$ are constants that apply to all lattices. If we then define the probability of an up-jump by $p$, then the probability of a down-jump (by definition) is $1-p.$

Now that we have the lattice parameters we will use to match the first two moments of the lognormal distribution. This results in the following equation for our:

$$E[S_{t+\Delta t}] = p_tu + (1-p)S_td = S_t \exp(r\Delta t).$$ (5.3.11)

The corresponding equation for the variance requires a little more

$$Var[S_{t+\Delta t}] = E[(S_{t+\Delta t})^2] - (E[S_{t+\Delta t}])^2.$$$ (5.3.12)

Since

$$E[(S_{t+\Delta t})^2] = pS_tu^2 + (1-p)S_td^2 = S_t^2\{u^2 + (1-p)d^2\$$ (5.3.13)

and, from equation (5.3.9), we

$$E[(S_{t+\Delta t})^2] = (S_t \exp(r\Delta t))^2 = S_t^2 \exp(2r\Delta t).$$ (5.3.14)

we can substitute equation (5.3.13) and equation (5.3.14) into equation (5.3.12) to obtain

$$Var[S_{t+\Delta t}] = S_t^2\{pu^2 + (1-p)d^2\} - S_t^2 \exp(2r\Delta t).$$ (5.3.15)