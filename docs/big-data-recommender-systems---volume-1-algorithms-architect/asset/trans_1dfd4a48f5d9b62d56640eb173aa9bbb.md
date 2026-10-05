

# 用于推荐系统的深度生成式模型 117

| | Mousna | Drt | | |
|---|---|---|---|---|
| 喜剧 | 0.4 | 0.2 | 0.1 |
| 恐怖 | 0.1 | 0.0 | 0.7 |
| 剧情 | 0.2 | 0.7 | 0.2 |
| 动作 | 0.3 | 0.6 | 0.1 |

![](img/6d0ce7dba01af52e1c2fae47d5b04a05_133_0.png)

**图 6.4 使用 LDA 模型的推荐生成框架：**
(a) 展示了用户电影选择过程的简单示例，
(b) 代表了推荐系统的模型正式图化结构，该结构说明了用户 $u$ 观看电影 $v$ 的决策过程。在这个例子中，在颜色编码代码上有四个主题（即分布 $\theta$）和四部电影，它们被描述为 $\phi$ 矩阵的颜色。以下步骤描绘了 LDA 的生成过程。

- 用户对多个主题有兴趣，比例不同，这遵循从超参数为 $\alpha$ 的狄利雷分布 $\theta$。
- 从主题兴趣 $\theta$ 中，他随后使用多项分布选择一个单一主题 $z$（用颜色代码表示）。在示例中，用户选择了“恐怖”电影主题，该主题由橙色硬币表示。
- 为了观看电影 $v$，他查阅主题-电影矩阵 $\phi$，该矩阵指示了 $v$ 属于主题 $z$ 的概率，并使用多项分布选择一个符合其主题兴趣的单部电影。在图 6.4 中，用户选择了*指环王》（*Rings*），它对应于恐怖类型。

然而，在现实中，我们无法观察到特定的主题 $z$，这意味着用户-主题比例 $\theta$ 和电影-主题比例 $\phi$ 都是不可观测的。观测到的变量是集合 $U = \{u_i\}_{i=1}^n$ 及其项目选择 $N_u = \{v_{uj}\}_{j=1}^m$。因此，LDA 的核心推理问题是从观测变量 $v$ 和 $u$ 中估计 $\theta$ 和 $\phi$。LDA 图化模型的正式表示如图 6.4(b) 所示。

**参数推理：** LDA 的后验概率定义如下：

```
$P(\theta, z|v, \alpha) = \frac{P(\theta, z|v, \alpha)}{P(v|\alpha)}$
```

通过检查模型的图化结构，单个用户 $u$ 的似然性可以扩展如下：

```
$P(\theta, z, v|\alpha, \beta) = P(v|\beta, z)P(z|\theta)P(\theta|\alpha)$
```

# 118 大规模推荐系统，卷 1

其中 $P(\theta|\alpha)$ 是狄利雷分布，$P(v|\beta, z)$ 是 $K \times V$ 概率矩阵 $\beta$。将这些值代入似然函数得到以下结果：

```
$P(\theta, z, w|\alpha, \beta) = \frac{\Gamma(\sum_{k=1}^K \alpha_k)}{\prod_{k=1}^K \Gamma(\alpha_k)} \prod_{i=1}^U \alpha_{z_i}^{-1} \prod_{k=1}^K \prod_{j=1}^V (\theta_k \beta_{k,j})^{w_{i,j}-1}$ (6.10)
```

$(6.8)$ 的归一化因子定义如下：

```
$P(v|\alpha, \beta) = \frac{\Gamma(\sum_{k=1}^K \alpha_k)}{\prod_{k=1}^K \Gamma(\alpha_k)} \prod_{k=1}^K \alpha_k^{-1} \prod_{i=1}^U \prod_{j=1}^V (\theta_k \beta_{k,j})^{w_{i,j}-1} d\theta$ (6.11)
```

上述表达式与似然性相似，除了边缘积分 $\theta$ 和对主题空间 $[z]_i$ 的求和外外。然而，这个归一化因子是无法计算的。这是因为在 LDA 6.4(b) 的图化模型中，$\theta$ 和 $\beta$ 之间存在耦合。在对 (6.11) 取对数时，无法分离参数 $\theta$ 和 $\beta$。为了解决这个问题，LDA 尝试使用 Gibbs 采样或变分推断（VI）来近似参数。前者通过从后验中抽取 MCMC 样本来近似参数，而后者通过优化似然函数的证据下界（ELBO）来实现这一目标。在这里，我们将解释限制在 VI 技术上。对基于 Gibbs 采样的推理感兴趣的读者请参考关于文本分析参数估计的教程 [25]。

VI 通过假设分布 $\theta$ 和 $\beta$ 仅依赖于它们各自的变分参数 $\gamma$ 和 $\phi$ 来解决耦合问题 [26, 27]。在此假设下，ELBO 可以表述为：

```
$ln P(v|\alpha, \beta) = \mathcal{L}(\alpha, \beta) + KL(q(\theta, z|v)|P(\theta, z|v, \alpha, \beta))$ $ (6.12)
```

VI 的目标是学习 $\mathcal{L}(\alpha, \beta)$ 使尽可能接近 $ln P(v|\alpha)$。换句话说，目标是学习参数 $\gamma$ 和 $\phi$，使得变分分布 $q(\theta, z:|)$ 与真实后验之间的 KL 散度最小。实现这一点的方法之一是使用迭代固定点法，它产生了以下更新：

```
$\phi_{uk} \propto \beta_{kv} \exp[\log(\theta_k)|\gamma_k]$ (6.13)
```

```
$$\gamma_k = \alpha_k + \sum_{i=1}^U \phi_{ik} (14)
```

期望定义如下：

```
$E_q[log(\theta_k)] = \Psi(\gamma_k) - \Psi(\sum \gamma_k)$ (15)
```

# 用于推荐系统的深度生成式模型

其中 $\psi$ 是 digamma 函数。变分推断 VI 通过假设分布 $\theta$ 和 $\beta$ 仅依赖于它们各自的变分参数 $\gamma$ 和 $\phi$ 来解决耦合问题 [26, 27]。在此假设下，ELBO 可以表述为：

```
$ln P(v|\alpha, \beta) = \mathcal{L}(\alpha, \beta) + KL(q(\theta, z|v)|P(\theta, z|v, \alpha, \beta))$ $ (6.12)
```

VI 的目标是学习 $\mathcal{L}(\alpha, \beta)$ 使尽可能接近 $ln P(v|\alpha)$。换句话说，目标是学习参数 $\gamma$ 和 $\phi$，使得变分分布 $q(\theta, z:|)$ 与真实后验之间的 KL 散度最小。实现这一点的方法之一是使用迭代固定点法，它产生了以下更新：

```
$\phi_{uk} \propto \beta_{kv} \exp[\log(\theta_k)|\gamma_k]$ (6.13)
```

```
$$\gamma_k = \alpha_k + \sum_{i=1}^U \phi_{ik} (14)
```

期望定义如下：

```
$E_q[log(\theta_k)] = \Psi(\gamma_k) - \Psi(\sum \gamma_k)$ (15)
```

其中 $\psi$ 是 digamma 函数。变分推断 VI 通过假设分布 $\theta$ 和 $\beta$ 仅依赖于它们各自的变分参数 $\gamma$ 和 $\phi$ 来解决耦合问题 [26, 27]。在此假设下，ELBO 可以表述为：

```
$ln P(v|\alpha, \beta) = \mathcal{L}(\alpha, \beta) + KL(q(\theta, z|v)|P(\theta, z|v, \alpha, \beta))$ $ (6.12)
```

