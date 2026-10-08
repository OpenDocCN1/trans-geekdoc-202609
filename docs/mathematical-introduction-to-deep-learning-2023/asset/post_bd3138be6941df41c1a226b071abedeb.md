
## **Definition 9.17.2** (Generalized **KL** functions).

*Let* $\mathfrak{d} \in \mathbb{N}$, $\mathscr{L} \in C(\mathbb{R}^\mathfrak{d}, \mathbb{R})$. *Then we say that* $\mathscr{L}$ *is a generalized* **KL** *function if and only if for all* $\theta \in \mathbb{R}^\mathfrak{d}$ *there exist* $\varepsilon, c \in (0, \infty)$, $\alpha \in (0, 1)$ *such that for all* $v \in \{v \in \mathbb{R}^\mathfrak{d} : \|v - \theta\|_2 < \varepsilon\}$ *it holds that*

$$|\mathscr{L}(\theta) - \mathscr{L}(v)|^\alpha \leq c \, |\xi_{\mathscr{L}}(v)| \tag{9.321}$$

*(cf. Definitions 3.3.4 and 9.16.1).*

## **Remark 9.17.3** (Examples and convergence results for generalized **KL** functions).

In Theorem 9.9.1 and Corollary 9.13.5 above we have seen that in the case of an analytic activation function we have that the associated empirical risk function is also analytic and therefore a standard **KL** function. In deep learning algorithms often deep **ANNs** with non-analytic activation functions such as the **ReLU** activation (cf. Section 1.2.3) and the leaky **ReLU** activation (cf. Section 1.2.11) are used. In the case of such non-differentiable activation functions, the associated risk function is typically not a standard **KL** function. However, under suitable assumptions on the target function and the underlying probability measure of the input data of the considered learning problem, using Bolte et al. [44, Theorem 3.1] one can verify in the case of such non-differentiable activation functions that the risk function is a generalized **KL** function in the sense of Definition 9.17.2 above; cf., for instance, [126, 224]. Similar as for standard **KL** functions (cf., for example, Dereich & Kassing [100] and Sections 9.11 and 9.12) one can then also develop a convergence theory for gradient based optimization methods for generalized **KL** function (cf., for instance, Bolte et al. [44, Section 4] and Corollary 9.11.5).

## **Remark 9.17.4** (Further convergence analyses).

We refer, for example, to [2, 7, 8, 44, 100, 391] and the references therein for convergence analyses under **KL**-type conditions for gradient based optimization methods in the literature. Beyond the **KL** approach reviewed in this chapter there are also several other approaches in the literature with which one can conclude convergence of gradient based optimization methods to suitable generalized critical points; cf., for instance, [45, 65, 93] and the references therein.

# Chapter 10

## ANNs with batch normalization

In data-driven learning problems popular methods that aim to accelerate ANN training procedures are BN methods. In this chapter we rigorously review such methods in detail. In the literature BN methods have first been introduced in Ioffe & Szegedi [217]. Further investigation on BN techniques and applications of such methods can, for example, be found in [4, Section 12.3.3], [131, Section 6.2.3], [164, Section 8.7.1], and [40, 364].

### 10.1 Batch normalization (BN)

**Definition 10.1.1 (Batch).**

Let $d, M \in \mathbb{N}$. Then we say that $x$ is a batch of $d$-dimensional data points of size $M$ (we say that $x$ is a batch of $M$ $d$-dimensional data points, we say that $x$ is a batch) if and only if it holds that $x \in (\mathbb{R}^{d})^{M}$.

**Definition 10.1.2 (Batch mean).**

Let $d, M \in \mathbb{N}$, $x = (x^{(m)})_{m \in \{1,2,\ldots,M\}} \in (\mathbb{R}^{d})^{M}$. Then we denote by $\text{Batchmean}(x) = (\text{Batchmean}_{1}(x), \ldots, \text{Batchmean}_{d}(x)) \in \mathbb{R}^{d}$ the vector given by

$$\text{Batchmean}(x) = \frac{1}{M} \left[ \sum_{m=1}^{M} x^{(m)} \right] \quad\quad (10.1)$$

and we call $\text{Batchmean}(x)$ the batch mean of the batch $x$.

**Definition 10.1.3 (Batch variance).**

Let $d, M \in \mathbb{N}$, $x = ((x_{i}^{(m)})_{i \in \{1,2,\ldots,d\}})_{m \in \{1,2,\ldots,M\}} \in (\mathbb{R}^{d})^{M}$. Then we denote by

$$\text{Batchvar}(x) = (\text{Batchvar}_{1}(x), \ldots, \text{Batchvar}_{d}(x)) \in \mathbb{R}^{d} \quad\quad (10.2)$$

the vector which satisfies for all $i \in \{1,2,\ldots,d\}$ that

$$\text{Batchvar}_{i}(x) = \frac{1}{M} \left[ \sum_{m=1}^{M} (x_{i}^{(m)} - \text{Batchmean}_{i}(x))^{2} \right] \quad\quad (10.3)$$

and we call $\text{Batchvar}(x)$ the batch variance of the batch $x$ (cf. Definition 10.1.2).

**Lemma 10.1.4.**

*Let $d, M \in \mathbb{N}$, $x = (x^{(m)})_{m \in \{1,2,\ldots,M\}} = ((x_i^{(m)})_{i \in \{1,2,\ldots,d\}})_{m \in \{1,2,\ldots,M\}} \in (\mathbb{R}^d)^M$, let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, and let $U: \Omega \to \{1, 2, \ldots, M\}$ be a $\{1, 2, \ldots, M\}$-uniformly distributed random variable. Then*

- (i) it holds that $\text{Batchmean}(x) = \mathbb{E}[x^{(U)}]$ and
- (ii) it holds for all $i \in \{1, 2, \ldots, d\}$ that $\text{Batchvar}_i(x) = \text{Var}(x_i^{(U)})$.

*Proof of Lemma 10.1.4.* *Note that (10.1) proves item (i). Furthermore, note that item (i) and (10.3) establish item (ii). The proof of Lemma 10.1.4 is thus complete.*

**Definition 10.1.5 (BN operations for given batch mean and batch variance).**

*Let $d \in \mathbb{N}$, $\varepsilon \in (0, \infty)$, $\beta = (\beta_1, \ldots, \beta_d)$, $\gamma = (\gamma_1, \ldots, \gamma_d)$, $\mu = (\mu_1, \ldots, \mu_d) \in \mathbb{R}^d$, $V = (V_1, \ldots, V_d) \in [0, \infty)^d$. Then we denote by*

$$\text{batchnorm}_{\beta, \gamma, \mu, V, \varepsilon}: \mathbb{R}^d \to \mathbb{R}^d \tag{10.4}$$

*the function which satisfies for all $x = (x_1, \ldots, x_d) \in \mathbb{R}^d$ that*

$$\text{batchnorm}_{\beta, \gamma, \mu, V, \varepsilon}(x) = \left(\gamma_i \left[ \frac{x_i - \mu_i}{\sqrt{V_i + \varepsilon}} + \beta_i \right]\right)_{i \in \{1, 2, \ldots, d\}} \tag{10.5}$$

*and we call $\text{batchnorm}_{\beta, \gamma, \mu, V, \varepsilon}$ the BN operation with mean parameter $\beta$, standard deviation parameter $\gamma$, and regularization parameter $\varepsilon$ given the batch mean $\mu$ and batch variance $V$.*

**Definition 10.1.6 (Batch normalization).**

*Let $d \in \mathbb{N}$, $\varepsilon \in (0, \infty)$, $\beta, \gamma \in \mathbb{R}^d$. Then we denote by*

$$\text{Batchnorm}_{\beta, \gamma, \varepsilon}: \left( \bigcup_{M \in \mathbb{N}} (\mathbb{R}^d)^M \right) \to \left( \bigcup_{M \in \mathbb{N}} (\mathbb{R}^d)^M \right) \tag{10.6}$$

*the function which satisfies for all $M \in \mathbb{N}$, $x = (x^{(m)})_{m \in \{1, 2, \ldots, M\}} \in (\mathbb{R}^d)^M$ that*

$$\text{Batchnorm}_{\beta, \gamma, \varepsilon}(x) = \left( \left( \text{batchnorm}_{\beta, \gamma}(\text{Batchmean}(x), \text{Batchvar}(x), \varepsilon) x^{(m)} \right) \right)_{m \in \{1, 2, \ldots, M\}} \in (\mathbb{R}^d)^M \tag{10.7}$$

*and we call $\text{Batchnorm}_{\beta, \gamma, \varepsilon}$ the BN with mean parameter $\beta$, standard deviation parameter $\gamma$, and regularization parameter $\varepsilon$ (cf. Definitions 10.1.2, 10.1.3, and 10.1.5).*

**Lemma 10.1.7.**

*Let $d, M \in \mathbb{N}$, $\beta = (\beta_1, \ldots, \beta_d)$, $\gamma = (\gamma_1, \ldots, \gamma_d) \in \mathbb{R}^d$. Then*

- (i) it holds for all $\varepsilon \in (0, \infty)$, $x = ((x_i^{(m)})_{i \in \{1, 2, \ldots, d\}})_{m \in \{1, 2, \ldots, M\}} \in (\mathbb{R}^d)^M$ that

$$\text{Batchnorm}_{\beta, \gamma, \varepsilon}(x) = \left( \left( \gamma_i \left[ \frac{x_i^{(m)} - \text{Batchmean}_i(x)}{\sqrt{\text{Batchvar}_i(x) + \varepsilon}} + \beta_i \right] \right)_{i \in \{1, 2, \ldots, d\}} \right)_{m \in \{1, 2, \ldots, M\}}, \tag{10.8}$$

- (ii) it holds for all $\varepsilon \in (0, \infty)$, $x \in (\mathbb{R}^d)^M$ that

$$\text{Batchmean}(\text{Batchnorm}_{\beta,\gamma,\varepsilon}(x)) = \beta, \tag{10.9}$$

- (iii) it holds for all $x = ((x_i^{(m)})_{i \in \{1,2,\dots,d\}})_{m \in \{1,2,\dots,M\}} \in (\mathbb{R}^d)^M$, $i \in \{1,2,\dots,d\}$ with $\#(\bigcup_{m=1}^{M}\{x_i^{(m)}\}) > 1$ that

$$\lim\limits_{\varepsilon\searrow0}\left|\text{Batchvar}_i(\text{Batchnorm}_{\beta,\gamma,\varepsilon}(x)) - (\gamma_i)^2\right| = 0 \tag{10.10}$$

*(cf. Definitions 10.1.2, 10.1.3, and 10.1.6).*

*Proof of Lemma 10.1.7.* *Note that* (10.1), (10.3), (10.5), *and* (10.7) *establish item* (i). *In addition, note that item* (i) *ensures that for all* $\varepsilon \in (0, \infty)$, $x = ((x_i^{(m)})_{i \in \{1,2,\dots,d\}})_{m \in \{1,2,\dots,M\}} \in (\mathbb{R}^d)^M$, $i \in \{1,2,\dots,d\}$ *it holds that*

$$\begin{align*}
&\text{Batchmean}_i(\text{Batchnorm}_{\beta,\gamma,\varepsilon}(x)) = \frac{1}{M}\sum_{m=1}^{M} \left[\gamma_i \left[\frac{x_i^{(m)} - \text{Batchmean}_i(x)}{\sqrt{\text{Batchvar}_i(x) + \varepsilon}}\right] + \beta_i\right] \\
&\hspace{2.5cm}= \gamma_i \left[\frac{\frac{1}{M}\sum_{m=1}^{M} x_i^{(m)} - \text{Batchmean}_i(x)}{\sqrt{\text{Batchvar}_i(x) + \varepsilon}}\right] + \beta_i \\
&\hspace{2.5cm}= \gamma_i \left[\frac{\text{Batchmean}_i(x) - \text{Batchmean}_i(x)}{\sqrt{\text{Batchvar}_i(x) + \varepsilon}}\right] + \beta_i = \beta_i
\end{align*}
\tag{10.11}$$

*(cf. Definitions 10.1.2, 10.1.3, and 10.1.6). This implies item* (ii). *Furthermore, observe that* (10.11) *and item* (i) *ensure that for all* $\varepsilon \in (0, \infty)$, $x = ((x_i^{(m)})_{i \in \{1,2,\dots,d\}})_{m \in \{1,2,\dots,M\}} \in (\mathbb{R}^d)^M$, $i \in \{1,2,\dots,d\}$ *it holds that*

$$\begin{align*}
&\text{Batchvar}_i(\text{Batchnorm}_{\beta,\gamma,\varepsilon}(x)) \\
&= \frac{1}{M}\sum_{m=1}^{M} \left[\gamma_i \left[\frac{x_i^{(m)} - \text{Batchmean}_i(x)}{\sqrt{\text{Batchvar}_i(x) + \varepsilon}}\right] + \beta_i - \text{Batchmean}_i(\text{Batchnorm}_{\beta,\gamma,\varepsilon}(x))\right]^2 \\
&= \frac{1}{M}\sum_{m=1}^{M} (\gamma_i)^2 \left[\frac{x_i^{(m)} - \text{Batchmean}_i(x)}{\sqrt{\text{Batchvar}_i(x) + \varepsilon}}\right]^2 \\
&= (\gamma_i)^2 \left[\frac{\frac{1}{M}\sum_{m=1}^{M} (x_i^{(m)} - \text{Batchmean}_i(x))^2}{\text{Batchvar}_i(x) + \varepsilon}\right] = (\gamma_i)^2 \left[\frac{\text{Batchvar}_i(x)}{\text{Batchvar}_i(x) + \varepsilon}\right].
\end{align*}
\tag{10.12}$$

Combining this with the fact that for all $x = ((x_i^{(m)})_{i \in \{1,2,\dots,d\}})_{m \in \{1,2,\dots,M\}} \in (\mathbb{R}^d)^M$, $i \in \{1,2,\dots,d\}$ with $\#(\bigcup_{m=1}^{M}\{x_i^{(m)}\}) > 1$ it holds that

$$\text{Batchvar}_i(x) > 0 \tag{10.13}$$

implies item (iii). The proof of Lemma 10.1.7 is thus complete. $\square$
