
由此可得

$$\begin{aligned}
D_f(h(W)\|h(Z)) &= \mathbb{E}_{X'\sim Q}f\left(\frac{P(X')}{Q(X')}\right) \\
&\overset{(a)}{=} \mathbb{E}_{X'\sim Q}f\left(\mathbb{E}_{X\sim Q(\cdot\mid X')}\left[\frac{P(X,X')}{Q(X,X')}\right]\right) \\
&\overset{(b)}{\leq} \mathbb{E}_{X'\sim Q}\mathbb{E}_{X\sim Q(\cdot\mid X')}f\left(\frac{P(X,X')}{Q(X,X')}\right) \\
&\overset{(c)}{=} \mathbb{E}_{X'\sim Q}\mathbb{E}_{X\sim Q(\cdot\mid X')}f\left(\frac{P(X)}{Q(X)}\right) \\
&= \mathbb{E}_{[X,X']\sim Q}f\left(\frac{P(X)}{Q(X)}\right)=D_f(W\|Z).
\end{aligned}$$

注意，(B.2) 蕴含 (a)；(b) 由 Jensen 不等式得出，(c) 可由 (B.1) 得到。

## B.2 $f$-散度的例子

下面，我们列出正文中遇到的 $f$-散度的一些有用例子。然而，值得注意的是，不同的 $f(t)$ 可能导致相同的散度，如下面的简单事实所示。

**命题 B.5** 对于任意 $\beta\in\mathbb{R}$，由 $f(t)$ 定义的 $f$-散度与由 $\tilde f(t)=f(t)+\beta(1-t)$ 定义的 $f$-散度相同。

在示例中，我们将为每种散度只选择一个 $f(t)$，尽管为了方便起见，也可以选择不同的 $f(t)$。这些例子中的 $f(t)$ 在 $t=1$ 处均为严格凸的，因此 $D_f(P\|Q)=0$ 当且仅当 $P=Q$。

### KL 散度

取 $f(t)=t\ln t$，我们得到如下 KL 散度（Kullback–Leibler 散度）：

$$\mathrm{KL}(P\|Q)=\int_{\Omega}\ln\left(\frac{p(z)}{q(z)}\right)p(z)\,d\mu(z).$$

KL 散度可能是无界的。

给定随机变量 $[X,X']$，其概率测度为 $P$，它们的互信息定义为

$$I(X,X')=\mathrm{KL}(P(X,X')\|P(X)P(X')).$$

互信息通常用于衡量随机变量 $X$ 和 $X'$ 的独立性。如果随机变量相互独立，则互信息为零。在一般情况下，互信息可能是无界的。

### $\chi^2$ 散度

取 $f(t) = (t - 1)^2$，我们得到如下 $\chi^2$ 散度：

$$\chi^2(P\|Q) = \int_{\Omega} \left(\frac{p(z)-q(z)}{q(z)}\right)^2 q(z)\,d\mu(z) = \int_{\Omega} \left(\frac{p(z)}{q(z)}\right)^2 q(z)\,d\mu(z) - 1.$$

$\chi^2$ 散度可能是无界的。

### 平方 Hellinger 距离

取 $f(t) = (1 - \sqrt{t})^2$，我们得到如下平方 Hellinger 距离：

$$H(P\|Q)^2 = \int_{\Omega} \left(\sqrt{p(z)} - \sqrt{q(z)}\right)^2 d\mu(z) = 2 - 2 \int_{\Omega} \sqrt{p(z)q(z)}\,d\mu(z).$$

Hellinger 距离始终介于 $[0,2]$ 之间。

### $\alpha$ 散度

KL 散度、$\chi^2$ 散度和 Hellinger 散度都属于 $\alpha \ge 0$ 的 $\alpha$ 散度这一更一般的族。对于 $\alpha > 0$，它由 $f(t) = (1-\alpha)^{-1}(t - t^{\alpha})$ 定义：

$$D_{\alpha}(P\|Q) = \frac{1}{1-\alpha} \left(1 - \int_{\Omega} \left(\frac{p(z)}{q(z)}\right)^{\alpha} q(z)\,d\mu(z)\right). \quad (B.3)$$

我们有

- $D_1(P\|Q) = \mathrm{KL}(P\|Q)$：当 $\alpha \to 1$ 时，$f(t) \to t \ln t$。
- $D_2(P\|Q) = \chi^2(P\|Q)$。
- $D_{0.5}(P\|Q) = H(P\|Q)^2$。

当 $\alpha < 1$ 时，$\alpha$ 散度是有界的；当 $\alpha \ge 1$ 时，$\alpha$ 散度是无界的。

我们也可以将 $\alpha$ 散度写成如下不同形式：

$$D_{\alpha}^{\mathrm{R\acute{e}}}(P\|Q) = \frac{1}{\alpha - 1} \ln[1 + (\alpha - 1)D_{\alpha}(P\|Q)] = \frac{1}{\alpha - 1} \ln \int_{\Omega} \left(\frac{p(z)}{q(z)}\right)^{\alpha - 1} p(z)\,d\mu(z).$$

量 $D_{\alpha}^{\mathrm{R\acute{e}}}(\cdot)$ 通常称为 Rényi 熵，它也是非负的。当 $\alpha = 1$ 时，我们采用如下约定：

$$D_{1}^{\mathrm{R\acute{e}}}(P\|Q) = \lim_{\alpha \to 1} D_{\alpha}^{\mathrm{R\acute{e}}}(P\|Q) = \mathrm{KL}(P\|Q). \quad (B.4)$$

$\alpha$ 散度的一个重要性质是，计算乘积分布的 $\alpha$ 散度很方便。该性质可用于获得统计估计的下界。

**定理 B.6** 设 $P^n$ 和 $Q^n$ 分别是来自 $P$ 和 $Q$ 的 $n$ 个独立同分布样本的乘积分布。则

$$D_{\alpha}^{\mathrm{R\acute{e}}}(P^n\|Q^n)=n\cdot D_{\alpha}^{\mathrm{R\acute{e}}}(P\|Q).$$

对于 $\alpha=1$，这变为

$$\mathrm{KL}(P^n\|Q^n)=n\cdot\mathrm{KL}(P\|Q).$$

### $L_1$ 范数和 TV 范数

取 $f(t)=|t-1|$，我们得到两个测度之间的 $L_1$ 范数为

$$\|P-Q\|_1=\int_{\Omega}|p(z)-q(z)|\,d\mu(z).$$

该量始终有界于 $[0,2]$ 之间。我们还可以定义两个测度之间的 TV 范数为

$$\|P-Q\|_{\mathrm{TV}}=\frac{1}{2}\|P-Q\|_1=1-\int_{\Omega}\min(p(z),q(z))\,d\mu(z),$$

它始终在 $[0,1]$ 之间。

TV 范数也可以等价地定义如下。

**命题 B.7**

$$\|P-Q\|_{\mathrm{TV}}=\sup_A|P(A)-Q(A)|=\frac{1}{2}\sup_{g:\,\|g\|_{\infty}\le 1}\left[\mathbb{E}_{Z\sim P}g(Z)-\mathbb{E}_{Z\sim Q}g(Z)\right],$$

*其中 $A$ 取遍所有可测集，$g$ 取遍所有 $L_\infty$ 范数有界的可测函数。*

## B.3 基本不等式

许多 $f$-散度不等式可见于 Sason 和 Verdú (2016)。下面我们仅介绍本书中使用的一些不等式。

在许多应用中，用其他散度来界定两个分布的 TV 范数是有用的。下面的不等式是数据处理不等式的直接应用。

**引理 B.8** *我们有*

$$\|P-Q\|_{\mathrm{TV}}^2\le\frac{1}{c_f}D_f(P\|Q),$$

*其中 $c_f$ 如下定义，$p(s)=(1-s)q+sp$：*

$$c_f=\min_{p,q\in[0,1]}\int_0^1\left[\frac{1}{q}f''\left(\frac{p(s)}{q}\right)+\frac{1}{1-q}f''\left(\frac{1-p(s)}{1-q}\right)\right](1-s)\,ds.$$

**证明** 给定任意可测集 $A$，令 $p=P(A)$，$q=Q(A)$。由数据处理不等式，取 $h(z)=\mathbb{1}(z\in A)$，我们有

$$\begin{aligned}
D_f(P\|Q) &\ge q f(p/q) + (1-q) f((1-p)/(1-q)) \\
&= \left. q f\left(1 + \frac{s(p-q)}{q}\right) + (1-q) f\left(1 + \frac{s(q-p)}{1-q}\right) \right|_{s=1} \\
&= g(0) + g'(0) + \int_0^1 g''(s)(1-s)\,ds \\
&= (p-q)^2 \int_0^1 \left[\frac{1}{q} f''\left(\frac{p(s)}{q}\right) + \frac{1}{1-q} f''\left(\frac{1-p(s)}{1-q}\right)\right](1-s)\,ds \\
&\ge c_f (p-q)^2,
\end{aligned}$$

其中我们使用了泰勒展开，且 $g(0)=g'(0)=0$。因此，

$$\frac{1}{c_f}D_f(P\|Q) \ge \sup_A (P(A)-Q(A))^2 = \|P-Q\|_{\mathrm{TV}}^2.$$

这就证明了所需的界。

该结果蕴含以下不等式。KL 散度中 TV 范数的界通常称为 Pinsker 不等式。

**定理 B.9** 我们有

$$\begin{aligned}
\|P-Q\|_{\mathrm{TV}}^2 &\le \frac{1}{4}\chi^2(P\|Q), \\
\|P-Q\|_{\mathrm{TV}}^2 &\le \frac{1}{2}\mathrm{KL}(P\|Q), \\
\|P-Q\|_{\mathrm{TV}}^2 &\le H(P\|Q)^2.
\end{aligned}$$

**证明** 考虑 $\alpha=1,2$ 的 $\alpha$ 散度。令 $f(t)=(1-\alpha)^{-1}(t-t^\alpha)$，且 $f''(t)=\alpha t^{\alpha-2}$。令

$$c(p,q)=\int_0^1\left[q^{1-\alpha}p(s)^{\alpha-2}+(1-q)^{1-\alpha}(1-p(s))^{\alpha-2}\right](1-s)\,ds.$$

存在 $p_0\in(0,1)$，使得（对于 $\alpha=1,2$）

$$c(p,q)=\frac{1}{2}\left[q^{1-\alpha}p_0^{\alpha-2}+(1-q)^{1-\alpha}(1-p_0)^{\alpha-2}\right]\ge 2.$$

现在我们可以应用引理 B.8，取 $c_f = \alpha \min_{p,q} c(p,q)$ 和 $c(p,q)\ge 2\alpha$，即可得到结果。这蕴含了定理的前两个不等式。对于第三个不等式，我们仍然可以估计所定义的 $c(p,q)$ 的下界。然而，下面的推导更为直接：

$$\begin{aligned}
\|P-Q\|_{\mathrm{TV}}^2 &= \left[\frac{1}{2}\int_{\Omega}|p(z)-q(z)|\,d\mu(z)\right]^2 \\
&= \frac{1}{4}\left[\int_{\Omega}|\sqrt{p(z)}-\sqrt{q(z)}|\cdot|\sqrt{p(z)}+\sqrt{q(z)}|\,d\mu(z)\right]^2 \\
&\le \frac{1}{4}\int_{\Omega}|\sqrt{p(z)}-\sqrt{q(z)}|^2\,d\mu(z)\cdot\int_{\Omega}|\sqrt{p(z)}+\sqrt{q(z)}|^2\,d\mu(z) \\
&\le \frac{1}{4}\int_{\Omega}|\sqrt{p(z)}-\sqrt{q(z)}|^2\,d\mu(z)\cdot\int_{\Omega}2[p(z)+q(z)]\,d\mu(z) \\
&= \int_{\Omega}|\sqrt{p(z)}-\sqrt{q(z)}|^2\,d\mu(z) = H(P\|Q)^2.
\end{aligned}$$

第一个不等式使用了柯西–施瓦茨不等式。第二个不等式使用了 $(\sqrt{a}+\sqrt{b})^2\le 2(a+b)$。最后两个等式使用了 Hellinger 距离的定义以及每个密度 $p(z)$ 和 $q(z)$ 的积分为 1 这一事实。

我们还可以用 TV 范数的平方根推导 Hellinger 距离的上界。然而，一般来说，当范数较小时，这个界并不紧。

**命题 B.10** 我们有

$$H(P\|Q)^2 \le 2\|P-Q\|_{\mathrm{TV}}.$$

**证明** 我们注意到

$$\begin{aligned}
H(P\|Q)^2 &= \int_{\Omega}|\sqrt{p(z)}-\sqrt{q(z)}|^2\,d\mu(z) \\
&\le \int_{\Omega}|\sqrt{p(z)}-\sqrt{q(z)}|\cdot|\sqrt{p(z)}+\sqrt{q(z)}|\,d\mu(z) \\
&= \int_{\Omega}|p(z)-q(z)|\,d\mu(z).
\end{aligned}$$

这就推出了结果。

下面的结果也很有用。

**命题 B.11** 设 $\rho=\sup_z\ln(p(z)/q(z))$。则

$$H(P\|Q)^2 \le \mathrm{KL}(P\|Q) \le (3+\rho)H(P\|Q)^2.$$

**证明** 令 $\kappa=\sup_{t\in[0,\infty)} f_{\mathrm{KL}}(t)/f_H(t)$。利用 $f_{\mathrm{KL}}(t)/f_H(t)$ 是 $t\in[0,\infty)$ 上的增函数这一事实，我们得到

$$\kappa \le \frac{f_{\mathrm{KL}}(\exp(\rho))}{f_H(\exp(\rho))}.$$

此外，由于 $p(z)/q(z)\le\exp(\rho)$，其中 $\rho\ge0$，且当 $\rho\in(0,\infty)$ 时，我们有

$$\kappa \le \frac{f_{\mathrm{KL}}(\exp(\rho))}{f_H(\exp(\rho))} \le 2.5+\rho.$$

我们现在有

$$\mathrm{KL}(P\|Q)=\mathbb{E}_{Z\sim Q}f_{\mathrm{KL}}(p(z)/q(z)) \le \kappa\mathbb{E}_{Z\sim Q}f_H(p(z)/q(z)) = \kappa H(P\|Q)^2,$$

这就推出了所需的界。

对于不同的 $\alpha$ 值，获得 $\alpha$ 散度的界也相对容易。一般来说，如果 $\alpha < \alpha'$，那么我们可以如下用 $\alpha'$ 散度来界定 $\alpha$ 散度。这是 Jensen 不等式的直接推论。

**命题 B.12** 如果 $0 < \alpha < \alpha'$，则

$$D_{\alpha}^{\mathrm{R\acute{e}}}(P\|Q) \le D_{\alpha'}^{\mathrm{R\acute{e}}}(P\|Q),$$

其中当 $\alpha=1$ 或 $\alpha'=1$ 时采用 (B.4) 的约定。

**证明** 我们考虑 $1 < \alpha \le \alpha'$ 的情形。此时 Jensen 不等式蕴含

$$\left[\int_{\Omega}\left(\frac{p(z)}{q(z)}\right)^{\alpha-1}p(z)\,d\mu(z)\right]^{(\alpha'-1)/(\alpha-1)} \le \int_{\Omega}\left(\frac{p(z)}{q(z)}\right)^{\alpha'-1}p(z)\,d\mu(z).$$

通过取对数并将两边除以 $\alpha'-1$，我们得到所需的界。类似地，我们可以证明 $0 < \alpha \le \alpha' < 1$ 的情形。将这两种情形结合，并在 $\alpha\to1$ 或 $\alpha'\to1$ 处取极限，我们便对所有 $0 < \alpha \le \alpha'$ 得到所需的不等式。

定理 B.9 对于通过 $\alpha$ 散度界定乘积分布的 TV 范数很有用。根据命题 B.12，使用 $\alpha<1$ 是有利的。特别地，我们有以下使用 Hellinger 距离的结果。

**定理 B.13** 设 $P^n$ 和 $Q^n$ 分别是来自 $P$ 和 $Q$ 的 $n$ 个独立同分布样本的乘积分布。我们有

$$\|P^n-Q^n\|_{\mathrm{TV}}^2 \le H(P^n\|Q^n)^2 = 2 - 2\left(1 - \frac12 H(P\|Q)^2\right)^n.$$

**证明** 由定理 B.6 取 $\alpha=0.5$，我们得到

$$\ln\left(1 - \frac12 H(P^n\|Q^n)^2\right) = n\ln\left(1 - \frac12 H(P\|Q)^2\right).$$

由此可得

$$H(P^n\|Q^n)^2 = 2 - 2\left(1 - \frac12 H(P\|Q)^2\right)^n.$$

结合定理 B.9，我们得到所需的界。

