# 尖峰-平板先验 稀疏深度神经网络学习






## 摘要

深度学习在许多机器学习任务中取得了巨大成功。然而，深度神经网络（DNNs）往往严重过参数化，使得它们计算成本高昂、内存密集、可解释性差且校准失准。我们在贝叶斯框架下研究稀疏DNN：我们建立了带尖峰-底座先验的贝叶斯DNN的后验一致性和结构选择一致性，并通过高维非线性变量选择、大型网络压缩和模型校准的示例说明其性能。我们的数值结果表明，稀疏性对于提高DNN的预测精度和校准至关重要。


## 1. 引言

在过去十年中，深度神经网络（DNNs）在解决许多复杂机器学习任务（如模式识别和自然语言处理）方面取得了巨大成功。这些成功的关键因素是其通用近似能力，同时高度依赖大量参数。这些任务中使用的DNN可能包含数百层和数十亿个参数，例如 He et al. (2016) 关于图像分类。许多DNN严重过参数化；对于某些网络，仅 5% 的参数足以实现可接受的模型（Denil et al., 2013）。此外，这些过参数化网络不再具有良好的校准性（Guo et al., 2017）。

为了降低DNN的复杂性并提高其校准性，一些研究者考虑了稀疏深度学习，例如 Schmidt-Hieber (2020)、Bauer and Kohler (2019)、Polson and Ročková (2018) 和 Sun et al. (2021)。稀疏DNN的近似能力已从频率学派和贝叶斯两种视角进行了研究。从频率学派角度，Schmidt-Hieber (2020) 和 Bauer and Kohler (2019) 量化了稀疏DNN在逼近 Hölder 光滑函数时的近似误差。从贝叶斯角度，Polson and Ročková (2018) 建立了带尖峰-底座先验的贝叶斯DNN的后验一致性，Sun et al. (2021) 建立了带混合高斯先验的贝叶斯DNN的后验一致性。最近，稀疏深度学习的理论也在变分推断框架下得到发展，例如 Chérief-Abdellatif (2020)、Bai et al. (2020b) 和 Bai et al. (2020a)。然而，由于变分后验分布的近似性质，得到的统计推断往往是次优的。

本文研究了带尖峰-底座先验的贝叶斯稀疏DNN的理论性质。它与 Polson and Ročková (2018) 密切相关，两者都采用尖峰-底座先验，但我们的理论更一般。具体来说，我们的理论是在输入维度和连接权重上界可随训练样本量增加、且激活函数为 Lipschitz 连续的假设下发展而来的，这涵盖了 ReLU、tanh 和 sigmoid 等许多流行激活函数。相比之下，Polson and Ročková (2018) 假设输入维度为 O(1) 阶、连接权重有界且激活函数为 ReLU。本文还提供了一种可扩展算法，用于从贝叶斯DNN的后验分布中进行模拟。数值结果表明，稀疏性对于提高DNN的预测精度和模型校准至关重要。

本文其余部分组织如下。第 2 节介绍理论结果。第 3 节描述了一种用于贝叶斯DNN模拟的随机梯度马尔可夫链蒙特卡罗（SGMCMC）算法。第 4 节介绍网络压缩示例。第 5 节以简短讨论结束全文。

* 通讯作者。
E-mail address: fliang@purdue.edu (F. Liang)。

## 2. 理论结果

令 \(D_n = \{x^{(i)}, y^{(i)}\}_{i=1}^n\) 表示含 \(n\) 个独立同分布观测的训练数据集，其中 \(x^{(i)} \in \mathbb{R}^{p_n}\)，\(y^{(i)} \in \mathbb{R}\)，且 \(p_n\) 表示输入变量的维度，并假设其随训练样本量 \(n\) 增长。我们假设数据来自广义线性模型，其概率密度/概率质量函数（pdf/pmf）由

```
\(f(y|\mu^*(x)) = \exp\{A(\mu^*(x))y + B(\mu^*(x)) + C(y)\},\)
```

给出，其中 \(\mu^*(x)\) 表示 \(x\) 的未知函数，\(A(\cdot)\)、\(B(\cdot)\) 和 \(C(\cdot)\) 是适当定义的函数。例如，对于逻辑回归，有 \(A(\mu^*) = \mu^*\)，\(B(\mu^*) = -\log(1+e^{\mu^*})\) 且 \(C(y) = 1\)；对于正态回归，通过引入额外离散参数 \(\sigma^2\)，有 \(A(\mu^*) = \mu^*/\sigma^2\)，\(B(\mu^*) = -\mu^{*2}/2\sigma^2\) 且 \(C(y) = -y^2/2\sigma^2 - \log(2\pi\sigma^2)/2\)。为简化分析，假设 \(\sigma^2\) 已知。为建模数据，我们建议用具有 \(H_n - 1\) 个隐藏层的 DNN 近似 \(\mu^*(x)\)。令 \(L_h\) 表示第 \(h\) 层的隐藏单元数，其中输出层 \(L_{H_n} = 1\)，输入层 \(L_0 = p_n\)。令 \(w^h \in \mathbb{R}^{L_h \times L_{h-1}}\) 和 \(b^h \in \mathbb{R}^{L_h \times 1}\)，\(h \in \{1, 2, \dots, H_n\}\) 分别表示第 \(h\) 层的权重和偏置。令 \(\psi^h: \mathbb{R}^{L_h \times 1} \to \mathbb{R}^{L_h \times 1}\) 表示一种映射，它将分段可微激活函数 \(\psi\) 应用于输入的每个元素。总之，DNN 构成一个非线性映射

```
\(\mu(\beta, x) = w^{H_n}\psi^{H_n-1}[\cdots \psi^1[w^1x + b^1]\cdots] + b^{H_n},\) (1)
```

其中 \(\beta = \{w_{ij}^h, b_k^h : 1 \le h \le H_n, 1 \le i, k \le L_h, 1 \le j \le L_{h-1}\}\) 表示 DNN 的权重和偏置集合。完全连接的 DNN 包含 \(K_n = |\beta| = \sum_{h=1}^{H_n} (L_{h-1} \times L_h + L_h)\) 个可调参数。为便于稀疏 DNN 的表示，我们通过为 \(\beta\) 的每个元素引入指示变量来重新参数化 \(\beta\)，该变量指示相应连接是否存在。这里偏置被视为一种具有常数输入 1 的特殊连接。令 \(w^h = \tilde{w}^h \circ y^{w^h}\) 和 \(b^h = \tilde{b}^h \circ y^{b^h}\)，其中 \(y^{w^h}\) 和 \(y^{b^h}\) 为指示变量的矩阵或向量，\(\circ\) 表示元素逐元乘积。相应地，我们定义 \(\tilde{\beta} = \{\tilde{w}_{ij}^h, \tilde{b}_k^h\}\) 和 \(\gamma = \{y_{ij}^{w^h}, y_k^{b^h}\}\)，分别表示连接权重和网络结构。为简化记号，我们重写 \(\tilde{\beta}\) 和 \(\gamma\) 为 \(\tilde{\beta} = (\tilde{\beta}_1, \tilde{\beta}_2, \dots, \tilde{\beta}_{K_n}) \in \mathbb{R}^{K_n}\) 和 \(\gamma = (\gamma_1, \gamma_2, \dots, \gamma_{K_n}) \in \{0, 1\}^{K_n}\)。相应地，有 \(\beta = \tilde{\beta} \circ \gamma\)。

### 2.1. 稀疏 DNN 的正则性条件

稍作记号滥用，我们将 (1) 中的 \(\mu(\beta, x)\) 为稀疏 DNN 重写为 \(\mu(\beta, \gamma, x)\)，以包含网络结构信息。在下文中，我们将从贝叶斯视角刻画 \(\mu^*(x)\) 能被稀疏 DNN 的 \(\mu(\beta, \gamma, x)\) 多好逼近。为此，我们假设以下正则性条件：

- A.1 输入 \(x\) 分量wise 被 1 界限，即 \(x \in \Omega = [-1, 1]^{p_n}\)，且 \(x\) 在其支撑集 \(\Omega\) 上的密度关于 \(n\) 一致界限。

- A.2 未知回归均值函数 \(\mu^*(x)\) 可由稀疏 DNN 模型较好逼近，使得 \(\mu(\beta^*, \gamma^*, x)\) 满足

  - A.2.1 \(\|\mu^*(x) - \mu(\beta^*, \gamma^*, x)\|_{l^2(\Omega)}^2 \le \varpi_n\)，其中近似误差 \(\varpi_n \to 0\) 当样本量 \(n \to \infty\)。

  - A.2.2 \(H_n \log K_n \ge C \log n\) 对某个常数 \(C > 0\)，\(1 < r_n^* H_n \log K_n < n^1\) 且 \(\|\beta^*\|_\infty < E_n\)，其中 \(E_n\) 是满足 \(\log E_n = O(\log K_n)\) 的一个序列，\(r_n^*\) 是网络大小，即 \(r_n^* = \sum_{i=1}^{K_n} \gamma_i^*\)。

- A.3 激活函数 \(\psi\) 是 Lipschitz 连续的，其 Lipschitz 常数为 1。

关于条件的更多讨论请参阅补充材料，其中我们展示了我们的贝叶斯 DNN 理论如何与现有稀疏 DNN 近似理论相容。





### 2.2. 尖峰-平板先验

To conduct Bayesian inference for the DNN, we consider a hierarchical prior given by

$\tilde{\beta}_i | \gamma_i = 1 \sim N(0, \sigma_{1,n}^2), \ i=1,2,\dots,K_n; \ \pi(\gamma) \propto \lambda_n^{|\gamma|} (1-\lambda_n)^{K_n-|\gamma|} \mathbf{1}\{||\gamma|| \le \bar{r}_n, \gamma \in \mathcal{G}\}, \quad (2)$

where $\sigma_{1,n}^2$ is the variance of the normal distribution, $\bar{r}_n$ is the maximum size of candidate sparse DNNs, $\lambda_n$ can be read as an approximate prior probability for each connection to be included in the DNN, and $\mathcal{G}$ is the set of all valid DNNs. With this hierarchical prior, $\beta_i$ follows a discrete spike-and-slab prior, i.e., $\beta_i = \tilde{\beta}_i \circ \gamma_i \sim \lambda_n N(0, \sigma_{1,n}^2) + (1-\lambda_n)\delta_0$ for $i=1,2,\dots,K_n$, where $\delta_0$ denotes the Dirac delta function.

### 2.3. 后验一致性

Posterior consistency measures the speed of posterior concentration around the true density function, which plays a major role in validating Bayesian methods. For DNNs, since the total number of parameters $K_n$ is often much larger than the sample size $n$, posterior consistency provides a general guideline for prior setting. Otherwise, the prior information may dominate data information, rendering a biased inference for the underlying true model. For learning sparse DNNs, we generally set $\lambda_n \to 0$ as $K_n \to \infty$, which provides an automatic control for the multiplicity involved in structural selection (Scott et al., 2010). Denote by $P^*$ and $E^*$ the respective probability measure and expectation with respective to the data $D_n$, denote by $d(p_1, p_2)$ the Hellinger distance between two densities $p_1(x,y)$ and $p_2(x,y)$, denote by $p_\beta$ the density function induced by a DNN associated with the parameters $\beta$, and denote by $p_{\mu^*}$ the true density function induced by the unknown function $\mu^*(x)$. Let $\pi(A|D_n)$ denote the posterior probability of an event $A$. The following theorem establishes posterior consistency for sparse DNNs under the spike-and-slab prior (2).

#### Theorem 2.1.

Consider a DNN with $H_n$ layers and at most $K_n$ possible connections, where both $H_n$ and $K_n$ are increasing with $n$. If the assumptions A.1-A.3 hold, and $\hat{\beta}$ and $y$ are subject to the prior (2) with the hyperparameters subject to the constraints $\log \sigma_{1,n}^2 + E_n^2/\sigma_{1,n}^2 = O(H_n \log K_n)$ and $1 \le r_n \le \bar{r}_n < K_n$, where $r_n = \lambda_n K_n$. Then there exists a sequence $\epsilon_n \asymp \max\{\varpi_n, \sqrt{r_n H_n \log K_n/n}\}$ such that for sufficiently large n, the posterior distribution satisfies

$$ \begin{aligned} P^* \left\{ \pi(d(p_\beta, p_{\mu^*}) > 4\epsilon_n | D_n) \ge 2e^{-n\epsilon_n^2/4} \right\} \\ E^*\pi(d(p_\beta, p_{\mu^*}) > 4\epsilon_n | D_n) \le 4e^{-n\epsilon_n^2/2}, \end{aligned} \quad (3) $$

Theorem 2.1 establishes a Bayesian contraction rate for sparse DNNs under the Hellinger metric. Therefore, to obtain consistent Bayesian inference, it suffices to require $\varpi_n \to 0$ and $\bar{r}_n H_n \log(K_n) < n$. If $\mu^*$ can be optimally represented by a sparse DNN model (refer to Remark S2 in the supplementary material), then $\varpi_n$ polynomially decays to 0 as $r_n$ increases to infinity. On the other hand, $\bar{r}_n H_n \log(K_n) < n$ implies $\bar{r}_n = o(n/\log(n))$ by noticing that $K_n \ge \bar{r}_n$. Refer to the supplementary material for more discussions on this theorem. In conclusion, we only need $\bar{r}_n$, the upper bound of total connectivity, to increase slowly; or said differently, a sparse DNN of connectivity $O(n/\log(n))$ could have been large enough for providing a consistent approximation to the true posterior distribution.

### 2.4. DNN 结构选择的一致性

It is known that the DNN model is nonidentifiable in general due to the symmetry of the network structure. However, by introducing appropriate constraints (Pourzanjani et al., 2017; Liang et al., 2018), we can define a set of neural networks such that each network in the set is unique up to simple node permutations, sign changes, etc. Let $\Theta$ denote such a set of DNNs, where each element in $\Theta$ can be viewed as an equivalent class of networks. Let $\upsilon(\cdot)$ be the transformation such that $\upsilon(\beta) \in \Theta$. Since $p_\beta = p_{\upsilon(\beta)}$, the posterior consistency (3) holds for $\upsilon(\beta)$ as well. In what follows, we rewrite $\upsilon(\beta)$ by $\upsilon(y, \beta)$ by including the network structure information. To serve the purpose of structure selection for the DNN, we consider the marginal inclusion posterior probability (MIPP) approach proposed in Liang et al. (2013) for high-dimensional variable selection. For each entry of $y$, we define its MIPP by $q_i = \int \sum_y e_{i|\upsilon(y,\beta)} \pi(y|y, D_n) \pi(\beta|D_n) d\beta$, where $e_{i|\upsilon(y,\beta)}$ indicates existence of connection $i$ in the network $\upsilon(y, \beta)$. Similarly, we define $e_{i|\upsilon(y^*, \beta^*)}$ as the indicator for connection $i$ in the true DNN $\upsilon(y^*, \beta^*)$. The MIPP approach is to choose the connections for which the marginal inclusion posterior probability is greater than a threshold value $\hat{q}$; that is, setting $\hat{Y}_q = \{j: q_j > \hat{q}, j=1,2,\dots,K_n\}$ as a Bayes estimator of the true model. To establish the consistency of $\hat{Y}_q$, the following identifiability condition for the true network $Y_*$ is needed.

Let $A(\epsilon_n) = \{\beta : d(p_\beta, p_{\mu^*}) \ge \epsilon_n\}$. Define $\rho(\epsilon_n) = \max_{1 \le i \le K_n} \int_{A(\epsilon_n)^c} \sum_y e_{i|\upsilon(y,\beta)} - e_{i|\upsilon(y^*, \beta^*)} \pi(y|\beta, D_n) \pi(\beta|D_n) d\beta$, which measures the distance between the true DNN model and the models drawn from the posterior in the $\epsilon_n$-neighborhood $A(\epsilon_n)^c$. The identifiability condition can be stated as follows:

- B.1 $\rho(\epsilon_n) \to 0$, as $n \to \infty$ and $\epsilon_n \to 0$.

That is, when $n$ is sufficiently large, if a DNN produces approximately the same probability distribution as the true data, then its structure, after mapping into the network space $\Theta$, must coincide with the true DNN structure. Note that this identifiability is different from the one mentioned at the beginning of this section, which is only with respect to structure and parameter rearrangements. Theorem 2.2 concerns consistency of $\hat{\gamma}$ and its sure screening property.

#### Theorem 2.2.

If the conditions of Theorem 2.1 and condition B.1 hold, then (i) $\max_{1 \le i \le K_n} \{ |q_i - e_{i|\upsilon(y^*, \beta^*)}| \} \to 0$ in probability; and (ii) for any pre-specified $\hat{q} \in (0, 1)$, $\lim_{n \to \infty} P(Y_* \subset \hat{Y}_q) = 1$.

In practice, the value of $\hat{q}$ can be determined by a multiple hypothesis test, see e.g. Liang and Zhang (2008). For simplicity, we often set $\hat{q} = 0.5$. Recall that $\mathbf{y}^w \in \mathbb{R}^{L_h \times L_{h-1}}$ denotes the connection indicator matrix of layer h.

$$
\mathbf{y}^x = \mathbf{y}^{w^{h_n}} \mathbf{y}^{w^{h_n-1}} \cdots \mathbf{y}^{w^1} \in \mathbb{R}^{1 \times p_n},
$$
(4)

and let $\mathbf{y}_i^x$ denote the $i$th element of $\mathbf{y}^x$. If $\mathbf{y}_i^x > 0$ then the input variable $\mathbf{x}_i$ is effective in the network $\mathbf{y}$, and $\mathbf{y}_i^x = 0$ otherwise. As in treating network connections, we can define a MIPP for each input variable and determine a threshold value for the MIPP based on a multiple hypothesis test. As implied by (4), the consistency of structure selection implies consistency of variable selection with respect to the true network $\mathbf{y}^*$ as defined in Assumption A.2.1.

## 3. 计算算法

Although the spike-and-slab prior leads to nice theoretical properties for Bayesian sparse DNNs, the resulting posterior is a mixture of distributions with varying dimensions. Conventional Bayesian sampling algorithms adopt reversible jump moves (Green, 1995) to explore different network architectures, see e.g. Liang et al. (2018), and lack scalability necessarily required for big data scenarios. Song et al. (2020) proposed an extended stochastic gradient Langevin dynamics (SGLD) algorithm for Bayesian variable selection under the big data scenario, which allows the mini-batch data to be used in updating the model and regression coefficients at each iteration and is thus scalable to big data problems. In this paper, we extend it further by combining it with stochastic gradient Hamiltonian Monte Carlo (SGHMC) (Chen et al., 2014), see Algorithm 1 for the procedure and the supplementary material for more explanations.

```
**Algorithm 1** Extended Stochastic Gradient Hamiltonian Monte Carlo

Input: $T; m; \tau; t_0; t_1$
Initialization: Randomly initialize $\tilde{\beta}^{(1)}$. Set $\gamma_i^{(0,t_0)}=1$ for all $i \in \{1, \dots, K_n\}$;
for $t = 1, 2, \dots, T$ do
  (i) Draw a subsample of size $m$ from the full dataset $D_n$, and duplicate it to form a dataset $D_{m,n}^{(t)}$.
  (ii) Simulate models $\gamma^{(t,1)}, \gamma^{(t,2)}, \dots, \gamma^{(t,t_0)}$ from the conditional posterior $\pi(\gamma|\tilde{\beta}^{(t)}, D_{m,n}^{(t)})$ by Metropolis-Hastings(MH) algorithm with a magnitude-based proposal.
  (iii) Update $\tilde{\beta}^{(t)}$ via a SGHMC move,

  $$
  v^{(t+1)} = (1-\alpha)v^{(t)} + \frac{\epsilon_{t+1}}{2t_0} \sum_{k=1}^{t_0} \nabla_{\tilde{\beta}} \log \pi(\tilde{\beta}^{(t)}|\gamma^{(t,k)}, D_{m,n}^{(t)}) + \sqrt{\alpha \epsilon_{t+1} \tau} \eta_{t+1},
  $$

  $$
  \tilde{\beta}^{(t+1)} = \tilde{\beta}^{(t)} + v^{(t+1)},
  ```

  where $\eta_{t+1} \sim N(0, I_d)$, $\epsilon_{t+1}$ is the learning rate, $\tau$ is the temperature, and $1-\alpha$ gives the momentum parameter.
end for
```

The main parameters of the extended SGHMC algorithm are the prior hyperparameters $\lambda_n$ and $\sigma_{1,n}$ defined in (2). Our theory allows $\sigma_{1,n}$ to grow with $n$ from the perspective of data fitting, but in our experience, the magnitude of weights tend to adversely affect the generalization ability of the network. For this reason, we usually set $\sigma_{1,n}$ to a small number such as 0.01 or 0.02, and then tune the value of $\lambda_n$ for network sparsity such that the sparse constraint given in Assumption A.2.2 is satisfied.

## 4. 实验

This section presents an example on network compression for convolutional neural networks (CNNs). Refer to the supplementary material for examples on high-dimensional nonlinear variable selection and DNN model calibration. In terms of network compression, extended SGHMC can be viewed as an unstructured dynamic pruning algorithm, where the spike-and-slab prior is imposed on each parameter and the sparsity mask $\gamma$ can be adjusted during training (Lin et al., 2020). We test the proposed method on the CIFAR-10 data (Krizhevsky et al., 2009), pruning ResNet20 and ResNet32



| 模型 | 方法 | 剪枝比例 (%) | 测试准确率 (%) | 剪枝比例 (%) | 测试准确率 (%) |
|---|---|---|---|---|---|
| ResNet20 | BNN$_{bma}$ | 9.65(0.05) | **91.60(0.06)** | 19.76(0.02) | **92.65(0.02)** |
| ResNet20 | BNN$_{single}$ | 9.88(0.08) | **91.26(0.02)** | 19.83(0.02) | **92.32(0.04)** |
| ResNet20 | BNN$_{cs}$ | 9.55(0.03) | 91.27(0.05) | 19.67(0.05) | 92.27(0.03) |
| ResNet20 | SVI | 10 | 89.43(0.05) | 20 | 91.78(0.06) |
| ResNet20 | SM | 10 | 89.76(0.40) | 20 | 91.54(0.16) |
| ResNet20 | DSR | 10 | 87.88(0.04) | 20 | 91.78(0.28) |
| ResNet20 | DPF | 10 | 90.88(0.07) | 20 | 92.17(0.21) |
| ResNet32 | BNN$_{bma}$ | 4.89(0.09) | **91.84(0.09)** | 9.65(0.05) | **92.99(0.08)** |
| ResNet32 | BNN$_{single}$ | 4.99(0.06) | **91.39(0.10)** | 8.77(0.12) | **92.74(0.10)** |
| ResNet32 | BNN$_{cs}$ | 4.78(0.01) | 91.21(0.01) | 9.53(0.04) | 92.74(0.07) |
| ResNet32 | SVI | 5 | 86.31(0.23) | 10 | 91.61(0.10) |
| ResNet32 | SM | 5 | 88.68(0.22) | 10 | 91.54(0.18) |
| ResNet32 | DSR | 5 | 84.12(0.32) | 10 | 91.41(0.23) |
| ResNet32 | DPF | 5 | 90.94(0.35) | 10 | 92.42(0.18) |

网络 (He et al., 2016) 到不同稀疏水平。我们使用 Lin et al. (2020) 中的标准设置训练网络，即我们使用 128 的小批量大小，并以固定初始学习率 \(\epsilon_0 = 0.1\) 训练模型 300 个epoch，在epoch 150 和 225 时将 \(\epsilon_t\) 除以 10。我们设置 \(\sigma_{1,n}^2 = 0.04\)，并使用扩展 SGHMC 算法从后验中采样，参数为 \(t_0 = 1\)、\(\tau = 0.0001\)、\(\alpha = 0.1\)，并为 \(\gamma\) 使用基于幅度的提议。我们调整 \(\lambda_n\) 和 \(b\)（基于幅度提议的一个参数，如补充材料中所述），以实现不同 ResNet 的目标稀疏水平。后验样本在每个epoch结束时收集，前 225 个样本被丢弃用于烧入过程。

我们将所提方法与一些最近的非结构化压缩方法进行比较，包括带反馈的动态剪枝 (DPF) (Lin et al., 2020)、动态稀疏重参数化 (DSR) (Mostafa and Wang, 2019)、稀疏动量 (SM) (Dettmers and Zettlemoyer, 2019)、一致稀疏深度学习 (BNN$_{cs}$) (Sun et al., 2021) 和用于稀疏深度学习的变分推断 (SVI) (Bai et al., 2020b)。数值结果总结于表 1。比较表明，所提方法在相似稀疏水平下可实现高于现有方法的预测准确率。

## 5. 结论

本文从贝叶斯视角研究稀疏深度学习。从理论上，我们建立了带尖峰-平板先验的贝叶斯DNN的后验一致性和结构选择一致性。我们给出了后验收缩速率，并提出使用边际包含后验概率方法来确定稀疏DNN的结构。我们采用可扩展的SGMCMC算法来模拟稀疏DNN的后验，其计算复杂度阶数与SGD等流行优化算法大致相同。当数据集中存在无关特征时，我们的数值结果表明，与盲目学习大型全连接DNN相比，学习稀疏DNN在预测方面总是有回报的。所提方法可作为一种非结构化动态剪枝方法应用于大规模网络剪枝任务，其中稀疏掩码在训练期间系统地调整。我们的数值结果表明，所提方法在网络结构选择、大规模网络剪枝和模型校准方面可实现最先进的性能。

如前所述，稀疏性对改善DNN的校准至关重要 (Wang and Ročková, 2020; Lee et al., 2020)。这项工作为学习稀疏DNN提供了一种实用且高效的方法，并为识别适当的稀疏结构提供理论保证，因此将自然增强可信人工智能的发展。

## 致谢

梁的研究部分得到NSF资助DMS-2015498和NIH资助R01-GM117597及R01-GM126089的支持。宋的研究部分得到NSF资助DMS-1811812的支持。作者感谢编辑、副编辑和审稿人提出的建设性意见，这些意见显著改进了本文。

## 附录 A. 补充数据

与本文相关的补充材料可在线查阅 https://doi.org/10.1016/j.spl.2021.109246。在线补充材料包含理论结果的证明和评论、扩展随机梯度MCMC算法的描述以及更多数值结果。

## 参考文献

- Bai, J., Song, Q., Cheng, G., 2020a. 稀疏深度神经网络自适应变分贝叶斯推断. arXiv:1910.04355.
- Bai, J., Song, Q., Cheng, G., 2020b. 具有理论保证的稀疏深度学习高效变分推断. In: 神经信息处理系统进展. pp. 466–476.
- Bauer, B., Kohler, M., 2019. 深度学习作为非参数回归中维度灾难补救方法的探讨. Ann. Statist. 47 (4), 2261–2285.
- Chen, T., Fox, E., Guestrin, C., 2014. 随机梯度哈密顿蒙特卡洛. In: 国际机器学习会议. pp. 1683–1691.
- Chérief-Abdellatif, B.-E., 2020. 稀疏深度学习中变分推断的收敛速率. In: Illi, H.D., Singh, A. (Eds.), 第37届国际机器学习会议论文集. In: 机器学习研究论文集, vol. 119. PMLR, pp. 1831–1842.
- Denli, M., Shakibi, B., Dinh, L., Ranzato, M., de Freitas, N., 2013. 深度学习中的参数预测. In: 第26届神经信息处理系统会议论文集 – 第2卷. Curran Associates Inc., Red Hook, NY, USA, pp. 2148–2156.
- Dettmers, T., Zettlemoyer, L., 2019. 从零开始构建稀疏网络：在不损失性能的情况下加速训练. arXiv预印本 arXiv:1907.04840.
- Green, P.J., 1995. 可逆跳马尔可夫链蒙特卡洛计算与贝叶斯模型确定. Biometrika 82 (4), 711–732.
- Guo, C., Pleiss, G., Sun, Y., Weinberger, K.Q., 2017. 现代神经网络校准探讨. In: 第34届国际机器学习会议论文集 – 第70卷. In: ICML’17. JMLR.org, pp. 1321–1330.
- He, K., Zhang, X., Ren, S., Sun, J., 2016. 图像识别的深度残差学习. In: 2016年IEEE计算机视觉与模式识别会议(CVPR). pp. 770–778.
- Krizhevsky, A., Hinton, G., et al., 2009. 从小图像中学习多层特征. 技术报告, Citeseer.
- Lee, J., Hunt, M., Feng, J., Triebel, R., 2020. 稀疏信息形式中神经网络模型不确定性估计. In: Illi, H.D., Singh, A. (Eds.), 第37届国际机器学习会议论文集. 第119卷. PMLR, pp. 5702–5713.
- Liang, F., Li, Q., Zhou, L., 2018. 用于药物敏感基因选择的贝叶斯神经网络. J. Amer. Statist. Assoc. 113 (523), 955–972.
- Liang, F., Song, Q., Yu, K., 2013. 高维广义线性模型的贝叶斯子集建模. J. Amer. Statist. Assoc. 108, 589–606.
- Liang, F., Zhang, J., 2008. 使用随机近似估计假发现率. Biometrika 95, 961–977.
- Lin, T., Stich, S.U., Barba, L., Dmitriev, D., Jaggi, M., 2020. 带反馈的动态模型剪枝. In: 国际学习表征会议.
- Mostafa, H., Wang, X., 2019. 通过动态稀疏重参数化实现深度卷积神经网络的参数高效训练. In: 国际机器学习会议. pp. 4646–4655.
- Polson, N., Ročková, V., 2018. 稀疏深度学习的后验集中. In: 神经信息处理系统进展. pp. 930–941.
- Pourzanjani, A.A., Jiang, R.M., Petzold, L.R., 2017. 贝叶斯推断中神经网络可辨识性的改进. In: NIPS贝叶斯深度学习研讨会.
- Schmidt-Hieber, J., 2020. 使用带ReLU激活函数的深度神经网络进行非参数回归. Ann. Statist. 48 (4), 1875–1897.
- Scott, J.G., Berger, J.O., et al., 2010. 变量选择问题中的贝叶斯和经验贝叶斯多重性调整. Ann. Statist. 38 (5), 2587–2619.
- Song, Q., Sun, Y., Ye, M., Liang, F., 2020. 大规模贝叶斯变量选择的扩展随机梯度MCMC. Biometrika 107 (4), 997–1004.
- Sun, Y., Song, Q., Liang, F., 2021. 一致稀疏深度学习：理论与计算. J. Amer. Statist. Assoc. http://dx.doi.org/10.1080/01621459.2021.1895175, 即将发表.
- Wang, Y., Ročková, V., 2020. 稀疏深度学习的不确定性量化. In: AISTATS.

