
## Other financial derivatives

Now, from Eq. (7.2.35) we have:

```
$E^Q [F(t_{k-1}, t_{k-1}, t_k)]$
$$= E^Q \left[ F(t_0, t_{k-1}, t_k) \exp\left((t-t_0)\mu_k - \frac{(t_{k-1}-t_0)\sigma_k^2}{2} + \sigma_k W_{k-1}^i\right) \right]$$
$$= F(t_0, t_{k-1}, t_k) \exp((t_{k-1}-t_0)\mu_k)$$
$$=times E^Q \left[ \exp\left(-\frac{(t_{k-1}-t_0)\sigma_k^2}{2} + \sigma_k W_{k-1}^i\right) \right]$$
$$= F(t_0, t_{k-1}, t_k) \exp((t_{k-1}-t_0)\mu_k) \quad (7.2.37)$$
```

where, as before we have the expectation given in Appendix D.2.
By Expanding Eq. (7.2.37) to first order obtain:

```
$E^Q [F(t_{k-1}, t_{k-1}, t_k)]$
$$= F(t_0, t_{k-1}, t_k) + F(t_{k-1}, t_k)(t_{k-1}-t_0)\mu_k \quad (7.2.38)$$
```

Substituting Eq. (7.2.38) into Eq. (7.2.36), we obtain a general expression for the value of the coupon payment:

```
$V_{t_0} = \tau \left\{ F(t_0, t_{k-1}, t_k) + F(t_0, t_k, t_k)(t_{k-1}-t_0)\mu_k \right\} \quad (7.2.39)$
```

We will consider the cases of early and late coupon payments.

### Early coupon payment

Let us consider the case when $i = k - 1$. From Eq. (7.2.50):

```
$$\mu_k = \frac{\sigma_k^2 F(t, t_{k-1}, t_k)}{1 + \tau F(t, t_{k-1}, t_k)}$$
```

First we freeze the forward rates in $\mu_k$ so we obtain the following:

```
$$\mu_k = \frac{\sigma_k^2 F(t, t_{k-1}, t_k)}{1 + \tau F(t, t_{k-1}, t_k)}$$
```

Substituting for $\mu_k$ in Eq. (7.2.39) we obtain:

```
$V_{t_0} = DF(t_0, t_k) \tau \left\{ F(t_0, t_{k-1}, t_k) + (t_{k-1}-t_0)\frac{\sigma_k^2 \tau_k F^2(t_0, t_{k-1}, t_k)}{1 + \tau F(t_0, t_{k-1}, t_k)} \right\}$
```

(see Brito and Mercurio, 2001, p. 387, and Hull, 2003).

### Late coupon payment

We consider the case when $i = k + 1$. From Eq. (7.2.66):

```
$$\mu_k = \frac{\rho t_{k,k+1}\sigma_k\sigma_{k+1}F(t, t_k, t_{k+1})}{1 + \tau F(t, t_k, t_{k+1})}$$
```

Freezing the forward rates we obtain:

```
$$\mu_k = \frac{\tau\rho_{k,k+1}\sigma_k\sigma_{k+1}F(t_0, t_k, t_{k+1})}{1+\tau F(t_0, t_k, t_{k+1})}$$
```

Substituting for $\mu_k$ in Eq. (7.2.39) we obtain:

```
$V_{t_0} = DF(t_0, t_{k+1}) \times \tau P \left\{ F(t_0, t_{k-1}, t_k) - \frac{\tau\rho_{k,k+1}\sigma_k\sigma_{k+1}F(t_0, t_{k-1}, t_k)F(t_0, t_k, t_{k+1})}{1+\tau F(t_0, t_k, t_{k+1})} \right\}$
```

## 7.2.3 Timing adjust

In this section we derive expressions for the drift of the forward rate $F(t, t_{k-1}, t_k)$ under various probability measures. We will denote the time $t$ of a zero coupon bond with 1 unit of currency at maturity $t$ by $DF(t)$. For convenience we will also use the shortened notation $F_k = F(t, t_{k-1}, t_k)$ and $DF_k = DF(t, t_k)$.

The probability measure under which all tradable assets are priced relative to the bond price $DF_k$ (that is, $DF_k$ is the numeraire) will be denoted by $\mathbb{Q}^k$; under this probability the relative prices will be martingales. We will also denote Brownian motion under probability measure $\mathbb{Q}^k$ by $W^k$.

Case $i = k$

Here the maturity of the numeraire $DF_k$ is at the expiry of the forward rate $F_k$. Since $(1+\tau F_k)$ is a tradable relative price, $(1+\tau F_k)/DF_k$, is a martingale under $\mathbb{Q}^k$ and thus has zero drift. Also $DF_i(1+\tau F_k)/DF_k = 1+\tau F_k$ and since $\tau$ and 1 are constants, $F_k$ must be a martingale under $\mathbb{Q}^k$. Thus the process for $F_k$ has zero drift and is:

```
$dF_k = F_k\sigma_k dW^k \quad (7.2.40)$
```

For the general case in which $i \neq k$, the process followed by $F_k$ is:

```
$dF_k = F_k\mu_k dt + F_k\sigma_k dW^i \quad (7.2.41)$
```

where $\mu_k$ is a drift that needs to be determined. Equation (7.2.41) can then be rewritten as:

```
$dF_k = F_k\sigma_k \left( \frac{\mu_k}{\sigma_k} dt + dW^i \right) \quad (7.2.42)$
```

Comparing Eqs. (7.2.41) and (7.2.42) we have:

```
$dW^k = \frac{\mu_k}{\sigma_k} dt + dW^i \quad (7.2.43)$
```

This equation gives the relation between Brownian motions under probability measures $\mathbb{Q}^k$ and $\mathbb{Q}^i$. We will now show how to compute the value of $\mu_k$.

### Other financial derivatives

Case $i < k$

Here we consider situations in which the maturity of the numeraire $DF_i$ is before the expiry of the forward rate $F_k$.

$i = k - 1$

In this case $DF_{k-1}$ is the numeraire, the forward rate is $F_k = F(t, t_{k-1}, t_k)$, and the numeraire matures at time $t_{k-1}$, while the forward rate has expiry $t_k$.

Since $DF_k$ is a tradable relative price, $\phi = DF_k/DF_{k-1}$, is a martingale under $\mathbb{Q}^{k-1}$, and thus has zero drift. Now

```
$\phi = \frac{DF_k}{DF_{k-1}} \frac{1}{1 + \tau F_k} \quad (7.2.44)$
```

where we have used:

```
$DF_{k-1} = DF_k(1 + \tau F_k) \quad (7.2.45)$
```

Let the stochastic process followed by $F_k$ under $\mathbb{Q}^{k-1}$ be:

```
$dF_k = F_k \mu_k dt + F_k \sigma_k dW^{k-1} \quad (7.2.46)$
```

and the drift, $\mu_k$, is to be determined. Using Ito we have:

```
$\frac{\partial \phi}{\partial F_k} dF_k + \frac{1}{2} \frac{\partial^2 \phi}{\partial F_k^2} E[(dF_k)^2], E[(dF_k)^2] = \sigma_k^2 F_k^2 dt \quad (7.2.47)$
```

where from Eq. (7.2.44)

```
$\frac{\partial \phi}{\partial F_k} = \frac{\tau}{1 + \tau F_k}, \frac{\partial^2 \phi}{\partial F_k^2} = \frac{-2\tau}{(1 + \tau F_k)^3} \quad (7.2.48)$
```

Substituting the values in Eq. (7.2.48) into Eq. (7.2.47) we obtain:

```
$d\phi = - \frac{\tau \phi}{1 + \tau F_k} [F_k \mu_k dt + F_k \sigma_k dW^{k-1}] + \frac{\tau^2 \phi \sigma_k^2 F_k^2}{2(1 + \tau F_k)^2} \quad (7.2.49)$
```

which can be rearranged as:

```
$d\phi = - \left( \frac{\tau F_k \mu_k \phi}{1 + \tau F_k} + \frac{\phi \phi \sigma_k^2 F_k^2}{(1 + \tau F_k)^2} \right) dt - \frac{\tau \phi \sigma_k}{1 + \tau F_k} dW^{k-1}$
```

Now since Eq. (7.2.49) is driftless

```
$\left( \frac{\tau F_k \mu_k \phi}{1 + \tau F_k} + \frac{\phi \phi \sigma_k^2 F_k^2}{(1 + \tau F_k)^2} \right) dt = 0$
```

and

```
$\mu_k = - \frac{\tau \sigma_k^2 F_k}{1 + \tau F_k} \quad (7.2.50)$
```

Substituting Eq. (7.2.50) into Eq. (7.2.46):

```
$dF_k = \frac{\tau \sigma_k^2 F_k^2}{1+\tau F_k} dt + F_k\sigma_k dW^{k-1}$
```

or

```
$dF_k = F_k\sigma_k \left( \frac{\tau F_k}{1+F_k} dt + dW^{k-1} \right) \quad (7.2.51)$
```

Comparing Eqs. (7.2.51) and (7.2.40) thus yields:

```
$dW^k = \frac{\mu_k}{\sigma_k} dt + dW^{k-1} \quad (7.2.52)$
```

which is the relationship between Brownian motions $dW^{k-1}$ and $dW^k$ under the respective probability measures $\mathbb{Q}^{k-1}$ and $\mathbb{Q}^k$.

$i \le k-2$

Let the stochastic process followed by $F_k$ under $\mathbb{Q}^{k-2}$ be:

```
$dF_k = F_k\sigma_k dt + \sigma_k dW^{k-2} \quad (7.2.53)$
```

Where $dW^{k-2}$ is Brownian motion under probability measure $\mathbb{Q}^{k-2}$, and the drift, $\mu_k$, is unknown. Replacing $k$ with $k-1$ in Eq. (7.2.52) gives:

```
$dW^{k-1} = \frac{\tau\sigma_{k-1} F_{k-1}}{1+F_{k-1}} dt + dW^{k-2} \quad (7.2.54)$
```

and using Eq. (7.2.54) to substitute for $dW^{k-1}$ in Eq. (7.2.52) we obtain:

```
$dW^k = \frac{\tau F_k}{1+\tau F_k} dt - \frac{\tau\sigma_{k-1} F_{k-1}}{1+F_{k-1}} dt + dW^{k-2} \quad (7.2.55)$
```

Replacing $dW^k$ in Eq. (7.2.40) with that given in Eq. (7.2.55):

```
$dF_k = F_k\sigma_k \left( \frac{\tau F_k}{1+\tau F_k} dt - \frac{\tau\sigma_{k-1} F_{k-1}}{1+F_{k-1}} dt \right) + F_k\sigma_k dW^{k-1} \quad (7.2.56)$
```

so the drift is:

```
$\mu_k = \frac{\tau\sigma_k^2 F_k}{1+F_k\tau} - \frac{\tau\sigma_k\sigma_{k-1} \rho_{k,k-1} F_{k-1}}{1+F_{k-1}\tau} \quad (7.2.57)$
```

The following general expression can be derived in a similar manner:

```
$dF_k = \sigma_k F_k \sum_{j=i+1}^k \frac{\rho_{k,j}\tau\sigma_j F_j}{1+F_j\tau} dt + \sigma_k dW^i \quad (7.2.58)$
```

where all the symbols have the same meanings as before, but now $i$ can take any value less than $k$.

### Case $i > k$

We now consider the case when the maturity of the numeraire $DF_i$ is after the expiry of the forward rate $F_k$.

$i = k+1$

Here $DF_{k+1}$ is the numeraire and $F_k$ is the forward rate which starts at time $t_{k-1}$ and ends at time $t_k$.

Since $DF_{k-1}$ is a tradable price, $\phi = DF_{k-1}/DF_{k+1}$, is a martingale under $Q^{k+1}$, and has zero drift.

Now:

```
$\phi = \frac{DF_{k-1}}{DF_{k+1}} = (1+\tau F_k)(1+\tau F_{k+1})$
```

where the processes for $F_{k+1}$ and $F_k$ are are

```
$dF_{k+1} = F_{k+1}\sigma_{k+1}dW^{k+1}$
```

```
$dF_k = F_k\mu_k dt + F_k\sigma_k dW^k \text{ (actually } F_k\mu_k dt + F_k\sigma_k dW^k\text{)}$
```

and the drift, $\mu_k$, is to be determined. Using Ito:

```
$\frac{\partial \phi}{\partial F_k} dF_k + \frac{1}{2} \frac{\partial^2 \phi}{\partial F_k^2} E[(dF_k)^2], E[(dF_k)^2] = \sigma_k^2 F_k^2 dt \quad (7.2.59)$
```

(Note: The provided OCR text cut off or contained repetitions at the end; I have processed the available logical flow based on the instructions).
