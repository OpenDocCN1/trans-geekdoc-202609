
Proof of Lemma 4.3.10. Throughout this proof, assume without loss of generality that $q < \infty$, let $e_{1}, e_{2}, \ldots, e_{d} \in \mathbb{R}^{d}$ satisfy $e_{1} = (1, 0, \ldots, 0)$, $e_{2} = (0, 1, 0, \ldots, 0)$, $\ldots$, $e_{d} = (0, \ldots, 0, 1)$, let $r \in \mathbb{R}$ satisfy

$$ r = p^{-1}q, \quad (4.126) $$

and let $x = (x_{1}, \ldots, x_{d})$, $y = (y_{1}, \ldots, y_{d}) \in \mathbb{R}^{d}$ satisfy for all $i \in \{1, 2, \ldots, d\}$ that

$$ y_{i} = |x_{i}|^{p}. \quad (4.127) $$

Observe that (4.127), the fact that

$$ y = \sum_{i=1}^{d} y_{i} e_{i}, \quad (4.128) $$

and the fact that for all $v, w \in \mathbb{R}^{d}$ it holds that

$$ \|v + w\|_{r} \leq \|v\|_{r} + \|w\|_{r} \quad (4.129) $$

(cf. Definition 3.3.4) ensures that

\begin{align*}
\|x\|_{q} &= \left[\sum_{i=1}^{d} |x_{i}|^{q}\right]^{1/q} = \left[\sum_{i=1}^{d} |x_{i}|^{pr}\right]^{1/q} = \left[\sum_{i=1}^{d} |y_{i}|^{r}\right]^{1/q} = \left[\sum_{i=1}^{d} |y_{i}|^{r}\right]^{1/(pr)} = \|y\|_{r}^{1/p} \\
&= \left\|\sum_{i=1}^{d} y_{i} e_{i}\right\|_{r}^{1/p} \leq \left[\sum_{i=1}^{d} \|y_{i} e_{i}\|_{r}\right]^{1/p} = \left[\sum_{i=1}^{d} \|y_{i}\| \|e_{i}\|_{r}\right]^{1/p} = \left[\sum_{i=1}^{d} |y_{i}|\right]^{1/p} \\
&= \|y\|_{1}^{1/p} = \|x\|_{p}. \quad (4.130)
\end{align*}

This establishes (4.125). The proof of Lemma 4.3.10 is thus complete.

### Corollary 4.3.11 (Implicit multi-dimensional ANN approximations with prescribed error tolerances and asymptotic parameter bounds)

Let $d \in \mathbb{N}$, $L$, $a \in \mathbb{R}$, $b \in [a, \infty)$ and let $f : [a, b]^{d} \rightarrow \mathbb{R}$ satisfy for all $x, y \in [a, b]^{d}$ that

$$ |f(x) - f(y)| \leq L \|x - y\|_{1} \quad (4.131) $$

(cf. Definition 3.3.4). Then there exist $\mathfrak{C} \in \mathbb{R}$ such that for all $\varepsilon \in (0, 1]$ there exists $\mathbf{F} \in \mathbf{N}$ such that

$$ \mathcal{R}_{\varepsilon}^{\mathbf{N}}(\mathbf{F}) \in C([a, b]^{d}, \mathbb{R}), \quad \sup_{x \in [a, b]^{d}} |\mathcal{R}_{\varepsilon}^{\mathbf{N}}(\mathbf{F})(x) - f(x)| \leq \varepsilon, \quad \text{and} \quad \mathcal{P}(\mathbf{F}) \leq \mathfrak{C} \varepsilon^{-2d} \quad (4.132) $$

(cf. Definitions 1.2.4, 1.3.1, and 1.3.4).

Proof of Corollary 4.3.11. Note that Corollary 4.3.9 establishes (4.132). The proof of Corollary 4.3.11 is thus complete.

In Chapter 15 below we establish estimates for the *overall error* in the training of suitable rectified clipped ANNs (see Section 4.4.1 below) in the specific situation of GD-type optimization methods with many independent random initializations. Besides *optimization error* estimates from Part III and *generalization error* estimates from Part IV, for this overall error analysis we also employ suitable *approximation error* estimates with a somewhat more refined control on the architecture of the approximating ANNs than the approximation error estimates established in the previous sections of this chapter (cf., for instance, Corollaries 4.3.9 and 4.3.11 above). It is exactly the subject of this section to establish such refined approximation error estimates (see Proposition 4.4.12 below).

This section is specifically tailored to the requirements of the overall error analysis presented in Chapter 15 and does not offer much more significant insights into the approximation error analyses of ANNs than the content of the previous sections in this chapter. It can therefore be skipped at the first reading of this book and only needs to be considered when the reader is studying Chapter 15 in detail.

## 4.4.1 Rectified clipped ANNs

### Definition 4.4.1 (Rectified clipped ANNs)

Let $L$, $\mathfrak{d} \in \mathbb{N}$, $u \in [-\infty, \infty)$, $v \in (u, \infty]$, $\mathbf{1} = (l_0, l_1, \ldots, l_L) \in \mathbb{N}^{L+1}$, $\theta \in \mathbb{R}^{\mathfrak{d}}$ satisfy

$$ \mathfrak{d} \geq \sum_{k=1}^{L} l_k(l_{k-1}+1). \quad (4.133) $$

Then we denote by $\mathcal{N}_{u,v}^{\theta,1}: \mathbb{R}^{l_0} \rightarrow \mathbb{R}^{l_L}$ the function which satisfies for all $x \in \mathbb{R}^{l_0}$ that

$$ \mathcal{N}_{u,v}^{\theta,1}(x)= \begin{cases}
\left(\mathcal{N}_{\mathcal{C}_{u,v}^{l_L}}^{\theta_{l_0}} \right)(x) & : L=1 \\
\left(\mathcal{N}_{\mathfrak{G}_{l_1}, \mathfrak{G}_{l_2}, \ldots, \mathfrak{G}_{l_{L-1}}, \mathcal{C}_{u,v}^{l_L}}^{\theta_1, \theta_2, \ldots, \theta_L} \right)(x) & : L>1
\end{cases} \quad (4.134) $$

(cf. Definitions 1.1.3, 1.2.5, and 1.2.10).

### Lemma 4.4.2

Let $\Phi \in \mathbf{N}$ (cf. Definition 1.3.1). Then it holds for all $x \in \mathbb{R}^{\mathcal{T}^{(\Phi)}}$ that

$$ \left(\mathcal{N}_{-\infty,\infty}^{\mathcal{T}^{(\Phi)}, \mathcal{D}^{(\Phi)}} \right)(x) = \left( \mathcal{R}_{\infty}^{\mathbf{N}}(\Phi) \right)(x) \quad (4.135) $$

(cf. Definitions 1.2.4, 1.3.4, 1.3.5, and 4.4.1).

Proof of Lemma 4.4.2. Observe that Proposition 1.3.9, (4.134), (1.27), and the fact that for all $d \in \mathbb{N}$ it holds that $\mathcal{C}_{-\infty,\infty,d} = \text{id}_{\mathbb{R}^d}$ demonstrate (4.135) (cf. Definition 1.2.10). The proof of Lemma 4.4.2 is thus complete.

## 4.4.2 Embedding ANNs in larger architectures

### Lemma 4.4.3

Let $a \in C(\mathbb{R}, \mathbb{R})$, $L \in \mathbb{N}$, $l_0, l_1, \ldots, l_L \in \mathbb{N}$ satisfy for all $k \in \{1, 2, \ldots, L\}$ that $l_0 = \mathcal{l}_0$, $l_L = \mathcal{l}_L$, and $\mathcal{l}_k \geq l_k$ for every $k \in \{1, 2, \ldots, L\}$. Let $W_k = (W_{k,i,j})_{(i,j) \in \{1, 2, \ldots, l_k\} \times \{1, 2, \ldots, l_{k-1}\}} \in \mathbb{R}^{l_k \times l_{k-1}}$, $\mathcal{W}_k = (\mathcal{W}_{k,i,j})_{(i,j) \in \{1, 2, \ldots, \mathcal{l}_k\} \times \{1, 2, \ldots, l_{k-1}\}} \in \mathbb{R}^{\mathcal{l}_k \times l_{k-1}}$, $B_k = (B_{k,i})_{i \in \{1, 2, \ldots, l_k\}} \in \mathbb{R}^{l_k}$, $\mathcal{B}_k = (\mathcal{B}_{k,i})_{i \in \{1, 2, \ldots, \mathcal{l}_k\}} \in \mathbb{R}^{\mathcal{l}_k}$. Assume for all $k \in \{1, 2, \ldots, L\}$, $i \in \{1, 2, \ldots, \mathcal{l}_k\}$, $j \in \mathbb{N} \cap (0, l_{k-1}]$ that

$$ W_{k,i,j} = \mathcal{W}_{k,i,j} \quad \text{and} \quad B_{k,i} = \mathcal{B}_{k,i}, \quad (4.136) $$

and assume for all $k \in \{1, 2, \ldots, L\}$, $i \in \{1, 2, \ldots, \mathcal{l}_k\}$, $j \in \mathbb{N} \cap (l_{k-1}, \mathcal{l}_k)$ that $\mathcal{W}_{k,i,j} = 0$. Then

$$ \mathcal{R}_a^{\mathbb{N}}(((W_1, B_1), (W_2, B_2), \ldots, (W_L, B_L))) = \mathcal{R}_a^{\mathbb{N}}(((\mathcal{W}_1, \mathcal{B}_1), (\mathcal{W}_2, \mathcal{B}_2), \ldots, (\mathcal{W}_L, \mathcal{B}_L))) \quad (4.137) $$

(cf. Definition 1.3.4).

Proof of Lemma 4.4.3. Throughout this proof, let $\pi_k: \mathbb{R}^{l_k} \to \mathbb{R}^{l_k}$, $k \in \{0, 1, \ldots, L\}$, satisfy for all $k \in \{0, 1, \ldots, L\}$, $x = (x_1, x_2, \ldots, x_{l_k})$ that

$$ \pi_k(x) = (x_1, x_2, \ldots, x_{l_k}). \quad (4.138) $$

Note that the assumption that $l_0 = \mathcal{l}_0$ and $l_L = \mathcal{l}_L$ proves that

$$ \mathcal{R}_a^{\mathbb{N}}(((W_1, B_1), (W_2, B_2), \ldots, (W_L, B_L))) \in C(\mathbb{R}^{l_0}, \mathbb{R}^{l_L}) \quad (4.139) $$

(cf. Definition 1.3.4). Furthermore, observe that the assumption that for all $k \in \{1, 2, \ldots, L\}$, $i \in \{1, 2, \ldots, \mathcal{l}_k\}$, $j \in \mathbb{N} \cap (l_{k-1}, \mathcal{l}_k)$ it holds that $\mathcal{W}_{k,i,j} = 0$ shows that for all $k \in \{1, 2, \ldots, L\}$, $x = (x_1, x_2, \ldots, x_{l_{k-1}}) \in \mathbb{R}^{l_{k-1}}$ it holds that

\begin{align*}
\pi_k(\mathcal{W}_k x + \mathcal{B}_k) &= \begin{pmatrix}
\left[\sum_{i=1}^{l_{k-1}} \mathcal{W}_{k,1,i} x_i \right] + \mathcal{B}_{k,1}, \left[\sum_{i=1}^{l_{k-1}} \mathcal{W}_{k,2,i} x_i \right] + \mathcal{B}_{k,2}, \ldots, \left[\sum_{i=1}^{l_{k-1}} \mathcal{W}_{k,\mathcal{l}_k,i} x_i \right] + \mathcal{B}_{k,\mathcal{l}_k}
\end{pmatrix} \quad (4.140) \\
&= \begin{pmatrix}
\left[\sum_{i=1}^{l_{k-1}} \mathcal{W}_{k,1,i} x_i \right] + \mathcal{B}_{k,1}, \left[\sum_{i=1}^{l_{k-1}} \mathcal{W}_{k,2,i} x_i \right] + \mathcal{B}_{k,2}, \ldots, \left[\sum_{i=1}^{l_{k-1}} \mathcal{W}_{k,\mathcal{l}_k,i} x_i \right] + \mathcal{B}_{k,\mathcal{l}_k}
\end{pmatrix}.
\end{align*}

Combining this with the assumption that for all $k \in \{1, 2, \ldots, L\}$, $i \in \{1, 2, \ldots, \mathcal{l}_k\}$, $j \in \mathbb{N} \cap (0, l_{k-1}]$ it holds that $\mathcal{W}_{k,i,j} = W_{k,i,j}$ and $\mathcal{B}_{k,i} = B_{k,i}$ ensures that for all $k \in \{1, 2, \ldots, L\}$, $x = (x_1, x_2, \ldots, x_{l_{k-1}}) \in \mathbb{R}^{l_{k-1}}$ it holds that

\begin{align*}
\pi_k(\mathcal{W}_k x + \mathcal{B}_k) &= \begin{pmatrix}
\left[\sum_{i=1}^{l_{k-1}} W_{k,1,i} x_i \right] + B_{k,1}, \left[\sum_{i=1}^{l_{k-1}} W_{k,2,i} x_i \right] + B_{k,2}, \ldots, \left[\sum_{i=1}^{l_{k-1}} W_{k,\mathcal{l}_k,i} x_i \right] + B_{k,\mathcal{l}_k}
\end{pmatrix} \quad (4.141) \\
&= W_k \pi_{k-1}(x) + B_k.
\end{align*}
