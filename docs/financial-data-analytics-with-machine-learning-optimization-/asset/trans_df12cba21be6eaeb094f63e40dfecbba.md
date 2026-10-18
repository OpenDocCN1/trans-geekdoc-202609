

10. 对拟合残差进行 Shapiro–Wilk 诊断检验时，为简化记号，记其为 $\hat{\epsilon}_i$'s，检验统计量变为

$$W = \frac{\left(\sum_{i=1}^{n} a_i \hat{\epsilon}_{(i)}\right)^2}{\sum_{i=1}^{n} \left(\bar{\hat{\epsilon}} - \hat{\epsilon}_i\right)^2}$$

由于 $\hat{\epsilon}_i = \epsilon_i + O_p\left(\frac{1}{\sqrt{n}}\right)$，其中 $\epsilon_i$'s 为独立同分布的真随机噪声，且回顾 $\mathbf{a}$ 为单位向量，分子等于

$$\left(\sum_{i=1}^{n} a_i \epsilon_{(i)}\right)^2 + 2 \sum_{i \neq j} a_i a_j \epsilon_{(i)} O_p\left(\frac{1}{\sqrt{n}}\right) + \text{higher order terms}$$

其首项 $\left(\sum_{i=1}^{n} a_i \epsilon_{(i)}\right)^2 \approx \sum_{i=1}^{n} a_i^2 \cdot \sum_{i=1}^{n} \epsilon_i^2 = \sum_{i=1}^{n} \epsilon_i^2 \approx O_p(n)$；而对第二个交叉项的平方应用柯西–施瓦茨不等式，

$$\left(\sum_{i,j; i \neq j} a_i a_j \epsilon_{(i)} O_p\left(\frac{1}{\sqrt{n}}\right)\right)^2 \leq \left(\sum_{j=1}^{n} a_j \sum_{i \neq j} a_i O_p\left(\frac{1}{\sqrt{n}}\right)\right)^2 \leq \sum_{j=1}^{n} a_j^2 \cdot \left(\sum_{i \neq j} a_i O_p\left(\frac{1}{\sqrt{n}}\right)\right)^2 \leq \sum_{j=1}^{n} a_j^2 \cdot \sum_{i=1}^{n} a_i^2 \cdot \sum_{i=1}^{n} O_p\left(\frac{1}{n}\right) = O_p(1)$$

因此，分子中占主导地位的是首项 $\left(\sum_{i=1}^{n} a_i \epsilon_{(i)}\right)^2$。同样，分母 $\sum_{i=1}^{n} \left(\bar{\hat{\epsilon}} - \hat{\epsilon}_i\right)^2$ 由仅涉及真随机噪声的项 $\sum_{i=1}^{n} \left(\bar{\epsilon} - \epsilon_i\right)^2$ 所主导。因此，对原始检验统计量直接代入是合理的。

