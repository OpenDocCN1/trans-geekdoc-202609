(i) it holds that $\{\theta \in \mathbb{R}$ : $\mathscr{L}(\theta) = \inf_{w \in \mathbb{R}} \mathscr{L}(w)\} = \{\vartheta\}$,

(ii) it holds that $0 \leq 1 - 2c\gamma + \gamma^{2}L^{2} < 1$,

(iii) it holds for all $n \in \mathbb{N}_{0}$ that

```
$$\| \Theta_{n} - \vartheta \|_{2} \leq [1 - 2c\gamma + \gamma^{2}L^{2}]^{n/2} \|\xi - \vartheta\|_{2},$$
```

and

(iv) it holds for all $n \in \mathbb{N}_{0}$ that

```
$$0 \leq \mathscr{L}(\Theta_{n}) - \mathscr{L}(\vartheta) \leq \frac{L}{2} \| \Theta_{n} - \vartheta \|_{2}^{2} \leq \frac{L}{2} [1 - 2c\gamma + \gamma^{2}L^{2}]^{n} \|\xi - \vartheta\|_{2}^{2}.$$
```

*Proof of Corollary 6.1.10.* Observe that item (iii) in Lemma 6.1.8 proves item (ii). In addition, note that Proposition 6.1.9 establishes items (i), (iii), and (iv). The proof of Corollary 6.1.10 is thus complete.

Corollary 6.1.10 above establishes under suitable hypotheses convergence of the considered **GD** process in the case where the learning rates are constant and strictly smaller than $\frac{2c}{L^{2}}$. The next result, Theorem 6.1.11 below, demonstrates that the condition that the learning rates are strictly smaller than $\frac{2c}{L^{2}}$ in Corollary 6.1.10 can, in general, not be relaxed.

# Theorem 6.1.11 (Sharp bounds on the learning rate for the convergence of GD ). *Let* $\mathfrak{d} \in \mathbb{N}$, $\alpha \in (0, \infty)$, $\gamma \in \mathbb{R}$, $\vartheta \in \mathbb{R}^{\mathfrak{d}}$, $\xi \in \mathbb{R}^{\mathfrak{d}} \setminus \{\vartheta\}$, *let* $\mathscr{L}$ : $\mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}$ *satisfy for all* $\theta \in \mathbb{R}^{\mathfrak{d}}$ *that*

```
$$\mathscr{L}(\theta) = \frac{\alpha}{2} \| \theta - \vartheta \|_{2}^{2},$$
```

*and let* $\Theta$ : $\mathbb{N}_{0} \rightarrow \mathbb{R}^{\mathfrak{d}}$ *satisfy for all* $n \in \mathbb{N}$ *that*

```
$$\Theta_{0} = \xi \quad \text{ and } \quad \Theta_{n} = \Theta_{n-1} - \gamma (\nabla \mathscr{L})(\Theta_{n-1})$$
```

(cf. *Definition* 3.3.4). Then

(i) it holds for all $\theta \in \mathbb{R}^{\mathfrak{d}}$ that $\langle \theta - \vartheta , (\nabla \mathscr{L})(\theta)\rangle = \alpha \| \theta - \vartheta \|_{2}^{2}$,

(ii) it holds for all $\theta \in \mathbb{R}^{\mathfrak{d}}$ that $\| (\nabla \mathscr{L})(\theta) \|_{2} = \alpha \| \theta - \vartheta \|_{2}$,

(iii) it holds for all $n \in \mathbb{N}_{0}$ that $\| \Theta_{n} - \vartheta \|_{2} = [1 - \alpha\gamma]^{n} \|\xi - \vartheta\|_{2}$, and

(iv) it holds that

```
$$\operatorname*{lim\,inf}_{n \to \infty} \| \Theta_{n} - \vartheta \|_{2} = \operatorname*{lim\,sup}_{n \to \infty} \| \Theta_{n} - \vartheta \|_{2} = \left\{ \begin{array}{lr} 0 & : \gamma \in (0, \nicefrac{2}{\alpha}) \\ \| \xi - \vartheta \|_{2} & : \gamma \in \{0, \nicefrac{2}{\alpha}\} \\ \infty & : \gamma \in \mathbb{R} \setminus [0, \nicefrac{2}{\alpha}] \end{array} \right.$$ 
```