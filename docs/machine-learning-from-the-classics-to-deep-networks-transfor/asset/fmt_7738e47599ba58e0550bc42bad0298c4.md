
对于这个高阶多项式拟合的实验设置，以下推理成立。每个点 $x_n$ 处的偏差项为零，因为

$$
\mathbb{E}_{\mathcal{D}}[f_2(x_n;\mathcal{D})] = \mathbb{E}_{\mathcal{D}}[g(x_n)+\eta] = g(x_n) = \mathbb{E}_{\mathcal{D}}[y|x_n].
$$

另一方面，点 $x_n$ ($n=1,2,\dots,N$) 处的方差项预计会很大，因为

$$
\mathbb{E}_{\mathcal{D}} \left[(f_2(x_n;\mathcal{D})-g(x_n))^2\right] = \mathbb{E}_{\mathcal{D}} \left[(g(x_n)+\eta-g(x_n))^2\right] = \sigma_\eta^2.
$$

假设函数 $f_2$ 和 $g$ 足够连续平滑，且点 $x_n$ 采样得足够密集以覆盖实轴上的感兴趣区间，我们预期在所有点 $x \neq x_n$ 处会有类似的行为。

### 示例 3.6

这是一个建立在前一个示例基础上的更现实的例子。数据生成方式与之前相同，通过回归模型（公式 [(3.54)](#Chp003_65-117_B9780443292385000093.xhtml#deq93)）使用五阶多项式作为 $g$。训练点数量等于 $N=10$，并生成了 1000 个训练集 $\mathcal{D}_i$ ($i=1,2,\dots,1000$)。已经运行了两组实验。
