

## 数学推导

$$t_{n} = \left. \sigma\left( \mathbf{\theta}^{T}\mathbf{\phi}(\mathbf{x}_{n}) \right)\left( 1 - \sigma\left( \mathbf{\theta}^{T}\mathbf{\phi}(\mathbf{x}_{n}) \right) \right) \right|_{\mathbf{\theta} = {\widehat{\mathbf{\theta}}}_{MAP}}.$$

![Equation](images/B9780443292385000196/si283.png)

### 步骤 3
得到 ${\widehat{\mathbf{\theta}}}_{MAP}$ ![Equation](images/B9780443292385000196/si279.png) 并计算 $\Sigma$ 后，将公式 [(12.37)](#Chp012_583-634_B9780443292385000184.xhtml) 适配到我们当前的符号表示中，可得

$$P(\mathbf{y}|\mathbf{\alpha}) = P(\mathbf{y}|{\widehat{\mathbf{\theta}}}_{MAP})p({\widehat{\mathbf{\theta}}}_{MAP}|\mathbf{\alpha}){(2\pi)}^{\frac{N}{2}}|\Sigma|^{1/2}.$$

![Equation](images/B9780443292385000196/si284.png) (13.76)

### 步骤 4
接下来，对公式 [(13.76)](#Chp013_635-716_B9780443292385000196.xhtml#deq110) 关于 $\alpha$ 进行最大化，可得到更新的迭代估计值。请注意，右侧乘积的第一项与 $\alpha$ 无关。取对数并最大化可轻松得到（问题 [13.15](#Chp013_635-716_B9780443292385000196.xhtml#o0175)）

$$- \frac{1}{2}\theta_{{MAP},k}^{2} + \frac{1}{2\alpha_{k}} - \frac{1}{2}\Sigma_{kk} = 0.$$

![Equation](images/B9780443292385000196/si285.png) (13.77)

### 步骤 5
因为 $\Sigma[kk]$ ![Equation](images/B9780443292385000196/si230.png) 和 $\theta[MAP, k]$ ![Equation](images/B9780443292385000196/si286.png) 依赖于 $\alpha$，该方程通过迭代求解，其结果与公式 (13.62) 中的方案完全相同，即

