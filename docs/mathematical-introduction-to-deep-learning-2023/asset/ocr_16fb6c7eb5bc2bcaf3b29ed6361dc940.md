(i) there exists a unique continuous function $\Theta: [0, \infty) \to \mathbb{R}^3$ such that for all $t \in [0, \infty)$ it holds that

```
$$\Theta_t = \xi - \int_0^t (\nabla \mathcal{L}) (\Theta_s) \, \mathrm{d}s,$$
(5.181)
```

(ii) it holds that $\{\theta \in \mathbb{R}^3 : \mathcal{L}(\theta) = \inf_{w \in \mathbb{R}} \mathcal{L}(w)\} = \{\vartheta\}$,

(iii) it holds for all $t \in [0, \infty)$ that $\|\Theta_t - \vartheta\|_2 \leq e^{-ct} \|\xi - \vartheta\|_2$, and

(iv) it holds for all $t \in [0, \infty)$ that

```
$$0 \leq \frac{c}{2} \|\Theta_t - \vartheta\|_2^2 \leq \mathcal{L}(\Theta_t) - \mathcal{L}(\vartheta).$$
(5.182)
```

Proof of Theorem 5.7.4. First, observe that the assumption that $\mathcal{L} \in C^2(\mathbb{R}^3, \mathbb{R})$ ensures that

```
$$\mathbb{R}^3 \ni \theta \mapsto -(\nabla \mathcal{L})(\theta) \in \mathbb{R}^3$$
(5.183)
```

is continuously differentiable. The fundamental theorem of calculus hence implies that

```
$$\mathbb{R}^3 \ni \theta \mapsto -(\nabla \mathcal{L})(\theta) \in \mathbb{R}^3$$
(5.184)
```

is locally Lipschitz continuous. Combining this with Lemma 5.7.3 (applied with $\mathfrak{G} \sim (\mathbb{R}^3 \ni \theta \mapsto -(\nabla \mathcal{L})(\theta) \in \mathbb{R}^3)$ in the notation of Lemma 5.7.3) proves that there exists a unique extended real number $\tau \in (0, \infty]$ and a unique continuous function $\Theta: [0, \tau) \to \mathbb{R}^3$ such that for all $t \in [0, \tau)$ it holds that

```
$$\liminf_{s \uparrow \tau} \|\Theta_s \|_2 + s] = \infty \quad\text{and}\quad \Theta_t = \xi - \int_0^t (\nabla \mathcal{L}) (\Theta_s) \, \mathrm{d}s.$$
(5.185)
```

Next observe that Proposition 5.7.1 proves that for all $t \in [0, \tau)$ it holds that

```
$$\|\Theta_t - \vartheta\|_2 \leq e^{-ct} \|\xi - \vartheta\|_2.$$
(5.186)
```

This implies that

```
$$\begin{aligned}
&\liminf_{s \uparrow \tau} \|\Theta_s \|_2 \leq \left[\liminf_{s \uparrow \tau} \|\Theta_s - \vartheta\|_2\right] + \|\vartheta\|_2 \\
&\quad \leq \left[\liminf_{s \uparrow \tau} e^{-cs} \|\xi - \vartheta\|_2\right] + \|\vartheta\|_2 \leq \|\xi - \vartheta\|_2 + \|\vartheta\|_2 < \infty .
\end{aligned}$$
(5.187)
```

This and (5.185) demonstrate that

```
$$\tau = \infty.$$
(5.188)
```

This and (5.185) prove item (i). Moreover, note that Proposition 5.7.1 and item (i) establish items (ii), (iii), and (iv). The proof of Theorem 5.7.4 is thus complete. \(\square\)