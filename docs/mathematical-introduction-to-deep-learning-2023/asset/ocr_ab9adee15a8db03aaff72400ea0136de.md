$\mathbb{R}^{\mathfrak{d}}: \mathcal{V}$ is open\}, \vartheta \in U$ with $\mathscr{L}\mid_{U} \in C^{1}(U, \mathbb{R}^{\mathfrak{d}})$ that

$\mathfrak{G}(\vartheta)=(\nabla \mathscr{L})(\vartheta)$.

Then we say that $\Theta$ is a $GF$ trajectory for the objective function $\mathscr{L}$ with generalized gradient $\mathfrak{G}$ and initial value $\xi$ (we say that $\Theta$ is a $GF$ trajectory for the objective function $\mathscr{L}$ with initial value $\xi$, we say that $\Theta$ is a solution of the $GF$ ODE for the objective function $\mathscr{L}$ with generalized gradient $\mathfrak{G}$ and initial value $\xi$, we say that $\Theta$ is a solution of the $GF$ ODE for the objective function $\mathscr{L}$ with initial value $\xi$) if and only if it holds that $\Theta: [0, \infty) \to \mathbb{R}^{\mathfrak{d}}$ is a function from $[0, \infty)$ to $\mathbb{R}^{\mathfrak{d}}$ which satisfies for all $t \in [0, \infty)$ that

$\Theta_{t}=\xi-\int_{0}^{t} \mathfrak{G}(\Theta_{s}) \mathrm{d} s$.

# 5.2.2 Direction of negative gradients

**Lemma 5.2.2.** Let $\mathfrak{d} \in \mathbb{N}$, $\mathscr{L} \in C^{1}\left(\mathbb{R}^{\mathfrak{d}}, \mathbb{R}\right)$, $\vartheta \in \mathbb{R}^{\mathfrak{d}}$, $r \in(0, \infty)$ and let $\mathfrak{G}: \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}$ satisfy for all $v \in \mathbb{R}^{\mathfrak{d}}$ that

$\mathfrak{G}(v)=\lim _{h \rightarrow 0}\left(\frac{\mathscr{L}(\vartheta+h v)-\mathscr{L}(\vartheta)}{h}\right)=\left[\mathscr{L}^{\prime}(\vartheta)\right](v)$.

Then

+   (i) it holds that

$\underset{v \in\{w \in \mathbb{R}^{\mathfrak{d}}:\|w\|_{2}=r\}}{\sup} \mathfrak{G}(v)=r\| (\nabla \mathscr{L})(\vartheta)\|_{2}=\begin{cases}0 & : (\nabla \mathscr{L})(\vartheta)=0 \\ \mathfrak{G}\left(\frac{r(\nabla \mathscr{L})(\vartheta)}{\|(\nabla \mathscr{L})(\vartheta)\|_{2}}\right) & : (\nabla \mathscr{L})(\vartheta) \neq 0\end{cases}$

and

+   (ii) it holds that

$\underset{v \in\{w \in \mathbb{R}^{\mathfrak{d}}:\|w\|_{2}=r\}}{\inf} \mathfrak{G}(v)=-r\| (\nabla \mathscr{L})(\vartheta)\|_{2}=\begin{cases}0 & : (\nabla \mathscr{L})(\vartheta)=0 \\ \mathfrak{G}\left(\frac{-r(\nabla \mathscr{L})(\vartheta)}{\|(\nabla \mathscr{L})(\vartheta)\|_{2}}\right) & : (\nabla \mathscr{L})(\vartheta) \neq 0\end{cases}$

(cf. Definition 3.3.4).

**Proof of Lemma 5.2.2.** Note that (5.11) implies that for all $v \in \mathbb{R}^{\mathfrak{d}}$ it holds that

$\mathfrak{G}(v)=\langle(\nabla \mathscr{L})(\vartheta), v\rangle$