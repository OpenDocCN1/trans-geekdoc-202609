# Multiset options

189

$$exp(r\Delta t) \sim 1 + r\Delta t$$
$$$u = exp(\sigma\sqrt{\Delta t}) \sim 1 + \sigma\sqrt{\Delta t} + \frac{\sigma^2}{2}\Delta t$$
n$$$d = exp(\sigma\sqrt{\Delta t}) \sim 1 - \sigma\sqrt{\Delta t} + \frac{\sigma^2}{2}\Delta t$$

so

$$exp(r\Delta t) - d \sim r\Delta t + \sigma\Delta t - \frac{\sigma^2}{2}\Delta t$$

and

$$u - d \sim 2\sigma\sqrt{\Delta t}$$

So

$$p_u = \frac{exp(r\Delta t)}{u - d} \sim \frac{r\Delta t + \sigma - \sigma^2/2\Delta t}{2\sigma\sqrt{\Delta t}}$

which simplifies to

$$p_u = \frac{1}{2} \left[ 1 + \frac{\mu\sqrt{\Delta t}}{\sigma} \right]$$$

and therefore

$$p_d = 1 - p_u = \frac{1}{2} \left[ 1 - \frac{\mu\sqrt{\Delta t}}{\sigma} \right]$$$

where the expressions for $p_u$ and $p_d$ given in Eqs. (6.4.1) and (6.4.2), respectively. So we have shown, that to first order in $\Delta t$, both the size of the jump and the probability of the jump are the same as the CRR binomial model.

The attractive feature of the BEGKR binomial lattice model is that it can easily be generalized to describe a model consisting of $k$ assets. Here we will merely quote the results in Kamrad and Ritchen (1991). As before it is assumed that the asset prices follow a multivariate lognormal distribution. Let $\mu_i = r - \sigma_i^2/2$, and $\sigma_i$ be the instantaneous mean and variance, respectively ($i = 1, 2, \dots, k$) and let $\rho_{ij}$ be the correlation between asset $i$ and asset $j$. The binomial model requires $2^k$ possible jumps in the time interval $\Delta t$ with $p_m$ representing the probability of state $m$ ($m=1,\dots, 2^k$). The properties of these jumps are now given by:

$$p_m = \left\{ 1 + \Delta t \sum_{i=1}^k x_{im}^{(k)} \frac{\mu_i}{\sigma_i} \right) + \sum_{i=1}^{k-1} \sum_{j=i+1}^k (x_{ij}^{(k)} \rho_{ij}) \right\}$$$

$$m = 1, 2, \dots, 2^k, k \geq 2$.$$

where $x_{im} = 1$ if asset $i$ has an up jump in state $m$, and $x_{im} = -1$ if asset $i$ has a down jump in state $m$. In addition $x_{ij}^{(m)} = 1$ if asset $i$ and asset $j$ have jumps in the same direction in state $m$, and $x_{ij}^{(m)} = -1$ if asset $i$ and asset $j$ have jumps in the opposite direction in state $m$.