By incorporating Eq. (3.18) and inequality (3.19) into inequality (3.17), we can infer that

$$
\mathbb{E}[\|\bar{x}_{k+1} - x^*\|^2]\\
\le ((1-\eta\lambda)^2 + \eta(1-\eta\lambda)b + (1-\eta\lambda)c)\mathbb{E}[\|\bar{x}_k - x^*\|^2]\\
+ \frac{(1+a^{-1})\eta^2}{m^2}\mathbb{E}[\|g(P_\Omega(x_k)) - \nabla F(P_\Omega(x_k))\|^2]\\
+ (\frac{(1+a^{-1})\eta^2\beta^2}{m} + \frac{\eta(1-\eta\lambda)b^{-1}\beta^2}{m} + \frac{(1+a)\sigma_2}{m}\\
+ \frac{(1-\eta\lambda)c^{-1}\sigma_2}{m})\mathbb{E}[\|x_k - A^\infty x_k\|^2].
$$
(3.20)

By assigning \(a=1\), \(b=k_1/2\), \(c=\eta k_1/2\), respectively, and multiplying both sides of the inequality denoted by (3.20) by \(m\), we finalize the demonstration of Lemma 3.6. \(\square\)

Subsequently, we constrain \(\mathbb{E}[\|y_{k+1} - A^\infty y_{k+1}\|^2]\).

**Lemma 3.7.** Provided that Assumptions 3.1 and 3.2 are valid and given that \(0 < \eta \le \frac{1}{4\sqrt{2}\beta}\), the subsequent correlation applies: \(\forall k \ge 0\),

$$
\mathbb{E}[\|y_{k+1} - A^\infty y_{k+1}\|^2]\\
\le \frac{52\beta^2}{1-\sigma_2^2}\mathbb{E}[\|x_k - A^\infty x_k\|^2] + \frac{52\beta^2}{1-\sigma_2^2}\mathbb{E}[m\|\bar{x}_k - x^*\|^2]\\
+ \frac{6}{1-\sigma_2^2}\mathbb{E}[\|g(s_k) - \nabla F(s_k)\|^2] + \frac{4}{1-\sigma_2^2}\mathbb{E}[\|g(s_{k+1}) - \nabla F(s_{k+1})\|^2]\\
+ (\frac{1+\sigma_2^2}{2} + \frac{32\beta^2\eta^2}{1-\sigma_2^2})\mathbb{E}[\|y_k - A^\infty y_k\|^2].
$$
(3.21)

*Proof.* Based on the updating principle denoted by (3.7) and Young’s inequality [19], we infer that:

$$
\|y_{k+1} - A^\infty y_{k+1}\|^2\\
\le \|A y_k - A^\infty y_k + (I_m - A^\infty)(g(s_{k+1}) - g(s_k))\|^2\\
\le (1+a)\|A y_k - A^\infty y_k\|^2 + (1+a^{-1})\|g(s_{k+1}) - g(s_k)\|^2.
$$
(3.22)

By assigning \(a^{-1} = \frac{20\sigma_2^2}{1-\sigma_2^2}\), the inequality denoted by (3.22) can be rephrased as

$$
\|y_{k+1} - A^\infty y_{k+1}\|^2\\
\le \frac{1+\sigma_2^2}{2}\|A y_k - A^\infty y_k\|^2 + \frac{2}{1-\sigma_2^2}\|g(s_{k+1}) - g(s_k)\|^2.
$$
(3.23)