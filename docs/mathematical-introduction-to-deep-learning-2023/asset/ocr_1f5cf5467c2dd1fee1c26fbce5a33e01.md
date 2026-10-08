*(cf. Definition* 1.4.7).

*Proof of Theorem* 6.1.11. *First of all, note that Lemma* 5.6.4 *ensures that for all* $\theta \in \mathbb{R}^{9}$ *it holds that* $\mathscr{L} \in C^{\infty}(\mathbb{R}^{9}, \mathbb{R})$ *and*

```
$$(\nabla \mathscr{L})(\theta)=\frac{\alpha}{2}(2(\theta-\vartheta))=\alpha(\theta-\vartheta).$$
```

*This proves item (ii). Moreover, observe that* (6.63) *assures that for all* $\theta \in \mathbb{R}^{9}$ *it holds that*

```
$$\langle\theta-\vartheta,(\nabla \mathscr{L})(\theta)\rangle=\langle\theta-\vartheta,\alpha(\theta-\vartheta)\rangle=\alpha\|\theta-\vartheta\|_{2}^{2}$$
```

*(cf. Definition* 1.4.7). *This establishes item (i). Observe that* (6.61) *and* (6.63) *demonstrate that for all* $n \in \mathbb{N}$ *it holds that*

```
$$\begin{gathered}\Theta_{n}-\vartheta=\Theta_{n-1}-\gamma(\nabla \mathscr{L})(\Theta_{n-1})-\vartheta \\ =\Theta_{n-1}-\gamma\alpha(\Theta_{n-1}-\vartheta)-\vartheta \\ =(1-\gamma\alpha)(\Theta_{n-1}-\vartheta).\end{gathered}$$
```

*The assumption that* $\Theta_{0}=\xi$ *and induction hence prove that for all* $n \in \mathbb{N}_{0}$ *it holds that*

```
$$\Theta_{n}-\vartheta=(1-\gamma\alpha)^{n}(\Theta_{0}-\vartheta)=(1-\gamma\alpha)^{n}(\xi-\vartheta).$$
```

*Therefore, we obtain for all* $n \in \mathbb{N}_{0}$ *that*

```
$$\|\Theta_{n}-\vartheta\|_{2}=|1-\gamma\alpha|^{n}\|\xi-\vartheta\|_{2}.$$
```

*This establishes item (iii). Combining item (ii) with the fact that for all* $t \in(0,2 / \alpha)$ *it holds that* $|1-t \alpha| \in[0,1)$, *the fact that for all* $t \in\{0,2 / \alpha\}$ *it holds that* $|1-t \alpha|=1$, *the fact that for all* $t \in \mathbb{R} \backslash[0,2 / \alpha]$ *it holds that* $|1-t \alpha| \in(1, \infty)$, *and the fact that* $\|\xi-\vartheta\|_{2}>0$ *establishes item (iv). The proof of Theorem* 6.1.11 *is thus complete.*

*Exercise* 6.1.9. *Let* $\mathscr{L}: \mathbb{R} \rightarrow \mathbb{R}$ *satisfy for all* $\theta \in \mathbb{R}$ *that*

```
$$\mathscr{L}(\theta)=2 \theta^{2}$$
```

*and let* $\Theta: \mathbb{N}_{0} \rightarrow \mathbb{R}$ *satisfy for all* $n \in \mathbb{N}$ *that* $\Theta_{0}=1$ *and*

```
$$\Theta_{n}=\Theta_{n-1}-n^{-2}(\nabla \mathscr{L})(\Theta_{n-1}).$$
```

*Prove or disprove the following statement: It holds that*

```
$$\lim _{n \rightarrow \infty} \sup \left|\Theta_{n}\right|=0 .$$
```