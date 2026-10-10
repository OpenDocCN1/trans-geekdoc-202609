
**引理 6.1.20**。设 \(\mathfrak{d} \in \mathbb{N}\)，设 \(\langle\cdot, \cdot\rangle: \mathbb{R}^{\mathfrak{d}} \times \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}\) 为内积，设 \(\|\cdot\|: \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}\) 满足对所有 \(v \in \mathbb{R}^{\mathfrak{d}}\) 有 \(\|v\| = \sqrt{\langle v, v\rangle}\)，设 \(c \in (0, \infty)\)， \(r \in (0, \infty)\)， \(\vartheta \in \mathbb{R}^{\mathfrak{d}}\)， \(\mathbb{B} = \{w \in \mathbb{R}^{\mathfrak{d}} : \|w - \vartheta\| \leq r\}\)，且设 \(\mathscr{G}: \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}^{\mathfrak{d}}\) 满足对所有 \(\theta \in \mathbb{B}\) 有

$$\langle\theta - \vartheta, \mathscr{G}(\theta)\rangle \geq c \max \left\{\|\theta - \vartheta\|^2, \|\mathscr{G}(\theta)\|^2\right\} . \tag{6.142}$$

那么对所有 \(\theta \in \mathbb{B}\) 有

$$\langle\theta - \vartheta, \mathscr{G}(\theta)\rangle \geq c \|\theta - \vartheta\|^2 \quad \text{且} \quad \|\mathscr{G}(\theta)\| \leq \frac{1}{c} \|\theta - \vartheta\| . \tag{6.143}$$

*引理 6.1.20 的证明*。注意到 (6.142) 和柯西-施瓦茨不等式保证了对所有 \(\theta \in \mathbb{B}\) 有

$$\|\mathscr{G}(\theta)\|^2 \leq \max \left\{\|\theta - \vartheta\|^2, \|\mathscr{G}(\theta)\|^2\right\} \leq \frac{1}{c}\langle\theta - \vartheta, \mathscr{G}(\theta)\rangle \leq \frac{1}{c}\|\theta - \vartheta\|\|\mathscr{G}(\theta)\| . \tag{6.144}$$

因此，我们对所有 \(\theta \in \mathbb{B}\) 得到

$$\|\mathscr{G}(\theta)\| \leq \frac{1}{c} \|\theta - \vartheta\| . \tag{6.145}$$

将此与 (6.142) 结合，即完成了引理 6.1.20 的证明。 \(\square\)

**引理 6.1.21**。设 \(\mathfrak{d} \in \mathbb{N}\)， \(c \in (0, \infty)\)， \(r \in (0, \infty)\)， \(\vartheta \in \mathbb{R}^{\mathfrak{d}}\)， \(\mathbb{B} = \{w \in \mathbb{R}^{\mathfrak{d}} : \|w - \vartheta\|_2 \leq r\}\)， \(\mathscr{L} \in C^1(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})\) 满足对所有 \(\theta \in \mathbb{B}\) 有

$$(\theta - \vartheta)\langle\nabla \mathscr{L}\rangle(\theta)\rangle \geq c \|\theta - \vartheta\|_2^2 . \tag{6.146}$$

那么对所有 \(v \in \mathbb{R}^{\mathfrak{d}}\)， \(s, t \in [0, 1]\) 且满足 \(\|v\|_2 \leq r\) 和 \(s \leq t\) 有

$$\mathscr{L}(\vartheta + t v) - \mathscr{L}(\vartheta + s v) \geq \frac{c}{2} (t^2 - s^2) \|v\|_2^2 . \tag{6.147}$$

*引理 6.1.21 的证明*。首先，注意到 (6.146) 暗示了对所有满足 \(\|v\|_2 \leq r\) 的 \(v \in \mathbb{R}^{\mathfrak{d}}\) 有

$$\langle(\nabla \mathscr{L})(\vartheta + v), v\rangle \geq c \|v\|_2^2, \tag{6.148}$$

因此，微积分基本定理保证了对所有 \(v \in \mathbb{R}^{\mathfrak{d}}\)， \(s, t \in [0, 1]\) 且满足 \(\|v\|_2 \leq r\) 和 \(s \leq t\) 有

$$\begin{aligned} \mathscr{L}(\vartheta+t v)-\mathscr{L}(\vartheta+s v) & =\left[\mathscr{L}(\vartheta+h v)\right]_{h=s}^{h=t} \\

& =\int_s^t \mathscr{L}^{\prime}(\vartheta+h v) v \, \mathrm{d} h \\

& =\int_s^t \frac{1}{h}\langle(\nabla \mathscr{L})(\vartheta+h v), h v\rangle \, \mathrm{d} h \\

& \geq \int_s^t \frac{c}{h}\|h v\|_2^2 \mathrm{d} h \\

& =c\left[\int_s^t h \, \mathrm{d} h\right]\|v\|_2^2=\frac{c}{2}(t^2-s^2) \|v\|_2^2 .\end{aligned} \tag{6.149}$$

引理 6.1.21 的证明到此完成。 \(\square\)

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

&\quad - \mathscr{L}\big(\vartheta + \frac{\|\theta - \vartheta\|_2}{s}\big(\frac{s}{\|\theta - \vartheta\|_2}(\theta - \vartheta)\big)\big)\big] \\

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
