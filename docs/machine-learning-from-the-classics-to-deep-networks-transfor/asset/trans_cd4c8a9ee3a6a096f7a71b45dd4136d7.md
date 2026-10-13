

## 拉普拉斯特征映射目标函数推导

拉普拉斯特征映射的目标函数定义为：

$$E_{L} = \sum_{i=1}^{N}\sum_{j=1}^{N}||\mathbf{z}_{i} - \mathbf{z}_{j}||^{2}W(i,j).$$

![Equation](images/B9780443292385000263/si492.png)

现在我们重新表述公式 [(20.108)](#Chp020_1103-1179_B9780443292385000263.xhtml#deq165)。经过简单的代数变换，我们得到：

$$E_{L} = \sum_{i}z_{i}^{2}\sum_{j}W(i,j) + \sum_{j}z_{j}^{2}\sum_{i}W(i,j) - 2\sum_{i}\sum_{j}z_{i}z_{j}W(i,j) = \sum_{i}z_{i}^{2}D_{ii} + \sum_{j}z_{j}^{2}D_{jj} - 2\sum_{i}\sum_{j}z_{i}z_{j}W(i,j) = 2\mathbf{z}^{T}L\mathbf{z},$$

![Equation](images/B9780443292385000263/si493.png)

(20.109)

其中

![Equation](images/B9780443292385000263/fx011.jpg)

(20.110)

