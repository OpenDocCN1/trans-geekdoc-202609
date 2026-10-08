

将上述不等式与(12.139)结合，可知对于所有 \(N \in \mathbb{N}\)，\(i \in \{1, 2, \ldots, N\}\)，以及 \(x \in [a + \frac{(i-1)(b-a)}{N}, a + \frac{i(b-a)}{N}]\)，均有 \(|x - g_{N,i}| \leq \frac{b-a}{2N}\)。这证明了对于任意 \(N \in \mathbb{N}\) 和 \(x \in [a, b]\)，存在 \(y \in \{g_{N,1}, g_{N,2}, \ldots, g_{N,N}\}\) 使得

\(|x - y| \leq \frac{b-a}{2N}\)。 (12.141)

这表明对于任意 \(x = (x_1, x_2, \ldots, x_d) \in [a, b]^d\)，存在 \(y = (y_1, y_2, \ldots, y_d) \in A\) 使得

\(\delta(x, y) = \|x - y\|_\infty = \max_{i \in \{1, 2, \ldots, d\}} |x_i - y_i| \leq \frac{b-a}{2N} \leq \frac{(b-a)2r}{2(b-a)} = r\)。 (12.142)

将上述结果与(4.82)、(12.138)、(12.136)以及事实 \(\forall x \in [0, \infty) : |x| \leq \mathbb{I}_{(0,r]}(x)r + 2x\mathbb{I}_{(r, \infty)}(x)\) 结合，可证明

\(\mathcal{C}^{([a,b]^d,\delta), r} \leq |A| = \left|\mathbb{N}^d = \left(\frac{b-a}{2r}\right)^d\right| \leq \mathbb{I}_{(0,r]}\left(\frac{b-a}{2}\right) + \left(\frac{b-a}{r}\right)^d \mathbb{I}_{(r, \infty)}\left(\frac{b-a}{2}\right)\)。 (12.143)

(参见定义 4.3.2)。至此，命题 12.2.24 的证明结束。

## 12.3 经验风险最小化

### 12.3.1 随机场的集中不等式

**引理 12.3.1。** 设 \((E, d)\) 为可分度量空间，且设 \(F \subseteq E\) 为一个集合。则

\((F, d|_{F \times F})\)。 (12.144)

是一个可分度量空间。

*引理 12.3.1 的证明。* 在整个证明过程中，不妨设 \(F \neq \emptyset\)。令 \(e = (e_n)_{n \in \mathbb{N}} : \mathbb{N} \to E\) 为 \(E\) 中元素的一个序列，使得 \(\{e_n \in E : n \in \mathbb{N}\}\) 在 \(E\) 中稠密；令 \(f = (f_n)_{n \in \mathbb{N}} : \mathbb{N} \to F\) 为 \(F\) 中元素的一个序列，使得对于所有 \(n \in \mathbb{N}\)，有

\(d(f_n, e_n) \leq \left\{\begin{array}{ll}0 & : e_n \in F \\ \inf_{x \in F} d(x, e_n) + \frac{1}{2^n} & : e_n \notin F.\end{array}\right.\)。 (12.145)

注意到对于所有 \(v \in F \setminus \{e_m \in E : m \in \mathbb{N}\}\) 以及 \(n \in \mathbb{N}\)，有

\(\inf_{m \in \mathbb{N}} d(v, f_m) \leq \inf_{m \in \mathbb{N}[n, \infty)} d(v, f_m)\)

\(\leq \inf_{m \in \mathbb{N}[n, \infty)} \left[ d(v, e_m) + d(e_m, f_m) \right]\)

\(\leq \inf_{m \in \mathbb{N}[n, \infty)} \left[ d(v, e_m) + \inf_{x \in F} d(x, e_m) \right] + \frac{1}{2^n}\)

\(\leq \inf_{m \in \mathbb{N}[n, \infty)} \left[ 2 d(v, e_m) + \frac{1}{2^n} \right]\)

\(\leq 2 \left[ \inf_{m \in \mathbb{N}[n, \infty)} d(v, e_m) \right] + \frac{1}{2^n} = \frac{1}{2^n}\)。 (12.146)

结合事实：对于所有 $v \in F \cap \{e_m \in E: m \in \mathbb{N}\}$，有 $\inf_{m \in \mathbb{N}} d(v, f_m) = 0$，可以确保集合 $\{f_n \in F: n \in \mathbb{N}\}$ 在 $F$ 中稠密。至此，引理 **12.3.1** 的证明结束。

**引理 12.3.2。** 设 $(E, \mathfrak{E})$ 为一个拓扑空间，假设 $E \neq \emptyset$。令 $\mathbf{E} \subseteq E$ 为一个至多可数集，假设 $\mathbf{E}$ 在 $E$ 中稠密。令 $(\Omega, \mathcal{F})$ 为一个可测空间。对于每个 $x \in E$，令 $f_x: \Omega \rightarrow \mathbb{R}$ 是 $\mathcal{F}/\mathcal{B}(\mathbb{R})$-可测的。假设对于所有 $\omega \in \Omega$，映射 $E \ni x \mapsto f_x(\omega) \in \mathbb{R}$ 是连续的。令 $F: \Omega \rightarrow \mathbb{R} \cup \{\infty\}$ 满足对于所有 $\omega \in \Omega$，有

$$F(\omega) = \sup_{x \in E} f_x(\omega)。 \tag{12.147}$$

则

-   (i) 对于所有 $\omega \in \Omega$，有 $F(\omega) = \sup_{x \in \mathbf{E}} f_x(\omega)$；
-   (ii) $F$ 是 $\mathcal{F}/\mathcal{B}(\mathbb{R} \cup \{\infty\})$-可测的。

*引理 12.3.2 的证明。* 注意到假设 $\mathbf{E}$ 在 $E$ 中稠密表明，对于所有 $g \in C(E, \mathbb{R})$，有

$$\sup_{x \in E} g(x) = \sup_{x \in \mathbf{E}} g(x)。 \tag{12.148}$$

结合假设：对于所有 $\omega \in \Omega$，映射 $E \ni x \mapsto f_x(\omega) \in \mathbb{R}$ 是连续的，可证明对于所有 $\omega \in \Omega$，有

$$F(\omega) = \sup_{x \in E} f_x(\omega) = \sup_{x \in \mathbf{E}} f_x(\omega)。 \tag{12.149}$$

这证明了条目 **(i)**。此外，注意条目 **(i)** 与假设“对于所有 $x \in E$，$f_x: \Omega \rightarrow \mathbb{R}$ 是 $\mathcal{F}/\mathcal{B}(\mathbb{R})$-可测的”共同建立了条目 **(ii)**。至此，引理 **12.3.2** 的证明结束。

**引理 12.3.3。** 设 $(E, \delta)$ 为一个可分度量空间。令 $\varepsilon, L \in \mathbb{R}$，$N \in \mathbb{N}$。设 $z_1, z_2, \ldots, z_N \in E$ 满足 $E \subseteq \bigcup_{i=1}^{N}\{x \in E: 2 L \delta(x, z_i) \leq \varepsilon\}$。令 $(\Omega, \mathcal{F}, \mathbb{P})$ 为一个概率空间。令 $Z_x: \Omega \rightarrow \mathbb{R}$，$x \in E$，为满足对于所有 $x, y \in E$ 有 $|Z_x - Z_y| \leq L \delta(x, y)$ 的随机变量。则

$$\mathbb{P}(\sup_{x \in E}|Z_x| \geq \varepsilon) \leq \sum_{i=1}^{N} \mathbb{P}(|Z_{z_i}| \geq \tfrac{\varepsilon}{2}) \tag{12.150}$$

(*参见* 引理 **12.3.2**)。

*引理 12.3.3 的证明。* 在整个证明过程中，令 $B_1, B_2, \ldots, B_N \subseteq E$ 满足对于所有 $i \in \{1, 2, \ldots, N\}$，有 $B_i = \{x \in E: 2 L \delta(x, z_i) \leq \varepsilon\}$。注意到三角不等式以及假设“对于所有 $x, y \in E$，有 $|Z_x - Z_y| \le L \delta(x, y)$”表明，对于所有 $i \in \{1, 2, \ldots, N\}$ 和 $x \in B_i$，有

$|Z_x| = |Z_x - Z_{z_i} + Z_{z_i}| \le |Z_x - Z_{z_i}| + |Z_{z_i}| \le L \delta(x, z_i) + |Z_{z_i}| \le \frac{\varepsilon}{2} + |Z_{z_i}|。$ (12.151)

结合引理 **12.3.2** 和引理 **12.3.1**，可证明对于所有 $i \in \{1, 2, \ldots, N\}$，有

$\mathbb{P}\big(\sup_{x \in B_i}|Z_x| \ge \varepsilon\big) \le \mathbb{P}\big(\frac{\varepsilon}{2} + |Z_{z_i}| \ge \varepsilon\big) = \mathbb{P}\big(|Z_{z_i}| \ge \frac{\varepsilon}{2}\big)。$ (12.152)

结合上述结果、引理 **12.3.2** 和引理 **12.3.1**，可建立

$\mathbb{P}\big(\sup_{x \in E}|Z_x| \ge \varepsilon\big) = \mathbb{P}\bigg(\sup_{x \in \bigcup_{i=1}^N B_i}|Z_x| \ge \varepsilon\bigg) = \mathbb{P}\bigg(\bigcup_{i=1}^N \big\{\sup_{x \in B_i}|Z_x| \ge \varepsilon\big\}\bigg)$

$\le \sum_{i=1}^N \mathbb{P}\big(\sup_{x \in B_i}|Z_x| \ge \varepsilon\big) \le \sum_{i=1}^N \mathbb{P}\big(|Z_{z_i}| \ge \frac{\varepsilon}{2}\big)。$ (12.153)

至此，引理 **12.3.3** 的证明结束。$\quad \square$

**引理 12.3.4。** 设 $(E, \delta)$ 为一个可分度量空间，假设 $E \neq \emptyset$。令 $\varepsilon, L \in (0, \infty)$。令 $(\Omega, \mathcal{F}, \mathbb{P})$ 为一个概率空间。令 $Z_x: \Omega \to \mathbb{R}$，$x \in E$，为满足对于所有 $x, y \in E$ 有 $|Z_x - Z_y| \le L \delta(x, y)$ 的随机变量。则

$\big[\mathcal{C}(E, \delta, \frac{\varepsilon}{2L})\big]^{-1}\mathbb{P}\big(\sup_{x \in E}|Z_x| \ge \varepsilon\big) \le \sup_{x \in E}\mathbb{P}\big(|Z_x| \ge \frac{\varepsilon}{2}\big)。$ (12.154)

*(参见定义 4.3.2 和引理 12.3.2)。*

*引理 **12.3.4** 的证明。* 在整个证明过程中，令 $N \in \mathbb{N} \cup \{\infty\}$ 满足 $N = \mathcal{C}(E, \delta, \frac{\varepsilon}{2L})$。不妨设 $N < \infty$。令 $z_1, z_2, \ldots, z_N \in E$ 满足 $E \subseteq \bigcup_{i=1}^N \{x \in E: \delta(x, z_i) \le \frac{\varepsilon}{2L}\}$（参见定义 **4.3.2**）。注意到引理 **12.3.2** 和引理 **12.3.3** 建立了*

$\mathbb{P}\big(\sup_{x \in E}|Z_x| \ge \varepsilon\big) \le \sum_{i=1}^N \mathbb{P}\big(|Z_{z_i}| \ge \frac{\varepsilon}{2}\big) \le N\big[\sup_{x \in E}\mathbb{P}\big(|Z_x| \ge \frac{\varepsilon}{2}\big)\big]。$ (12.155)

至此，引理 **12.3.4** 的证明结束。$\quad \square$

**引理 12.3.5。** 设 $(E, \delta)$ 为一个可分度量空间，假设 $E \neq \emptyset$。令 $(\Omega, \mathcal{F}, \mathbb{P})$ 为一个概率空间。令 $L \in \mathbb{R}$。对于每个 $x \in E$，令 $Z_x: \Omega \to \mathbb{R}$ 为随机变量，且 $\mathbb{E}[|Z_x|] < \infty$。假设对于所有 $x, y \in E$，有 $|Z_x - Z_y| \le L \delta(x, y)$。则

-   (i) 对于所有 $x, y \in E$ 和 $\eta \in \Omega$，有

$|(Z_x(\eta) - \mathbb{E}[Z_x]) - (Z_y(\eta) - \mathbb{E}[Z_y])| \le 2L \delta(x, y)$ (12.156)

且

