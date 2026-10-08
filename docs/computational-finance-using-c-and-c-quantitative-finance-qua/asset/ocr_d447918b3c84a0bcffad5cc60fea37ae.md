European options

93

We will use some algebra to simplify this expression.

$P(m_{t_1,t_2}^X \leq b|X_{t_2}, X_{t_1})\n= \exp\left{\{\frac{4v\Delta t(b - X_{t_1}) - (X_{t_2} + X_{t_1} - 2b - v\Delta t)^2 + (X_{t_2} - X_{t_1} - v\Delta t)^2}{2\sigma^2\Delta t}}\right\right\
\= \exp\left{\{\frac{4v\Delta t(b - X_{t_1}) - (X_{t_2} - X_{t_1} - v\Delta t)^2 - 2(b - X_{t_1})^2}{2\sigma^2\Delta t}}\right\\
\= \exp\left{\{\frac{4v\Delta t(b - X_{t_1}) + 4(b - X_{t_1})(X_{t_2} - X_{t_1} - v\Delta t) + 4(b - X_{t_1})^2}{2\sigma^2\Delta t}}\right\\
\= \exp\left{\{\frac{2(b - X_{t_1})(b - X_{t_2})}{\sigma^2\Delta t}}\right\{\}$

which yields

$P(m_{t_1,t_2}^{\log(S)} \leq b|\log(S_{t_2}))\n= \exp\left{\{\{\frac{2(\log(B) - \log(S_{t_1}))(\log(B) - \log(S_{t_2}))}{\sigma^2\Delta t}}\right\{\} (4.5.19)

Equation (4.5.19) gives the probability of the option having been knocked out between times $t_1$ and $t_2$ even though the asset prices $S_{t_1}$ and $S_{t_2}$ are greater than $B$. The probability that the option hasn't been knocked out between times $t_1$ and $t_2$ is therefore

$P(m_{t_1,t_2}^{\log(S)} > b|\log(S_{t_2}))\n = 1 - \exp\left{\{\{\frac{2(\log(B) - \log(S_{t_1}))(\log(B) - \log(S_{t_2}))}{\sigma^2\Delta t}}\right\{\} (4.5.20)

This means that for the (complete) $ith$ scenario path, of $n$ time steps, the probability that $m^{\log(S)} > b$ is

$BB_i^n = \prod_{j=0}^{n-1} \left\{1 - \exp\left{\{\{\frac{2(\log(B) - \log(S_{t_j}^i))(\log(B) - \log(S_{t_{j+1}}^i))}{\sigma^2\Delta t}}\right\{\}\}\right\$

$S_{t_j}^i$ is the $ith$ scenario asset price at time $t_j$.

The basic Monte Carlo $ith$ scenario option value $DO_i$ can therefore be adjusted as follows

$DO_i^n = DO_i BB_i^n$