
## 2. Jensen 不等式与熵的推导

Jensen's inequality states that for a convex function $\phi$ and a random variable $y$,
$$\phi(E[y]) \le E[\phi(y)]$$

If we set $\phi(x) = -\log_2 x$, which is convex, and $y = \frac{1}{p(x)}$ for a discrete random variable $x$, then
$$E[y] = \sum_{i=1}^{n} p_i \cdot \frac{1}{p_i} = n$$

and
$$H(x) = E[-\log_2(\frac{1}{p(x)})] \le -\log_2(E[\frac{1}{p(x)}]) = \log_2 n$$

where the equality holds if and only if $p_i \equiv \frac{1}{n}$ for all $i$.

## 3. 微分熵的定义

As a common practice, the differential entropy is defined in terms of natural logarithm instead of binary logarithm as used in the Shannon entropy for the discrete cases.

## 4. 定义的一致性

For the sake of consistency with the concept of the unconditional differential entropy, we also use the natural logarithm instead of binary logarithm in this definition.

## 5. 相对熵的非负性证明

To see $D(P \| Q) \ge 0$, we only need a simple application of Jensen's inequality to the convex function $-\ln x$:

$$
D(P \| Q) = E_P[-\ln(\frac{Q(x)}{P(x)})] \ge -\ln(E_P[\frac{Q(x)}{P(x)}]) = -\ln(\sum_{x \in \mathcal{X}} Q(x)) = 0.
$$
