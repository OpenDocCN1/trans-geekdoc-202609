

²¹Apley, Daniel. W., and Jingyu Zhu. "Visualizing the effects of predictor variables in black box supervised learning models." Journal of the Royal Statistical Society: Series B (Statistical Methodology) 82.4 (2020): 1059–1086.

## 7.4 函数分解 (FUNCTIONAL DECOMPOSITION)

该公式看起来与函数分解非常相似，但有两个主要的修改。修改 1：排除所有的交互作用，只保留截距和主效应。修改 2：主效应只能是线性的，即 $f_j(x_j) = \beta_jx_j$。从函数分解的角度来看线性回归模型，模型本身代表了将特征映射到目标的真函数的函数分解，但在强假设下进行，即效应是线性效应且不存在交互作用。

广义加性模型（GAM）通过使用样条允许更灵活的函数 $f_j$，从而放宽了第二个假设。也可以添加交互作用，但这个过程是手动的。像 GA2M 这样的方法尝试自动向 GAM 中添加 n 路交互作用。^{22}

将线性回归模型或 GAM 视为函数分解也可能导致困惑。如果你应用本章早前的分解方法（广义函数 ANOVA 和累积局部效应），你可能会得到与直接从 GAM 中读取的不同的组件。当在 GAM 中对相关特征的交互作用进行建模时，就会发生这种情况。差异是因为其他函数分解方法通过交互作用和主效应以不同的方式划分特征。

那么，什么时候使用 GAM 而不是复杂模型 + 分解？当大多数交互作用为零时，你应该坚持使用 GAM，特别是当不存在三个或更多特征的交互作用时。如果我们知道参与交互的特征最大数目为 $|S|\le2$，那么我们就使用 MARS 或 GA2M 等方法。模型在测试数据上的性能可能表明 GAM 是否足够，或者更复杂的模型表现更好。

### 7.4.8 奖励：部分依赖图 (Partial Dependence Plot)

部分依赖图也提供函数分解吗？简单回答是：不是。详细回答是：特征集 $S$ 的部分依赖图始终包含层级的所有效应——$[1,2]$ 的 PDP 不仅包含交互，还包含单个特征效应。因此，添加所有子集的 PDP 并不会产生原始函数，所以这不是有效的分解。但可以调整 PDP，例如移除所有低级效应吗？是的，可以，但我们将得到类似于函数 ANOVA 的东西。然而，PDP 不是在均匀分布上积分，而是在 $X_{-S}$ 的边缘分布上积分，后者是通过蒙特卡洛采样估计的。

> 22Caruana, Rich, et al. "Intelligible models for healthcare: Predicting pneumonia risk and hospital 30-day readmission." Proceedings of the 21th ACM SIGKDD international conference on knowledge discovery and data mining. (2015).

### 7.4.9 优点

我认为函数分解是机器学习可解释性的核心概念。

函数分解为我们将高维且复杂的机器学习模型分解为单个效应和交互作用提供了理论依据——这是一个必要的步骤，允许我们解释单个效应。函数分解是统计回归模型、ALE、（广义）函数 ANOVA、PDP、H 统计量和 ICE 曲线等技术的核心思想。

函数分解还为理解其他方法提供了帮助。例如，排列特征重要性（permutation feature importance）打破了特征与目标之间的关联。从函数分解的角度看，我们可以看到排列“破坏”了特征中所有组件的效应。这影响了特征的主效应，以及与其他特征的所有交互作用。作为另一个例子，Shapley 值将预测结果分解为单个特征的加性效应。函数分解告诉我们分解中也应该存在交互效应，那么它们在哪里呢？Shapley 值对单个特征提供了公平的效应归因，这意味着所有交互作用都公平地归于特征，并在 Shapley 值之间分配。

在考虑函数函数分解工具时，ALE 图提供了许多优势。ALE 图提供了一种计算快速、具有软件实现（参见 ALE 章节）并具有理想伪正交特性的函数分解。

### 7.4.10 缺点

函数分解的概念在处理两个特征之间的高维组件时很快达到了局限。不仅特征数量的指数级爆炸限制了实用性（因为我们无法轻易可视化高阶交互作用），而且如果我们计算所有交互作用，计算时间将是惊人的。

每种函数分解方法都有各自的缺点。自底上的方法——构建回归模型——是一个手动过程，并对模型施加了许多影响预测性能的限制。函数 ANOVA 需要特征独立。广义函数 ANOVA 很难估计。累积局部效应图不提供方差分解。

函数分解方法更适用于分析表格数据，而不是文本或图像。

## 7.5 排列特征重要性 (Permutation Feature Importance)

排列特征重要性衡量了我们在排列特征值后模型预测误差的增加，这打破了特征与真实内容之间的关系。

### 7.5.1 理论

这个概念非常直观：我们通过计算排列特征后模型预测误差的增加来衡量特征的重要性。如果洗乱其值增加了模型误差，则该特征是“重要的”。

基于 Fisher, Rudin, 和 Dominici (2018) 的排列特征重要性算法：

输入：训练好的模型 $f$，特征矩阵 $X$，目标向量 $y$，误差度量 $L(y, \hat{f})$。

- 1. 估计原始误差 $e_{orig}$
- 2. 对于每个特征 $j \in \{1, \dots, p\}$：
   - 通过排列 $j$ 生成特征矩阵 $X_{perm}$。
   - 估计误差 $e_{perm} = L(y, \hat{f}(X_{perm}))$
   - 计算重要性 $FI = e_{perm}/e_{orig}$
- 3. 按 $FI$ 降序对特征排序。

Fisher, Rudin, 和 Dominici (2018) 建议将数据集分成两半以查看重要性是否具有通用性。23Breiman, "Random Forests." Machine Learning 45 (2001). $^{24Fisher, Aaron, Cynthia Rudin and Francesca Dominici. "All models are wrong, but many are useful: Learning a variable's importance." http://arxiv.org/abs/1801.01418

