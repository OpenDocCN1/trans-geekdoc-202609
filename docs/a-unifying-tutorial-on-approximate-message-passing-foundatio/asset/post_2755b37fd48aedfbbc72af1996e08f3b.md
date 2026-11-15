
for \(k \in \mathbb{N}_0\). Here, \(E_i^k\) and \(H_j^{k+1}\) denote the \(i^{th}\) and \(j^{th}\) rows of \(E^k \in \mathbb{R}^{n \times \ell_E}\) and \(H^{k+1} \in \mathbb{R}^{p \times \ell_H}\) respectively. Also, \(g'_k : \mathbb{R}^{\ell_E} \times \mathbb{R} \rightarrow \mathbb{R}^{\ell_H \times \ell_E}\) and \(f'_{k+1} : \mathbb{R}^{\ell_H} \times \mathbb{R} \rightarrow \mathbb{R}^{\ell_E \times \ell_H}\) are bounded, Borel measurable functions that agree with the derivatives (Jacobians) of \(g_k, f_{k+1}\) respectively with respect to their first arguments, wherever the latter are defined.

Consider now a sequence of recursions (A.52) indexed by \(n\) and \(p \equiv p_n\) with \(n/p \to \delta \in (0, \infty)\) as \(n \to \infty\), and assume appropriate analogues of (B0)-(B5) with \(r \in [2, \infty)\). In particular, suppose in place of (B2) that \((M^0)^\top M^0/n \xrightarrow{\Sigma} \Sigma_0\) for some non-negative definite \(\Sigma_0 \in \mathbb{R}^{\ell_E \times \ell_E}\), and that \(p^{-1} \sum_{i=1}^p \sum_{j=1}^{\ell_E} |M_{ij}^0|^r = O_c(1)\). The state evolution recursion for (A.52) is then defined analogously to that in (2.11), via

$$
\mathrm{T}_{k+1} := \mathbb{E}(g_k(G_k^\sigma, \bar{\gamma}) g_k(G_k^\sigma, \bar{\gamma})^\top) \in \mathbb{R}^{\ell_H \times \ell_H},\qquad
\Sigma_{k+1} := \delta^{-1} \mathbb{E}(f_{k+1}(G_{k+1}^\tau, \bar{\beta}) f_{k+1}(G_{k+1}^\tau, \bar{\beta})^\top) \in \mathbb{R}^{\ell_E \times \ell_E}
$$ (A.53)

for \(k \in \mathbb{N}_0\), where we take \(G_k^\sigma \sim N_{\ell_E}(0, \Sigma_k)\) to be independent of \(\bar{\gamma} \sim \pi_{\bar{\gamma}}\), and \(G_{k+1}^\tau \sim N_{\ell_H}(0, \mathrm{T}_{k+1})\) to be independent of \(\bar{\beta} \sim \pi_{\bar{\beta}}\).

For \(k \in \mathbb{N}_0\), it can be shown that the empirical distributions of the rows of \((E^k \gamma)\) and \((H^{k+1} \beta)\) converge completely in \(d_r\) to \(N_{\ell_E}(0, \Sigma_k) \otimes \pi_\gamma\) and \(N_{\ell_H}(0, \mathrm{T}_{k+1}) \otimes \pi_\beta\) respectively as \(n, p \to \infty\) with \(n/p \to \delta\). Similarly as in Remark 2.4, these limiting distributions remain unchanged if one or both of \(C_k, B_{k+1}\) are replaced with the deterministic matrices \(\bar{C}_k := \mathbb{E}(g'_k(G_k^\Sigma, \bar{\gamma}))\) and \(\bar{B}_{k+1} := \delta^{-1} \mathbb{E}(f'_{k+1}(G_{k+1}^\tau, \bar{\beta}))\) respectively. Moreover, by generalising the definitions (2.12)-(2.13) of the limiting covariance matrices in line with (A.53), one can obtain the \(d_r\) limits of the joint empirical distributions for (A.52) above.

The proofs of these results are conceptually very similar to that of Theorem 2.5. For further details, see Javanmard and Montanari (2013), who first consider a generalisation of the symmetric iteration (2.1) with matrix-valued iterates, and then handle the asymmetric case by a reduction argument.

## A.8 Proofs for Section 3

Proof of Theorem 3.1. As described in the proof sketch on page 34, we introduce the recursion (3.13) given by \(u^1 \equiv u^1(n) = W \hat{v}^0 = W g_0(v^0)\) and

$$
u^{k+1} \equiv u^{k+1}(n) = W g_k(u^k + \mu_k v) - \tilde{b}_k g_{k-1}(u^{k-1} + \mu_{k-1} v) = W f_k(u^k, v) - \tilde{b}_k f_{k-1}(u^{k-1}, v)
$$

for $k, n \in \mathbb{N}$, where $f_k(x, y) = g_k(x + \mu_k y)$ and $f'_k(x, y) = g'_k(x + \mu_k y)$ for $x, y \in \mathbb{R}$, and $\tilde{b}_k \equiv \tilde{b}_k(n) = \langle g'_k(u^k + \mu_k v) \rangle_n = \langle f'_k(u^k, v) \rangle_n$. First, we verify that this is an iteration of the form (2.1) to which we can apply the master theorems from Section 2.1 for symmetric AMP. Indeed, it follows from (M0) and (M1) respectively that (3.13) satisfies (A0) and (A1^+), where the latter holds with $m^0 = v$, $\gamma = v$, $\bar{\gamma} = V \sim \pi$, $\bar{\eta} = U$ and $\tilde{f}_0(x, y) = f_0(\mu_0 x + \sigma_0 y)$ for $x, y \in \mathbb{R}$. By Remark A.5, (A1^+) implies that (A1)-(A3) hold with $r = 2$ and $\tau_1 = \text{c-lim}_{n \to \infty} \| \partial^0 \|_n^2 = \sigma_1^2$. As verified in (3.14), the state evolution parameters $(\tau_k : k \in \mathbb{N})$ for (3.13) satisfy $\tau_k^2 = \sigma_k^2$ for all $k$ in view of (3.6). Finally, by (M2), each $f_k: \mathbb{R}^2 \to \mathbb{R}$ is Lipschitz and the corresponding $f'_k$ satisfies (A5). Consequently, for each $k \in \mathbb{N}$, it follows from Theorem 2.3 that

$$
\sup_{\psi \in \text{PL}_{k+1}(2,1)} \left| \frac{1}{n} \sum_{i=1}^n \psi(v_i^0, v_i^1, \dots, v_i^k, v_i) - \mathbb{E}(\psi(\mu_0 V + \sigma_0 U, \sigma_1 G_1, \dots, \sigma_k G_k, V)) \right| \xrightarrow{\mathfrak{c}} 0
$$

as \( n \to \infty \), where \((\sigma_1 G_1, \dots, \sigma_k G_k) \sim N_k(0, \bar{\Sigma}^{[k]})\) is taken to be independent of \((U, V)\) from (M1). Since \(\Phi_k: (x_1, \dots, x_k, y) \mapsto (x_1 + \mu_1 y, \dots, x_k + \mu_k y, y)\) is a linear map with Lipschitz constant \(\tilde{L}_k := \| (\mu_1, \dots, \mu_k, 1) \|\), we have \(\tilde{L}_k^{-2}(\psi \circ \Phi_k) \in \text{PL}_{k+1}(2, 1)\) whenever \(\psi \in \text{PL}_{k+1}(2, 1)\), so it follows from the display above that

$$
\sup_{\psi \in \text{PL}_{k+2}(2,1)} \left| \frac{1}{n} \sum_{i=1}^n \psi(v_i^0, v_i^1 + \mu_1 v_i, \dots, v_i^k + \mu_k v_i, v_i) - \mathbb{E}(\psi(\mu_0 V + \sigma_0 U, \mu_1 V + \sigma_1 G_1, \dots, \mu_k V + \sigma_k G_k, V)) \right| \xrightarrow{\mathfrak{c}} 0
$$ (A.54)

as \( n \to \infty \). Defining \(\tilde{\Delta}^k \equiv \tilde{\Delta}^k(n) := v^k - (u^k + \mu_k v) \in \mathbb{R}^n\) for \( k, n \in \mathbb{N} \), we can apply Lemma B.24 to see that

$$
\begin{aligned}
&\sup_{\psi \in \text{PL}_{k+2}(2,1)} \left| \frac{1}{n} \sum_{i=1}^n \psi(v_i^0, v_i^1, \dots, v_i^k, v_i) \right. \\
&\qquad\left. - \psi(v_i^0, v_i^1 + \mu_1 v_i, \dots, v_i^k + \mu_k v_i, v_i) \right| \\
&\quad \le \left( \sum_{\ell=1}^k \|\tilde{\Delta}^\ell\|_n^2 \right)^{1/2} \left( 1 + \sum_{\ell=1}^k (\|v^\ell\|_n + \|u^\ell + \mu_\ell v\|_n) \right. \\
&\qquad\qquad\left. + 2(\|v^0\|_n + \|v\|_n) \right) \\
&\quad \le \left( \sum_{\ell=1}^k \|\tilde{\Delta}^\ell\|_n^2 \right)^{1/2} \left( 1 + \sum_{\ell=1}^k (\|\tilde{\Delta}^\ell\|_n + 2\|u^\ell + \mu_\ell v\|_n) \right. \\
&\qquad\qquad\left. + 2(\|v^0\|_n + \|v\|_n) \right)
\end{aligned}
$$ (A.55)

for all \( k \) and \( n \), where \(\|\cdot\|_n \equiv \|\cdot\|_{n,2} = n^{-1/2} \|\cdot\|\) on \(\mathbb{R}^n\). For every \(\ell \in \mathbb{N}\), it follows from (M1) and (A.54) that

$$
\begin{aligned}
\|v^0\|_n &\xrightarrow{\mathcal{L}} \mathbb{E}((\mu_0 V + \sigma_0 U)^2) = \mu_0^2 + \sigma_0^2, \qquad \|v\|_n^2 \to \mathbb{E}(V^2) = 1,\\
\|u^\ell + \mu_\ell v\|_n^2 &= \frac{1}{n} \sum_{i=1}^n (u_i^\ell + \mu_\ell v_i)^2 \xrightarrow{\mathcal{L}} \mathbb{E}((\mu_\ell V + \sigma_\ell G_\ell)^2) = \mu_\ell^2 + \sigma_\ell^2
\end{aligned}
$$ (A.56)

as \( n \to \infty \). We will now establish by induction on \( k \in \mathbb{N} \) that

$$
\|\tilde{\Delta}^k\|_n = \|v^k - (u^k + \mu_k v)\|_n \xrightarrow{\mathcal{L}} 0 \quad \text{as } n \to \infty
$$ (A.57)

and hence that the conclusion (3.8) of Theorem 3.1 holds for every \( k \). For the base case \( k=1 \), we have \(\|v\|_n \xrightarrow{p} 1\) by (3.4) and \(\lambda\langle \hat{v}^0, v \rangle_n \xrightarrow{p} \mu_1\) by (3.5), so

$$
\begin{aligned}
\|\tilde{\Delta}^1\|_n &= \|v^1 - (u^1 + \mu_1 v)\|_n = \|A\hat{v}^0 - (W\hat{v}^0 + \mu_1 v)\|_n \\
&= |\lambda\langle \hat{v}^0, v \rangle_n - \mu_1| \|v\|_n \xrightarrow{\mathcal{L}} 0
\end{aligned}
$$

as $n \to \infty$. It follows from this and (A.54)–(A.56) that (3.8) holds when $k=1$. For a general $k \ge 2$, we write

$$
\begin{aligned}
\tilde{\Delta}^{k+1} &\equiv \tilde{\Delta}^{k+1}(n) = v^{k+1} - (u^{k+1} + \mu_{k+1}v) \\
&= A g_k(v^k) - b_k g_{k-1}(v^{k-1}) - (W g_k(u^k + \mu_k v) \\
&\qquad - \tilde{b}_k g_{k-1}(u^{k-1} + \mu_{k-1}v) + \mu_{k+1}v) \\
&= (\lambda \langle v, g_k(v^k) \rangle_n - \mu_{k+1})v + W(g_k(v^k) - g_k(u^k + \mu_k v)) \\
&\qquad + (\tilde{b}_k g_{k-1}(u^{k-1} + \mu_{k-1}v) - b_k g_{k-1}(v^{k-1})) \\
&=: R_{n1} + R_{n2} + R_{n3}
\end{aligned}
$$

for each $n \in \mathbb{N}$, and consider $R_{n1}, R_{n2}, R_{n3}$ in turn. First, since $(x_1, \dots, x_k, y) \mapsto y g_k(x_k)$ belongs to \(\text{PL}_{k+1}(2)\) in view of Lemma B.22, it follows from the inductive hypothesis (3.8) and the definition of \(\mu_{k+1}\) in (3.6) that \(\lambda \langle v, g_k(v^k) \rangle_n = n^{-1} \sum_{i=1}^n \lambda v_i g_k(v_i^k) \xrightarrow{c} \lambda \mathbb{E}(V g_k(\mu_k V + \sigma_k G_k)) = \mu_{k+1}\). Together with (A.56), this implies that \(\|R_{n1}\|_n = |\lambda \langle v, g_k(v^k) \rangle_n - \mu_{k+1}| \|v\|_n \xrightarrow{c} 0\) as \( n \to \infty \).

Next, since \(\|W\| \equiv \|W\|_{2 \to 2} = O_c(1)\) (e.g. Anderson et al., 2010; Knowles and Yin, 2013) and \(g_k\) is \(L_k\)-Lipschitz for some \(L_k > 0\), the inductive hypothesis (A.57) ensures that

$$
\begin{aligned}
\|R_{n2}\|_n &\le \|W\| \|g_k(v^k) - g_k(u^k + \mu_k v)\|_n \le L_k \|W\| \|v^k - (u^k + \mu_k v)\|_n \\
&= L_k \|W\| \|\tilde{\Delta}^k\|_n \xrightarrow{c} 0
\end{aligned}
$$

as \( n \to \infty \). Similarly, \(\|\tilde{\Delta}^{k-1}\|_n \xrightarrow{c} 0\) by induction and \(g_{k-1}\) is \(L_{k-1}\)-Lipschitz for some \(L_{k-1} > 0\), so as a first step towards controlling \(\|R_{n3}\|_n\), we have

$$
\|g_{k-1}(u^{k-1} + \mu_{k-1}v) - g_{k-1}(v^{k-1})\|_n \le L_{k-1} \|\tilde{\Delta}^{k-1}\|_n \xrightarrow{c} 0.
$$

Note that since \((x_1, \dots, x_k, y) \mapsto g_{k-1}(x_{k-1})^2\) lies in \(\text{PL}_{k+1}(2)\) by Lemma B.22, it follows from (A.54) that

$$
\|g_{k-1}(u^{k-1} + \mu_{k-1}v)\|_n^2 \xrightarrow{c} \mathbb{E}(g_{k-1}(\mu_{k-1}V + \sigma_{k-1}G_{k-1})^2) = \sigma_k^2
$$

as \( n \to \infty \). Furthermore, since \(g'_k\) satisfies (M2), we can apply the inductive hypothesis (3.8) and argue as in the proof of Proposition A.16(f) to see that \(b_k \equiv b_k(n) = \langle g'_k(v^k) \rangle_n = n^{-1} \sum_{i=1}^n g'_k(v_i^k) \xrightarrow{c} \mathbb{E}(g'_k(\mu_k V + \sigma_k G_k))\). Similar reasoning based on (A.54) yields \(\tilde{b}_k \equiv \tilde{b}_k(n) = n^{-1}\).
