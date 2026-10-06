
# 212 CHAPTER | 7 Other Financial Derivatives

a zero coupon bond which pays 1 unit of currency at maturity $t_i$ by $DF(t,t_i)$. For convenience, we will also use the shortened notation $F_k = F(t,t_{k-1},t_k)$ and $DF_i = DF(t,t_i)$.

The probability measure under which all tradable assets are priced relative to the zero coupon bond price $DF_k$ (that is $DF_k$ is the numeraire) will be denoted by $Q^k$; under this probability measure, the relative prices are martingales. We will also denote Brownian motion under probability measure $Q^t$.

### Case $i = k$

Here, the numeraire of $DF_k$ is at the expiry of the forward rate $F_k$.

Since $DF_k(1+\tau F_k)$ is a tradable relative price, $(1+\tau F_k)/DF_k$ is a martingale under $Q^k$ and thus has zero drift.

Also $DF_k(1+\tau F_k)/DF_k = 1+\tau F_k$, and since $\tau$ and $1$ are constants, $F_k$ must be a martingale under $Q^k$. The process for $F_k$ has zero drift and

$ $dF_k = F_k \sigma_k dW_k$.

For the general case in $i \neq k$, the process followed by $F_k$ is

$ $dF_k = F_k \mu_k dt + F_k \sigma_k dW^k$.

where $\mu_k$ is a drift needs to be determined. Equation (7.2.41) can be rewritten as

$ $dF_k = F_k \sigma_k \left( \frac{\mu_k}{\sigma_k} dt + dW^i \right).$

Comparing equations (7.2.41) and (7.2.42), we have

$ $dW^k = \left( \frac{\mu_k}{\sigma_k} \right) dt + dW^i$.

This equation gives the relation between Brownian motions under probability measures $Q^k$ and $Q^t$. We will now show how to compute the value of $\mu_k$.

### Case $i < k$

Here, we consider situations in which the numeraire of $DF_i$ is before the expiry of the forward rate $F_i$.

#### $i = k-1$

In this case, $DF_{k-1}$ is the numeraire, the forward rate is $F_k = F(t,t_{k-1},t_k)$, and the numeraire matures at time $t_{k-1}$, while the forward rate has expiry $t_k$.

Since $DF_k$ is a tradable relative price, $\phi = DF_k/DF_{k-1}$ is a martingale under $Q^{k-1}$ and thus has zero drift.

Now

$ $\phi = \frac{DF_k}{DF_{k-1}} = \frac{1}{1+\tau F_k}$.

$ $DF_{k-1} = DF_k(1+\tau F_k).$

where we used The stochastic process followed by $F_k$ under $Q^{k-1}$ be

$ $dF_k = F_k \mu_k dt + F_k \sigma_k dW^{k-1}$

and the drift, $\mu_k$, is to be determined.

# Interest Rate Derivatives Section | 7.2 213

Using Ito, we have

$ $d\phi = \frac{\partial\phi}{\partial F_k}dF_k + \frac{1}{2}\frac{\partial^2\phi}{\partial F_k^2}E[(dF_k)^2], \text{ where } E[(dF_k)^2] = \sigma_k^2 F_k^2 dt, \quad (7.2.47)$

where from equation (7.2.44)

$ $\frac{\partial\phi}{\partial F_k} = -\frac{\tau}{(1+\tau F_k)^2}, \frac{\partial^2\phi}{\partial F_k^2} = \frac{2\tau^2}{(1+\tau F_k)^2}. \quad (7.2.48)$

Substituting the values in (7.2.48) into (7.2.47), we obtain

$ $d\phi = -\frac{\tau}{(1+\tau F_k)}F_k\mu_k dt + F_k\sigma_k dW^{k-1} + \frac{1}{2}\frac{\tau^2\sigma_k^2 F_k^2}{(1+\tau F_k)^2}.$

which can be re-arranged

$ $d\phi = -\frac{\tau F_k\mu_k}{1+\tau F_k}dt + \frac{\tau^2\sigma_k^2 F_k^2}{(1+\tau F_k)^2}dt - \frac{\tau F_k\sigma_k}{1+\tau F_k}dW^{k-1}. \quad (7.2.49)$

Now since equation (7.2.49) is driftless,

$ $$-\frac{\tau F_k\mu_k}{1+\tau F_k} + \frac{\tau^2\sigma_k^2 F_k^2}{(1+\tau F_k)^2}dt = 0$$

and

$ $\mu_k = \frac{\tau\sigma_k^2 F_k^2}{1+\tau F_k}. \quad (7.2.50)$

Substituting equation (7.2.50) into equation (7.2.46),

$ $dF_k = \frac{\tau\sigma_k^2 F_k^2}{1+\tau F_k}dt + F_k\sigma_k dW^{k-1}$

or

$ $dF_k = F_k\sigma_k \frac{\tau\sigma_k F_k}{1+\tau F_k}dt + F_k\sigma_k dW^{k-1}. \quad (7.2.51)$

Comparing equations (7.2.51) and (7.2.40) thus yields

$ $dW^k = \frac{\tau\sigma_k F_k}{1+\tau F_k}dt + dW^{k-1}. \quad (7.2.52)$

which is the relationship between the Brownian motions $dW^{k-1}$ and $dW^k$ under the respective probability measures $Q^{k-1}$ and $Q^k$.

Let the stochastic process follow by $F_k$ under $Q^{k-2}$ be

$ $dF_k = F_k\mu_k dt + F_k\sigma_k dW^{k-2}. \quad (7.2.53)$

where $dW^{k-2}$ is Brownian motion under probability measure $Q^{k-2}$, and the drift, $\mu_k$, is unknown.

# 214 CHAPTER | 7 Other Financial Derivatives

Replacing $k$ with $k-1$ in equation (7.2.52) gives

$ $dW^{k-1} = \frac{\sigma_{k-1}F_{k-1}}{1+\tau F_{k-1}}dt + dW^{k-2}, \quad (7.2.54)$

and using (7.2.54) to substitute for $dW^{k-1}$ in equation (7.2.52), we obtain

$ $dW^k = \frac{\sigma_k F_k}{1+\tau F_k}dt + \frac{\sigma_{k-1}F_{k-1}}{1+\tau F_{k-1}}dt + dW^{k-2}, \quad (7.2.55)$

Replacing $dW^k$ in equation (7.2.40) with that given in equation (7.2.55),

$ $dF_k = F_k\sigma_k(\frac{\sigma_k F_k}{1+\tau F_k}dt + \frac{\sigma_{k-1}F_{k-1}}{1+\tau F_{k-1}}dt), \quad (7.2.56)$

so the drift is

$ $\mu_k = \frac{\sigma_k^2 F_k}{1+\tau F_k} + \frac{\sigma_k\sigma_{k-1}F_{k-1}}{1+\tau F_{k-1}}, \quad (7.2.57)$

The general expression can be derived in a similar manner:

$ $dF_k = F_k\sigma_k \sum_{j=i+1}^k \frac{\sigma_j F_j}{1+F_j}dt + \sigma_k dW^i, \quad (7.2.58)$

where all the symbols have the same as before, but $i$ can take any integer value less than $k$.

### Case $i > k$

We now consider the case when the maturity of numeraire $DF_i$ is after the expiry of the forward rate $F_k$.

### Case $i = k+1$

Here, $DF_{k+1}$ is the numeraire and $F_k$ is the forward rate which starts at time $t_{k-1}$ and ends at time $t_k$. Since $DF_{k-1}$ is a tradable, its relative price, $\phi = DF_{k-1}/DF_{k+1}$, is a martingale under $Q^{k+1}$ and thus has zero drift.

Now

$ $\phi = \frac{DF_{k-1}}{DF_{k+1}} = (1+\tau F_k)(1+\tau F_{k+1}), \quad (7.2.59)$

where the processes for $F_k$ and $F_{k+1}$ are

$ $dF_k = F_k(1+\tau F_k)\sigma_k dW^{k+1}, \quad (7.2.60)$

$ $dF_k = F_k\mu_k dt + F_k\sigma_k dW^{k+1}, \quad (7.2.61)$

and the drift, $\mu_k$, is to be determined. Using Ito, we have

$ $\phi = \frac{\partial\phi}{\partial F_k}dF_k + \frac{\partial\phi}{\partial F_{k+1}}dF_{k+1} + \frac{1}{2}\sum_{i=k}^{k+1} \sum_{j=k}^{k+1} \frac{\partial^2\phi}{\partial F_i\partial F_j}E[dF_i, dF_j], \quad (7.2.62)$

# Interest Rate Derivatives Section | 7.2 215

where

$\frac{\partial\phi}{\partial F_k} = \tau(1+\tau F_{k+1}), \quad \frac{\partial\phi}{\partial F_{k+1}} = \tau(1+\tau F_k)$

$\frac{\partial^2\phi}{\partial F_k^2} = 0, \quad \frac{\partial^2\phi}{\partial F_{k+1}^2} = 0, \quad \frac{\partial^2\phi}{\partial F_k\partial F_{k+1}} = \tau^2.$

$E[dF_k, dF_{k+1}] = \rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1}dt, \quad (7.2.63)$

Substituting the values in (7.2.63) into equation (7.2.62), we obtain after expanding the terms in $d\phi$ and $dF_k$, we have

$ $d\phi = \tau(1+\tau F_{k+1})F_k\mu_k dt + F_k\sigma_k dW^{k+1} + \tau(1+\tau F_k)F_{k+1}\sigma_{k+1}dW^{k+1} + \tau^2\rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1}dt,$

and this can be re-expressed as

$ $d\phi = D + \tau(1+\tau F_{k+1})F_k\sigma_kdW^{k+1} + \tau(1+\tau F_k)F_{k+1}\sigma_{k+1}dW^{k+1}, \quad (7.2.64)$

where the drift $D$ in equation (7.2.64) is given by

$ $D = \tau(1+\tau F_{k+1})F_k\mu_k dt + \tau^2\rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1}dt. \quad (7.2.65)$

Now since $\phi$ is a martingale under $Q^{k+1}$, we know that $D=0$, and therefore equation (7.2.65) results in

$ $(1+\tau F_{k+1})F_k\mu_k dt = -\rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1}dt. \quad (7.2.66)$

This means that the drift is

$ $$\mu_k = \frac{\rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1}}{(1+\tau F_{k+1}}. \quad (7.2.67)$

Substituting for $\mu_k$ in equation (7.2.61)

$ $dF_k = F_k\sigma_k \left( \frac{\rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1} dt + dW^{k+1}}{(1+\tau F_{k+1})} \right). \quad (7.2.67)$

Comparing equation (7.2.67) with equation (7.2.40), we have

$ $dW^k = \frac{\rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1}}{(1+\tau F_{k+1})}dt + dW^{k+1}. \quad (7.2.68)$

which is the relationship between Brownian motions $dW^k$ and $dW^{k+1}$.

#### $i \ge 2$

The stochastic process followed by $F_k$ under $Q^{k+2}$ be

$ $dF_k = F_k\mu_k dt + F_k\sigma_kdW^{k+2}. \quad (7.2.69)$

where $W^{k+2}$ is Brownian motion under probability measure $Q^{k+2}$, and drift term $\mu_k$ is to be found.
