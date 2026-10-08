
（参见定义 $1.4.7$）。由于 $O$ 是正交矩阵，且 $A = O\Lambda O^*$，因此可以证明，对于所有 $v \in \mathbb{R}^{\mathfrak{d}}$，都有

![](img/dec290f673e6357c31893c67b579ffe1_229_0.png)

此外，注意到 $(6.108)$ 意味着，对于所有 $v = (v_1, v_2, \dots, v_\mathfrak{d}) \in \mathbb{R}^{\mathfrak{d}}$，都有

![](img/dec290f673e6357c31893c67b579ffe1_229_1.png)

由于 $O$ 是正交矩阵，且 $A = O\Lambda O^*$，因此可以证明，对于所有 $v \in \mathbb{R}^{\mathfrak{d}}$，都有

![](img/dec290f673e6357c31893c67b579ffe1_229_2.png)

将此结果与 $(6.116)$ 结合，便证明了第 $(iii)$ 项。引理 $6.1.15$ 的证明至此完成。 $\square$

我们现在给出所承诺的命题 $6.1.16$，该命题揭示了目标函数海森矩阵（Hessians）满足的适当条件（参见下文 $(6.119)$ 和 $(6.120)$），这些条件是充分的，可确保 $(6.47)$ 成立，从而使我们能够应用上述第 $6.1.4.1$、$6.1.4.2$、$6.1.4.3$ 和 $6.1.4.4$ 节中的误差分析。

**命题 $6.1.16$** （目标函数在局部极小点处海森矩阵谱的条件）。设 $\mathfrak{d} \in \mathbb{N}$，设范数 $\|\cdot\|\colon \mathbb{R}^{\mathfrak{d} \times \mathfrak{d}} \to [0, \infty)$ 满足：对于所有 $A \in \mathbb{R}^{\mathfrak{d} \times \mathfrak{d}}$，有 $\|A\| = \sup_{v \in \mathbb{R}^{\mathfrak{d}} \setminus \{0\}} \frac{\|Av\|_2}{\|v\|_2}$；设 $\lambda, \alpha \in (0, \infty)$，$\beta \in [\alpha, \infty)$，$\vartheta \in \mathbb{R}^\mathfrak{d}$，$\mathcal{L} \in C^2(\mathbb{R}^\mathfrak{d}, \mathbb{R})$ 满足：对于所有 $v, w \in \mathbb{R}^\mathfrak{d}$，有

![](img/dec290f673e6357c31893c67b579ffe1_229_3.png)

![](img/dec290f673e6357c31893c67b579ffe1_229_4.png)

（参见定义 $3.3.4$）。那么，对于所有 $\theta \in \{w \in \mathbb{R}^\mathfrak{d}\colon \|w - \vartheta\|_2 \le \frac{\alpha}{\lambda}\}$，都有

![](img/dec290f673e6357c31893c67b579ffe1_229_5.png)

（参见定义 $1.4.7$）。

命题 6.1.16 的证明。在整个证明过程中，设 $\mathbb{B} \subseteq \mathbb{R}^n$ 为由下式给出的集合

$$\mathbb{B} = \{w \in \mathbb{R}^n : \|w - \vartheta\|_2 \leq \tfrac{\alpha}{\lambda}\} \tag{6.122}$$

并设 $\mathcal{S} \subseteq \mathbb{C}$ 为由下式给出的集合

$$\mathcal{S} = \{\mu \in \mathbb{C} : (\exists \, u \in \mathbb{C}^n \backslash \{0\} : [\text{Hess} \, \mathscr{L}(\vartheta)]u = \mu u)\}. \tag{6.123}$$

注意到，事实 $\text{Hess} \, \mathscr{L}(\vartheta) \in \mathbb{R}^{n \times n}$ 是一个对称矩阵，引理 6.1.15 中的第 **(i)** 项以及 **(6.120)** 意味着

$$\mathcal{S} = \{\mu \in \mathbb{R} : (\exists \, u \in \mathbb{R}^n \backslash \{0\} : [\text{Hess} \, \mathscr{L}(\vartheta)]u = \mu u)\} \subseteq [\alpha, \beta]. \tag{6.124}$$

接下来注意到，假设 $\nabla \mathscr{L}(\vartheta) = 0$ 以及微积分基本定理保证，对于所有 $\theta, w \in \mathbb{R}^n$，都有

\begin{align}
\langle w, (\nabla \mathscr{L})(\theta) \rangle &= \langle w, (\nabla \mathscr{L})(\theta) - (\nabla \mathscr{L})(\vartheta) \rangle \\
&= \left\langle w, \left[(\nabla \mathscr{L})(\theta + t(\theta - \vartheta))\right]_{t = 0}^{t = 1} \right\rangle \\
&= \left\langle w, \int_0^1 [([\text{Hess} \, \mathscr{L})(\vartheta + t(\theta - \vartheta))](\theta - \vartheta)] \, \text{d}t \right\rangle \\
&= \int_0^1 \left\langle w, ([\text{Hess} \, \mathscr{L})(\vartheta + t(\theta - \vartheta))](\theta - \vartheta)\right\rangle \, \text{d}t \\
&= \left\langle w, [([\text{Hess} \, \mathscr{L})(\vartheta)](\theta - \vartheta)) \right\rangle \\
&\quad + \int_0^1 \left\langle w, \left([(\text{Hess} \, \mathscr{L})(\vartheta + t(\theta - \vartheta)) - (\text{Hess} \, \mathscr{L})(\vartheta)](\theta - \vartheta)\right\rangle \, \text{d}t \tag{6.125}
\end{align}

（参见定义 1.4.7）。由于 $\text{Hess} \, \mathscr{L}(\vartheta) \in \mathbb{R}^{n \times n}$ 是一个对称矩阵，引理 6.1.15 中的第 **(iii)** 项以及柯西-施瓦茨不等式意味着，对于所有 $\theta \in \mathbb{B}$，都有

\begin{align}
\langle \theta - \vartheta, (\nabla \mathscr{L})(\theta) \rangle 
&\geq \langle \theta - \vartheta, ([\text{Hess} \, \mathscr{L}(\vartheta)](\theta - \vartheta) \rangle \\
&\quad - \left| \int_0^1 \left\langle \theta - \vartheta, \left([(\text{Hess} \, \mathscr{L})(\vartheta + t(\theta - \vartheta)) - (\text{Hess} \, \mathscr{L})(\vartheta)](\theta - \vartheta)\right\rangle \, \text{d}t \right| \\
&\geq \min(\mathcal{S})\|\theta - \vartheta\|_2^2 \\
&\quad - \int_0^1 \|\theta - \vartheta\|_2 \left\| [\text{Hess} \, \mathscr{L}(\vartheta + t(\theta - \vartheta)) - (\text{Hess} \, \mathscr{L})(\vartheta)](\theta - \vartheta) \right\|_2 \, \text{d}t. \tag{6.126}
\end{align}

将此结果与 $(\mathbf{6.124})$ 和 $(\mathbf{6.119})$ 结合可知，对于所有 $\theta \in \mathbb{B}$，都有

$$
\begin{gathered} 
\left\langle \theta-\vartheta, \nabla \mathcal{L}(\theta)\right\rangle \\ 
\quad \geq \alpha\left\|\theta-\vartheta\right\|_{2}^{2} \\ 
\quad-\int_{0}^{1}\left\|\theta-\vartheta\right\|_{2}\| \text { (Hess } \mathcal{L}) \vartheta+t(\theta-\vartheta))-\text { (Hess } \mathcal{L}) \vartheta\|\left\|\theta-\vartheta\right\|_{2} \mathrm{~d} t \\ 
\geq \alpha\left\|\theta-\vartheta\right\|_{2}^{2}-\left[\int_{0}^{1} \lambda\|\vartheta+t(\theta-\vartheta)-\vartheta\|_{2} \mathrm{~d} t\right]\left\|\theta-\vartheta\right\|_{2}^{2} \\ 
=\left(\alpha-\left[\int_{0}^{1} t \mathrm{~d} t\right]\lambda\|\theta-\vartheta\|_{2}\right)\left\|\theta-\vartheta\right\|_{2}^{2}=\left(\alpha-\frac{\lambda}{2}\left\|\theta-\vartheta\right\|_{2}\right)\left\|\theta-\vartheta\right\|_{2}^{2} \\ 
\geq\left(\alpha-\frac{\lambda \alpha}{2 \Lambda}\right)\left\|\theta-\vartheta\right\|_{2}^{2}=\frac{\alpha}{2}\left\|\theta-\vartheta\right\|_{2}^{2} . 
\end{gathered}
$$

此外，注意到 $(\mathbf{6.119}), (\mathbf{6.124}), (\mathbf{6.125})$、事实（Hess $\mathcal{L}$)($\vartheta$) $\in \mathbb{R}^{n \times n}$ 是一个对称矩阵、引理 $\mathbf{6.1 . 1 5}$ 中的第 (ii) 项、柯西-施瓦茨不等式以及假设 $\alpha \leq \beta$ 保证，对于所有满足 $\|w\|_{2}=1$ 的 $\theta \in \mathbb{B}, w \in \mathbb{R}^{n}$，都有

$$
\begin{aligned} 
& \langle w, \nabla \mathcal{L}(\theta)\rangle \\ 
& \leq\left|\left\langle w,\left[\text { (Hess } \mathcal{L}) \vartheta\right](\theta-\vartheta)\right\rangle\right| \\ 
& \quad+\left|\int_{0}^{1}\left\langle w,\left[\text { (Hess } \mathcal{L}) \vartheta+t(\theta-\vartheta)\right)-(\text { (Hess } \mathcal{ L}) \vartheta)\right](\theta-\vartheta)\right\rangle \mathrm{d} t\right| \\ 
& \leq\|w\|_{2}\|(\text { (Hess } \mathcal{L}) \vartheta)\|(\theta-\vartheta)\|_{2} \\ 
& \quad+\int_{0}^{1}\|w\|_{2}\|(\text { (Hess } \mathcal{ L}) \vartheta+t(\theta-\vartheta))-(\text { (Hess } \mathcal{ L}) \vartheta)\|\|(\theta-\vartheta)\|_{2} \mathrm{~d} t \\ 
& \leq\left[\sup _{v \in \mathbb{R}^{n} \backslash\{0\}} \frac{\|[(\text { (Hess } \mathcal{ L}) \vartheta) v\|_{2}}{\|v\|_{2}}\right]\left\|\theta-\vartheta\right\|_{2} \\ 
& \quad+\int_{0}^{1}\|\text { (Hess } \mathcal{ L}) \vartheta+t(\theta-\vartheta)-(\text { (Hess } \mathcal{ L}) \vartheta\|\|\theta-\vartheta\|_{2} \mathrm{~d} t \\ 
& \leq \max (\mathcal{S})\left\|\theta-\vartheta\right\|_{2}+\left[\int_{0}^{1} \lambda\|\vartheta+t(\theta-\vartheta)-\vartheta\|_{2} \mathrm{~d} t\right]\left\|\theta-\vartheta\right\|_{2} \\ 
& \leq\left(\beta+\lambda\left[\int_{0}^{1} t \mathrm{~d} t\right]\right)\|\theta-\vartheta\|_{2}\left\|\theta-\vartheta\right\|_{2}=\left(\beta+\frac{\lambda}{2}\left\|\theta-\vartheta\right\|_{2}\right)\left\|\theta-\vartheta\right\|_{2} \\ 
& \leq\left(\beta+\frac{\lambda \alpha}{2 \Lambda}\right)\left\|\theta-\vartheta\right\|_{2}=\left[\frac{2 \beta+\alpha}{2}\right]\left\|\theta-\vartheta\right\|_{2} \leq \frac{3 \beta}{2}\left\|\theta-\vartheta\right\|_{2} . 
\end{aligned}
$$

因此，对于所有 $\theta \in \mathbb{B}$，我们得到

$$
\|\nabla \mathcal{L}(\theta)\|_{2}=\sup _{w \in \mathbb{R}^{n},\|w\|_{2}=1}\left|\left\langle w,\left(\nabla \mathcal{L}(\theta)\right)\right\rangle\right| \leq \frac{3 \beta}{2}\left\|\theta-\vartheta\right\|_{2} .
$$

将此结果与 $(\mathbf{6.127})$ 结合便证明了 $(\mathbf{6.121})$。命题 $\mathbf{6.1 . 1 6}$ 的证明至此完成。

