
意味着

$$r \le e_n^{h'}(\mathcal{F},\mathcal{D}) + 0.5r'.$$

令 $r' = \max(r,\alpha b_0)$，我们得到要么 $r \le \alpha b_0$，要么

$$r \le e_n^{h'}(\mathcal{F},\mathcal{D}) + 0.5r.$$

因此

$$r \le \max\left(2e_n^{h'}(\mathcal{F},\mathcal{D}),\alpha b_0\right).$$

这意味着期望的界。□

通过使用速率函数的概念，我们可以从推论 6.34 得到以下一致收敛结果，其中我们假设局部化函数满足类似于 (3.13) 的方差条件。

## 定理 6.41
考虑 $\mathcal{F}$、$\mathcal{D}$ 以及 iid 样本 $S_n=\{Z_1,\ldots,Z_n\}\sim\mathcal{D}$。令 $f(\mathcal{D})=\mathbb{E}_{Z\sim\mathcal{D}}[f(Z)]$，且 $f(S_n)=n^{-1}\sum_{i=1}^n f(Z_i)$。假设对所有 $f\in\mathcal{F}$，

$$\operatorname{Var}_{\mathcal{D}}[f(Z)]\le c_0^2+c_1h(f)$$

对某些 $c_0,c_1,h(\cdot)>0$ 成立。还假设 $\mathcal{F}$ 有界：$\sup_{z,z'}|f(\mathcal{D})-f(z')|<M$ 对所有 $f\in\mathcal{F}$ 成立。则在 $S_n$ 上以至少 $1-\delta$ 的概率，$\forall f\in\mathcal{F}$ 且 $\forall\alpha>0$，

$$f(\mathcal{D})\le f(S_n)+5\alpha h(f)+5r_0+\sqrt{\frac{2c_0^2\ln(1/\delta)}{n}}+\frac{(3c_1+4\alpha M)\ln(1/\delta)}{3\alpha n},$$

其中

$$r_0=\bar r_n^h(\alpha,\mathcal{F},\mathcal{D})+\alpha\inf_{f\in\mathcal{F}}h(f)+\sqrt{\frac{2c_0^2}{n}+\frac{(3c_1+4\alpha M)}{3\alpha n}}$$

$$\le 2e_n^{h'}(\alpha,\mathcal{F},\mathcal{D})+2\alpha\inf_{f\in\mathcal{F}}h(f)+\sqrt{\frac{2c_0^2}{n}+\frac{(3c_1+4\alpha M)}{3\alpha n}},$$

其中 $h'(f,S_n)=0.5\alpha h(f)$。

### 证明
$r_0$ 的不等式是命题 6.40 的直接结果。我们现在使用剥离论证。对 $\ell=1,2,\ldots$，令 $r_\ell=\alpha^{-1}(1.5)^{\ell-1}r_0$。定义 $\mathcal{F}_\ell=\{f\in\mathcal{F}:h(f)\le r_\ell\}$。由此可得

$$\sup_{f\in\mathcal{F}_\ell}\operatorname{Var}_{\mathcal{D}}[f(Z)]\le c_0^2+c_1h(f)\le c_0^2+c_1r_\ell.$$

对每个 $\ell\ge1$，令 $\delta_\ell=4\delta/((\ell+3)(\ell+4))$。我们以概率 $1-\delta_\ell$ 有

$f(\mathcal{D}) \le f(S_n) + O\left(\epsilon_n(\mathcal{F},\mathcal{D}) + \sqrt{\frac{2c_0^2\ln(1/\delta)}{n}} + \frac{M\ln(1/\delta)}{n}\right).$

如果 $c_0$ 很小，则该结果改进了 $h = 0$ 时的推论 6.19，因为在 $O(1/\sqrt{n})$ 项中 $M$ 被可能更小的量 $c_0$ 替代。

## 例 6.43
在定理 6.41 中，假设 $f(Z) \in [0,1]$。则我们可以取 $h(f)=f(\mathcal{D})$ 使得方差条件以 $c_0 = 0$ 和 $c_1 = 1$ 成立。在这种情况下，我们可以取 $\alpha$ 为常数。这意味着以下界：

$(1 - 5\alpha)f(\mathcal{D}) \le f(S_n) + 5\bar r_n^h(\alpha,\mathcal{F},\mathcal{D}) + O\left(\frac{(1 + \alpha)\ln(1/\delta)}{\alpha n}\right).$

这导致 $O(1/n)$ 的集中项。该结果可用于改进例 6.24 中的乘性界的集中性。我们将其留作练习。

虽然推论 6.19 的 Chernoff 风格界仅对 ERM 隐含一个收敛速率不优于 $O(1/\sqrt{n})$ 的 oracle 不等式，但定理 6.41 中的 Bennett 风格界可以导致更快的收敛速率。我们陈述以下结果，它是定理 6.41 的直接推论。

## 推论 6.44
令 $\phi(w,z)=L(f(w,x),y)-L_s(x,y)$ 对适当定义的 $L_s(x,y)$ 使得 $\phi(w,\mathcal{D})\ge0$。假设 $\sup_w\sup_{z,z'}[\phi(w,z)-\phi(w,z')]\le M$，且方差条件 (3.13) 成立。考虑 $h_0(w)\ge0$，并令 $h(w,S_n)=5\alpha h_0(w)$。则对满足 $\ln(2/\delta)\ge1$ 的 $\delta$，以至少 $1-\delta$ 的概率，对所有 $\alpha>0$，近似 ERM 方法 (6.1) 满足

$(1 - 5\alpha)\phi(\hat w,\mathcal{D}) \le \inf_{w\in\Omega}[(1 + 6\alpha)\phi(w,\mathcal{D}) + 10\alpha h_0(w)] + \epsilon' + 5\bar r_n^{h'}(\alpha,\mathcal{G},\mathcal{D}) + 7\sqrt{\frac{2c_0^2\ln(2/\delta)}{n}} + \frac{(7c_1 + 10\alpha M)\ln(2/\delta)}{\alpha n},$
其中 $h'(w)=h_0(w)+\phi(w,\mathcal{D})$ 且 $\mathcal{G}=\{\phi(w,z):w\in\Omega\}$。此外，以至少 $1-\delta$ 的概率，我们有

$(1 - 5\alpha)\phi(\hat w,\mathcal{D}) \le \inf_{w\in\Omega}[(1 + 11\alpha)\phi(w,\mathcal{D}) + 15\alpha h_0(w)] + \epsilon' + 10\epsilon_n^{0.5\alpha h'}(\mathcal{G},\mathcal{D}) + 7\sqrt{\frac{2c_0^2\ln(2/\delta)}{n}} + \frac{(7c_1 + 10\alpha M)\ln(2/\delta)}{\alpha n}.$

### 证明
对任意 $w \in \Omega$，我们根据 Bennett 不等式知道以概率

$1 - \delta/2$,

$\phi(w, S_n) \le \phi(w, \mathcal{D}) + \sqrt{[2 \operatorname{Var}_{Z\sim\mathcal{D}}[\phi(w,Z)] \ln(2/\delta) / n]} + M \ln(2/\delta)/(3n)$
$\le \phi(w, \mathcal{D}) + \sqrt{[2(c_0^2 + c_1 \phi(w, \mathcal{D})) \ln(2/\delta) / n]} + M \ln(2/\delta)/(3n)$
$\le \phi(w, \mathcal{D}) + \sqrt{2c_0^2 \ln(2/\delta)/n} + \sqrt{2c_1 \phi(w, \mathcal{D}) \ln(2/\delta)/n} + M \ln(2/\delta)/(3n)$
$\le (1 + 0.5\alpha) \phi(w, \mathcal{D}) + \sqrt{2c_0^2 \ln(2/\delta)/n} + (3c_1 + \alpha M) \ln(2/\delta)/(3\alpha n).$

第一个不等式使用了独立随机变量和的 Bennett 不等式。第二个不等式使用了方差条件。第三个不等式使用了 $\sqrt{a + b} \le \sqrt{a} + \sqrt{b}$。最后一个不等式使用了 $\sqrt{2ab} \le 0.5\alpha a + b/\alpha$。

此外，由定理 6.41 且 $h(\phi(w,\cdot)) = h'(w)$，我们以概率 $1 - \delta/2$ 得到：

$(1 - 5\alpha) \phi(\hat w, \mathcal{D}) \le \phi(\hat w, S_n) - 5\alpha \phi(\hat w, \mathcal{D}) + 5\alpha h'(\hat w) + 5r_0 + \sqrt{2c_0^2 \ln(2/\delta)/n} + (3c_1 + 4\alpha M) \ln(2/\delta)/(3\alpha n)$
$= \phi(\hat w, S_n) + 5\alpha h_0(\hat w) + 5r_0 + \sqrt{2c_0^2 \ln(2/\delta)/n} + (3c_1 + 4\alpha M) \ln(2/\delta)/(3\alpha n)$
$\le \phi(w, S_n) + 5\alpha h_0(w) + \epsilon' + 5r_0 + \sqrt{2c_0^2 \ln(2/\delta)/n} + (3c_1 + 4\alpha M) \ln(2/\delta)/(3\alpha n).$

第一个不等式使用了定理 6.41。第二个不等式使用了 (6.1)。通过对两个不等式取并集界，我们得到以至少 $1 - \delta$ 的概率：

$(1 - 5\alpha) \phi(\hat w, \mathcal{D}) \le [(1 + 0.5\alpha) \phi(w, \mathcal{D}) + 5\alpha h_0(w)] + \epsilon' + 5 \bar r_n^{h'}(\alpha, \mathcal{G}, \mathcal{D}) + 5\alpha[\phi(w, \mathcal{D}) + h_0(w)] + 7 \sqrt{2c_0^2 \ln(2/\delta)/n} + (7c_1 + 10\alpha M) \ln(2/\delta)/(\alpha n),$

其中我们使用了 $\ln(2/\delta) \ge 1$ 来简化结果。通过在右端对 $w \in \Omega$ 取下确界，我们得到第一个界。利用命题 6.40，我们得到

$5 \bar r_n^{h'}(\alpha, \mathcal{G}, \mathcal{D}) \le 10 e_n^{0.5\alpha h'}(\mathcal{G}, \mathcal{D}) + 5\alpha[\phi(w, \mathcal{D}) + h_0(w)].$
将其代入前一个不等式，并在右端对 $w \in \Omega$ 取下确界，我们得到第二个界。

我们对推论 6.44 有以下解释。

## 例 6.45
在推论 6.44 中，我们取 $L_*(x,y)=L(f(w_*,x),y)$ 对某个 $w_*\in\Omega$，并假设方差条件以 $c_0=0$ 成立。收敛速率由 $\bar r_n^h(\alpha,\mathcal G,\mathcal D)$ 决定，其中 $h(w)=\phi(w,\mathcal D)$（即推论 6.44 中 $h_0(w)=0$）和常数 $\alpha=0.1$。

$\mathbb E_{Z\sim\mathcal D}L(f(\hat w,X),Y)\le\mathbb E_{Z\sim\mathcal D}L(f(w_*,X),Y)+O\!\left(\epsilon'+\bar r_n^h(0.1,\mathcal G,\mathcal D)+\frac{(c_1+M)\ln(1/\delta)}{n}\right)$。

由于例 3.18 意味着最小二乘回归满足方差条件，该界对最小二乘回归成立。

以下结果表明速率函数可以从 Rademacher 复杂度的均匀上界得到。

## 命题 6.46
考虑函数类 $\mathcal G=\{\phi(w,z):w\in\Omega\}$ 且 $h(w)=\phi(w,\mathcal D)$ 且 $\inf_{w\in\Omega}h(w)=0$。假设 $|\phi(\cdot)|\le M$ 且方差条件 (3.14) 以 $c_0=0$ 成立。假设对任意 $b>0$，我们有

$\displaystyle\sup_{\mathcal S_n}R\!\left(\left\{\phi(w,\cdot):\frac1n\sum_{i=1}^n\phi(w,Z_i)^2\le b\right\},\mathcal S_n\right)\le r_n(b)$,
其中 $r_n(b)$ 是 $b$ 的连续凹函数。令 $\alpha\le0.5c_1/M$ 且
$\displaystyle b_0=\sup\{b>0:b\le(4c_1/\alpha)r_n(b)\}$,
则 $\bar r_n^h(\alpha,\mathcal G,\mathcal D)\le0.5\alpha b_0/c_1$。

### 证明
考虑任意 $b'_0>b_0$ 并令

$\displaystyle\mathcal G_0=\{\phi(w,\cdot):\phi(w,\mathcal D)\le0.5b'_0/c_1\}$,
并定义
$\displaystyle\hat b(\mathcal S_n)=\sup_{g\in\mathcal G_0}\frac1n\sum_{i=1}^n g(Z_i)^2$。

我们有
$R(\mathcal G_0,\mathcal S_n)\le r_n(\hat b(\mathcal S_n)),\quad R(-\mathcal G_0^2,\mathcal S_n)\le2Mr_n(\hat b(\mathcal S_n)).\tag{6.8}$

第一个不等式使用了 $r_n$ 的定义和 $\hat b$ 的定义。第二个不等式使用了定理 6.28 和 $|\phi(w_1,z)^2-\phi(w_2,z)^2|\le2M|\phi(w_1,z)-\phi(w_2,z)|$。

令 $\tilde b=\mathbb E_{\mathcal S_n}\hat b(\mathcal S_n)$，则我们有
$\tilde b=\mathbb E_{\mathcal S_n}\hat b(\mathcal S_n)\le\epsilon_n(-\mathcal G_0^2,\mathcal D)+0.5b'_0\le2R_n(-\mathcal G_0^2,\mathcal D)+0.5b'_0\le4M\mathbb E_{\mathcal S_n}r_n(\hat b(\mathcal S_n))+0.5b'_0\le(2c_1/\alpha)r_n(\tilde b)+0.5b'_0$。
