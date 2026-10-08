(cf. Definition 1.4.7). The proof of Lemma 9.12.1 is thus complete. \fbox{}

**Corollary 9.12.2**. Let $\mathbf{0} \in \mathbb{N}$, $L, \gamma \in \mathbb{R}$, let $U \subseteq \mathbb{R}^{d}$ be open and convex, let $\mathscr{L} \in \mathrm{C}^{1}(U, \mathbb{R})$, and assume for all $x, y \in U$ that
\begin{equation}
\| ( \nabla \mathscr{L}) ( x ) - ( \nabla \mathscr{L}) ( y ) \| _ {2} \leq L \| x - y \| _ {2}
\end{equation}
(cf. Definition 3.3.4). Then it holds for all $x \in U$ with $x - \gamma ( \nabla \mathscr{L}) ( x ) \in U$ that
\begin{equation}
\mathscr{L}\left(x - \gamma ( \nabla \mathscr{L}) ( x )\right) \leq \mathscr{L}\left(x\right) + \gamma \left( \frac{L \gamma}{2} - 1 \right) \| ( \nabla \mathscr{L}) ( x ) \| _ {2} ^ {2}
\end{equation}

*Proof of Corollary 9.12.2*. Observe that Lemma 9.12.1 ensures that for all $x \in U$ with $x - \gamma ( \nabla \mathscr{L}) ( x ) \in U$ it holds that
\begin{align}
\mathscr{L}\left(x - \gamma ( \nabla \mathscr{L}) ( x )\right) \leq & \mathscr{L}\left(x\right) + \left\langle ( \nabla \mathscr{L}) ( x ), -\gamma ( \nabla \mathscr{L}) ( x ) \right\rangle + \frac{L}{2} \| \gamma ( \nabla \mathscr{L}) ( x ) \| _ {2} ^ {2} \\
= & \mathscr{L}\left(x\right) - \gamma \| ( \nabla \mathscr{L}) ( x ) \| _ {2} ^ {2} + \frac{L \gamma ^ {2}}{2} \| ( \nabla \mathscr{L}) ( x ) \| _ {2} ^ {2}.
\end{align}
This establishes (9.208). The proof of Corollary 9.12.2 is thus complete. \fbox{}

**Corollary 9.12.3**. Let $\mathbf{0} \in \mathbb{N}$, $L \in (0, \infty)$, $\gamma \in [0, L ^ { - 1}]$, let $U \subseteq \mathbb{R}^{d}$ be open and convex, let $\mathscr{L} \in \mathrm{C}^{1}(U, \mathbb{R})$, and assume for all $x, y \in U$ that
\begin{equation}
\| ( \nabla \mathscr{L}) ( x ) - ( \nabla \mathscr{L}) ( y ) \| _ {2} \leq L \| x - y \| _ {2}
\end{equation}
(cf. Definition 3.3.4). Then it holds for all $x \in U$ with $x - \gamma ( \nabla \mathscr{L}) ( x ) \in U$ that
\begin{equation}
\mathscr{L}\left(x - \gamma ( \nabla \mathscr{L}) ( x )\right) \leq \mathscr{L}\left(x\right) - \frac{\gamma}{2} \| ( \nabla \mathscr{L}) ( x ) \| _ {2} ^ {2} \leq \mathscr{L}\left(x\right).
\end{equation}
*Proof of Corollary 9.12.3*. Note that Corollary 9.12.2, the fact that $\gamma \geq 0$, and the fact that $\frac{L \gamma}{2} - 1 \leq - \frac{1}{2}$ establish (9.211). The proof of Corollary 9.12.3 is thus complete. \fbox{}

*Exercise 9.12.1*. Let $\left(\gamma_{n}\right)_{n \in \mathbb{N}} \subseteq (0, \infty)$ satisfy for all $n \in \mathbb{N}$ that $\gamma_{n} = \frac{1}{n+1}$ and let $\mathscr{L} \colon \mathbb{R} \rightarrow \mathbb{R}$ satisfy for all $x \in \mathbb{R}$ that
\begin{equation}
\mathscr{L}\left(x\right) = 2 x + \sin ( x ).
\end{equation}
Prove or disprove the following statement: For every $\Theta = \left( \Theta_{k}\right)_{k \in \mathbb{N}_{0}} \colon \mathbb{N}_{0} \rightarrow \mathbb{R}$ with $\forall k \in \mathbb{N}$: $\Theta_{k} = \Theta_{k-1} - \gamma_{k} ( \nabla \mathscr{L}) ( \Theta_{k-1})$ and every $n \in \mathbb{N}$ it holds that
\begin{equation}
\mathscr{L}\left( \Theta_{n}\right) \leq \mathscr{L}\left( \Theta_{n-1}\right) - \frac{1}{n+1} \left( 1 - \frac{3}{2(n+1)} \right) 2 + \cos ( \Theta_{n-1} ) ^ {2}.
\end{equation}

*Exercise 9.12.2*. Let $\mathscr{L} \colon \mathbb{R} \rightarrow \mathbb{R}$ satisfy for all $x \in \mathbb{R}$ that
\begin{equation}
\mathscr{L}\left(x\right) = 4 x + 3 \sin ( x ).
\end{equation}
Prove or disprove the following statement: For every $\Theta = \left( \Theta_{n}\right)_{n \in \mathbb{N}_{0}} \colon \mathbb{N}_{0} \rightarrow \mathbb{R}$ with $\forall n \in \mathbb{N}$: $\Theta_{n} = \Theta_{n-1} - \frac{1}{n+1} ( \nabla \mathscr{L}) ( \Theta_{n-1})$ and every $k \in \mathbb{N}$ it holds that
\begin{equation}
\mathscr{L}\left( \Theta_{k}\right) < \mathscr{L}\left( \Theta_{k-1}\right).
\end{equation}