
不同 $g_{\ell}(g)-g_{\ell-1}(g)$ 的个数不超过 $N_{\ell}N_{\ell-1}$。由此可得

$R(\mathcal{G},\mathcal{S}_n)=\mathbb{E}_{\sigma}\sup_{g\in\mathcal{G}}\frac{1}{n}\sum_{i=1}^{n}\sigma_i\Big[(g-g_L(g))(Z_i)+\sum_{\ell=1}^{L}(g_{\ell}(g)-g_{\ell-1}(g))(Z_i)\Big]$ $\le \mathbb{E}_{\sigma}\sup_{g\in\mathcal{G}}\frac{1}{n}\sum_{i=1}^{n}\sigma_i(g-g_L(g))(Z_i)+\sum_{\ell=1}^{L}\mathbb{E}_{\sigma}\sup_{g\in\mathcal{G}}\frac{1}{n}\sum_{i=1}^{n}\sigma_i(g_{\ell}(g)-g_{\ell-1}(g))(Z_i)$ $\stackrel{(a)}{\le} \epsilon_L+\sum_{\ell=1}^{L}\sup_{g\in\mathcal{G}}\big\|g_{\ell}(g)-g_{\ell-1}(g)\big\|_{L_2(\mathcal{S}_n)}\sqrt{\frac{2\ln[N_{\ell}N_{\ell-1}]}{n}}$ $\stackrel{(b)}{\le} \epsilon_L+3\sum_{\ell=1}^{L}\epsilon_{\ell}\sqrt{\frac{2\ln[N_{\ell}N_{\ell-1}]}{n}}$ $\le \epsilon_L+12\sum_{\ell=1}^{L}(\epsilon_{\ell}-\epsilon_{\ell+1})\sqrt{\frac{\ln[N_{\ell}]}{n}}$ $\le \epsilon_L+12\int_{\epsilon_L/2}^{\infty}\sqrt{\frac{\ln N(\epsilon',\mathcal{G},L_2(\mathcal{S}_n))}{n}}\,d\epsilon'$.

$(a)$ 的推导使用了定理 6.23，$(b)$ 的推导使用了 $(6.7)$。接下来两个不等式将 $N(\epsilon,\mathcal{G},L_2(\mathcal{S}_n))$ 用作 $\epsilon$ 的非增函数。现在给定任意 $\epsilon>0$，我们可以选择 $\epsilon_L$ 使得 $\epsilon\in[\epsilon_L/4,\epsilon_L/2]$。这导致了期望的结果。

## 示例 6.26

由推论 5.7 可知，若二值函数类 $\mathcal{G}$（或取值在 $[0,1]$ 的 VC 下图类）具有 VC 维 $d$，则

$\ln N_2(\epsilon,\mathcal{G},n)\le 1+\ln(d+1)+d\ln(2e/\epsilon^2)$。

由于 $N_2(0.5,\mathcal{G},n)=1$，我们有

$12\int_{0}^{\infty}\sqrt{\ln N_2(\epsilon,\mathcal{G},n)}\,d\epsilon\le 12\int_{0}^{0.5}\sqrt{1+\ln(d+1)+d\ln(2e/\epsilon^2)}\,d\epsilon\le 16\sqrt{d}$。

由此可得

$R(\mathcal{G},\mathcal{S}_n)\le\frac{16\sqrt{d}}{\sqrt{n}}$。

该常数并非最优，事实上使用 packing 数（参见示例 6.4）可以得到更好的常数。该结果蕴含以下一致收敛结果：以至少 $1-\delta$ 的概率，对所有 $w\in\Omega$，

$\phi(w,\mathcal{D})\le\phi(w,\mathcal{S}_n)+\frac{32\sqrt{d}}{\sqrt{n}}+\sqrt{\frac{\ln(1/\delta)}{2n}}$。

该界去掉了定理 4.17 中加性一致收敛界中的 $\ln n$ 因子。

## 示例 6.27

若 $\ln N_2(\epsilon, \mathcal{G}, n) \le 1/\epsilon^q$ 且 $q \in (0,2)$，则

$$\int_0^{\infty} \sqrt{\ln N_2(\epsilon, \mathcal{G}, n)} d\epsilon < \infty.$$

因此存在 $C > 0$ 使得

$$R(\mathcal{G}, \mathcal{S}_n) \le \frac{C}{\sqrt{n}}.$$

若 $\ln N_2(\epsilon, \mathcal{G}, n) \le 1/\epsilon^q$ 且 $q > 2$，则

$$R(\mathcal{G}, \mathcal{S}_n) \le O\left(\inf_{\epsilon>0}\left(\epsilon + \frac{\epsilon^{1-q/2}}{\sqrt{n}}\right)\right) = O(n^{-1/q}).$$

这意味着收敛速度慢于 $1/\sqrt{n}$。

关于 Rademacher 平均的一个方便事实是以下结果。设 $\{\phi_i\}$ 为一组函数，每个函数由 Lipschitz 常数 $\gamma_i$ 刻画。则该结果蕴含了函数复合 $\phi \circ f$ 的 Rademacher 复杂度的界。

## 定理 6.28

设 $\{\phi_i\}_{i=1}^n$ 为函数，其 Lipschitz 常数分别为 $\{\gamma_i\}_{i=1}^n$；即 $\forall i \in [n]$：

$$|\phi_i(\theta) - \phi_i(\theta')| \le \gamma_i |\theta - \theta'|.$$

则对于任意实值函数 $h: \mathcal{F} \times \mathcal{Z}^n \to \mathbb{R}$，且 $\mathcal{S}_n = \{Z_1, \dots, Z_n\} \subset \mathcal{Z}^n$，我们有

$$\mathbb{E}_\sigma \sup_{f \in \mathcal{F}} \left[ \sum_{i=1}^n \sigma_i \phi_i(f(Z_i)) - h(f, \mathcal{S}_n) \right] \le \mathbb{E}_\sigma \sup_{f \in \mathcal{F}} \left[ \sum_{i=1}^n \sigma_i \gamma_i f(Z_i) - h(f, \mathcal{S}_n) \right].$$

证明 该结果是引理 6.29 的直接推论，其中我们简单地令 $c(w) = -h(w, \mathcal{S}_n)$，$g_i(w) = \phi_i(f(Z_i))$，且 $\tilde{g}_i(w) = \gamma_i f(Z_i)$。

## 引理 6.29（Rademacher 比较引理）

设 $\{g_i(w)\}$ 和 $\{\tilde{g}_i(w)\}$ 为在某个域 $\Omega$ 上对所有 $w$ 定义的函数集。若对所有 $i, w, w'$，

$$|g_i(w) - g_i(w')| \le |\tilde{g}_i(w) - \tilde{g}_i(w')|,$$

则对任意函数 $c(w)$，
$$\mathbb{E}_\sigma \sup_{w \in \Omega} \left[ c(w) + \sum_{i=1}^n \sigma_i g_i(w) \right] \le \mathbb{E}_\sigma \sup_{w \in \Omega} \left[ c(w) + \sum_{i=1}^n \sigma_i \tilde{g}_i(w) \right].$$

证明 我们用归纳法证明该结果。该结果对 $n = 0$ 成立。假设该结果对 $n = k$ 成立，则当 $n = k + 1$ 时，我们有

\[ \mathbb{E}_{\sigma_1,\dots,\sigma_{k+1}} \sup_w \left[ c(w) + \sum_{i=1}^{k+1} \sigma_i g_i(w) \right] \]
\[ = \mathbb{E}_{\sigma_1,\dots,\sigma_k} \sup_{w_1,w_2} \left[ \frac{c(w_1)+c(w_2)}{2} + \sum_{i=1}^{k} \sigma_i \frac{g_i(w_1)+g_i(w_2)}{2} + \frac{g_{k+1}(w_1)-g_{k+1}(w_2)}{2} \right] \]
\[ = \mathbb{E}_{\sigma_1,\dots,\sigma_k} \sup_{w_1,w_2} \left[ \frac{c(w_1)+c(w_2)}{2} + \sum_{i=1}^{k} \sigma_i \frac{g_i(w_1)+g_i(w_2)}{2} + \frac{|g_{k+1}(w_1)-g_{k+1}(w_2)|}{2} \right] \]
\[ \le \mathbb{E}_{\sigma_1,\dots,\sigma_k} \sup_{w_1,w_2} \left[ \frac{c(w_1)+c(w_2)}{2} + \sum_{i=1}^{k} \sigma_i \frac{g_i(w_1)+g_i(w_2)}{2} + \frac{|\tilde g_{k+1}(w_1)-\tilde g_{k+1}(w_2)|}{2} \right] \]
\[ = \mathbb{E}_{\sigma_1,\dots,\sigma_k} \sup_{w_1,w_2} \left[ \frac{c(w_1)+c(w_2)}{2} + \sum_{i=1}^{k} \sigma_i \frac{g_i(w_1)+g_i(w_2)}{2} + \frac{\tilde g_{k+1}(w_1)-\tilde g_{k+1}(w_2)}{2} \right] \]
\[ = \mathbb{E}_{\sigma_1,\dots,\sigma_k} \mathbb{E}_{\sigma_{k+1}} \sup_w \left[ c(w) + \sigma_{k+1} \tilde g_{k+1}(w) + \sum_{i=1}^{k} \sigma_i g_i(w) \right] \]
\[ \le \mathbb{E}_{\sigma_1,\dots,\sigma_k} \mathbb{E}_{\sigma_{k+1}} \sup_w \left[ c(w) + \sigma_{k+1} \tilde g_{k+1}(w) + \sum_{i=1}^{k} \sigma_i \tilde g_i(w) \right]. \]

最后一个不等式由归纳假设得出。

以下示例展示了定理 6.28 的一个应用。

## 示例 6.30

考虑二分类问题 $y \in \{\pm1\}$，并设 $\mathcal{F} = \{f(w, x) = wᵀ \psi(x)\}$ 为线性分类器类。考虑平滑分类损失函数 $L(f(x), y) = \min(1, \max(0, 1−γ f(x) y))$，其中 $\gamma > 0$，如图 6.1 所示。设 $\mathcal{G} = \{L(f(w, x), y)\}$。则 $L(f, y)$ 在 $f$ 上是 $\gamma$ Lipschitz。考虑示例 6.12 中的正则化项，其中 $h(w) = h_0(w) = 0.5 \lambda \|w\|_2^2$ 在 $(6.3)$ 中。我们由定理 6.28 得到，

\[ R^{h}(\mathcal{G}, \mathcal{S}_n) \le \gamma R^{h/\gamma}(\mathcal{F}, \mathcal{S}_n), \]

这意味着

\[ R^{h}(\mathcal{G}, \mathcal{S}_n) \le \frac{\gamma^{2}}{\lambda n^{2}} \sum_{i=1}^{n} \|\psi(X_i)\|_{2}^{2}. \]

![](img/49407831b69246276f2b471882509fb2_111_0.png)

**图 6.1** 平滑分类损失

由此可得

$$R_n^h(\mathcal{G},\mathcal{D}) \leq \frac{\gamma^2}{\lambda n}\mathbb{E}_{X\sim\mathcal{D}}[\|\psi(X)\|_2^2].$$

以下结果是定理 6.28 和推论 6.21 的直接推论。

## 定理 6.31

*考虑实值函数类* $\mathcal{F}=\{f(w,\cdot):w\in\Omega\}$，*且* $\mathcal{G}=\{\phi(w,z)=L(f(w,x),y):w\in\Omega,z=(x,y)\}$。*假设我们在 $(6.3)$ 中有分解且* $h_1(w,S_n)=0$。*假设*

$$\sup_{(x,y),(x',y')}\left|L(f(w,x),y)-L(f(w,x'),y')\right|\leq M,$$

且 $L(f,y)$ 在 $f$ 上是 $\gamma$-Lipschitz：

$$|L(f,y)-L(f',y)|\leq\gamma|f-f'|.$$

设 $S_n$ 为来自 $\mathcal{D}$ 的 $n$ 个 iid 样本。以至少 $1-\delta$ 的概率，对所有 $w\in\Omega$，

$$\begin{aligned}
\mathbb{E}_{\mathcal{D}}L(f(w,X),Y)\ &\leq\ \frac{1}{n}\sum_{i=1}^{n}L(f(w,X_i),Y_i)+h_0(w)\\
&\quad +2\gamma R_n^{h/\gamma}(\mathcal{F},\mathcal{D})+M\sqrt{\frac{\ln(1/\delta)}{2n}}.
\end{aligned}$$

此外，对于近似正则化 ERM 方法 $(6.1)$，其中 $\phi(w,z)=L(f(w,x),y)$，我们以至少 $1-\delta$ 的概率有

$$\begin{aligned}
\mathbb{E}_{\mathcal{D}}L(\hat f(w,X),Y)\ &\leq\ \inf_{w\in\Omega}\left[\mathbb{E}_{\mathcal{D}}L(f(w,X),Y)+h_0(w)\right]\\
&\quad +\epsilon' +2\gamma R_n^{h/\gamma}(\mathcal{F},\mathcal{D})+M\sqrt{\frac{2\ln(2/\delta)}{n}}.
\end{aligned}$$

我们给出平滑分类损失的一个示例。

## 示例 6.32

考虑示例 6.30 中的平滑分类损失，其中

$$h(w,S_n)=g(w)=\frac{\lambda}{2}\|w\|_2^2.$$
