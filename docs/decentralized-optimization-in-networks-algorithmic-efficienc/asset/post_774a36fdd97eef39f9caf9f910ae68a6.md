
\le \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n \langle g_t^i(x_t^j), x_t^j - \bar{x}_t + \bar{x}_t - x_t^i \rangle]\\
\le nK \sum_{t=1}^T \mathbb{E}[||x_t^j - \bar{x}_t||] + K \sum_{t=1}^T \sum_{i=1}^n \mathbb{E}[||x_t^i - \bar{x}_t||].

Recall the outcome pertaining to the projection operator \(\Pi_\Omega^\phi(\cdot)\), which states that for any vectors \(u, v \in \mathbb{R}^m\), the inequality \(||\Pi_\Omega^\phi(u, \alpha) - \Pi_\Omega^\phi(v, \alpha)|| \le \alpha ||u - v||\) holds true, as documented in [21]. Consequently, for any \(i\) belonging to the set \(\mathcal{V}\),

```
\(\mathbb{E}[||x_t^i - \bar{x}_t||] \le \alpha_t \max_{i \in \mathcal{V}} \mathbb{E}[||q_t^i - \bar{q}_t||].\)
```

Given that \(\alpha_t = \frac{\alpha_0}{\sqrt{t+1}}\), it follows that \((1/\alpha_T) < \frac{2\sqrt{T}}{\alpha_0}\) and the cumulative sum of the step-sizes up to time \(T\) satisfies \(\sum_{t=1}^T \alpha_{t-1} \le \sum_{t=1}^T (\frac{\alpha_0}{\sqrt{t}}) \le 2\alpha_0 \sqrt{T}\). Invoking Lemma 6.4, we can conclude that the initial term of Eq. (6.20) is confined within a certain bound:

```
\(\mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^j) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^i)] \le 4\alpha_0 n K O_1 \sqrt{T}.\quad (6.21)\)
```

It is worth noting that the distance between \(\check{x}\) and \(x^*\) is upper-bounded by \(\xi D\). Consequently, the second component of Eq. (6.20) is limited within a certain range:

```
\(\mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n f_t^i(\check{x}) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(x^*)] \le \xi T n K D.\quad (6.22)\)
```

Note that \(\nabla \hat{f}_t^i(x) = \mathbb{E}_{\beta_t^i \in \mathbb{S}^m}[\hat{g}_t^i(x)], \forall x \in (1-\xi)\Omega\). Subsequently, it is inferred from the combined assertions of Lemma 6.1(a) and 6.1(b) that

```
\(\mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n (f_t^i(x_t^i) - f_t^i(\check{x}))]\\
\le \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n (\hat{f}_t^i(x_t^i) - \hat{f}_t^i(\check{x}) + \delta K)]\\
\le \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n \langle \nabla \hat{f}_t^i(x_t^i), \bar{x}_t - \check{x} + x_t^i - \bar{x}_t \rangle] + T n \delta K\\
\le \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n \langle \hat{g}_t^i, \bar{x}_t - \check{x} \rangle] + \alpha_0 n m K O_1 \sqrt{T} + T n \delta K\\
= \Theta_1 + \Theta_2 + \alpha_0 n m K O_1 \sqrt{T} + T n \delta K,\quad (6.23)\)
```

where

```
\(\Theta_1 = \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n \langle \frac{n \hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} (\frac{\nu_{t+1}^i}{n} - \theta_{t+1}^i), \bar{x}_t - \tilde{x} \rangle],\)

\(\Theta_2 = \mathbb{E}[n \sum_{t=1}^T \sum_{i=1}^n (\langle \frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i - \vartheta_t^i \theta_t^i, \bar{x}_t - \tilde{x} \rangle].\)
```

Under Assumption 6.2, it can be inferred that \(\|\bar{x}_t - x^*\| \le D\). Subsequently, it is deduced from Lemma 6.1(c) and Lemma 6.2 that

```
\(\Theta_1 \le \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n || \frac{n \hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} || \frac{\nu_{t+1}^i}{n} || \theta_{t+1}^i - \theta_{t+1}^i || || \bar{x}_t - \tilde{x} ||]\)

\(\le n^2 \omega m K D Q \sum_{t=1}^T \lambda^{T-t-1} \le \frac{n^2 \omega m K D Q}{1 - \lambda}.\) (6.24)
```

Next, we proceed with the analysis of the term \(\Theta_2\). Given that \(\vartheta_t^i\) follows a distribution \(\mathcal{L}(0, b_t)\), it follows that the expected value of \(\vartheta_t^i\) is zero for all \(i\) belonging to the set \(\mathcal{V}\) and for all \(t\) greater than or equal to 1. Consequently,

```
\(\Theta_2 = \mathbb{E}[n \sum_{t=1}^T \sum_{i=1}^n \langle \frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i, \bar{x}_t \rangle]\)

\(- \mathbb{E}[n \sum_{t=1}^T \sum_{i=1}^n \langle \frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i, \tilde{x} \rangle].\) (6.25)
```

Next, we delve into the examination of the second component situated on the right-hand portion of Eq. (6.25). This particular term can be traced back to its origins in Eq. (6.13),

```
\(\sum_{t=1}^T \sum_{i=1}^n \langle \frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i, \tilde{x} \rangle = \langle \bar{q}_{T+1} - \bar{q}_1, \tilde{x} \rangle.\) (6.26)
```

Observing the inequality \(\alpha_t \le \alpha_{t-1}\), we can conclude that \(\mathcal{H}_\Omega^\phi(-\bar{q}_{t+1}, \alpha_t)\) is less than or equal to \(\mathcal{H}_\Omega^\phi(-\bar{q}_{t+1}, \alpha_{t-1})\). Subsequently, applying Lemma 6.3, we arrive at

```
\(\mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_{t+1}, \alpha_t)\)

\(\le \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_t - \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i), \alpha_{t-1})\)

\(\le \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_t, \alpha_{t-1}) - \langle \bar{x}_t, \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i) \rangle\)

+ \frac{1}{2}\alpha_{t-1}|| \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i) ||^2.\quad (6.27)
```

By reorganizing the terms, we have

```
\langle \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i), \bar{x}_t \rangle
\le \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_t, \alpha_{t-1}) - \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_{t+1}, \alpha_t)
+ \frac{1}{2}\alpha_{t-1}|| \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i) ||^2,\quad (6.28)
```

which, by aggregating Eq. (6.28) across all values of \( t \), we additionally obtain the following result:

```
\sum_{t=1}^T \sum_{i=1}^n \langle \frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i, \bar{x}_t \rangle
\le \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_1, \alpha_0) - \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_{T+1}, \alpha_T)
+ \frac{1}{2} \sum_{t=1}^T \alpha_{t-1}|| \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i) ||^2.\quad (6.29)
```

Moreover, utilizing the conceptions of \(\bar{x}_t\) and \(\mathcal{H}_\Omega^\phi(\cdot)\), it can be inferred that \(\mathcal{H}_\Omega^\phi(-\bar{q}_{T+1}, \alpha_T) = -\langle \bar{q}_{T+1}, \bar{x}_{T+1} \rangle - (1/\alpha_T)\phi(\bar{x}_{T+1})\). As a result, combining (6.26) and (6.29) leads to the derivation of

```
\sum_{t=1}^T \sum_{i=1}^n \langle \frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i, \bar{x}_t - \tilde{x} \rangle
\le \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_1, \alpha_0) - \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_{T+1}, \alpha_T)
+ \frac{1}{2} \sum_{t=1}^T \alpha_{t-1} || \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i) ||^2
- \langle \bar{q}_{T+1}, \tilde{x} \rangle + \langle \bar{q}_1, \tilde{x} \rangle
\le \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_1, \alpha_0) + \langle \bar{q}_1, \tilde{x} \rangle + \langle \bar{q}_{T+1}, \bar{x}_{T+1} - \tilde{x} \rangle
+ \frac{\phi(\bar{x}_{T+1})}{\alpha_T} + \frac{1}{2} \sum_{t=1}^T \alpha_{t-1} || \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i) ||^2.\quad (6.30)
```

Let us define \(\psi(x)\) as the inner product of \(\bar{q}_{T+1}\) and \(x\) augmented by the scaled function \(\phi(x)/\alpha_T\), and recognize that \(\bar{x}_{T+1}\) is the projection of \(\bar{q}_{T+1}\) onto the set \(\Omega\) with respect to the function \(\phi\) and parameter \(\alpha_T\), denoted as \(\Pi_{\Omega}^{\phi}(\bar{q}_{T+1}, \alpha_T)\). Given that \(\phi(x)\) possesses 1-strong convexity, it implies that \(\psi(x)\) exhibits strong convexity with a modulus of \(1/\alpha_T\). According to Lemma 4 in [43], we can infer that

\((\bar{q}_{T+1}, \bar{x}_{T+1} - \tilde{x}) + \frac{\phi(\bar{x}_{T+1})}{\alpha_T} \le \frac{\phi(\tilde{x})}{\alpha_T}.\) (6.31)

Furthermore, leveraging the Cauchy–Schwarz inequality, we can infer that

```
\(\mathbb{E}[|| \sum_{i=1}^n ( \frac{\hat{g}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i ) ||^2]\)
\(\le \mathbb{E}[|| \sum_{i=1}^n || \frac{\hat{g}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i ||^2]\)
\(\le 2 \mathbb{E}[ \sum_{i=1}^n || \frac{\hat{g}_t^i}{\nu_{t+1}^i} ||^2 || \theta_{t+1}^i ||^2 + \sum_{i=1}^n || \vartheta_t^i ||^2 || \theta_t^i ||^2 ]\)
\(\le 2nm^2 K^2 \omega^2 + 4nm b_{\max}^2 = O_2.\) (6.32)
```

Hence, it can be deduced from Eqs. (6.25) and (6.29)-(6.31) that

```
\(\Theta_2 = \mathbb{E}[n \sum_{t=1}^T \sum_{i=1}^n ( \frac{\hat{g}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i, \bar{x}_t - \tilde{x} ) ]\)
\(\le n \mathcal{H}_{(1-\xi)\Omega}^{\phi}(-\bar{q}_1, \alpha_0) + n \langle \bar{q}_1, \tilde{x} \rangle + n( \frac{2\phi(\tilde{x})}{\alpha_0} + \alpha_0 O_2 )\sqrt{T}.\) (6.33)
```

Drawing upon (6.24) and (6.33), the third component of (6.20) is constrained within the bounds of

```
\(\mathbb{E}[ \sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^i) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(\tilde{x}) ]\)
\(\le O_3 + ( \frac{2n\phi(\tilde{x})}{\alpha_0} + \alpha_0 n O_2 + 2\alpha_0 nm K O_1 )\sqrt{T} + Tn\delta K,\) (6.34)
```

where

\(O_3 = \frac{n^2 \omega m K D Q}{1 - \lambda} + n \mathcal{H}_{(1-\xi)\Omega}^{\phi}(-\bar{q}_1, \alpha_0) + n \langle \bar{q}_1, \tilde{x} \rangle.\)

Hence, it follows from (6.21), (6.22), and (6.34) that

```
\(\bar{R}_T^j \le (2(2+m)\alpha_0 n K O_1 + \frac{2n\phi(\tilde{x})}{\alpha_0} + \alpha_0 n O_2 )\sqrt{T}\)
\(+ O_3 + Tn\delta K + \xi Tn K D,\)
```

which is the expected result.
