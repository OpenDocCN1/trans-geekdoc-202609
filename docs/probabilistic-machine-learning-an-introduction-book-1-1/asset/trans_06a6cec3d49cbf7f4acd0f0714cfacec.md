

上述目标是一个包含 $N$ 个变量的二次规划问题。标准 QP 求解器需要 $O(N^3)$ 时间。然而，针对这一问题已经开发出避免使用通用 QP 求解器的专门算法，例如序列**最小优化**（SMO）算法 [Pl98]，其时间复杂度为 $O(N)$ 到 $O(N^2)$。

由于这是一个凸目标函数，解必须满足 KKT 条件（第 5.5.2 节），这些条件告诉我们以下性质成立：

$$
\begin{aligned}
\alpha_n &\ge 0 &&\tag{17.115}\\
\tilde y_n f(x_n)-1 &\ge 0 &&\tag{17.116}\\
\alpha_n\bigl(\tilde y_n f(x_n)-1\bigr) &= 0 &&\tag{17.117}
\end{aligned}
$$

因此，要么 $\alpha_n=0$（此时在计算 $\hat{\mathbf w}$ 时样本 $n$ 被忽略），要么约束 $\tilde y_n(\hat{\mathbf w}^{\mathsf T}\mathbf x_n+\hat w_0)=1$ 是活跃的。后一种情况意味着样本 $n$ 位于间隔边界上；这些点被称为**支持向量**，如图 17.15(b) 所示。我们用 $\mathcal S$ 表示支持向量集合。

为了进行预测，我们使用

$$f(\mathbf{x};\hat{\mathbf w},\hat w_0)=\hat{\mathbf w}^{\mathsf T}\mathbf x+\hat w_0=\sum_{n\in\mathcal S}\alpha_n\tilde y_n\mathbf x_n^{\mathsf T}\mathbf x+\hat w_0 \tag{17.118}$$

为了求解 $\hat w_0$，我们可以利用如下事实：对于任何支持向量，都有 $\tilde y_n f(\mathbf x;\hat{\mathbf w},\hat w_0)=1$。将两边同时乘以 $\tilde y_n$，并利用 $\tilde y_n^2=1$，我们得到 $\hat w_0=\tilde y_n-\hat{\mathbf w}^{\mathsf T}\mathbf x_n$。在实践中，对所有支持向量取平均可以得到更好的结果：

$$\hat w_0=\frac{1}{|\mathcal S|}\sum_{n\in\mathcal S}(\tilde y_n-\hat{\mathbf w}^{\mathsf T}\mathbf x_n)=\frac{1}{|\mathcal S|}\sum_{n\in\mathcal S}\left(\tilde y_n-\sum_{m\in\mathcal S}\alpha_m\tilde y_m\mathbf x_m^{\mathsf T}\mathbf x_n\right) \tag{17.119}$$

## 17.5.3 软间隔分类器

如果数据不是线性可分的，则不存在对所有 $n$ 都满足 $\tilde y_n f_n\ge 1$ 的可行解。因此，我们引入**松弛变量** $\xi_n\ge 0$，并将 $\tilde y_n f_n\ge 1$ 的硬约束替换为 $\tilde y_n f_n\ge 1-\xi_n$ 的**软间隔约束**。新的目标函数变为

$$\min_{\mathbf w,w_0,\boldsymbol\xi}\ \frac{1}{2}\|\mathbf w\|^2+C\sum_{n=1}^{N}\xi_n\quad \text{s.t.}\quad \xi_n\ge 0,\quad \tilde y_n(\mathbf x_n^{\mathsf T}\mathbf w+w_0)\ge 1-\xi_n \tag{17.120}$$

其中 $C\ge 0$ 是一个超参数，控制我们允许有多少个点违反间隔约束。（如果 $C=\infty$，则恢复为无正则化的硬间隔分类器。）

软间隔分类器对应的拉格朗日函数变为

$$\mathcal L(\mathbf w,w_0,\boldsymbol\alpha,\boldsymbol\xi,\boldsymbol\mu)=\frac{1}{2}\mathbf w^{\mathsf T}\mathbf w+C\sum_{n=1}^{N}\xi_n-\sum_{n=1}^{N}\alpha_n\bigl(\tilde y_n(\mathbf w^{\mathsf T}\mathbf x_n+w_0)-1+\xi_n\bigr)-\sum_{n=1}^{N}\mu_n\xi_n \tag{17.121}$$

其中 $\alpha_n\ge 0$ 和 $\mu_n\ge 0$ 是拉格朗日乘子。消去 $\mathbf w$、$w_0$ 和 $\boldsymbol\xi$ 后得到对偶形式

$$\mathcal L(\boldsymbol\alpha)=\sum_{i=1}^{N}\alpha_i-\frac{1}{2}\sum_{i=1}^{N}\sum_{j=1}^{N}\alpha_i\alpha_j\tilde y_i\tilde y_j\mathbf x_i^{\mathsf T}\mathbf x_j \tag{17.122}$$

这与硬间隔情形相同；但约束条件不同。特别地，KKT 条件蕴含

$$0 \le \alpha_n \le C \tag{17.123}$$

$$\sum_{n=1}^N \alpha_n \tilde{y}_n = 0 \tag{17.124}$$

如果 $\alpha_n = 0$，则该点被忽略。如果 $0 < \alpha_n < C$，则 $\xi_n = 0$，因此该点位于间隔上。如果 $\alpha_n = C$，该点可以位于间隔内部，并且当 $\xi_n \le 1$ 时被正确分类，当 $\xi_n > 1$ 时被错误分类。参见图 17.15(b) 的示意。因此，$\sum_n \xi_n$ 是误分类点数量的一个上界。

与之前一样，偏置项可以使用下式计算

$$\hat{w}_0 = \frac{1}{|\mathcal{M}|} \sum_{n \in \mathcal{M}} \left( \tilde{y}_n - \sum_{m \in \mathcal{S}} \alpha_m \tilde{y}_m \mathbf{x}_m^\top \mathbf{x}_n \right) \tag{17.125}$$

其中 $\mathcal{M}$ 是满足 $0 < \alpha_n < C$ 的点的集合。

还有一种软间隔 SVM 的替代形式，称为 $\nu$-SVM 分类器 [Sch+00]。它涉及最大化

$$\mathcal{L}(\boldsymbol{\alpha}) = -\frac{1}{2} \sum_{i=1}^N \sum_{j=1}^N \alpha_i \alpha_j \tilde{y}_i \tilde{y}_j \mathbf{x}_i^\top \mathbf{x}_j \tag{17.126}$$

并满足约束

$$0 \le \alpha_n \le 1/N \tag{17.127}$$

$$\sum_{n=1}^N \alpha_n \tilde{y}_n = 0 \tag{17.128}$$

$$\sum_{n=1}^N \alpha_n \ge \nu \tag{17.129}$$

其优点是，替代 $C$ 的参数 $\nu$ 可以被解释为间隔错误（即 $\xi_n > 0$ 的点）比例的上界，同时也是支持向量数量的下界。

## 17.5.4 核技巧

到目前为止，我们已经将大间隔二分类问题转化为包含 $N$ 个未知数 $(\boldsymbol{\alpha})$ 的对偶问题，其求解通常需要 $O(N^3)$ 时间，这可能很慢。然而，对偶问题的主要好处在于，我们可以用对正定（Mercer）核函数 $\mathcal{K}(\mathbf{x}, \mathbf{x}')$ 的调用来替换所有内积运算 $\mathbf{x}^\top \mathbf{x}'$。这被称为核技巧。

特别地，我们可以将式 (17.118) 中的预测函数重写如下：

$$f(\mathbf{x}) = \hat{\mathbf{w}}^\top \mathbf{x} + \hat{w}_0 = \sum_{n \in \mathcal{S}} \alpha_n \tilde{y}_n \mathbf{x}_n^\top \mathbf{x} + \hat{w}_0 = \sum_{n \in \mathcal{S}} \alpha_n \tilde{y}_n \mathcal{K}(\mathbf{x}_n, \mathbf{x}) + \hat{w}_0 \tag{17.130}$$

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_578_0.png)

图 17.17：三种不同方法的对数几率与 \(x\) 的关系。改编自 [Tip01] 的图 10。经 Mike Tipping 善意许可使用。

我们还需要对偏置项进行核化。这可以通过将式 (17.119) 核化来实现：

$$\hat{w}_0 = \frac{1}{|\mathcal{S}|} \sum_{i\in\mathcal{S}} \left( \tilde{y}_i - \left(\sum_{j\in\mathcal{S}} \hat{\alpha}_j \tilde{y}_j \mathbf{x}_j \right)^\top \mathbf{x}_i \right) = \frac{1}{|\mathcal{S}|} \sum_{i\in\mathcal{S}} \left( \tilde{y}_i - \left(\sum_{j\in\mathcal{S}} \hat{\alpha}_j \tilde{y}_j \mathcal{K}(\mathbf{x}_j, \mathbf{x}_i) \right) \right) \tag{17.131}$$

核技巧使我们不必处理数据的显式特征表示，并使我们能够轻松地将分类器应用于结构化对象，例如字符串和图。

## 17.5.5 将 SVM 输出转换为概率

SVM 分类器产生一个硬标签输出 $\hat{y}(\mathbf{x}) = \operatorname{sign}(f(\mathbf{x}))$。然而，我们通常希望得到预测的置信度度量。一种启发式方法是将 $f(\mathbf{x})$ 解释为对数几率比 $\log \frac{p(y=1|\mathbf{x})}{p(y=0|\mathbf{x})}$。然后我们可以使用下式将 SVM 的输出转换为概率：

$$p(y=1|\mathbf{x},\boldsymbol{\theta}) = \sigma\big(a f(\mathbf{x}) + b\big) \tag{17.132}$$

其中 $a$、$b$ 可以通过在单独的验证集上进行最大似然估计来得到。（使用训练集来估计 $a$ 和 $b$ 会导致严重的过拟合。）该技术最早由 [Pla00] 提出，被称为 Platt 缩放。

然而，由此得到的概率校准效果并不特别好，因为在 SVM 训练过程中没有任何依据可以将 $f(\mathbf{x})$ 解释为对数几率比。为了说明这一点，考虑 [Tip01] 中的一个例子。假设我们有一维数据，其中 $p(x|y=0)=\text{Unif}(0,1)$，$p(x|y=1)=\text{Unif}(0.5,1.5)$。由于类条件分布在 $[0.5,1]$ 区间内重叠，类别 1 相对于类别 0 的对数几率在该区域应为零，而在该区域之外应为无穷大。我们从模型中采样了 1000 个点，然后拟合了一个概率核分类器（相关向量机，在第 17.6.1 节中描述）和一个宽度为 0.1 的高斯核 SVM。两种模型都能完美捕捉决策边界，并达到 25% 的泛化误差，这是该问题的最优贝叶斯误差。RVM 的概率输出是对真实对数几率的一个良好近似，但 SVM 并非如此，如图 17.17 所示。

