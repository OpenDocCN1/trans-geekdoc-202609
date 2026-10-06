# Lattice Methods for Vanilla Options | 5.3 113

which gives

$au^2 - u + a - a^2u - b^2u = 0.$

So we obtain the following quadratic equation in u:

$au^2 - u(1 + a^2 + b^2) + a = 0.$

The solution is

$u = \frac{(1 + a^2 + b^2) + \sqrt{(1 + a^2 + b^2)^2 - 4a^2}}{2a}$

If $\Delta t$ is small, we can obtain a reasonable approximation to the solution by neglecting terms of order higher than $\Delta t$.

In these circumstances, we have

$a^2 + b^2 + 1 = \exp(2\Delta t) + \exp(2\Delta t)\exp(\sigma^2\Delta t) - 1 + 1$
\sim 1 + 2\Delta t + (1 + 2\Delta t)\sigma^2\Delta t + 1 \sim 2\Delta t + \sigma^2\Delta t.$

Therefore,

$\sqrt{(a^2 + b^2 + 1)^2 - 4a^2} \sim \sqrt{(2 + 2\Delta t + \sigma^2\Delta t)^2 - 4(1 + 2\Delta t)}$
\sim 4 + 8\Delta t + \sigma^2\Delta t - 4 - 8\Delta t = \sqrt{4\sigma^2\Delta t} = 2\sigma\sqrt{\Delta t}$

and so

$u \sim \frac{2 + 2\Delta t + \sigma^2\Delta t + 2\sigma\sqrt{\Delta t}}{\exp(r\Delta t)}$
$u \sim (1 + r\Delta t + \frac{\sigma^2\Delta t}{2} + \sigma\sqrt{\Delta t})(1 - r\Delta t)$
$u \sim 1 + r\Delta t + \frac{\sigma^2\Delta t}{2} + \sigma\sqrt{\Delta t} - r\Delta t = 1 + \sigma\sqrt{\Delta t} + \frac{\sigma^2\Delta t}{2}$

which to order $\Delta t$ gives

$u = \exp(\sigma\sqrt{\Delta t}) \quad (5.3.20)$

since

$\exp(\sigma\sqrt{\Delta t}) = 1 + \sigma\sqrt{\Delta t} + \frac{\sigma^2\Delta t}{2} + \frac{\sigma^3(\Delta t)^{3/2}}{6} + \dots,$

which also gives

$d = \frac{1}{u}\exp(-\sigma\sqrt{\Delta t}). \quad (5.3.21)$

It is interesting to note that when $r \to 0$ we have $p \to \frac{1}{2}$.

Now that we know the values of the lattice parameters $u, d,$ and $p$ we can use these to build a lattice with a specified number of time steps. Once this has been