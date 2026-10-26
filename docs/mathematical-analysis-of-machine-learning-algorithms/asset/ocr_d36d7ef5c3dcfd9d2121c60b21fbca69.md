**Proof**  The proof of Lemma 16.2 shows that with probability at least \(1-\delta\), for all \(t \ge K+1\),

$$\mu(a_*) \le \mu(a_t) + [\hat{c}'_{t-1}(a_t)+\hat{c}_{t-1}(a_t)]\mathbf{1}(a_t\ne a_*),$$

which implies that

$$\Delta(a_t) \le [\hat{c}'_{t-1}(a_t)+\hat{c}_{t-1}(a_t)]\mathbf{1}(a_t\ne a_*).$$

Using the assumption of the lemma, we obtain for all \(a\ne a_*\) and \(1\le t\le T\), \(\hat{n}_{t-1}(a)\mathbf{1}(a_t=a)\le T(a)\).

It follows that for all \(a\ne a_*\), let \(t\) be the last time such that \(a_t=a\), then \(t\le T\) and \(\hat{n}_T(a)=\hat{n}_{t-1}(a_t)+1\le T(a)+1\). We thus obtain the following regret bound for any \(\Delta_0\ge0\):

$$\sum_{t=1}^{T}|\mu(a_*)-\mu(a_t)|=\sum_{a=1}^{K}\hat{n}_T(a)\Delta(a)$$

$$\le \sum_{a=1}^{K}\Delta(a)+\sum_{a=1}^{K}(\hat{n}_T(a)-1)\Delta_0+\sum_{a=1}^{K}(\hat{n}_T(a)-1)\Delta(a)\mathbf{1}(\Delta(a)>\Delta_0)$$

$$\le \sum_{a=1}^{K}\Delta(a)+(T-K)\Delta_0+\sum_{a=1}^{K}T(a)\Delta(a)\mathbf{1}(\Delta(a)>\Delta_0).$$

The second inequality used \(\sum_{a=1}^{K}\hat{n}_T(a)=T-K\) and \(\hat{n}_T(a)-1\le T(a)\). This implies the bound.

We note that in Lemma 16.6, \(\delta_1\) is still the failure probability for the upper confidence bound, and \(\delta_2\) is the failure probability for the lower confidence bound. The intuition of the quantity \(T(a)\) is that after we have pulled arm \(a\) for more than \(T(a)\) times, the confidence interval for \(a\) becomes smaller than the gap \(\Delta(a)\), which means that we will not choose arm \(a\) in the future. That is, \(T(a)\) is the maximum number of times that one will pull a particular arm \(a\). This means that the regret caused by choosing \(a\) is upper bounded by \(T(a)\Delta(a)\).

Using Lemma 16.6, we can now obtain a gap-dependent bound in Theorem 16.7.

# **Theorem 16.7**  Assume that the reward \(r_t(a)\in[0,1]\). Let \(a_*\in\arg\max_a\mu(a)\).

With a choice of

$$\hat{c}_t(a)=\sqrt{\frac{\ln(2(\hat{n}_t(a)+1)^2/\delta)}{2\hat{n}_t(a)}}.$$

we have

$$\mathrm{REG}_T\le \inf_{\Delta_0>0}\left[(T-K)\Delta_0+\sum_{a=1}^{K}\frac{2\ln(2KT^2/\delta)}{\Delta(a)}\mathbf{1}(\Delta(a)>\Delta_0)\right]+\sum_{a=1}^{K}\Delta(a).$$