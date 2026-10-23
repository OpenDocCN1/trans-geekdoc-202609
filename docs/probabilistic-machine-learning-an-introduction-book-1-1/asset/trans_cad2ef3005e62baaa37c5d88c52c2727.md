
其中 $\mathrm{IW}$ 为逆威沙特分布。不幸的是，$\boldsymbol{\mu}$ 和 $\boldsymbol{\Sigma}$ 在式 (7.117) 的似然函数中以非分解形式共同出现（参见第一个指数项），因此式 (7.118) 中的分解先验并非似然函数的共轭先验。

上述先验有时被称为**条件共轭**，因为两个条件分布 $p(\boldsymbol{\mu}\mid\boldsymbol{\Sigma})$ 和 $p(\boldsymbol{\Sigma}\mid\boldsymbol{\mu})$ 各自都是共轭的。为了构建一个完全共轭的先验，我们需要使用一个 $\boldsymbol{\mu}$ 和 $\boldsymbol{\Sigma}$ 相互依赖的先验。我们将使用如下形式的联合分布：$p(\boldsymbol{\mu},\boldsymbol{\Sigma})=p(\boldsymbol{\mu}\mid\boldsymbol{\Sigma})p(\boldsymbol{\Sigma})$。观察似然方程的形式，即式 (7.117)，我们发现自然的共轭先验具有**正态-逆威沙特**（Normal-inverse-Wishart）或 **NIW** 分布的形式，定义如下：

$$\operatorname{NIW}(\boldsymbol{\mu},\boldsymbol{\Sigma}\mid\tilde{\mathbf m},\tilde{\kappa},\tilde{\nu},\tilde{\mathbf S}) \triangleq \mathcal N\left(\boldsymbol{\mu}\mid\tilde{\mathbf m},\frac{1}{\tilde{\kappa}}\boldsymbol{\Sigma}\right)\times\operatorname{IW}(\boldsymbol{\Sigma}\mid\tilde{\mathbf S},\tilde{\nu})$$

$$=\frac{1}{Z_{\mathrm{NIW}}}|\boldsymbol{\Sigma}|^{-\frac{1}{2}}\exp\left(-\frac{\tilde{\kappa}}{2}(\boldsymbol{\mu}-\tilde{\mathbf m})^\top\boldsymbol{\Sigma}^{-1}(\boldsymbol{\mu}-\tilde{\mathbf m})\right)$$

$$\times |\boldsymbol{\Sigma}|^{-\frac{\tilde{\nu}+D+1}{2}}\exp\left(-\frac{1}{2}\operatorname{tr}(\boldsymbol{\Sigma}^{-1}\tilde{\mathbf S})\right)$$

其中归一化常数由下式给出：

$$Z_{\mathrm{NIW}} \triangleq 2^{\tilde{\nu}D/2}\Gamma_D(\tilde{\nu}/2)(2\pi/\tilde{\kappa})^{D/2}|\tilde{\mathbf S}|^{-\tilde{\nu}/2}$$

NIW 的参数可以解释如下：$\tilde{\mathbf m}$ 是 $\boldsymbol{\mu}$ 的先验均值，$\tilde{\kappa}$ 表示我们对这一先验的置信程度；$\tilde{\mathbf S}$ （成正比于）$\boldsymbol{\Sigma}$ 的先验均值，$\tilde{\nu}$ 表示我们对这一先验的置信程度。

使用有向图模型的术语来看，我们发现 $\boldsymbol{\mu}$ 和 $\boldsymbol{\Sigma}$ 在给定 $\mathcal D$ 的条件下变为依赖关系，这是由于“解释消除”（explaining away）造成的。参见图 7.15(a)。

请注意，我们在均值上的不确定性成正比于协方差。特别地，如果我们认为方差很大，那么我们在 $\boldsymbol{\mu}$ 上的不确定性也必须很大。这在直观上是合理的，因为如果数据具有较大的离散度，就很难确定其均值。

## 后验

为了推导后验分布，让我们定义平方和矩阵

$$\mathbf S_0 \triangleq \sum_{n=1}^{N}\mathbf y_n\mathbf y_n^\top=\mathbf Y^\top\mathbf Y$$

因此我们可以重写散布矩阵如下：

$$\mathbf S_{\mathbf y}=\mathbf S_0-\frac{1}{N}\left(\sum_{n=1}^{N}\mathbf y_n\right)\left(\sum_{n=1}^{N}\mathbf y_n\right)^\top=\mathbf S_0-N\bar{\mathbf y}\bar{\mathbf y}^{\top}$$

现在我们可以将似然函数与先验相乘，得到

$$p(\boldsymbol{\mu},\boldsymbol{\Sigma}\mid\mathcal D)\propto |\boldsymbol{\Sigma}|^{-N/2}\exp\left(-\frac{N}{2}(\boldsymbol{\mu}-\bar{\mathbf y})^\top\boldsymbol{\Sigma}^{-1}(\boldsymbol{\mu}-\bar{\mathbf y})\right)\exp\left(-\frac{1}{2}\operatorname{tr}(\boldsymbol{\Sigma}^{-1}\mathbf S_{\mathbf y})\right)$$

$$\times |\boldsymbol{\Sigma}|^{-\frac{\tilde{\nu}+D+1}{2}}\exp\left(-\frac{\tilde{\kappa}}{2}(\boldsymbol{\mu}-\tilde{\mathbf m})^\top\boldsymbol{\Sigma}^{-1}(\boldsymbol{\mu}-\tilde{\mathbf m})\right)\exp\left(-\frac{1}{2}\operatorname{tr}(\boldsymbol{\Sigma}^{-1}\tilde{\mathbf S})\right)$$

$$=|\boldsymbol{\Sigma}|^{-\frac{N+\tilde{\nu}+D+2}{2}}\exp\left(-\frac{1}{2}\operatorname{tr}(\boldsymbol{\Sigma}^{-1}\mathbf M)\right)$$

其中

$$\mathbf{M} \triangleq N(\boldsymbol{\mu}-\overline{\mathbf{y}})(\boldsymbol{\mu}-\overline{\mathbf{y}})^{\top}+\tilde{\kappa}\, (\boldsymbol{\mu}-\tilde{\mathbf{m}})(\boldsymbol{\mu}-\tilde{\mathbf{m}})^{\top}+\mathbf{S}_{\mathbf{y}}+\tilde{\mathbf{S}} \tag{7.127}$$

$$= (\tilde{\kappa}+N)\boldsymbol{\mu}\boldsymbol{\mu}^{\top}-\boldsymbol{\mu}(\tilde{\kappa}\tilde{\mathbf{m}}+N\overline{\mathbf{y}})^{\top}-(\tilde{\kappa}\tilde{\mathbf{m}}+N\overline{\mathbf{y}})\boldsymbol{\mu}^{\top}+\tilde{\kappa}\tilde{\mathbf{m}}\tilde{\mathbf{m}}^{\top}+\mathbf{S}_{0}+\tilde{\mathbf{S}} \tag{7.128}$$

我们可以使用一种称为配平法（completing the square）的技巧来简化 $\mathbf{M}$ 矩阵（见 B.2.1.6 节）。将其应用于上述表达式，我们有

$$(\tilde{\kappa}+N)\boldsymbol{\mu}\boldsymbol{\mu}^{\top}-\boldsymbol{\mu}(\tilde{\kappa}\tilde{\mathbf{m}}+N\overline{\mathbf{y}})^{\top}-(\tilde{\kappa}\tilde{\mathbf{m}}+N\overline{\mathbf{y}})\boldsymbol{\mu}^{\top} \tag{7.129}$$

$$= (\tilde{\kappa}+N)\left(\boldsymbol{\mu}-\frac{\tilde{\kappa}\tilde{\mathbf{m}}+N\overline{\mathbf{y}}}{\tilde{\kappa}+N}\right)\left(\boldsymbol{\mu}-\frac{\tilde{\kappa}\tilde{\mathbf{m}}+N\overline{\mathbf{y}}}{\tilde{\kappa}+N}\right)^{\top} \tag{7.130}$$

$$-\frac{(\tilde{\kappa}\tilde{\mathbf{m}}+N\overline{\mathbf{y}})(\tilde{\kappa}\tilde{\mathbf{m}}+N\overline{\mathbf{y}})^{\top}}{\tilde{\kappa}+N} \tag{7.131}$$

$$=\tilde{\kappa}\, (\boldsymbol{\mu}-\tilde{\mathbf{m}})(\boldsymbol{\mu}-\tilde{\mathbf{m}})^{\top}-\tilde{\kappa}\tilde{\mathbf{m}}\tilde{\mathbf{m}}^{\top} \tag{7.132}$$

因此我们可以将后验分布重写如下：

$$p(\boldsymbol{\mu},\mathbf{\Sigma}|\mathcal{D})\propto |\mathbf{\Sigma}|^{-(\hat{\nu}+D+1)/2}\exp\left(-\frac{1}{2}\operatorname{tr}\left[\mathbf{\Sigma}^{-1}\left(\hat{\kappa}\, (\boldsymbol{\mu}-\hat{\mathbf{m}})(\boldsymbol{\mu}-\hat{\mathbf{m}})^{\top}+\hat{\mathbf{S}}\right)\right]\right) \tag{7.133}$$

$$=\mathrm{NIW}(\boldsymbol{\mu},\mathbf{\Sigma}\,|\,\hat{\mathbf{m}},\hat{\kappa},\hat{\nu},\hat{\mathbf{S}}) \tag{7.134}$$

其中

$$\hat{\mathbf{m}}=\frac{\tilde{\kappa}\tilde{\mathbf{m}}+N\overline{\mathbf{y}}}{\hat{\kappa}}=\frac{\tilde{\kappa}}{\tilde{\kappa}+N}\tilde{\mathbf{m}}+\frac{N}{\tilde{\kappa}+N}\overline{\mathbf{y}} \tag{7.135}$$

$$\hat{\kappa}=\tilde{\kappa}+N \tag{7.136}$$

$$\hat{\nu}=\tilde{\nu}+N \tag{7.137}$$

$$\hat{\mathbf{S}}=\tilde{\mathbf{S}}+\mathbf{S}_{\mathbf{y}}+\frac{\tilde{\kappa}\,N}{\tilde{\kappa}+N}(\overline{\mathbf{y}}-\tilde{\mathbf{m}})(\overline{\mathbf{y}}-\tilde{\mathbf{m}})^{\top} \tag{7.138}$$

这个结果其实相当直观：后验均值 $\hat{\mathbf{m}}$ 是先验均值和最大似然估计（MLE）的凸组合；后验散布矩阵 $\hat{\mathbf{S}}$ 是先验散布矩阵 $\tilde{\mathbf{S}}$ 加上经验散布矩阵 $\mathbf{S}_{\mathbf{y}}$ 再加上一个由均值不确定性引起的额外项（该不确定性产生了其自身的虚拟散布矩阵）；而后验置信因子 $\hat{\kappa}$ 和 $\hat{\nu}$ 都增加了我们所条件化的数据量大小。

### 后验边缘分布

我们已经计算了联合后验分布

$$p(\boldsymbol{\mu},\mathbf{\Sigma}|\mathcal{D})=\mathcal{N}(\boldsymbol{\mu}|\mathbf{\Sigma},\mathcal{D})p(\mathbf{\Sigma}|\mathcal{D})=\mathcal{N}\left(\boldsymbol{\mu}\,|\,\hat{\mathbf{m}},\frac{1}{\hat{\kappa}}\mathbf{\Sigma}\right)\mathrm{IW}(\mathbf{\Sigma}\,|\,\hat{\mathbf{S}},\hat{\nu}) \tag{7.140}$$

我们现在讨论如何计算后验边缘分布 $p(\mathbf{\Sigma}|\mathcal{D})$ 和 $p(\boldsymbol{\mu}|\mathcal{D})$。

很容易看出 $\Sigma$ 的后验边缘分布为

$$p(\mathbf{\Sigma}|\mathcal{D}) = \int p(\boldsymbol{\mu}, \mathbf{\Sigma}|\mathcal{D}) d\boldsymbol{\mu} = \mathrm{IW}(\mathbf{\Sigma}|\widehat{\mathbf{S}}, \hat{\nu}) \tag{7.141}$$

对于均值，可以证明

$$p(\boldsymbol{\mu}|\mathcal{D}) = \int p(\boldsymbol{\mu}, \mathbf{\Sigma}|\mathcal{D}) d\mathbf{\Sigma} = \mathcal{T}\left(\boldsymbol{\mu} \mid \widehat{\boldsymbol{\mu}}, \frac{\widehat{\mathbf{S}}}{\hat{\kappa}\hat{\nu}'}, \hat{\nu}'\right) \tag{7.142}$$

其中 $\hat{\nu}' \triangleq \hat{\nu} - D + 1$。从直觉上理解，这是因为 $p(\boldsymbol{\mu}|\mathcal{D})$ 是无穷多个高斯分布的混合，其中每个混合组件的 $\mathbf{\Sigma}$ 值是从 IW 分布中抽取的；通过混合所有这些，我们诱导出了一个具有比单个高斯分布更重尾巴的 Student 分布。

### 后验预测

遵循 7.2.2.4 节，我们现在讨论如何通过积分消去参数来预测未来数据。如果 $\mathbf{y} \sim \mathcal{N}(\boldsymbol{\mu}, \mathbf{\Sigma})$，且 $(\boldsymbol{\mu}, \mathbf{\Sigma}|\mathcal{D}) \sim \mathrm{NIW}(\widehat{\mathbf{m}}, \hat{\kappa}, \hat{\nu}, \widehat{\mathbf{S}})$，则可以证明对于单个观测向量的后验预测分布如下：

$$p(\mathbf{y}|\mathcal{D}) = \int \mathcal{N}(\mathbf{x}|\boldsymbol{\mu}, \mathbf{\Sigma}) \mathrm{NIW}(\boldsymbol{\mu}, \mathbf{\Sigma} | \widehat{\mathbf{m}}, \hat{\kappa}, \hat{\nu}, \widehat{\mathbf{S}}) d\boldsymbol{\mu} d\mathbf{\Sigma} \tag{7.143}$$

$$= \mathcal{T}\left(\mathbf{y} \mid \widehat{\mathbf{m}}, \frac{\widehat{\mathbf{S}} (\hat{\kappa}+1)}{\hat{\kappa}\hat{\nu}'}, \hat{\nu}'\right) \tag{7.144}$$

其中 $\hat{\nu}' = \hat{\nu} - D + 1$。

## 7.2.5 超越共轭先验

我们看到了各种共轭先验的例子，它们都来自指数族（参见 12.2 节）。这些先验的优点在于易于解释（就来自虚拟先验数据集的充分统计量而言）且易于计算。然而，对于大多数模型来说，指数族中不存在与似然函数共轭的先验。此外，即使存在共轭先验，共轭性的假设也可能过于局限。因此，在下面的章节中，我们简要讨论了其他各种类型的先验。

## 7.3 非信息先验

当我们拥有很少或没有特定领域知识时，使用**无信息**、**非信息**或**客观**先验是理想的，以便“让数据自己说话”。不幸的是，定义这类先验并没有唯一的方法，而且它们都编码了某种知识。因此，最好使用**弥散先验**、**最小信息先验**或**默认先验**这些术语。

作为无信息先验难度的一个例子，考虑伯努利参数 $\theta \in [0,1]$。人们可能认为最无信息的先验是均匀分布，Beta(1,1)。（拉普拉斯基于他所谓的**充分理由原理**主张使用这种先验，以偏爱任何其他分布。）然而，这种先验在对数几率 $\eta = \log(\theta/(1-\theta))$ 上并不是均匀的，

