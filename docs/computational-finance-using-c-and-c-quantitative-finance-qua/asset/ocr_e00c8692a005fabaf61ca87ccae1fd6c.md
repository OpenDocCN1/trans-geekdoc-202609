and the product rule

$d(X_1X_2) = X_2 dX_1 + X_1 dX_2 + E[dX_1dX_2]$

Brownian motion with one source of randomness

For the special case where $X_1$ is Brownian motion and $X_2$ has no random term we have:

$dX_1 = X_1\mu_1 dt + X_1\sigma_1 dW_1 \quad dX_2 = X_2\mu_2 dt$

Now

$E[dX_1dX_2] = E[(X_1\mu_1 dt + X_1\sigma_1 dW_1)X_2\mu_2 dt] \\n = X_1X_2\mu_1\mu_2 dt^2 + X_1X_2\sigma_1\mu_2 dt dX_2 E[dW_1] \\n = 0$

where we have ignored terms in $dt$ with order higher than 1, and used $E[dW_1] = 0$.

Therefore Eq. (2.6.2) becomes:

$d(X_1X_2) = X_2 dX_1 + X_1 dX_2$

$d(X_1X_2) = X_2(X_1\mu_1 dt + X_1\sigma_1 dW_1) + X_1X_2\mu_2 dt$

So we obtain:

$d(X_1X_2) = (X_1X_2)(\mu_1 + \mu_2) dt + X_1X_2\sigma_1 dW_1$

# 2.6.2 Ito quotient rule

Here $\phi = \phi(X_1/X_2)$ and the partial derivatives are as:

$$\frac{\partial\phi}{\partial X_1} = \frac{1}{X_2}, \quad \frac{\partial\phi}{\partial X_2} = -frac{X_1}{X_2^2}, \quad \frac{\partial^2\phi}{\partial X_1^2} = 0,$

$$\frac{\partial^2\phi}{\partial X_2^2} = \frac{X_1}{X_2^3}, \quad \frac{\partial^2\phi}{\partial X_2\partial X_1} = -\frac{1}{X_2^2}$

Therefore using Eq. (2.6.1)

$$d\phi = \frac{dX_1}{X_2} - X_1\frac{dX_2}{X_2^2} + \frac{1}{2}\left[\frac{2X_1}{X_2^3}dX_2^2 - 2\frac{dX_1dX_2}{X_2^2}\right]$

We obtain the following expression for the quotient rule:

$$d(\\frac{X_1}{X_2}) = (\frac{X_1}{X_2})\left[\frac{dX_1}{X_1} - \frac{dX_2}{X_2} + E(\frac{dX_2}{X_2})(\frac{dX_2}{X_2})\right] \\n - E[\left(\frac{dX_1}{X_1})(\frac{dX_2}{X_2})\right]]$$