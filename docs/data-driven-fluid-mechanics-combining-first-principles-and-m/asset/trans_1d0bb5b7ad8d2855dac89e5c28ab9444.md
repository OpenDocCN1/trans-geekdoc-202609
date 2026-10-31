
恢复其单位范数（能量）。我们在第 8 章会回到这一性质。在转向连续信号之前，值得介绍另一个与狄拉克函数相关的重要信号，即 Heaviside 阶跃函数。其定义为

$$u_S[k - l] = \begin{cases} 1 & \text{if } k \ge l \\ 0 & \text{if } k < l \end{cases} \quad \text{that is } \longrightarrow u_S[k - l] = \sum_{r=-\infty}^{k} \delta[r - l]. \tag{4.7}$$

两个移位阶跃函数之差产生一个盒函数 $u_{Ba,p}$，其在范围 $k = [a, b-1]$ 内为单位值，在外部为零。相差一个步长的两个阶跃函数之差是一个狄拉克函数，即 $\delta[k - l] = u_S[k - l] - u_S[k - l - 1]$。在离散情形下，这等价于微分。因此，*狄拉克函数是阶跃函数的导数*，而式 (4.7) 中的求和表明 *阶跃函数是狄拉克函数的积分*。读者应以关于离散信号某些显著特征的练习结束本小节。

### 练习 1：连续与离散

考虑连续信号 $y(t) = e^{-0.2t} \cos(2\pi t)$，其中 $t$ 以秒为单位。假设信号以 $f = 100\text{Hz}$ 采样，且从 $t = 0$ 开始采集 $n_t = 320$ 个点，所得到的离散信号是什么？绘制该信号并对其与连续信号的联系进行评述。

## 4.3.2 连续信号

将先前引入的概念推广到连续信号会带来若干复杂性，其详细解决超出了本章范围。有兴趣的读者可参考 Kaiser (2010) 以获得温和的介绍。主要困难在于需要定义一个内积空间，既能对函数推广 (4.3)，又能允许以脉冲为基，即除一点外处处为零的函数。这一推广由希尔伯特空间提供，其中两个复值函数 $a(t), b(t) \in \mathbb{C}$ 的内积为

$$\langle a, b \rangle = \int_{-\infty}^{\infty} a(t) \overline{b(t)}\; dt. \tag{4.8}$$

式 (4.5)–(4.6) 中的能量（范数）、相关性和投影概念可利用式 (4.8) 中的内积⁸ 推广到连续信号。式 (4.4) 的推广需要定义具有与 $\delta[k]$ 相同性质的连续狄拉克函数 $\delta(t)$：它仅在给定时刻非零且绝对可积。它可以构造为在无穷小时间间隔上具有单位面积的适当选择函数的极限。一个例子是归一化高斯函数 $G(t, \mu, \sigma)$，其积分无论标准差 $\sigma$ 如何均为单位值：

$$\int_{-\infty}^{\infty} G(t, \mu = 0, \sigma)\, dt = \frac{1}{\sqrt{2\pi\sigma^2}} \int_{-\infty}^{\infty} e^{\frac{-t^2}{2\sigma^2}} dt = 1. \tag{4.9}$$

⁸ 注意对于连续函数使用大写表示范数，即 $||a(t)||_2 = \sqrt{\langle a, a \rangle}$，其中内积见式 (4.8)，是函数 $a(t)$ 的 $L^2$ 范数。

当 σ → 0 时，该函数变得越来越窄且越高，在仍保持单位面积的同时在 t = 0 处变得无穷大，在其他处为零。这就是连续狄拉克函数的定义，其平移形式为

$$\delta(t - \tau) = \begin{cases} 0 & \text{if } t \neq \tau, \\ \infty & \text{if } t = \tau \end{cases} \quad \text{and} \quad \int_{-\infty}^{+\infty} \delta(t - \tau) dt = 1. \tag{4.10}$$

该函数不是普通函数，因为其积分带来若干技术困难。不涉及测度与分布理论的细节（Richards & Youn 1990），我们将接受其为广义函数，足以满足我们采样连续信号的目的。根据式 (4.10) 的定义，容易推导出筛选（采样）性质：

$$y(t) = \langle y(\tau),\delta(t - \tau)\rangle = \int_{-\infty}^{\infty} y(\tau)\delta(t - \tau)d\tau = \int_{-\infty}^{\infty} y(t)\delta(t - \tau)d\tau$$
$$= y(t) \int_{-\infty}^{\infty} \delta(t - \tau)d\tau = y(t). \tag{4.11}$$

积分中 y(τ) = y(t) 的等价性源于乘积 y(τ)δ(t − τ) 除 t 外处处为零；然后在最后一步，可以将 y(t) 移出积分，因为它与积分域 τ 无关。

与离散情形类似，值得引入单位阶跃函数及其与狄拉克函数的联系：

$$u_S(t - t_0) = \begin{cases} 1 & \text{if } t > t_0, \\ 0 & \text{if } t < t_0 \end{cases} \quad \text{that is,} \longrightarrow u_S(t - t_0) = \int_{-\infty}^{t} \delta(\tau - t_0)d\tau. \tag{4.12}$$

注意阶跃函数在 t = t0 处未定义。该定义是式 (4.7) 的连续类比。为了证明狄拉克函数是阶跃函数的导数，我们必须引入广义导数的概念。对于连续信号 u(t)，记 u′ 和 u(n) 为其一阶和 n 阶导数，利用适当的测试函数 ξ(t) 分部积分得到

$$\int_{-\infty}^{\infty} \xi(t) u^{(n)}(t) dt = (-1)^n \int_{-\infty}^{\infty} \xi^{(n)} u(t) dt, \tag{4.13}$$

$$\int_{-\infty}^{\infty} \xi(t) u'_S(t - t_0) dt = - \int_{-\infty}^{\infty} \xi'(t) u_S(t - t_0) dt = - \int_{t_0}^{\infty} \xi'(t) dt$$
$$= \xi(t_0) - \xi(\infty) = \xi(t_0) = \int_{-\infty}^{\infty} \xi(t) \delta(t - t_0) dt. \tag{4.14}$$

第一个等式直接由式 (4.13) 得到；第二个等式源于 uS(t−t0) 在 t < t0 时为零。积分后使用狄拉克函数的筛选性质 (4.11)，结果由最后一步与第一步的等价性得到，其成立基于 ξ(t) 是任意的这一事实。

## 4.4 卷积与特征函数

在 *线性系统* 中，输入-输出关系满足 *齐次性* 和 *叠加* 条件。对于连续 ($\mathcal{S}_c\{u(t)\}=y(t)$) 和离散 ($\mathcal{S}_d\{u[k]\}=y[k]$) 系统，它们为：

*齐次性：*

$$\mathcal{S}_c\{a u(t)\}=a\mathcal{S}_c\{u(t)\}=a y(t)\quad\text{for all }a\in\mathbb{C},$$
$$\mathcal{S}_d\{a u[k]\}=a\mathcal{S}_d\{u[k]\}=a y[k]\quad\text{for all }a\in\mathbb{C}.\tag{4.15}$$

*叠加：*

$$\mathcal{S}_c\left\{\int_{-\infty}^{\infty}u(t)\right\}dt=\int_{-\infty}^{\infty}\mathcal{S}_c\{u(t)\}dt=\int_{-\infty}^{\infty}y(t)dt,$$
$$\mathcal{S}_d\left\{\sum_{n=1}^{N}u_n[k]\right\}=\sum_{n=1}^{N}\mathcal{S}_d\{u_n[k]\}=\sum_{n=1}^{N}y_n[k],\tag{4.16}$$

其中我们对离散情形考虑了 $N$ 个输入的有限求和，对连续情形考虑了无穷多个无限接近的输入的求和。结合这些性质，我们看到输入的线性组合导致输出的相同线性组合：

$$\mathcal{S}_c\left\{\int_{-\infty}^{\infty}a(\tau)u(t,\tau)\right\}d\tau=\int_{-\infty}^{\infty}a(\tau)\mathcal{S}_c\{u(t,\tau)\}d\tau=\int_{-\infty}^{\infty}a(\tau)y(t,\tau)d\tau,$$
$$\mathcal{S}_d\left\{\sum_{n=1}^{N}a_n u_n[k]\right\}=\sum_{n=1}^{N}a_n \mathcal{S}_d\{u_n[k]\}=\sum_{n=1}^{N}a_n y_n[k].\tag{4.17}$$

如果系统对输入的响应不随时间（或空间）变化，则系统是 *时不变* 的（或 *平移不变* 的，如果时间被空间替代），即

if $\mathcal{S}_c\{u(t)\}=y(t)$ then $\mathcal{S}_c\{u(t-t_0)\}=y(t-t_0)$ for all $t_0\in\mathbb{R}$,
if $\mathcal{S}_d\{u[k]\}=y[k]$ then $\mathcal{S}_d\{u[k-k_0]\}=y[k-k_0]$ for all $k_0\in\mathbb{Z}.\tag{4.18}$

系统若同时线性 *且* 时/平移不变，则为线性时/平移不变系统（LTI）。这两个性质结合式 (4.10)–(4.11) 中的信号表示，使得 LTI 系统的分析特别简单：对 *任意* 输入的响应可完全由对 *单一脉冲* 的响应表征。

将 $h(t)=\mathcal{S}_c\{\delta(t)\}$ 定义为连续系统的脉冲响应，对任意输入的响应为
