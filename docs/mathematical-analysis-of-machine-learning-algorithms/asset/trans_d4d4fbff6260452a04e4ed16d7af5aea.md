
证明 注意通过在引理 2.20 中采用 Bennett 不等式的矩估计，我们得到

$$\frac{1}{\lambda}\ln\mathbb{E}_{Z_t^{(y)}}e^{-\lambda f(Z_t)}\le -\mathbb{E}_{Z_t^{(y)}}[f(Z_t)]+\lambda\phi(\lambda b)\mathrm{Var}_{Z_t^{(y)}}[f(Z_t)]$$ $$\le -\mathbb{E}_{Z_t^{(y)}}[f(Z_t)]+\lambda\phi(\lambda b)[c_0^2+c_1\mathbb{E}_{Z_t^{(y)}}[f(Z_t)]]$$

我们现在可以从定理 13.11 得到期望界。

## 示例 13.13

我们考虑示例 3.18 中的最小二乘回归，其中 $(x,y)=(Z^{(x)},Z^{(y)})$。在可实现情形下，方差条件以 $c_0=0$、$c_1=2M^2$ 和 $b=2M^2$ 满足。若取 $\lambda=0.2M^{-2}$，则 $\lambda c_1\phi(\lambda b)<0.5$。推论 13.12 表明以概率 $1-\delta$，对所有 $\phi\in\mathcal{G}$，

$$\sum_{i=1}^n\mathbb{E}_{Z_t^{(y)}}[\phi(Z_t)]\le 2\sum_{i=1}^n\phi(Z_t)+\inf_{\epsilon>0}\left[4n\epsilon+10M^2\ln\left(M(\epsilon,\mathcal{G},\|\cdot\|_\infty)/\delta\right)\right]$$

由于 $(f(x)-y)^2$ 关于 $f(x)$ 是 $2M$ Lipschitz 的，我们得到

$$\sum_{i=1}^n\mathbb{E}_{Z_t^{(y)}}[\phi(Z_t)]\le 2\sum_{i=1}^n\phi(Z_t)+\inf_{\epsilon>0}\left[8nM\epsilon+10M^2\ln\left(M(\epsilon,\mathcal{F},\|\cdot\|_\infty)/\delta\right)\right]$$

注意定理 13.11 的结果可通过使用 $L_\infty$ 覆盖的链式方法改进。与命题 4.20 类似，我们有以下结果（参见练习 13.4）。

## 命题 13.14

考虑有界函数类 $\mathcal{F}$，使得对所有 $f\in\mathcal{F}$ 都有 $|f(Z)|\le b$。则以概率 $1-\delta$，对所有 $f\in\mathcal{F}$，我们有

$$\frac{1}{n}\sum_{i=1}^n\mathbb{E}_{Z_i^{(y)}}[f(Z_i)]\le\frac{1}{n}\sum_{i=1}^n f(Z_i)+C\inf_{\epsilon_0>0}\left[\epsilon_0+\int_0^\infty\sqrt{\frac{\ln(M(\epsilon,\mathcal{F},\|\cdot\|_\infty))}{n}}d\epsilon\right]+b\sqrt{\frac{\ln(1/\delta)}{n}}$$ 其中 $C$ 为绝对常数。

## 定理 13.15

设 $\{(X_t,\epsilon_t)\}$ 为 $\mathcal{X}\times\mathbb{R}$ 中的滤波序列，使得 $\epsilon_t$ 为条件零均值次高斯噪声：对所有 $\lambda\in\mathbb{R}$，$\ln\mathbb{E}[e^{\lambda\epsilon_t}|X_t,\mathcal{S}_{t-1}]\le\frac{\lambda^2\sigma^2}{2}$

其中 $\mathcal{S}_{t-1}$ 表示历史数据。假设 $Y_t = f_*(X_t) + \epsilon_t$，其中 $f_*(x) \in \mathcal{F}: \mathcal{X} \to \mathbb{R}$。设 $\hat f_t$ 为某个 $\epsilon' > 0$ 的近似 ERM 解：

$$\left(\sum_{s=1}^{t}(\hat f_t(X_s)-Y_s)^2\right)^{1/2} \le \min_{f\in\mathcal{F}}\left(\sum_{s=1}^{t}(f(X_s)-Y_s)^2\right)^{1/2} + \sqrt{t}\epsilon' .$$

则以概率至少 $1 - \delta$，对所有 $t \ge 0$，

$$\sum_{s=1}^{t}(\hat f_t(X_t)-f_*(X_t))^2 \le \inf_{\epsilon>0}\Big[8t(\epsilon+\epsilon')(\sigma+2\epsilon+2\epsilon')+12\sigma^2\ln\frac{2N(\epsilon,\mathcal{F},\|\cdot\|_\infty)}{\delta}\Big].$$

证明 设 $\eta = \sigma^{-2}/4$，且对 $f \in \mathcal{F}$，令

$$\phi(f,Z_t)=[(f(X_t)-Y_t)^2-(f_*(X_t)-Y_t)^2].$$

设 $\mathcal{F}_\epsilon$ 为 $\mathcal{F}$ 的 $\epsilon \|\cdot\|_\infty$ 覆盖，成员数为 $N = N(\epsilon,\mathcal{F},\|\cdot\|_\infty)$。

给定任意 $f \in \mathcal{F}_\epsilon$，

$$\begin{aligned}
\ln \mathbb{E}_{Y_t|X_t,\mathcal{S}_{t-1}} \exp(-\eta\phi(f,Z_t)) &= -\eta(f(X_t)-f_*(X_t))^2 \\
&+ \ln \mathbb{E}_{Y_t|X_t,\mathcal{S}_{t-1}} \exp(-2\eta(f(X_t)-f_*(X_t))(f_*(X_t)-Y_t)) \\
&\le -\eta(f(X_t)-f_*(X_t))^2 + \frac{4\eta^2\sigma^2}{2}(f(X_t)-f_*(X_t))^2 \\
&= -\frac{(f(X_t)-f_*(X_t))^2}{8\sigma^2}.
\end{aligned}$$

该不等式使用了次高斯噪声假设。由定理 13.11 可知，以概率至少 $1 - \delta/2$，对所有 $f \in \mathcal{F}_\epsilon$ 和 $t \ge 0$，

$$\sum_{i=1}^{t} -\eta\phi(f,Z_i) \le -\sum_{i=1}^{t}\frac{(f(X_i)-f_*(X_i))^2}{8\sigma^2} + \ln(2N/\delta). \qquad (13.5)$$

使用练习 13.3，我们有以概率至少 $1 - \delta/2$，对所有 $t \ge 0$，

$$\underbrace{\sum_{i=1}^{t}(f_*(X_i)-Y_i)^2}_{A} \le 2t\sigma^2 + 3\sigma^2\ln(2/\delta). \qquad (13.6)$$

由此可知以概率至少 $1 - \delta$，对所有 $t \ge 0$ 和 $f \in \mathcal{F}_\epsilon$，$(13.5)$ 和 $(13.6)$ 同时成立。现在，设 $f \in \mathcal{F}_\epsilon$ 使得 $\|\hat f_t - f\|_\infty \le \epsilon$。这意味着

$$\sum_{i=1}^t [(f(X_i)-Y_i)^2 - (f_*(X_i)-Y_i)^2] \le \left( \sqrt{\sum_{i=1}^t (\hat f_t(X_i)-Y_i)^2 + \sqrt{t}\epsilon } \right)^2 - A$$
$$\le \left( \sqrt{A} + \sqrt{t}(\epsilon + \epsilon') \right)^2 - A$$
$$\stackrel{(a)}{\le} (\epsilon' + \epsilon)^2 t + 2\sqrt{t}(\epsilon' + \epsilon)\sigma \sqrt{2t + 3\ln(2/\delta)}$$
$$\le 4(\epsilon' + \epsilon)^2 t + 3\sigma t(\epsilon' + \epsilon) + \sigma^2 \ln(2/\delta). \tag{13.7}$$

在推导中，第一个不等式使用了对所有 $i$ 都有 $|f(X_i)-Y_i| \le |\hat f_t(X_i)-Y_i| + \epsilon$。第二个不等式使用了 $\hat f_t$ 为近似 ERM 的事实。$(a)$ 由 $(13.6)$ 得出。最后一个不等式使用了 $2a\sigma\sqrt{2b}+3c \le 3a\sigma\sqrt{b}+3a^2+\sigma^2 c$。我们由此得到

$$\left( \sum_{i=1}^t (\hat f(X_i)-f_*(X_i))^2 \right)^{1/2}$$
$$\le \sqrt{\epsilon t} + \left( \sum_{i=1}^t (f(X_i)-f_*(X_i))^2 \right)^{1/2} \quad \text{(triangle inequality)}$$
$$\le \sqrt{\epsilon^2 t} + \left( 8\sigma^2 \ln(2N/\delta) + 8\sigma^2 \sum_{i=1}^t \eta\phi(f,Z_i) \right)^{1/2} \quad \text{(from (13.5))}$$
$$= \sqrt{\epsilon^2 t} + \left( 8\sigma^2 \ln(2N/\delta) + 2 \sum_{i=1}^t [(f(X_i)-Y_i)^2 - (f_*(X_i)-Y_i)^2] \right)^{1/2}$$
$$\le \sqrt{\epsilon^2 t} + (10\sigma^2 \ln(2N/\delta) + 8t(\epsilon' + \epsilon)^2 + 6\sigma t(\epsilon' + \epsilon))^{1/2} \quad \text{(from (13.7))}$$
$$\le (12\sigma^2 \ln(2N/\delta) + 16t(\epsilon + \epsilon')^2 + 8\sigma t(\epsilon + \epsilon'))^{1/2},$$

其中最后一个不等式使用了 $\sqrt{a}+\sqrt{b} \le \sqrt{6a + 1.2b}$。这意味着该界。$\square$

## 13.4 序贯统计估计的极小极大分析

我们可以考虑对第 12.2 节中监督学习统计估计问题的推广，推广到序贯决策设定。

考虑一个一般的序贯估计问题，其中我们通过使用学习策略序列 $\pi_t \in \Pi$ 与环境交互，从环境中观察数据 $Z_t \in \mathcal{Z}$。在每个时间 $t$，观测历史为 $\mathcal{S}_{t-1} = [(Z_1,\pi_1),..., (Z_{t-1},\pi_{t-1})]$。基于历史，参与者（或学习算法），记为 $\hat q$，确定下一个可与环境交互的策略 $\pi_t \in \Pi$。基于策略 $\pi_t$，环境根据未知分布 $q(Z_t|\pi_t,\mathcal{S}_{t-1})$ 生成下一个观测 $Z_t \in \mathcal{Z}$。

在序贯决策文献中，符号 $\mathcal{A}$ 常用于表示学习算法的动作空间。我们将遵循这一惯例，因此将使用符号 $\hat q$ 表示学习算法。下面的定义概括了可实现情形下的序贯统计估计问题。

## **定义 13.16 (顺序统计估计)**

考虑环境分布族 $\mathcal P_Z$，其中每个 $q\in\mathcal P_Z$ 根据策略 $\pi_t$ 生成 $Z_t$ 的概率为 $q(Z_t\mid\pi_t,S_{t-1})$。同时考虑学习算法族，由 $\mathcal P_A$ 表示。每个学习算法 $\hat q\in\mathcal P_A$ 将历史 $S_{t-1}$ 决定性地映射到下一个策略 $\pi_t\in\Pi$，即 $\pi_t=\hat q(S_{t-1})$。给定 $q\in\mathcal P_Z$ 和 $\hat q\in\mathcal P_A$，数据生成概率完全确定为

$$p(S_n\mid\hat q,q)=\prod_{t=1}^{n}q\bigl(Z_t\mid\hat q(S_{t-1}),S_{t-1}\bigr).$$

在观察到某个 $n$ 的 $S_n$ 后，学习算法 $\hat q$ 确定分布 $\hat q(\theta\mid S_n)$，并根据 $\hat q(\theta\mid S_n)$ 抽取估计量 $\theta\in\Theta$。学习算法承受损失（也称为遗憾）$Q(\theta,q)$。$\theta$ 和 $S_n$ 的总体概率为

$$p(\theta,S_n\mid\hat q,q)=\hat q(\theta\mid S_n)\prod_{t=1}^{n}q\bigl(Z_t\mid\hat q(S_{t-1}),S_{t-1}\bigr).\tag{13.8}$$

注意，尽管定义 13.16 中的记号假设 $\pi_t$ 是 $S_{t-1}$ 的确定性函数，但它也可以包含随机化算法。在这种情况下，策略只是随机选择的分布。由于随机选择始终可以用一个关于随机选择的分布来刻画，而该分布是 $S_{t-1}$ 的确定性函数，当我们在后续章节中考虑 *随机策略* 时，应理解此类策略可由定义 13.16 处理。以下是一个示例。

## **示例 13.17 (在线学习 (非对抗))**

我们考虑参数空间 $\Omega$，在每个时间 $t$，学习算法根据 $\Omega$ 上的概率分布 $\pi_t(\cdot)$ 选择参数 $w_t\in\Omega$。该概率分布即为策略。给定 $w_t\sim\pi_t$，我们随后从未知分布 $q_t$ 观察到 $Z_t\sim q_t$。我们假设损失函数 $\ell$ 已知。在 $n$ 轮之后，设 $\theta(S_n)=[\pi_1,\ldots,\pi_n]$，我们承受的损失为

$$Q(\theta,q)=\sum_{t=1}^{n}\mathbb E_{w_t\sim\pi_t}\mathbb E_{Z_t\sim q_t}\ell(w_t,Z_t)-\inf_{w\in\Omega}\sum_{t=1}^{n}\mathbb E_{Z\sim q_t}\ell(w,Z).$$

在非对抗在线学习中，策略 $\pi_t$ 仅影响最终损失，但不影响观测 $Z_t$。然而，对于某些问题，学习算法采取的策略可能会影响下一个观测。此类问题通常更复杂。

## **示例 13.18 (MAB)**

我们考虑多臂老虎机问题，其中我们有来自 $\mathcal A=\{1,\ldots,K\}$ 的 $K$ 个臂。对于每个臂 $a\in\mathcal A$，我们在 $[0,1]$ 上有一个概率分布 $q_a$。如果我们拉动臂 $a\in\mathcal A$，我们观察到一个随机奖励
