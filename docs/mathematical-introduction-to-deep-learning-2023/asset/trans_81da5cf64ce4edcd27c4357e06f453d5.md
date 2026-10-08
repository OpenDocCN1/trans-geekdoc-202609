

**引理 6.1.22.** 设 $\mathfrak{d} \in \mathbb{N}$，$c \in (0, \infty)$，$r \in (0, \infty)$，$\vartheta \in \mathbb{R}^{\mathfrak{d}}$，$\mathbb{B} = \{w \in \mathbb{R}^{\mathfrak{d}}: \|w - \vartheta\|_2 \leq r\}$，且 $\mathscr{L} \in C^1(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})$ 满足对于所有 $v \in \mathbb{R}^{\mathfrak{d}}$ 以及 $s, t \in [0, 1]$，若 $\|v\|_2 \leq r$ 且 $s \leq t$，则有

$$\mathscr{L}(\vartheta + tv) - \mathscr{L}(\vartheta + sv) \geq c^2(t^2 - s^2)\|v\|_2^2 \tag{6.150}$$

（参见*定义 3.3.4*）。则对于所有 $\theta \in \mathbb{B}$，有

$$(\theta - \vartheta, (\nabla \mathscr{L})(\theta)) \geq 2c\|\theta - \vartheta\|_2^2 \tag{6.151}$$

（参见*定义 1.4.7*）。

*引理 6.1.22 的证明.* 注意到 (6.150) 保证了对于所有 $s \in (0, r] \cap \mathbb{R}$ 以及满足 $\|\theta - \vartheta\|_2 < s$ 的 $\theta \in \mathbb{R}^{\mathfrak{d}} \backslash \{\vartheta\}$，成立

$$
\begin{aligned}
&(\theta - \vartheta, (\nabla \mathscr{L})(\theta)) = \mathscr{L}'(\theta)(\theta - \vartheta) = \underset{h \searrow 0}{\text{lim}} \big[\tfrac{1}{h}[\mathscr{L}(\theta + h(\theta - \vartheta)) - \mathscr{L}(\theta)]\big] \\
&= \underset{h \searrow 0}{\text{lim}} \big(\tfrac{1}{h}\big[\mathscr{L}\big(\vartheta + \frac{\|\theta + h\|\theta - \vartheta\|_2}{s}(\theta - \vartheta)\big) - \big. \\
&\quad - \mathscr{L}\big(\vartheta + \frac{\|\theta - \vartheta\|_2}{s}\big(\frac{s}{\|\theta - \vartheta\|_2}(\theta - \vartheta)\big)\big)\big]\big) \\
&\geq \underset{h \searrow 0}{\text{lim sup}} \big(\tfrac{c}{h}\big[\big(\frac{\|\theta + h\|\theta - \vartheta\|_2}{s}\big)^2 - \big[\tfrac{\|\theta - \vartheta\|_2}{s}\big]^2\big]\big\|\tfrac{s}{\|\theta - \vartheta\|_2}(\theta - \vartheta)\big\|_2^2\big) \tag{6.152} \\
&= c\big[\underset{h \searrow 0}{\text{lim sup}}\big(\frac{\|\theta + h\|^2 - 1}{h}\big)\big]\big[\big\|\frac{\|\theta - \vartheta\|_2}{s}\big\|^2\big]\big\|\tfrac{s}{\|\theta - \vartheta\|_2}(\theta - \vartheta)\big\|_2^2 \\
&= c\big[\underset{h \searrow 0}{\text{lim sup}}\big(\frac{2h + h^2}{h}\big)\big]\big\|\theta - \vartheta\big\|_2^2 \\
&= c\big[\underset{h \searrow 0}{\text{lim sup}}(2 + h)\big]\big\|\theta - \vartheta\big\|_2^2 = 2c\|\theta - \vartheta\|_2^2
\end{aligned}
$$

（参见*定义 1.4.7*）。因此，我们得到对于所有满足 $\|\theta - \vartheta\|_2 < r$ 的 $\theta \in \mathbb{R}^{\mathfrak{d}} \backslash \{\vartheta\}$，成立

$$(\theta - \vartheta, (\nabla \mathscr{L})(\theta)) \geq 2c\|\theta - \vartheta\|_2^2. \tag{6.153}$$

结合函数

$$\mathbb{R}^{\mathfrak{d}} \ni v \mapsto (\nabla \mathscr{L})(v) \in \mathbb{R}^{\mathfrak{d}} \tag{6.154}$$

是连续这一事实，便得证 (6.151).*引理 6.1.22* 的证明至此完成。 $\Box$

**引理 6.1.23.** 设 $\mathfrak{d} \in \mathbb{N}$，$L \in (0, \infty)$，$r \in (0, \infty)$，$\vartheta \in \mathbb{R}^{\mathfrak{d}}$，$\mathbb{B} = \{w \in \mathbb{R}^{\mathfrak{d}}: \|w - \vartheta\|_2 \leq r\}$，且 $\mathscr{L} \in C^1(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})$ 满足对于所有 $\theta \in \mathbb{B}$，有

$$\|(\nabla \mathscr{L})(\theta)\|_2 \leq L\|\theta - \vartheta\|_2 \tag{6.155}$$

（参见*定义 3.3.4*）。则对于所有 $v, w \in \mathbb{B}$，成立

$$|\mathscr{L}(v) - \mathscr{L}(w)| \leq L\max\{\|v - \vartheta\|_2, \|w - \vartheta\|_2\}\|v - w\|_2. \tag{6.156}$$

# 6.1. 梯度下降优化

引理 6.1.23 的证明。注意到 (6.155)、微积分基本定理以及柯西-施瓦茨不等式保证，对于所有 \(v, w \in \mathbb{B}\)，成立

$$
\begin{align*}
\left|\mathscr{L}(v)-\mathscr{L}(w)\right| &= \left|[\mathscr{L}(w + h(v - w))]_{h=0}^{h=1}\right| \\
&= \left|\int_0^1 \mathscr{L}'(w + h(v - w))\langle v - w \rangle \,\mathrm{d}h\right| \\
&= \left|\int_0^1 \langle \langle\nabla \mathscr{L}\rangle (w + h(v - w)), v - w \rangle \,\mathrm{d}h\right| \\
&\le \int_0^1 \|\langle\nabla \mathscr{L}\rangle (hv + (1 - h)w)\|_2\|v - w\|_2 \,\mathrm{d}h \\
&\le \int_0^1 L\|hv + (1 - h)w - \vartheta\|_2\|v - w\|_2 \,\mathrm{d}h \tag{6.157} \\
&\le \int_0^1 L(h\|v - \vartheta\|_2 + (1 - h)\|w - \vartheta\|_2)\|v - w\|_2 \,\mathrm{d}h \\
&= L\|v - w\|_2 \left[\int_0^1 (h\|v - \vartheta\|_2 + h\|w - \vartheta\|_2) \,\mathrm{d}h\right] \\
&= L\big(\|v - \vartheta\|_2 + \|w - \vartheta\|_2\big)\|v - w\|_2\left[\int_0^1 h \,\mathrm{d}h\right] \\
&\le L\max\{\|v - \vartheta\|_2, \|w - \vartheta\|_2\}\|v - w\|_2
\end{align*}
$$

（参见定义 1.4.7）。引理 6.1.23 的证明至此完成。 $\square$

**引理 6.1.24.** *设 $\mathfrak{d} \in \mathbb{N}$，$L \in (0, \infty)$，$r \in (0, \infty]$，$\vartheta \in \mathbb{R}^{\mathfrak{d}}$，$\mathbb{B} = \{w \in \mathbb{R}^{\mathfrak{d}} \colon \|w - \vartheta\|_2 \le r\}$，且 $\mathscr{L} \in C^1(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})$ 满足对于所有 $v, w \in \mathbb{B}$，有*

$$
\left|\mathscr{L}(v)-\mathscr{L}(w)\right| \le L\max\{\|v-\vartheta\|_2,\|w-\vartheta\|_2\}\|v-w\|_2 \tag{6.158}
$$

*(参见定义 3.3.4)。则对于所有 $\theta \in \mathbb{B}$，成立*

$$
\|\langle\nabla \mathscr{L}\rangle(\theta)\|_2 \le L\|\theta - \vartheta\|_2. \tag{6.159}
$$

*引理 6.1.24 的证明.* 注意 (6.158) 蕴含对于所有满足 $\|\theta - \vartheta\|_2 < r$ 的 $\theta \in \mathbb{R}^{\mathfrak{d}}$，成立

$$
\begin{align}
\|\nabla \mathscr{L}(\theta)\|_2 = \ & \underset{w \in \mathbb{R}^\mathfrak{d},\|w\|_2 = 1}{\text{sup}} \left[\mathscr{L}'(\theta)(w)\right] \\
= \ & \underset{w \in \mathbb{R}^\mathfrak{d},\|w\|_2 = 1}{\text{sup}} \left[\lim_{h \downarrow 0} \tfrac{1}{h} \big( \mathscr{L}(\theta + hw) - \mathscr{L}(\theta) \big)\right] \\
\leq \ & \underset{w \in \mathbb{R}^\mathfrak{d},\|w\|_2 = 1}{\text{sup}} \left[\liminf_{h \downarrow 0} \big\{ \tfrac{1}{h} \max \big\{ \|\theta + hw - \vartheta\|_2, \|\theta - \vartheta\|_2 \big\} \|\theta + hw - \theta\|_2 \big\} \right] \\
= \ & \underset{w \in \mathbb{R}^\mathfrak{d},\|w\|_2 = 1}{\text{sup}} \left[\liminf_{h \downarrow 0} \Big\{ L \max \big\{ \|\theta + hw - \vartheta\|_2, \|\theta - \vartheta\|_2 \big\} \tfrac{1}{h} \|hw\|_2 \Big\} \right] \\
= \ & \underset{w \in \mathbb{R}^\mathfrak{d},\|w\|_2 = 1}{\text{sup}} \left[ \liminf_{h \downarrow 0} \Big\{ L \max \big\{ \|\theta + hw - \vartheta\|_2, \|\theta - \vartheta\|_2 \big\} \Big\} \right] \\
= \ & \underset{w \in \mathbb{R}^\mathfrak{d},\|w\|_2 = 1}{\text{sup}} \Big[ L \|\theta - \vartheta\|_2 \Big] = L \|\theta - \vartheta\|_2.
\end{align}
$$

由于函数 $\mathbb{R}^\mathfrak{d} \ni v \mapsto (\nabla \mathscr{L})(v) \in \mathbb{R}^\mathfrak{d}$ 是连续的，因此得证 **(6.159)**。引理 **6.1.24** 的证明至此完成。

**推论 6.1.25.** 设 $\mathfrak{d} \in \mathbb{N}$，$r \in (0, \infty)$，$\vartheta \in \mathbb{R}^\mathfrak{d}$，$\mathbb{B} = \{w \in \mathbb{R}^\mathfrak{d} : \|w - \vartheta\|_2 \leq r\}$，$\mathscr{L} \in C^1(\mathbb{R}^\mathfrak{d}, \mathbb{R})$（参见定义 3.3.4）。则下列四个陈述等价：

(i) 存在 $c, L \in (0, \infty)$ 使得对于所有 $\theta \in \mathbb{B}$，成立
$$ \langle \theta - \vartheta, (\nabla \mathscr{L})(\theta) \rangle \geq c \|\theta - \vartheta\|_2^2 \quad \text{且} \quad \| (\nabla \mathscr{L})(\theta) \|_2 \leq L \|\theta - \vartheta\|_2 . $$

(ii) 存在 $\gamma \in (0, \infty)$，$\varepsilon \in (0,1)$ 使得对于所有 $\theta \in \mathbb{B}$，成立
$$ \|\theta - \gamma(\nabla \mathscr{L})(\theta) - \vartheta\|_2 \leq \varepsilon \|\theta - \vartheta\|_2 . $$

(iii) 存在 $c \in (0, \infty)$ 使得对于所有 $\theta \in \mathbb{B}$，成立
$$ \langle \theta - \vartheta, (\nabla \mathscr{L})(\theta) \rangle \geq c \max \big\{ \|\theta - \vartheta\|_2^2, \|(\nabla \mathscr{L})(\theta)\|_2^2 \big\} . $$

(iv) 存在 $c, L \in (0, \infty)$ 使得对于所有 $v, w \in \mathbb{B}$，$s, t \in [0,1]$ 且 $s \leq t$，成立
$$ \mathscr{L}\big( \vartheta + t(v - \vartheta) \big) - \mathscr{L}\big( \vartheta + s(v - \vartheta) \big) \geq c(t^2 - s^2) \|v - \vartheta\|_2^2 $$
且
$$ |\mathscr{L}(v) - \mathscr{L}(w)| \leq L \max \big\{ \|v - \vartheta\|_2, \|w - \vartheta\|_2 \big\} \|v - w\|_2 $$
（参见定义 1.4.7）。

*推论 6.1.25 的证明.* 注意引理 6.1.8 中的条目 (ii) 和 (iii) 证明了 (i) $\rightarrow$ (ii)。注意到引理 6.1.19 展示了 (ii) $\rightarrow$ (iii)。注意引理 6.1.20 建立了 (iii) $\rightarrow$ (i)。注意到引理 6.1.21 和引理 6.1.23 表明 (i) $\rightarrow$ (iv)。注意引理 6.1.22 和引理 6.1.24 建立了 (iv) $\rightarrow$ (i)。推论 6.1.25 的证明至此完成。

