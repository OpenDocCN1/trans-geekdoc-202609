
The fact that for all $ k \in \{0, 1, \dots, K\} $ it holds that $ \mathfrak{f}_k \leq \mathfrak{f}_K $ and (3.58) therefore demonstrate that for all $ x \in [\mathfrak{f}_K, \infty) $ it holds that

$$
\begin{aligned}
(\mathcal{R}_\mathfrak{c}^\mathbf{N}(\mathbf{F}))(x) - (\mathcal{R}_\mathfrak{c}^\mathbf{N}(\mathbf{F}))(\mathfrak{f}_K) &= \left[\sum_{n=0}^K c_n(\max\{x - \mathfrak{f}_n, 0\} - \max\{\mathfrak{f}_K - \mathfrak{f}_n, 0\}) \right] \quad (3.68) \\
&= \sum_{n=0}^K c_n[(x - \mathfrak{f}_n) - (\mathfrak{f}_K - \mathfrak{f}_n)] \\
&= \sum_{n=0}^K c_n(x - \mathfrak{f}_K) = 0.
\end{aligned}
$$

This and (3.64) show that for all $ x \in [\mathfrak{f}_K, \infty) $ it holds that

$$
(\mathcal{R}_\mathfrak{c}^\mathbf{N}(\mathbf{F}))(x) = (\mathcal{R}_\mathfrak{c}^\mathbf{N}(\mathbf{F}))(\mathfrak{f}_K) = f_{K-1} + \left(\frac{f_K - f_{K-1}}{\mathfrak{f}_K - \mathfrak{f}_{K-1}}\right)(\mathfrak{f}_K - \mathfrak{f}_{K-1}) = f_K. \quad (3.69)
$$

Combining this, (3.59), (3.64), and (3.11) proves item (ii). The proof of Proposition 3.2.5 is thus complete.

**Exercise 3.2.1.** Prove or disprove the following statement: There exists $ \Phi \in \mathbf{N} $ such that $ \mathcal{P}(\Phi) \leq 16 $ and

$$
\sup_{x \in [-2\pi, 2\pi]} |\cos(x) - (\mathcal{R}_\mathfrak{c}^\mathbf{N}(\Phi))(x)| \leq \frac{1}{2} \quad (3.70)
$$

(cf. Definitions 1.2.4, 1.3.1, and 1.3.4).

**Exercise 3.2.2.** Prove or disprove the following statement: There exists $ \Phi \in \mathbf{N} $ such that $ \mathcal{I}(\Phi) = 4 $, $ \mathcal{O}(\Phi) = 1 $, $ \mathcal{P}(\Phi) \leq 60 $, and $ \forall x, y, u, v \in \mathbb{R} : (\mathcal{R}_\mathfrak{c}^\mathbf{N}(\Phi))(x, y, u, v) = \max\{x, y, u, v\} $ (cf. Definitions 1.2.4, 1.3.1, and 1.3.4).

**Exercise 3.2.3.** Prove or disprove the following statement: For every $ m \in \mathbb{N} $ there exists $ \Phi \in \mathbf{N} $ such that $ \mathcal{I}(\Phi) = 2^m $, $ \mathcal{O}(\Phi) = 1 $, $ \mathcal{P}(\Phi) \leq 3(2^m(2^m+1)) $, and $ \forall x = (x_1, x_2, \dots, x_{2m}) \in \mathbb{R} : (\mathcal{R}_\mathfrak{c}^\mathbf{N}(\Phi))(x) = \max\{x_1, x_2, \dots, x_{2m}\} $ (cf. Definitions 1.2.4, 1.3.1, and 1.3.4).

## 3.3 ANN approximations results for one-dimensional functions

### 3.3.1 Constructive ANN approximation results

**Proposition 3.3.1 (ANN approximations through linear interpolations).** Let $ K \in \mathbb{N} $, $ L, a, \mathfrak{f}_0, \mathfrak{f}_1, \dots, \mathfrak{f}_K \in \mathbb{R} $, $ b \in (a, \infty) $ satisfy for all $ k \in \{0, 1, \dots, K\} $ that $ \mathfrak{f}_k = a + \frac{k(b-a)}{K} $, let $ f : [a, b] \to \mathbb{R} $ satisfy for all $ x, y \in [a, b] $ that

$$
|f(x) - f(y)| \leq L|x - y|, \quad (3.71)
$$

and let $ \mathbf{F} \in \mathbf{N} $ satisfy

$$
\mathbf{F} = \mathbf{A}_{1, f(\mathfrak{f}_0)} \bullet \left(\bigoplus_{k=0}^K \left(\left(\frac{K(f(f_{\min}(k+1)-2f(\mathfrak{f}_k)+f(f_{\max}(k-1, 0))}{b-a}\right) \otimes (\mathbf{i}_1 \bullet \mathbf{A}_{1, -\mathfrak{f}_k})\right)\right) \quad (3.72)
$$

(cf. Definitions 1.3.1, 2.1.1, 2.3.1, 2.3.4, 2.4.10, and 3.2.1). Then

- (i) it holds that $\mathcal{D}(\mathbf{F}) = \{1, K + 1, 1\}$,
- (ii) it holds that $\mathcal{R}_{\mathrm{r}}^{\mathbf{N}}(\mathbf{F}) = \mathcal{L}_{f_{0 \delta 1}, \dots, f_{K}}^{f_{(r_0)}, f_{(r_1)}, \dots, f_{(r_K)}}$,
- (iii) it holds for all $x, y \in \mathbb{R}$ that $|(\mathcal{R}_{\mathrm{r}}^{\mathbf{N}}(\mathbf{F}))(x) - (\mathcal{R}_{\mathrm{r}}^{\mathbf{N}}(\mathbf{F}))(y)| \leq L|x - y|$,
- (iv) it holds that $\sup_{x \in [a,b]} |(\mathcal{R}_{\mathrm{r}}^{\mathbf{N}}(\mathbf{F}))(x) - f(x)| \leq L(b - a)K^{-1}$, and
- (v) it holds that $\mathcal{P}(\mathbf{F}) = 3K + 4$ .

(cf. Definitions 1.2.4, 1.3.4, and 3.1.5).

**Proof of Proposition 3.3.1.** Note that the fact that for all $k \in \{0, 1, \dots, K\}$ it holds that

$$
\mathfrak{r}_{\min(k+1,K)} - \mathfrak{r}_{\min(k,K-1)} = \mathfrak{r}_{\max(k,1)} - \mathfrak{r}_{\max(k-1,0)} = (b - a)K^{-1}
$$

establishes that for all $k \in \{0, 1, \dots, K\}$ it holds that

$$
\begin{align*}
\frac{(f(\mathfrak{r}_{\min(k+1,K)}) - f(\mathfrak{r}_k)) - (f(\mathfrak{r}_k) - f(\mathfrak{r}_{\min(k-1,0)}))}{\left(\mathfrak{r}_{\min(k+1,K)} - \mathfrak{r}_{\min(k,K-1)}\right) - \left(\mathfrak{r}_{\max(k,1)} - \mathfrak{r}_{\max(k-1,0)}\right)} \\
= \frac{K(f(\mathfrak{r}_{\min(k+1,K)}) - 2f(\mathfrak{r}_k) + f(\mathfrak{r}_{\max(k-1,0)}))}{(b - a)}.
\end{align*}
$$

This and Proposition 3.2.5 prove items (i), (ii), and (v). Observe that item (i) in Corollary 3.1.8, item (ii), and the assumption that for all $x, y \in [a, b]$ it holds that

$$
|f(x) - f(y)| \leq L|x - y|
$$

prove item (iii). Note that item (ii), the assumption that for all $x, y \in [a, b]$ it holds that

$$
|f(x) - f(y)| \leq L|x - y|,
$$

item (ii) in Corollary 3.1.8, and the fact that for all $k \in \{1, 2, \dots, K\}$ it holds that

$$
\mathfrak{r}_k - \mathfrak{r}_{k-1} = \frac{(b - a)}{K}
$$

ensure that for all $x \in [a, b]$ it holds that

$$
|(\mathcal{R}_{\mathrm{r}}^{\mathbf{N}}(\mathbf{F}))(x) - f(x)| \leq L\left(\max_{k \in \{1,2,\dots,K\}} |\mathfrak{r}_k - \mathfrak{r}_{k-1}|\right) = \frac{L(b - a)}{K}.
$$

This establishes item (iv). The proof of Proposition 3.3.1 is thus complete.

## Chapter 3: One-dimensional ANN approximation results

**Lemma 3.3.2 (Approximations through ANNs with constant realizations).**

Let $L, a \in \mathbb{R}$, $b \in [a, \infty)$, $\xi \in [a, b]$, let $f: [a, b] \rightarrow \mathbb{R}$ satisfy for all $x, y \in [a, b]$ that

$$
|f(x) - f(y)| \leq L|x - y|, \quad (3.79)
$$

and let $\mathbf{F} \in \mathbf{N}$ satisfy

$$
\mathbf{F} = \mathbf{A}_{1,f(\xi)} \bullet (0 \otimes (\mathbf{i}_1 \bullet \mathbf{A}_{1,-\xi})) \quad (3.80)
$$

(cf. Definitions 1.3.1, 2.1.1, 2.3.1, 2.3.4, and 3.2.1). Then

- (i) it holds that $\mathcal{D}(\mathbf{F}) = (1, 1, 1)$,
- (ii) it holds that $\mathcal{R}_{\xi}^{\mathbf{N}}(\mathbf{F}) \in C(\mathbb{R}, \mathbb{R})$,
- (iii) it holds for all $x \in \mathbb{R}$ that $((\mathcal{R}_{\xi}^{\mathbf{N}}(\mathbf{F}))(x) = f(\xi)$,
- (iv) it holds that $\sup_{x \in [a,b]}(|(\mathcal{R}_{\xi}^{\mathbf{N}}(\mathbf{F}))(x) - f(x)| \leq L \max\{\xi - a, b - \xi\}$, and
- (v) it holds that $\mathcal{P}(\mathbf{F}) = 4$.

(cf. Definitions 1.2.4 and 1.3.4).

**Proof of Lemma 3.3.2.** Observe that items (i) and (ii) in Lemma 2.3.3, and items (ii) and (iii) in Lemma 3.2.4 establish items (i) and (ii). Note that item (iii) in Lemma 2.3.3 and item (iii) in Lemma 2.3.5 imply that for all $x \in \mathbb{R}$ it holds that

$$
\begin{aligned}
((\mathcal{R}_{\xi}^{\mathbf{N}}(\mathbf{F}))(x) &= ((\mathcal{R}_{\xi}^{\mathbf{N}}(0 \otimes (\mathbf{i}_1 \bullet \mathbf{A}_{1,-\xi}))) (x) + f(\xi) \\
&= 0 \big( (\mathcal{R}_{\xi}^{\mathbf{N}}(\mathbf{i}_1 \bullet \mathbf{A}_{1,-\xi})(x)) \big) + f(\xi) = f(\xi)
\end{aligned} \quad (3.81)
$$

(cf. Definitions 1.2.4 and 1.3.4). This proves item (iii). Observe that (3.81), the fact that $\xi \in [a, b]$, and the assumption that for all $x, y \in [a, b]$ it holds that

$$
|f(x) - f(y)| \leq L|x - y| \quad (3.82)
$$

demonstrate that for all $x \in [a, b]$ it holds that

$$
|(\mathcal{R}_{\xi}^{\mathbf{N}}(\mathbf{F}))(x) - f(x)| = |f(\xi) - f(x)| \leq L|x - \xi| \leq L \max\{\xi - a, b - \xi\}. \quad (3.83)
$$

This establishes item (iv). Note that (1.78) and item (i) show that

$$
\mathcal{P}(\mathbf{F}) = 1(1+1)+1(1+1) = 4. \quad (3.84)
$$

This proves item (v). The proof of Lemma 3.3.2 is thus complete.

**Corollary 3.3.3 (Explicit ANN approximations with prescribed error tolerances).** Let

$\epsilon \in (0, \infty)$, $L, a \in \mathbb{R}$, $b \in (a, \infty)$, $K \in \mathbb{N}_0 \cap [\frac{L(b-a)}{\epsilon}, \frac{L(b-a)}{\epsilon} + 1)$, $\mathbf{f}_0, \mathbf{f}_1, \dots, \mathbf{f}_K \in \mathbb{R}$ satisfy for all $ k \in \{0, 1, \dots, K\} $ that $\mathbf{f}_k = a + \frac{k(b-a)}{\max\{K, 1\}}$, let $f: [a, b] \to \mathbb{R}$ satisfy for all $x, y \in [a, b]$ that

$$
|f(x) - f(y)| \le L|x - y|,
$$

and let $\mathbf{F} \in \mathbf{N}$ satisfy

$$
\mathbf{F} = \mathbf{A}_{1, f(t_0)} \bullet \left( \bigoplus_{k=0}^{K} \left( \left( \frac{K(f(t_{\min\{k+1, K\}}) - 2f(t_k) + f(t_{\max\{k-1, 0\}}))}{(b-a)} \right) \otimes (\mathbf{1} \bullet \mathbf{A}_{1, -f_k}) \right) \right)
$$

(cf. Definitions 1.3.1, 2.1.1, 2.3.1, 2.3.4, 2.4.10, and 3.2.1). Then

- (i) it holds that $\mathcal{D}(\mathbf{F}) = (1, K + 1, 1)$,
- (ii) it holds that $\mathcal{R}^{\mathbf{N}}_{\epsilon}(\mathbf{F}) \in C(\mathbb{R}, \mathbb{R})$,
- (iii) it holds for all $x, y \in \mathbb{R}$ that $|(\mathcal{R}^{\mathbf{N}}_{\epsilon}(\mathbf{F}))(x) - (\mathcal{R}^{\mathbf{N}}_{\epsilon}(\mathbf{F}))(y)| \le L|x - y|$,
- (iv) it holds that $\sup_{x \in [a, b]} |(\mathcal{R}^{\mathbf{N}}_{\epsilon}(\mathbf{F}))(x) - f(x)| \le \frac{L(b-a)}{\max\{K, 1\}} \le \epsilon$, and
- (v) it holds that $\mathcal{P}(\mathbf{F}) = 3K + 4 \le 3L(b-a)\epsilon^{-1} + 7$

(cf. Definitions 1.2.4, 1.3.1, and 1.3.4).

**Proof of Corollary 3.3.3.** Observe that the assumption that $K \in \mathbb{N}_0 \cap [\frac{L(b-a)}{\epsilon}, \frac{L(b-a)}{\epsilon} + 1)$ ensures that

$$
\frac{L(b-a)}{\max\{K, 1\}} \le \epsilon.
$$

This, items (i), (iii), and (iv) in Proposition 3.3.1, and items (i), (ii), (iii), and (iv) in Lemma 3.3.2 establish items (i), (ii), (iii), and (iv). Note that item (v) in Proposition 3.3.1, item (v) in Lemma 3.3.2, and the fact that

$$
K \le 1 + \frac{L(b-a)}{\epsilon},
$$

imply that

$$
\mathcal{P}(\mathbf{F}) = 3K + 4 \le \frac{3L(b-a)}{\epsilon} + 7.
$$

This proves item (v). The proof of Corollary 3.3.3 is thus complete.
