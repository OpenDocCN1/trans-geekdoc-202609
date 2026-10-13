
### 局部代价函数与梯度下降更新

$$
\widetilde{J}_{k}^{\text{loc}}(\boldsymbol{\theta}) = \sum_{m \in \mathcal{N}_{k}} c_{mk} J_{m}(\boldsymbol{\theta}) + \lambda \|\boldsymbol{\theta} - \widetilde{\boldsymbol{\theta}}\|^{2}
$$
(5.84)

其中 $\widetilde{\boldsymbol{\theta}}$ 编码了关于未知向量的信息，该信息由邻居节点获得；$\lambda > 0$。对公式 [(5.84)](#Chp005_177-248_B9780443292385000111.xhtml#deq187) 应用梯度下降（并将指数产生的因子“2”吸收进步长中），可得：

$$
\boldsymbol{\theta}_{k}^{(i)} = \boldsymbol{\theta}_{k}^{(i - 1)} + \mu_{k} \sum_{m \in \mathcal{N}_{k}} c_{mk} \left( \boldsymbol{p}_{m} - \boldsymbol{\Sigma}_{x_{m}} \boldsymbol{\theta}_{k}^{(i - 1)} \right) + \mu_{k} \lambda \left( \widetilde{\boldsymbol{\theta}} - \boldsymbol{\theta}_{k}^{(i - 1)} \right)
$$
(5.85)

该更新可分解为以下两个步骤：
