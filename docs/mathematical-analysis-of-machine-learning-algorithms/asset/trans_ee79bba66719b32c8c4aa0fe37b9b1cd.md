

$\mathbb{E}e^{\lambda(X_1-\mu)}=\int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi}\sigma}e^{\lambda x}e^{-x^2/2\sigma^2}\,dx$

$\qquad=\int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi}}e^{\lambda^2\sigma^2/2}e^{-(x/\sigma-\lambda\sigma)^2/2}\,dx/\sigma=e^{\lambda^2\sigma^2/2}$.

因此，

$I_{X_1}(\mu+\epsilon)=\sup_{\lambda>0}[\lambda\epsilon-\ln\mathbb{E}e^{\lambda(X_1-\mu)}]=\sup_{\lambda>0}\left[\lambda\epsilon-\frac{\lambda^2\sigma^2}{2}\right]=\frac{\epsilon^2}{2\sigma^2}$，

其中最优的$\lambda$在$\lambda=\epsilon/\sigma^2$处取得。因此

$\Pr(\bar{X}_n\geq\mu+\epsilon)\leq\exp[-nI_{X_1}(\mu+\epsilon)]=\exp\left[-\frac{n\epsilon^2}{2\sigma^2}\right]$.

这导出了与定理2.1相同的概率界（相差一个常数因子）。

这个高斯例子连同定理2.1表明，由定理2.5导出的指数不等式是渐近紧的。该结果可以推广到一般随机变量的大偏差不等式。特别地，我们有如下定理。

## 定理2.7
*对于所有$\epsilon'>\epsilon>0$，*

$\displaystyle \lim_{n\to\infty}\frac{1}{n}\ln\Pr(\bar{X}_n\geq\mu+\epsilon)\geq-I_{X_1}(\mu+\epsilon')$.

*类似地，*

$\displaystyle \lim_{n\to\infty}\frac{1}{n}\ln\Pr(\bar{X}_n\leq\mu-\epsilon)\geq-I_{X_1}(\mu-\epsilon')$.

**证明**  我们只需证明第一个不等式。将$\Pr(X_i\leq x)$视为$x$的函数，并定义一个随机变量$X_i'$，其在$x$处的密度为

$\displaystyle d\Pr(X_i'\leq x)=e^{\lambda x-\Lambda_{X_1}(\lambda)}d\Pr(X_i\leq x)$.

这一选取意味着

$\displaystyle \frac{d}{d\lambda}\Lambda_{X_1}(\lambda)=\frac{\int xe^{\lambda x}\,d\Pr(X_1\leq x)}{\int e^{\lambda x}\,d\Pr(X_1\leq x)}=\mathbb{E}_{X_1'}X_1'$.

我们现在取$\lambda$使得

$\displaystyle \lambda=\arg\max_{\lambda'>0}[\lambda'(\mu+\epsilon')-\Lambda_{X_1}(\lambda')]$.

令导数为零，我们得到

$\displaystyle \mathbb{E}_{X_1'}X_1'=\frac{d}{d\lambda}\Lambda_{X_1}(\lambda)=\mu+\epsilon', \tag{2.3}$

$\displaystyle -\lambda(\mu+\epsilon')+\Lambda(\lambda)=-I(\mu+\epsilon'). \tag{2.4}$

设$\bar{X}_n' = n^{-1}\sum_{i=1}^n X_i'$。然后，根据大数定律，我们知道对于$\epsilon'' > \epsilon'$，由(2.3)可得

$$\lim_{n\to\infty} \Pr(\bar{X}_n' - \mu \in [\epsilon, \epsilon'']) = 1.\tag{2.5}$$

由于$(X_1',\dots,X_n')$的联合密度满足

$$e^{-\lambda\sum_{i=1}^n x_i + n\Lambda_{X_1}(\lambda)} \prod_i d\Pr(X_i' \le x_i) = \prod_i d\Pr(X_i \le x_i),\tag{2.6}$$

使用$\mathbb{1}(\cdot)$表示集合的指示函数，我们得到

$$\begin{aligned}
\Pr(\bar{X}_n \ge \mu + \epsilon) &\ge \Pr(\bar{X}_n - \mu \in [\epsilon, \epsilon''])\\
&= \mathbb{E}_{X_1,\dots,X_n} \mathbb{1}(\bar{X}_n - \mu \in [\epsilon, \epsilon''])\\
&= \mathbb{E}_{X_1',\dots,X_n'} e^{-\lambda n\bar{X}_n' + n\Lambda(\lambda)} \mathbb{1}(\bar{X}_n' - \mu \in [\epsilon, \epsilon''])\\
&\ge e^{-\lambda n(\mu + \epsilon'') + n\Lambda(\lambda)} \Pr(\bar{X}_n' - \mu \in [\epsilon, \epsilon'']).
\end{aligned}$$

第一个等式使用了$\Pr(\cdot)$的定义。第二个等式使用了(2.6)。最后一个不等式使用了马尔可夫不等式。现在取对数并除以$n$，我们得到

$$\frac{1}{n}\ln\Pr(\bar{X}_n \ge \mu + \epsilon)\tag{2.7}$$
$$\ge -\lambda(\mu + \epsilon'') + \Lambda(\lambda) + \frac{1}{n}\ln\Pr(\bar{X}_n' - \mu \in [\epsilon, \epsilon''])$$
$$= -I(\mu + \epsilon') - \lambda(\epsilon'' - \epsilon') + \frac{1}{n}\ln\Pr(\bar{X}_n' - \mu \in [\epsilon, \epsilon'']).\tag{2.8}$$

该等式使用了(2.4)。现在，通过令$n \to \infty$，应用(2.5)，并令$\epsilon'' \to \epsilon'$使得$\lambda(\epsilon'' - \epsilon') \to 0$（这成立是因为$\lambda$仅依赖于$\epsilon'$），我们得到所需的界。

定理2.5与定理2.7的结合表明，大偏差尾部概率由速率函数决定。该结果被称为克拉默定理（Cramér, 1938; Deuschel and Stroock, 2001）。

对于特定情形，可以在$\epsilon' = \epsilon + 2\sqrt{\operatorname{Var}(X_1)/n}$和$\epsilon'' = \epsilon + 4\sqrt{\operatorname{Var}(X_1)/n}$时，对(2.8)中的$\Pr(\bar{X}_n' - \mu \in [\epsilon, \epsilon''])$进行有限$n$的估计。利用切比雪夫不等式，我们预期$\Pr(\bar{X}_n' - \mu \in [\epsilon, \epsilon''])$有一个常数下界。这意味着当$n \to \infty$时，定理2.5的指数尾部不等式在偏差$\epsilon$方面通常至多宽松$O(\sqrt{\operatorname{Var}(X_1)/n})$。具体计算将在第2.5节针对有界随机变量给出。

在考察随机变量的具体例子之前，我们先陈述随机变量对数矩生成函数的如下性质，这有助于理解其行为。证明留作练习。

## 命题2.8
*给定一个具有有限方差的随机变量，我们有*

$$\left.\Lambda_X(\lambda)\right|_{\lambda=0}=0,\qquad \left.\frac{d\Lambda_X(\lambda)}{d\lambda}\right|_{\lambda=0}=\mathbb{E}[X],\qquad \left.\frac{d^2\Lambda_X(\lambda)}{d\lambda^2}\right|_{\lambda=0}=\operatorname{Var}[X].$$

在大偏差界的应用中，我们主要关注偏差$\epsilon$接近零的情形。如例2.6所示，我们应选择的最优$\lambda$为$\lambda = O(\epsilon) \approx 0$。因此，自然地考虑对数矩生成函数在$\lambda = 0$附近的泰勒展开。命题2.8表明泰勒展开的前几项为

$$\Lambda_X(\lambda) = \lambda\mu + \frac{\lambda^2}{2}\operatorname{Var}[X] + o(\lambda^2),$$

其中$\mu = \mathbb{E}[X]$。前两项与例2.6中正态随机变量的对应项一致。当$\epsilon > 0$较小时，为了得到速率函数

$$I_X(\mu + \epsilon) = \sup_{\lambda>0} \left[ \lambda(\mu + \epsilon) - \lambda\mu - \frac{\lambda^2}{2}\operatorname{Var}[X] - o(\lambda^2) \right],$$

我们应取最优$\lambda$近似为$\lambda \approx \epsilon/\operatorname{Var}[X]$，相应的速率函数变为

$$I_X(\mu + \epsilon) \approx \frac{\epsilon^2}{2\operatorname{Var}[X]} + o(\epsilon^2).$$

对于特定形式的对数矩生成函数，可以获得更精确的速率函数界。特别地，以下一般估计在许多应用中很有用。这是我们在本章中将始终使用的估计。

## 引理2.9
*考虑随机变量$X$满足$\mathbb{E}[X] = \mu$。假设存在$\alpha > 0$和$\beta \ge 0$，使得对$\lambda \in [0,\beta^{-1})$，*

$$\Lambda_X(\lambda) \le \lambda\mu + \frac{\alpha\lambda^2}{2(1-\beta\lambda)}, \tag{2.9}$$

*则对$\epsilon > 0$，*

$$-I_X(\mu + \epsilon) \le -\frac{\epsilon^2}{2(\alpha + \beta\epsilon)},$$ $$-I_X\left(\mu + \epsilon + \frac{\beta\epsilon^2}{2\alpha}\right) \le -\frac{\epsilon^2}{2\alpha}.$$

*证明*  注意 $$-I_X(\mu + \epsilon) \le \inf_{\lambda>0} \left[ -\lambda(\mu + \epsilon) + \lambda\mu + \frac{\alpha\lambda^2}{2(1-\beta\lambda)} \right].$$ 我们可以取$\lambda$为$\bar\lambda = \epsilon/(\alpha + \beta\epsilon)$。这意味着$\alpha\bar\lambda/(1-\beta\bar\lambda) = \epsilon$。因此 $$-I_X(\mu + \epsilon) \le -\bar\lambda\epsilon + \frac{\alpha\bar\lambda^2}{2(1-\beta\bar\lambda)} = -\frac{\bar\lambda\epsilon}{2} = -\frac{\epsilon^2}{2(\alpha + \beta\epsilon)}.$$ 此外，用同样的$\bar\lambda$，我们有 $$-I_X\left(\mu + \epsilon + \frac{\beta}{2\alpha}\epsilon^2\right) \le -\bar\lambda\epsilon\left(1 + \frac{\beta}{2\alpha}\epsilon\right) + \frac{\alpha\bar\lambda^2}{2(1-\beta\bar\lambda)} = -\frac{\epsilon^2}{2\alpha}.$$

这就证明了第二个所需的界。

引理2.9蕴含如下一般性定理。

## 定理2.10
*如果$X_1$的对数矩生成函数对$\lambda > 0$满足(2.9)，则对所有$\epsilon > 0$，*

Pr(X̄ₙ ≥ μ + ε) ≤ exp[−nε² / 2(α + βε)].

*此外，对$t > 0$，我们有*

Pr(X̄ₙ ≥ μ + √(2αt/n) + βt/n) ≤ e⁻ᵗ.

*证明*  定理的第一个不等式由引理2.9的第一个不等式和定理2.5得出。定理的第二个不等式由引理2.9的第二个不等式和定理2.5得出，其中$\epsilon = \sqrt{2\alpha t/n}$。

## 2.4 次高斯随机变量

正态随机变量的对数矩生成函数关于$\lambda$是二次的。更一般地，我们可以将次高斯随机变量定义为其对数矩生成函数被关于$\lambda$的二次函数支配的随机变量。这类随机变量具有轻尾，这意味着它们的尾部概率不等式与高斯随机变量的相似。

## 定义2.11
次高斯随机变量$X$对所有$\lambda \in \mathbb{R}$具有二次对数矩生成函数：

ln E e^(λX) ≤ λμ + (λ²/2)b.  (2.10)

利用(2.10)，我们可以获得次高斯随机变量速率函数的上界，从而得到如下尾部不等式。

## 定理2.12
*如果$X_1$满足(2.10)中的次高斯条件，则对所有$t > 0$，*

Pr(X̄ₙ ≥ μ + √(2bt/n)) ≤ e⁻ᵗ,

Pr(X̄ₙ ≤ μ − √(2bt/n)) ≤ e⁻ᵗ.

*证明*  该结果由定理2.10取$\alpha = b$和$\beta = 0$得出。

次高斯随机变量的常见例子包括高斯随机变量和有界随机变量。

