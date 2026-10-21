+   2. The sequence of the elementary Itô integrals converges to a well-defined random variable $I(w)$, therefore the Itô integral itself can be regarded as a random variable.
+   3. If $\sigma(t)$ is a deterministic function of time, then one can prove that the Itô integral is normally distributed with mean zero and variance equal to
+   $$\operatorname{var}\left[\int_{0}^{t} \sigma(s) dZ(s,w)\right] = \int_{0}^{t} \sigma(s)^{2} ds. \tag{27.5}$$

It is important to note here that the second integral is a non-random, simple integral of time.

The above results are essential for the understanding of the numerical method of integration through Monte Carlo simulation: Instead of evaluating analytically an Itô integral, one can sample through its distribution and calculate the average of the sample draws.

Having a concise model for randomness and uncertainty, we next move to the key notion of the stochastic calculus — the Itô process. This can be described by the integral equation

$S(t,w) = S(0) + \int_{0}^{t} \mu[u,S(u,w)] \cdot du + \int_{0}^{t} \sigma[u,S(u,w)] \cdot dZ(u,w). \tag{27.6}$

Although mathematically more meaningful as written above, it is usually presented in its shorthand form as a stochastic differential equation,

$dS(t,w) = \mu[t,S(t,w)] dt + \sigma[t,S(t,w)] dZ(t,w), \tag{27.7}$

which is analogous to the ordinary differential equation $dS(t)/dt = \mu[t,S(t)]$. A stochastic process is an Itô process if the random variable $dS(t,w)$ can be represented by equation (27.7). The first term, $\mu[t,S(t,w)] dt$, is the expected change in $S(t,w)$ at time $t$. The second term, $\sigma[t,S(t,w)] dZ(t,w)$, reflects the uncertain term.