

### 12.2.1 ML 估计器

$$
\Phi = \begin{bmatrix} 
\mathbf{\phi}^{T}(\mathbf{x}_{1}) \\ 
\mathbf{\phi}^{T}(\mathbf{x}_{2}) \\ 
\vdots \\ 
\mathbf{\phi}^{T}(\mathbf{x}_{N}) 
\end{bmatrix}
$$

(12.4)

和

**y** = [*y*[1], *y*[2], …, *y*[*N*]]^(*T*)。

在公式 [(3.61)](#Chp003_65-117_B9780443292385000093.xhtml) 中，简单地用 Φ 替换 *X*，即可将 ML 估计改为

$$
\widehat{\mathbf{\theta}}_{ML} = \left( \Phi^{T}\Sigma_{\eta}^{- 1}\Phi \right)^{- 1}\Phi^{T}\Sigma_{\eta}^{- 1}\mathbf{y}.
$$

(12.5)。

对于方差相等且不相关的噪声样本这一简单情况 *σ*[*η*]² (*Σ*[*η*] = *σ*[*η*]²*I*)，公式 [(12.5)](#Chp012_583-634_B9780443292385000184.xhtml#deq8) 变得与最小二乘 (LS) 解相同

$$
\widehat{\mathbf{\theta}}_{ML} = \left( \Phi^{T}\Phi \right)^{- 1}\Phi^{T}\mathbf{y} = \widehat{\mathbf{\theta}}_{LS}.
$$

(12.6)。

ML 方法的**一个主要缺点**是它容易过拟合，因为它不关心那些试图“学习”特定训练集细节的复杂模型，正如第 [3](#Chp003_65-117_B9780443292385000093.xhtml) 章中已经讨论的那样。

### 12.2.2 MAP 估计器

根据最大后验概率 (MAP) 方法，未知参数集被视为随机向量 **θ**，对于给定的一组输出观测值 **y**，其后验概率表示为

$$
p(\mathbf{\theta}|\mathbf{y}) = \frac{p(\mathbf{y}|\mathbf{\theta})p(\mathbf{\theta})}{p(\mathbf{y})},
$$

(12.7)

