

$$
\widehat{p}(\mathbf{x}_{1:n}|\mathbf{y}_{1:n}) = \sum\limits_{i = 1}^{N}W_{n}^{(i)}\delta\left( \mathbf{x}_{1:n} - \mathbf{x}_{1:n}^{(i)} \right).
$$

![Equation](images/B9780443292385000238/si161.png)

如前所述，如果我们的兴趣仅在于保留终端样本 $\mathbf{x}_{n}^{(i)}$，即丢弃路径历史 $\mathbf{x}_{1:n-1}^{(i)}$，则可以写成

$$
\widehat{p}(\mathbf{x}_{n}|\mathbf{y}_{1:n}) = \sum\limits_{i = 1}^{N}W_{n}^{(i)}\delta\left( \mathbf{x}_{n} - \mathbf{x}_{n}^{(i)} \right).
$$

![Equation](images/B9780443292385000238/si164.png)

请注意，随着粒子数量 $N$ 趋于无穷大，上述近似将趋向于真实的后验概率密度。[图 17.3](#Chp017_855-884_B9780443292385000238.xhtml#f0025) 给出了 SIS [算法 17.4](#Chp017_855-884_B9780443292385000238.xhtml#enun0030) 的图形解释。

![Figure 17.3 Three consecutive recursions, for the particle filtering scheme given in Algorithm 17.4, with N = 6 streams of particles. The area of the circles corresponds to the size of the normalized weights of the respective particles drawn from the proposal distribution.](images/B9780443292385000238/gr003.jpg)

[图 17.3](#Chp017_855-884_B9780443292385000238.xhtml#cf0420) 显示了 [算法 17.4](#Chp017_855-884_B9780443292385000238.xhtml#enun0030) 给出的粒子滤波方案的三次连续递归，$N$ = 6 条粒子流。圆的面积对应于从建议分布中抽取的相应粒子的归一化权重的大小。

### 示例 17.1

考虑写作如下的一维随机游走模型

$$
x[n] = x[n-1] + \eta[n], \tag{17.38}
$$

![Equation](images/B9780443292385000238/si165.png)

$$
y[n] = x[n] + v[n], \tag{17.39}
$$

![Equation](images/B9780443292385000238/si166.png)

