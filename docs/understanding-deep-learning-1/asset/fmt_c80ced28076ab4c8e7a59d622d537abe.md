
我们可以使用*似然比恒等式*简化此表达式：

![c19-fig-5027.jpg](images/c19-fig-5027.jpg)

 (19.26)

从而得到更新公式：

![c19-fig-5028.jpg](images/c19-fig-5028.jpg)

 (19.27)

轨迹的对数概率 `log[Pr(τ|θ)]` 由下式给出：

![c19-fig-5029.jpg](images/c19-fig-5029.jpg)

 (19.28)

注意到只有中间项依赖于 `θ`，我们可以将公式 19.27 的更新重写为：

![c19-fig-5030.jpg](images/c19-fig-5030.jpg)

 (19.29)

其中 `s[it]` 是第 `i` 个回合中时间 `t` 的状态，`a[it]` 是第 `i` 个回合中时间 `t` 采取的动作。请注意，由于与状态演化 `Pr(s[t+1]|s[t], a[t])` 相关的项消失了，此参数更新不假设马尔可夫时间演化过程。

我们可以通过注意到以下关系进一步简化：

![c19-fig-5031.jpg](images/c19-fig-5031.jpg)

 (19.30)

其中 `r[it]` 是第 `i` 个回合中时间 `t` 的奖励。第一项（时间 `t` 之前的奖励）不影响从时间 `t` 开始的更新，因此我们可以写为：

![c19-fig-5032.jpg](images/c19-fig-5032.jpg)

 (19.31)

### 19.5.2 REINFORCE 算法

*REINFORCE* 是一种早期的策略梯度算法，它利用了这一结果并结合了折扣因子。它是一种蒙特卡洛方法，基于当前策略 `π[a|s, θ]` 生成回合 `τ[i] = [s[i][1], a[i][1], r[i][2], s[i][2], a[i][2], r[i][3], …, r[iT]]`。对于离散动作，该策略可由神经网络 `π[s|θ]` 确定，该网络接收当前状态 `s` 并为每个可能的动作返回一个输出。这些输出通过 softmax 函数生成动作分布，并在每个时间步进行采样。

对于每个回合 `i`，我们遍历每一步 `t` 并计算从时间 `t` 开始的部分轨迹 `τ[it]` 的经验折扣回报：

![c19-fig-5033.jpg](images/c19-fig-5033.jpg)

 (19.32)

然后我们更新每个轨迹中每个时间步 `t` 的参数：

![c19-fig-5034.jpg](images/c19-fig-5034.jpg)

 (19.33)

其中 `c19-fig-5035.jpg` 是给定当前状态 `s[t]` 和参数 `θ` 时神经网络输出动作 `a[t]` 的概率，`α` 是学习率。额外项 `γ^t` 确保相对于序列开始对奖励进行折扣，因为我们最大化整个序列回报的对数概率（公式 19.23）。

### 19.5.3 基线

策略梯度方法的缺点是表现出高方差；可能需要许多回合才能获得稳定的导数更新。减少这种方差的一种方法是从基线 `b` 中减去轨迹回报 `r[τ]`：

![c19-fig-5036.jpg](images/c19-fig-5036.jpg)

 (19.34)

只要基线 `b` 不依赖于动作：

***

Problem 19.6

***

![c19-fig-5037.jpg](images/c19-fig-5037.jpg)

 (19.35)

期望值将不会改变。然而，如果基线与增加不确定性的无关因素协同变化，则减去它会减小方差（[图 19.16](#c019.xhtml#c19-fig-0016)）。这是*控制变量法*的一个特例（见 Problem 19.7）。

***

Notebook 19.5

Control variates

***

***

Problem 19.7

***

![Figure 19.16 Decreasing variance of estimates using control variates. a) Consider trying to estimate 𝔼[a] from a small number of samples. The estimate (the mean of the samples) will vary based on the number of samples and the variance of those samples. b) Now consider observing another variable b that co-varies with a and has 𝔼[b] = 0 and the same variance as a. c) The variance of the samples of a − b is much less than that of a, but the expected value 𝔼[a − b] = 𝔼[a], so we get an estimator with lower variance.](images/c19-fig-0016.jpg)

[图 19.16](#c019.xhtml#c19-fig-0016a) 使用控制变量降低估计方差。a) 考虑尝试从少量样本中估计 `𝔼[a]`。估计值（样本均值）将根据样本数量和样本方差而变化。b) 现在考虑观察另一个与 `a` 协同变化、且 `𝔼[b] = 0` 且方差与 `a` 相同的变量 `b`。c) `a − b` 样本的方差远小于 `a`，但期望值 `𝔼[a − b] = 𝔼[a]`，因此我们获得了一个方差更低的估计器。

这引出了如何选择 `b` 的问题。我们可以通过写出方差表达式、对 `b` 求导、将结果设为零并求解来找到使方差最小化的 `b` 值：

![c19-fig-5038.jpg](images/c19-fig-5038.jpg)

 (19.36)

***

Problem 19.8

***

在实践中，这通常近似为：

![c19-fig-5039.jpg](images/c19-fig-5039.jpg)

 (19.37)

减去此基线可以消除当所有轨迹的回报 `r[τ[i]]` 都大于典型值时可能出现的方差，但这仅仅是因为它们碰巧通过了无论采取何种动作回报都高于平均水平的状态。

### 19.5.4 状态相关基线

一个更好的选择是使用依赖于当前状态 `s[it]` 的基线 `b[s[it]]`。

![c19-fig-5040.jpg](images/c19-fig-5040.jpg)

 (19.38)

在这里，我们补偿了某些状态比其他状态具有更大总体回报所引入的方差，无论我们采取什么动作。

一个合理的选择是基于当前状态的期望未来奖励，即状态价值 `v[s]`。在这种情况下，经验观测奖励与基线之间的差值称为*优势估计*。由于我们处于蒙特卡洛背景下，这可以由一个神经网络 `b[s] = v[s, ϕ]` 进行参数化，参数为 `ϕ`，我们可以使用最小二乘损失将其拟合到观测回报：

![c19-fig-5041.jpg](images/c19-fig-5041.jpg)

 (19.39)

## 19.6 Actor-Critic 方法

Actor-Critic 算法是时序差分（TD）策略梯度算法。它们可以在每一步更新策略网络的参数。这与蒙特卡洛 REINFORCE 算法形成对比，后者*必须*等待一个或多个回合完成后才能更新参数。

在 TD 方法中，我们无法获得该轨迹未来的奖励 `c19-fig-5042.jpg`。Actor-Critic 算法用观测到的当前奖励加上下一状态的折扣价值来近似所有未来奖励的总和：

![c19-fig-5043.jpg](images/c19-fig-5043.jpg)

 (19.40)

此处价值 `v[s[i,t][+1], ϕ]` 由具有参数 `ϕ` 的第二个神经网络估计。

将其代入公式 19.38 得到更新：

![c19-fig-5044.jpg](images/c19-fig-5044.jpg)

 (19.41)

同时，我们通过使用损失函数进行自举来更新参数 `ϕ`：

![c19-fig-5045.jpg](images/c19-fig-5045.jpg)

 (19.42)

预测 `Pr(a|s[t])` 的策略网络 `π[s[t], θ]` 称为*Actor*。价值网络 `v[s[t], ϕ]` 称为*Critic*。通常同一个网络同时表示 Actor 和 Critic，具有两组输出分别预测策略和价值。请注意，尽管 Actor-Critic 方法可以在每一步更新策略参数，但在实践中很少这样做。智能体通常在更新策略之前，跨许多时间步收集一批经验。

## 19.7 离线强化学习
