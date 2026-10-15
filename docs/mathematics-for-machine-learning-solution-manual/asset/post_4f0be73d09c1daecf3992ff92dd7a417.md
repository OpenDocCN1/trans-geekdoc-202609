
two modes. In general, we would need to solve an optimization problem to find the maxima. However, in this particular case we can observe that the two modes correspond to the individual Gaussian means, that is

$\begin{bmatrix}10\\2\end{bmatrix}$ and $\begin{bmatrix}0\\0\end{bmatrix}$.

## 6.3

You have written a computer program that sometimes compiles and sometimes not (code does not change). You decide to model the apparent stochasticity (success vs. no success) $x$ of the compiler using a Bernoulli distribution with parameter $\mu$:

$p(x\mid\mu)=\mu^x(1-\mu)^{1-x},\quad x\in\{0,1\}$.

Choose a conjugate prior for the Bernoulli likelihood and compute the posterior distribution $p(\mu\mid x_1,\ldots,x_N)$.

The posterior is proportional to the product of the likelihood (Bernoulli) and the prior (Beta). Given the choice of the prior, we already know that the posterior will be a Beta distribution. With a conjugate Beta prior $p(\mu)=\mathrm{Beta}(a,b)$ obtain

$$p(\mu\mid X)=\frac{p(\mu)p(X\mid\mu)}{p(X)}\propto \mu^{a-1}(1-\mu)^{b-1}\prod_{i=1}^{N}\mu^{x_i}(1-\mu)^{1-x_i}$$

$$\propto \mu^{a-1+\sum_i x_i}(1-\mu)^{b-1+N-\sum_i x_i}\propto \mathrm{Beta}\left(a+\sum_i x_i,b+N-\sum_i x_i\right).$$

Alternative approach: We look at the log-posterior. Ignoring all constants that are independent of $\mu$ and $x_i$, we obtain

$$\log p(\mu\mid X)=(a-1)\log\mu+(b-1)\log(1-\mu)$$

$$\qquad+\log\mu\sum_i x_i+\log(1-\mu)\sum_i(1-x_i)$$

$$\qquad=\log\mu\left(a-1+\sum_i x_i\right)+\log(1-\mu)\left(b-1+N-\sum_i x_i\right).$$

Therefore, the posterior is again $\mathrm{Beta}\left(a+\sum_i x_i,b+N-\sum_i x_i\right)$.

## 6.4

There are two bags. The first bag contains four mangos and two apples; the second bag contains four mangos and four apples.
We also have a biased coin, which shows “heads” with probability 0.6 and “tails” with probability 0.4. If the coin shows “heads”, we pick a fruit at random from bag 1; otherwise we pick a fruit at random from bag 2.
Your friend flips the coin (you cannot see the result), picks a fruit at random from the corresponding bag, and presents you a mango.
What is the probability that the mango was picked from bag 2?

*Hint: Use Bayes’ theorem.*

We apply Bayes’ theorem and compute the posterior $p(b_2\mid m)$ of picking a mango from bag 2.

$$p(b_2\mid m)=\frac{p(m\mid b_2)p(b_2)}{p(m)}$$

where

\[
p(m)=p(b_1)p(m\mid b_1)+p(b_2)p(m\mid b_2)=\frac{3}{5}\frac{2}{3}+\frac{2}{5}\frac{1}{2}=\frac{2}{5}+\frac{1}{5}=\frac{3}{5}\quad\text{Evidence}
\]

\[
p(b_2)=\frac{2}{5}\quad\text{Prior}
\]

\[
p(m\mid b_2)=\frac{1}{2}\quad\text{Likelihood}
\]

Therefore,

\[
p(b_2\mid m)=\frac{p(m\mid b_2)p(b_2)}{p(m)}=\frac{\frac{2}{5}\frac{1}{2}}{\frac{3}{5}}=\frac{1}{3}.
\]

## 6.5

Consider the time-series model

\[
x_{t+1}=Ax_t+w,\qquad w\sim\mathcal{N}(0,Q),
\]
\[
y_t=Cx_t+v,\qquad v\sim\mathcal{N}(0,R),
\]

where $w,v$ are i.i.d. Gaussian noise variables. Further, assume that $p(x_0)=\mathcal{N}(\mu_0,\Sigma_0)$.

- a. What is the form of $p(x_0,x_1,\ldots,x_T)$? Justify your answer (you do not have to explicitly compute the joint distribution).
- 
- b. Assume that $p(x_t\mid y_1,\ldots,y_t)=\mathcal{N}(\mu_t,\Sigma_t)$.
- 
- 1. Compute $p(x_{t+1}\mid y_1,\ldots,y_t)$.
- 2. Compute $p(x_{t+1},y_{t+1}\mid y_1,\ldots,y_t)$.
- 3. At time $t+1$, we observe the value $y_{t+1}=\hat y$. Compute the conditional distribution $p(x_{t+1}\mid y_1,\ldots,y_{t+1})$.

- 1. The joint distribution is Gaussian: $p(x_0)$ is Gaussian, and $x_{t+1}$ is a linear/affine transformation of $x_t$. Since affine transformations leave the Gaussianity of the random variable invariant, the joint distribution must be Gaussian.

- 2. 1. We use the results from linear transformation of Gaussian random variables (Section 6.5.3). We immediately obtain
- 
- \[
p(x_{t+1}\mid y_{1:t})=\mathcal{N}(x_{t+1}\mid\mu_{t+1\mid t},\Sigma_{t+1\mid t})
\]
- \[
\mu_{t+1\mid t}:=A\mu_t
\]
- \[
\Sigma_{t+1\mid t}:=A\Sigma_tA^\mathsf{T}+Q.
\]

- 2. The joint distribution $p(x_{t+1},y_{t+1}\mid y_{1:t})$ is Gaussian (linear transformation of random variables). We compute every component of the Gaussian separately:
- 
- \[
\mathbb{E}[y_{t+1}\mid y_{1:t}]=C\mu_{t+1\mid t}:=\mu^y_{t+1\mid t}
\]
- \[
\mathbb{V}[y_{t+1}\mid y_{1:t}]=C\Sigma_{t+1\mid t}C^\mathsf{T}+R:=\Sigma^y_{t+1\mid t}
\]
- \[
\operatorname{Cov}[x_{t+1},y_{t+1}\mid y_{1:t}]=\operatorname{Cov}[x_{t+1},Cx_{t+1}\mid y_{1:t}]=\Sigma_{t+1\mid t}C^\mathsf{T}:=\Sigma_{xy}
\]
- 
- Therefore,
- 
- \[
p(x_{t+1},y_{t+1}\mid y_{1:t})=\mathcal{N}\left(\begin{bmatrix}\mu_{t+1\mid t}\\\mu^y_{t+1\mid t}\end{bmatrix},
\begin{bmatrix}\Sigma_{t+1\mid t}&\Sigma_{xy}\\\Sigma_{xy}&\Sigma^y_{t+1\mid t}\end{bmatrix}\right).
\]

- 3. We obtain the desired distribution (again: Gaussian) by applying the rules for Gaussian conditioning of the joint distribution in B):
- 
- $$p(x_{t+1}\mid y_{1:t+1})=\mathcal{N}(\mu_{t+1\mid t+1},\Sigma_{t+1\mid t+1})$$
- 
- $$\mu_{t+1\mid t+1}=\mu_{t+1\mid t}+\Sigma_{xy}(\Sigma^y_{t+1\mid t})^{-1}(\hat y-\mu^y_{t+1\mid t})$$
- 
- $$\Sigma_{t+1\mid t+1}=\Sigma_{t+1\mid t}-\Sigma_{xy}(\Sigma^y_{t+1\mid t})^{-1}\Sigma_{yx}$$

## 6.6

Prove the relationship in (6.44), which relates the standard definition of the variance to the raw-score expression for the variance.

The formula in (6.43) can be converted to the so called raw-score formula for variance

$$\frac{1}{N}\sum_{i=1}^{N}(x_i-\mu)^2=\frac{1}{N}\sum_{i=1}^{N}(x_i^2-2x_i\mu+\mu^2)$$

$$=\frac{1}{N}\sum_{i=1}^{N}x_i^2-\frac{2}{N}\mu\sum_{i=1}^{N}x_i+\mu^2$$

$$=\frac{1}{N}\sum_{i=1}^{N}x_i^2-\mu^2$$

$$=\frac{1}{N}\sum_{i=1}^{N}x_i^2-\left(\frac{1}{N}\sum_{i=1}^{N}x_i\right)^2.$$

## 6.7

Prove the relationship in (6.45), which relates the pairwise difference between examples in a dataset with the raw-score expression for the variance.

Consider the pairwise squared deviation of a random variable:

$$\frac{1}{N^2}\sum_{i,j=1}^{N}(x_i-x_j)^2=\frac{1}{N^2}\sum_{i,j=1}^{N}x_i^2+x_j^2-2x_ix_j \tag{6.5}$$

$$=\frac{1}{N}\sum_{i=1}^{N}x_i^2+\frac{1}{N}\sum_{j=1}^{N}x_j^2-2\frac{1}{N^2}\sum_{i,j=1}^{N}x_ix_j \tag{6.6}$$

$$=\frac{2}{N}\sum_{i=1}^{N}x_i^2-2\frac{1}{N}\sum_{i=1}^{N}x_i\left(\frac{1}{N}\sum_{j=1}^{N}x_j\right) \tag{6.7}$$

$$=2\left[\frac{1}{N}\sum_{i=1}^{N}x_i^2-\left(\frac{1}{N}\sum_{i=1}^{N}x_i\right)^2\right]. \tag{6.8}$$

Observe that the last equation above is twice of (6.44).

Going from (6.6) to (6.7), we need to make two observations. The first two terms in (6.6) are sums over all examples, and the index is not important, therefore they can be combined into one sum. The last term is obtained by “pushing in” the sum over $j$. This can be seen by a small example by considering $N=3$:

$$x_1x_1+x_1x_2+x_1x_3+x_2x_1+x_2x_2+x_2x_3+x_3x_1+x_3x_2+x_3x_3$$

$$=x_1(x_1+x_2+x_3)+x_2(x_1+x_2+x_3)+x_3(x_1+x_2+x_3).$$

Going from (6.7) to (6.8), we consider the sum over j as a common factor, as seen in the following small example:

$x_1(x_1 + x_2 + x_3) + x_2(x_1 + x_2 + x_3) + x_3(x_1 + x_2 + x_3) = (x_1 + x_2 + x_3)(x_1 + x_2 + x_3)$

## 6.8

Express the Bernoulli distribution in the natural parameter form of the exponential family, see (6.107).

$p(x \mid \mu) = \mu^x (1-\mu)^{1-x}$
$= \exp\left[\log\left(\mu^x (1-\mu)^{1-x}\right)\right]$
$= \exp\left[x \log \mu + (1 - x)\log(1-\mu)\right]$
$= \exp\left[x \log \frac{\mu}{1-\mu} + \log(1-\mu)\right]$
$= \exp\left[x\theta - \log(1+\exp(\theta))\right]$

where the last line is obtained by substituting $\theta = \log \frac{\mu}{1-\mu}$. Note that this is in exponential family form, as $\theta$ is the natural parameter, the sufficient statistic $\phi(x)=x$ and the log partition function is $A(\theta)=\log(1+\exp(\theta))$.

## 6.9

Express the Binomial distribution as an exponential family distribution. Also express the Beta distribution is an exponential family distribution. Show that the product of the Beta and the Binomial distribution is also a member of the exponential family.

Express Binomial distribution as an exponential family distribution:

Recall the Binomial distribution from Example 6.11

$p(x|N,\mu)=\binom{N}{x}\mu^x(1-\mu)^{(N-x)}\quad x=0,1,...,N.$

This can be written in exponential family form

$p(x|N,\mu)=\binom{N}{x}\exp\left[\log\left(\mu^x(1-\mu)^{(N-x)}\right)\right]$
$=\binom{N}{x}\exp\left[x\log\mu+(N-x)\log(1-\mu)\right]$
$=\binom{N}{x}\exp\left[x\log\frac{\mu}{1-\mu}+N\log(1-\mu)\right]$

The last line can be identified as being in exponential family form by observing that

$h(x)=\begin{cases}\binom{N}{x} & x=0,1,...,N.\\0 & \text{otherwise}\end{cases}$
$\theta=\log\frac{\mu}{1-\mu}$
