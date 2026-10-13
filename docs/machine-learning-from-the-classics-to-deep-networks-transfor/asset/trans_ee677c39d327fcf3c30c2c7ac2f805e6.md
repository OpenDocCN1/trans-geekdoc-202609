

### 几何平均规则

该规则是通过最小化 Kullback-Leibler 散度的替代公式得出的（注意 KL 散度不对称）；换句话说，

$$D_{j} = \sum\limits_{i = 1}^{M}P_{j}(\omega_{i}|\mathbf{x})\ln\frac{P_{j}(\omega_{i}|\mathbf{x})}{P(\omega_{i}|\mathbf{x})}.$$

![Equation](images/B9780443292385000135/si313.png)

$$D_{j} = \sum\limits_{i = 1}^{M}P(\omega_{i}|\mathbf{x})\ln\frac{P(\omega_{i}|\mathbf{x})}{P_{j}(\omega_{i}|\mathbf{x})},$$

![Equation](images/B9780443292385000135/si314.png)

其结果为（问题 [7.17](#Chp007_293-342_B9780443292385000135.xhtml#o0090)）：

![Equation](images/B9780443292385000135/fx013.jpg) (7.77)

### 堆叠法

另一种方法是使用各个分类器输出的加权平均，其中组合权重通过训练数据最优获得。假设每个单独分类器的输出 $f_{j}(\mathbf{x})$ 是软类型的，例如后验概率的估计。则组合输出由下式给出：

$$f(\mathbf{x}) = \sum\limits_{j = 1}^{L}w_{j}f_{j}(\mathbf{x}),$$

![Equation](images/B9780443292385000135/si316.png) (7.78)

其中权重通过以下优化任务估计：

