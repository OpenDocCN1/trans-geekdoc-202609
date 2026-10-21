
然后，我们可以基于状态变量 $x_t$ 的转移密度以及存在测量误差的收益率对应的横截面误差项 $u_t^m$，来表达联合对数似然函数：

$$\log(LG(\theta)) = \sum_{t=2}^{T} -\log|\det(J)| + \log f_x(x_t^o, x_t^u|x_{t-1}^o, x_{t-1}^u) + \log f_{u^m}(u_t^m)$$ $$= -(T-1)\log|\det(J)| - (T-1)\frac{1}{2}\log(\det(\Sigma\Sigma^T))$$ $$- \frac{1}{2}\sum_{t=2}^{T} (x_t - \mu - \Phi x_{t-1})^T (\Sigma\Sigma^T)^{-1} (x_t - \mu - \Phi x_{t-1})$$ $$- \frac{T-1}{2}\log\sum_{i=1}^{4}\sigma_i^2 - \frac{1}{2}\sum_{t=2}^{T}\sum_{i=1}^{4}\frac{(u_{t,i}^m)^2}{\sigma_i^2}. \qquad (61.17)$$

在这个表达式中，$\sigma_i^2$ 是第 $i$ 个测量误差项的方差，它适用于给定的参数向量 $\theta = (\mu, \Phi, \Sigma, \delta_0, \delta_1, \lambda_0, \lambda_1)$。需要估计的总参数个数（包括测量误差项）为31个（$\Phi$ 有6个，$\delta_1$ 有3个，$\lambda_0$ 有5个，$\lambda_1$ 有13个，$\sigma_i^2$ 有4个）。其余参数则如前几个步骤所述，通过普通最小二乘回归进行估计。我们使用Ang和Piazzesi（2003）论文第765页表6中给出的参数作为初始条件，进而最大化上述对数似然函数并选择上文给出的参数向量 $\theta$。我们之所以使用这些参数作为初始条件，是因为作者指出，由于其模型的复杂性，他们设计了一种非常特殊的算法程序来估计该模型，并通过几轮迭代加以实施。模型使用美国数据拟合出的期限结构动态如图61.1所示。由于我们使用前11个月的数据来构建VAR关系中的滞后项，我们的拟合数据从2000年12月开始。

## 61.2.2.2 Joslin、Singleton和Zhu（2011）的模型

在高斯设定下，JSZ提出了PCDTSM的一种规范化，其中定价因子被取为由主成分分析（PCA）获得的权重构成的收益率组合。为了概述其规范化的构建过程，我们先给出潜在因子 $x_t \in R^N$ 的如下离散时间刻画：

$$\Delta x_t = \kappa_{0x}^{\mathbb{P}} + \kappa_{1x}^{\mathbb{P}} x_{t-1} + \Sigma_x \epsilon_t^{\mathbb{P}}, \qquad (61.18)$$

$$\Delta x_t=\kappa_{0x}^{Q}+\kappa_{1x}^{Q}x_{t-1}+\Sigma_x\epsilon_t^{Q},$$

$$r_t=\rho_{0x}+\rho_{1x}x_t.$$

在方程（61.18）—（61.20）中，$r_t$ 是一期即期利率，$\Sigma_x\Sigma_x^T$ 是 $x_t$ 的条件协方差矩阵，且 $\epsilon_t\sim N(0,I_N)$。基于这一刻画，到期期限为 $m$ 的零息票收益率的价格可以表示为

$$D_{t,m}=E_t^Q\left[e^{-\sum_{i=0}^{m-1}r_{t+i}}\right]=e^{A_m+B_mx_t}.$$

对方程（61.21）取自然对数，可得如下零息票收益率的表达式：

$$y_t=A_m+B_mx_t.$$

在方程（61.22）中，$(A_m,B_m)$ 满足著名的Riccati差分方程

$$A_{m+1}-A_m=\kappa_0^{Q\prime}B_m+\frac{1}{2}B_m^{\prime}H_0B_m-\rho_0,$$

$$B_{m+1}-B_m=\kappa_1^{Q\prime}B_m-\rho_1,$$

初始条件为 $A_0=0$ 和 $B_0=0$，且相应债券收益率的载荷为 $a_m=-A_m/m$ 和 $b_m=-B_m/m$⁴。

⁴JSZ指出，尽管他们的所有结果都是在离散时间下给出的，但丝毫不失一般性，其所有结果也适用于连续时间模型。关于Riccati常微分方程，由于模型无论以连续时间还是离散时间估计，其结构都是相似的，因此我们可以展示如何在连续时间下得到Riccati常微分方程，并说明它如何与离散情形对应。接下来的步骤在很大程度上沿用Duffee和Kan（1996）、Fisher和Gilles（1996）以及Piazzesi（2010），因此我们建议读者参阅这些论文以了解更多信息。我们从仿射期限结构模型这一类模型开始，例如JSZ，这类模型的债券价格具有以下形式：

$$P(x,\tau)=\exp(A(\tau)+B(\tau)^Tx).$$

在上面的表达式中，A和B是定义债券价格与状态变量 $x$（例如主成分）之间关系的系数。在这个脚注中，我们解释如何获得A和B以用于估计仿射期限结构模型。为了得到状态因子系数，我们注意到，根据无套利条件，短期利率R(x)应等于瞬时债券回报 $\frac{dP}{P}$。因此，通过伊藤引理，我们推导出瞬时债券回报的过程，为此需要以下导数：

$$P_\tau(x,\tau)=\frac{\partial P(x,\tau)}{\partial\tau},\quad P_x(x,\tau)=\begin{bmatrix}\frac{\partial P(x,\tau)}{\partial x_1}\\\vdots\\\frac{\partial P(x,\tau)}{\partial x_d}\end{bmatrix},\qquad P_{xx}(x,\tau)=\begin{bmatrix}\frac{\partial^2P(x,\tau)}{\partial x_1^2}&\cdots&\frac{\partial^2P(x,\tau)}{\partial x_1\partial x_d}\\\vdots&\ddots&\vdots\\\frac{\partial^2P(x,\tau)}{\partial x_d\partial x_1}&\cdots&\frac{\partial^2P(x,\tau)}{\partial x_d^2}\end{bmatrix}.$$

用于定价的参数为

$$\Theta_x^{\mathbb{Q}} = (\kappa_0^{\mathbb{Q}}, \kappa_1^{\mathbb{Q}}, \Sigma_x, \rho_0, \rho_1).$$

于是，

$$P_\tau(x,\tau)=P(x,\tau)\bigl(A'(\tau)+B'(\tau)^T x\bigr)$$

$$\frac{P_\tau(x,\tau)}{P(x,\tau)}=A'(\tau)+B'(\tau)^T x$$

$$P_x(x,\tau)=P(x,\tau)B(\tau)$$

$$\frac{P_x(x,\tau)}{P(x,\tau)}=B(\tau)$$

$$P_{xx}(x,\tau)=P(x,\tau)B(\tau)B(\tau)^T$$

$$\frac{P_{xx}(x,\tau)}{P(x,\tau)}=B(\tau)B(\tau)^T.$$

因此，对于过程 $dx_t = \mu_x(x_t)dt + \sigma_x(x_t)^T dW_t$

$$\frac{dP}{P}=\mu_x^T \frac{P_x(x,\tau)}{P(x,\tau)}+\frac{1}{2}tr\left[\frac{P_{xx}(x,\tau)}{P(x,\tau)}\sigma_x^T\sigma_x\right]-\frac{P_\tau(x,\tau)}{P(x,\tau)}$$ 
$$=R(x)\quad\text{(absence of arbitrage)}.$$

将上述导数代入该表达式，可得

$$\mu_x^T B(\tau)+\frac{1}{2}[B(\tau)^T\sigma_x\sigma_x^T B(\tau)]-A'(\tau)-B'(\tau)^T x=R(x).$$

对于高斯动态期限结构模型的JSZ规范化，令 $H_0=\sigma_x^T\sigma_x$、$R(x)=\rho_0+\rho_1 x$ 以及 $\mu_x=\kappa_0^{Q^T}+\kappa_1^{Q^T}x$，则

$$(\kappa_0^{Q^T}+\kappa_1^{Q^T}x)B(\tau)+\frac{1}{2}[B(\tau)^T H_0 B(\tau)]-A'(\tau)-B'(\tau)^T x=\rho_0+\rho_1 x.$$

整理 $x$ 的项以及常数项，并注意到这两项都必须恒为零，可得

$$\kappa_0^{Q^T} B(\tau)+\frac{1}{2}[B(\tau)^T H_0 B(\tau)]-A'(\tau)-\rho_0=0$$

$$(\kappa_1^{\mathbb{Q}^T} B(\tau))x-\rho_1 x-B'(\tau)^T x=0.$$ 

因此，

$$A'(\tau)=\kappa_0^{Q^T} B(\tau)+\frac{1}{2}[B(\tau)^T H_0 B(\tau)]-\rho_0.$$ 

等价地，对于离散时间，并且不失一般性地对时期 $m$，

$$A_{m+1}-A_m=\kappa_0^{Q^T} B_m+\frac{1}{2}[B_m^T H_0 B_m]-\rho_0.$$ 

并且，

$$B_{m+1}-B_m=\kappa_1^{Q^T} B_m-\rho_1.$$

我们可以对方程（61.18）—（61.20）给定的系统施以不变变换（例如，参见Dai和Singleton，2000；Joslin、Singleton和Zhu，2011a），用从主成分分析（PCA）应用中获得权重构造的收益率组合PC_t（我们将在下文定义它）来替代原始风险因子，并且PC_t的Q分布（风险中性）可以完全由Θ_PC^Q = (κ_∞^Q, λ^Q, Σ_PC)刻画。P分布（历史分布）的参数为(κ_0PC^P, κ_1PC^P, Σ_PC)。我们可以将这一系统写为：

ΔPC_t = κ_0PC^P + κ_1PC^P PC_{t-1} + Σ_PC ε_t^P. (61.25)
ΔPC_t = κ_0PC^Q + κ_1PC^Q PC_{t-1} + Σ_PC ε_t^Q. (61.26)
r_t = ρ_0PC + ρ_1PC PC_t. (61.27)

在方程（61.25）—（61.27）中，由于不变变换，(κ_0PC^Q, κ_1PC^Q, ρ_0PC, ρ_1PC) 是 (κ_∞^Q, λ^Q, Σ_PC) 的解析（即闭式）函数。如果我们定义 PC_t = w y_t，那么利用方程（61.22），可得

PC_t = w A_m + w B_m x_t. (61.28)

我们可以通过求解方程（11）来用PC_t表示它：

w B_m x_t = PC_t - w A_m
x_t = (w B_m)^{-1} (PC_t - w A_m).

对方程（61.28）两边取差分，代入方程（61.19），并化简，得

ΔPC_t = w B_m Δx_t
= w B_m (κ_0x^Q + κ_1x^Q x_{t-1} + Σ_x ε_t^Q)
= w B_m (κ_0x^Q + κ_1x^Q ((w B_m)^{-1} (PC_{t-1} - w A_m)) + Σ_x ε_t^Q)
= w B_m κ_0x^Q - w B_m κ_1x^Q (w B_m)^{-1} w A_m + w B_m κ_1x^Q (w B_m)^{-1} PC_{t-1} + w B_m Σ_x ε_t^Q
= w B_m (κ_0x^Q - κ_1x^Q (w B_m)^{-1} w A_m) + w B_m κ_1x^Q (w B_m)^{-1} PC_{t-1} + w B_m Σ_x ε_t^Q
= -w B_m κ_1x^Q (w B_m)^{-1} w A_m + w B_m κ_1x^Q (w B_m)^{-1} PC_{t-1} + w B_m Σ_x ε_t^Q
= κ_0PC^Q + κ_1PC^Q PC_{t-1} + Σ_PC ε_t^Q.

最后一行即方程（61.26）所给出的内容，且在该表达式中，κ_1PC^Q = w B_m κ_1x^Q (w B_m)^{-1}，κ_0PC^Q = -w B_m κ_1x^Q (w B_m)^{-1} w A_m = -κ_1PC^Q w A_m，且Σ_PC = w B_m Σ_x。JSZ在他们的模型中将κ_0x^Q = 0设为0。
