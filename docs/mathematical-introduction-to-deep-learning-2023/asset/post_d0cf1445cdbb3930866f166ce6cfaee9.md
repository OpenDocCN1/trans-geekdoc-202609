
For $(x^1, x^2, \ldots, x^n)$ it holds that

$$
\begin{align*}
&\mathfrak{M}_{e_k, \mathrm{D}_k(\mathbf{P}_n(\Phi))}\left(\mathcal{W}_{k,\mathbf{P}_n(\Phi)}\mathbf{f} + \mathcal{B}_{k,\mathbf{P}_n(\Phi)}\right) \\
&= \mathfrak{M}_{e_k, \mathrm{D}_k(\mathbf{P}_n(\Phi))} \begin{pmatrix}
\mathcal{W}_{k,\Phi_1} & 0 & 0 & \cdots & 0 \\
0 & \mathcal{W}_{k,\Phi_2} & 0 & \cdots & 0 \\
0 & 0 & \mathcal{W}_{k,\Phi_3} & \cdots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \cdots & \mathcal{W}_{k,\Phi_n}
\end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \\ x_3 \\ \vdots \\ x_n \end{pmatrix} + \begin{pmatrix} \mathcal{B}_{k,\Phi_1} \\ \mathcal{B}_{k,\Phi_2} \\ \mathcal{B}_{k,\Phi_3} \\ \vdots \\ \mathcal{B}_{k,\Phi_n} \end{pmatrix} \\
&= \mathfrak{M}_{e_k, \mathrm{D}_k(\mathbf{P}_n(\Phi))} \begin{pmatrix}
\mathcal{W}_{k,\Phi_1}x_1 + \mathcal{B}_{k,\Phi_1} \\
\mathcal{W}_{k,\Phi_2}x_2 + \mathcal{B}_{k,\Phi_2} \\
\mathcal{W}_{k,\Phi_3}x_3 + \mathcal{B}_{k,\Phi_3} \\
\vdots \\
\mathcal{W}_{k,\Phi_n}x_n + \mathcal{B}_{k,\Phi_n}
\end{pmatrix} \\
&= \begin{pmatrix}
\mathfrak{M}_{e_k,\mathrm{D}_k(\Phi_1)}(\mathcal{W}_{k,\Phi_1}x_1 + \mathcal{B}_{k,\Phi_1}) \\
\mathfrak{M}_{e_k,\mathrm{D}_k(\Phi_2)}(\mathcal{W}_{k,\Phi_2}x_2 + \mathcal{B}_{k,\Phi_2}) \\
\mathfrak{M}_{e_k,\mathrm{D}_k(\Phi_3)}(\mathcal{W}_{k,\Phi_3}x_3 + \mathcal{B}_{k,\Phi_3}) \\
\vdots \\
\mathfrak{M}_{e_k,\mathrm{D}_k(\Phi_n)}(\mathcal{W}_{k,\Phi_n}x_n + \mathcal{B}_{k,\Phi_n})
\end{pmatrix}. \tag{2.55}
\end{align*}
$$

This proves that for all $k \in \{1, 2, \ldots, L\}$, $\mathbf{f} = (\mathbf{f}_0, \mathbf{f}_1, \ldots, \mathbf{f}_L) \in \mathfrak{X}$, $x^1 = (x_0^1, x_1^1, \ldots, x_L^1) \in X^1$, $x^2 = (x_0^2, x_1^2, \ldots, x_L^2) \in X^2$, $\ldots$, $x^n = (x_0^n, x_1^n, \ldots, x_L^n) \in X^n$ with $\mathbf{f}_{k-1} = (x_{k-1}^1, x_{k-1}^2, \ldots, x_{k-1}^n)$ it holds that

$$
\mathbf{f}_k = (x_k^1, x_k^2, \ldots, x_k^n). \tag{2.56}
$$

Induction, and (1.91) hence demonstrate that for all $k \in \{1, 2, \ldots, L\}$, $\mathbf{f} = (\mathbf{f}_0, \mathbf{f}_1, \ldots, \mathbf{f}_L) \in \mathfrak{X}$, $x^1 = (x_0^1, x_1^1, \ldots, x_L^1) \in X^1$, $x^2 = (x_0^2, x_1^2, \ldots, x_L^2) \in X^2$, $\ldots$, $x^n = (x_0^n, x_1^n, \ldots, x_L^n) \in X^n$ with $\mathbf{f}_0 = (x_0^1, x_0^2, \ldots, x_0^n)$ it holds that

$$
\begin{align*}
&\left(\mathcal{R}_{\mathfrak{a}}^\mathbf{N}(\mathbf{P}_n(\Phi))\right)(\mathbf{f}_0) = \mathbf{f}_L = (x_L^1, x_L^2, \ldots, x_L^n) \tag{2.57} \\
&= \left(\left(\mathcal{R}_{\mathfrak{a}}^\mathbf{N}(\Phi_1)\right)(x_0^1), \left(\mathcal{R}_{\mathfrak{a}}^\mathbf{N}(\Phi_2)\right)(x_0^2), \ldots, \left(\mathcal{R}_{\mathfrak{a}}^\mathbf{N}(\Phi_n)\right)(x_0^n)\right).
\end{align*}
$$

This establishes item (ii). The proof of Proposition 2.2.3 is thus complete.$\square$

## **Proposition 2.2.4** (Upper bounds for the numbers of parameters of parallelizations of fully-connected feedforward ANNs).

Let $n, L \in \mathbb{N}$, $\Phi_1, \Phi_2, \ldots, \Phi_n \in \mathbb{N}$ satisfy $L = \mathcal{L}(\Phi_1) = \mathcal{L}(\Phi_2) = \ldots = \mathcal{L}(\Phi_n)$ (cf. Definition 1.3.1). Then

$$
\mathcal{P}\left(\mathbf{P}_n(\Phi_1, \Phi_2, \ldots, \Phi_n)\right) \le \tfrac{1}{2}\left[\sum_{j=1}^n \mathcal{P}\left(\Phi_j\right)\right]^2 \tag{2.58}
$$

(cf. Definition 2.2.1).

Proof of Proposition 2.2.4. Throughout this proof, for every $j \in \{1, 2, \ldots, n\}$, $k \in \{0, 1, \ldots, L\}$ let $l_{j,k} = \mathbb{D}_k(\Phi_j)$. Note that item **(ii)** in Lemma 2.2.2 demonstrates that

$$
\begin{align*}
&\mathcal{P}\big(\mathbf{P}_n(\Phi_1, \Phi_2, \dots, \Phi_n)\big) = \sum_{k=1}^L \Big[\sum_{i=1}^n l_{i,k}\Big]\Big[\big(\sum_{i=1}^n l_{i,k-1}\big)+1\Big] \\
&= \sum_{k=1}^L \Big[\sum_{i=1}^n l_{i,k}\Big]\Big[\big(\sum_{j=1}^n l_{j,k-1}\big)+1\Big] \\
&\le \sum_{i=1}^n \sum_{j=1}^n \sum_{k=1}^L l_{i,k}(l_{j,k-1}+1) \le \sum_{i=1}^n \sum_{j=1}^n \sum_{k,\ell=1}^L l_{i,k}(l_{j,\ell-1}+1) \tag{2.59} \\
&= \sum_{i=1}^n \sum_{j=1}^n \Big[\sum_{k=1}^L l_{i,k}\Big]\Big[\sum_{\ell=1}^L(l_{j,\ell-1}+1)\Big] \\
&\le \sum_{i=1}^n \sum_{j=1}^n \Big[\sum_{k=1}^L \tfrac{1}{2}l_{i,k}(l_{i,k-1}+1)\Big]\Big[\sum_{\ell=1}^L l_{j,\ell}(l_{j,\ell-1}+1)\Big] \\
&= \sum_{i=1}^n \sum_{j=1}^n \tfrac{1}{2}\mathcal{P}(\Phi_i)\mathcal{P}(\Phi_j) = \tfrac{1}{2}\Big[\sum_{i=1}^n\mathcal{P}(\Phi_i)\Big]^2.
\end{align*}
$$

The proof of Proposition 2.2.4 is thus complete.

## **Corollary 2.2.5** (Lower and upper bounds for the numbers of parameters of parallelizations of fully-connected feedforward ANNs.)

Let $n \in \mathbb{N}$, $\Phi = (\Phi_1, \dots, \Phi_n) \in \mathbb{N}^n$ satisfy $\mathcal{D}(\Phi_1) = \mathcal{D}(\Phi_2) = \dots = \mathcal{D}(\Phi_n)$ (cf. Definition 1.3.1). Then

$$
\begin{align*}
\Big[\frac{n^2}{2}\Big]\mathcal{P}(\Phi_1) \le \Big[\frac{n^2+n}{2}\Big]\mathcal{P}(\Phi_1) \le \mathcal{P}\big(\mathbf{P}_n(\Phi)\big) \le n^2\mathcal{P}(\Phi_1) \le \tfrac{1}{2}\Big[\sum_{i=1}^n \mathcal{P}(\Phi_i)\Big]^2 \tag{2.60}
\end{align*}
$$

(cf. Definition 2.2.1).

Proof of Corollary 2.2.5. Throughout this proof, let $L \in \mathbb{N}$, $l_0, l_1, \dots, l_L \in \mathbb{N}$ satisfy

$$
\mathcal{D}(\Phi_1) = (l_0, l_1, \dots, l_L). \tag{2.61}
$$

Observe that (2.61) and the assumption that $\mathcal{D}(\Phi_1) = \mathcal{D}(\Phi_2) = \dots = \mathcal{D}(\Phi_n)$ imply that for all $j \in \{1, 2, \dots, n\}$ it holds that

$$
\mathcal{D}(\Phi_j) = (l_0, l_1, \dots, l_L). \tag{2.62}
$$

Combining this with item **(iii)** in Lemma 2.2.2 demonstrates that

$$
\mathcal{P}\big(\mathbf{P}_n(\Phi)\big) = \sum_{j=1}^L(nl_j)\big((nl_{j-1})+1\big). \tag{2.63}
$$

Hence, we obtain that

$$
\mathcal{P} (\mathbf{P}_{n}(\mathbb{\Phi})) \leq \sum_{j=1}^{L}(n l_{j})((n l_{j-1}) + n) = n^{2}\bigg[\sum_{j=1}^{L}l_{j}(l_{j-1}+1)\bigg] = n^{2}\mathcal{P}(\mathbb{\Phi}_{1}). \qquad(2.64)
$$

Furthermore, note that the assumption that $\mathcal{D}(\mathbb{\Phi}_{1}) = \mathcal{D}(\mathbb{\Phi}_{2}) = \dots = \mathcal{D}(\mathbb{\Phi}_{n})$ and the fact that $\mathcal{P}(\mathbb{\Phi}_{1}) \geq l_{1}(l_{0}+1) \geq 2$ ensure that

$$
n^{2}\mathcal{P}(\mathbb{\Phi}_{1}) \leq \frac{n^{2}}{2}[\mathcal{P}(\mathbb{\Phi}_{1})]^{2} = \tfrac{1}{2}[n\mathcal{P}(\mathbb{\Phi}_{1})]^{2} = \tfrac{1}{2}\bigg[\sum_{i=1}^{n}\mathcal{P}(\mathbb{\Phi}_{1})\bigg]^{2} = \tfrac{1}{2}\bigg[\sum_{i=1}^{n}\mathcal{P}(\mathbb{\Phi}_{i})\bigg]^{2}. \qquad(2.65)
$$

Moreover, observe that $(2.63)$ and the fact that for all $a$, $b \in \mathbb{N}$ it holds that

$$
2(ab+1) = ab + 1 + (a-1)(b-1) + a + b \geq ab + a + b + 1 = (a+1)(b+1) \qquad(2.66)
$$

show that

$$
\begin{aligned}
\mathcal{P}(\mathbf{P}_{n}(\mathbb{\Phi})) &\geq \tfrac{1}{2}\bigg[\sum_{j=1}^{L}(n l_{j})(n+1)(l_{j-1}+1)\bigg]\\
&= \frac{n(n+1)}{2}\bigg[\sum_{j=1}^{L}l_{j}(l_{j-1}+1)\bigg] = \bigg[\frac{n^{2}+n}{2}\bigg]\mathcal{P}(\mathbb{\Phi}_{1}). \end{aligned}\qquad(2.67)
$$

This, $(2.64)$, and $(2.65)$ establish $(2.60)$. The proof of Corollary 2.2.5 is thus complete. $\square$

### **Exercice 2.2.1**

Prove or disprove the following statement: For every $n \in \mathbb{N}$, $\mathbb{\Phi} = (\mathbb{\Phi}_{1}, \dots, \mathbb{\Phi}_{n}) \in \mathbf{N}^{n}$ with $\mathcal{L}(\mathbb{\Phi}_{1}) = \mathcal{L}(\mathbb{\Phi}_{2}) = \dots = \mathcal{L}(\mathbb{\Phi}_{n})$ it holds that

$$
\mathcal{P} (\mathbf{P}_{n}(\mathbb{\Phi}_{1}, \mathbb{\Phi}_{2}, \dots, \mathbb{\Phi}_{n})) \leq n \big[\sum_{i=1}^{n}\mathcal{P}(\mathbb{\Phi}_{i})\big]. \qquad(2.68)
$$

### **Exercice 2.2.2**

Prove or disprove the following statement: For every $n \in \mathbb{N}$, $\mathbb{\Phi} = (\mathbb{\Phi}_{1}, \dots, \mathbb{\Phi}_{n}) \in \mathbf{N}^{n}$ with $\mathcal{P}(\mathbb{\Phi}_{1}) = \mathcal{P}(\mathbb{\Phi}_{2}) = \dots = \mathcal{P}(\mathbb{\Phi}_{n})$ it holds that

$$
\mathcal{P}(\mathbf{P}_{n}(\mathbb{\Phi}_{1}, \mathbb{\Phi}_{2}, \dots, \mathbb{\Phi}_{n})) \leq n^{2}\mathcal{P}(\mathbb{\Phi}_{1}). \qquad(2.69)
$$

## 2.2.2 Representations of the identities with ReLU activation functions

### **Definition 2.2.6** (Fully-connected feedforward ReLU identity ANNs).

We denote by $\mathcal{I}_{d} \in \mathbf{N}$, $d \in \mathbf{N}$, the fully-connected feedforward ANNs which satisfy for all $d \in \mathbb{N}$ that

$$
\begin{aligned}
\mathcal{I}_{1} = \bigg(\bigg((\binom{1}{-1}), \bigg(\binom{0}{0}\bigg)\bigg), ((1\quad-1), 0)\bigg) \in ((\mathbb{R}^{2 \times 1} \times \mathbb{R}^{2}) \times (\mathbb{R}^{1 \times 2} \times \mathbb{R}^{1})) \qquad(2.70)
\end{aligned}
$$

and

$$
\mathcal{I}_{d} = \mathbf{P}_{d}(\mathcal{I}_{1}, \mathcal{I}_{1}, \dots, \mathcal{I}_{1}) \qquad(2.71)
$$

(cf. Definitions 1.3.1 and 2.2.1).
