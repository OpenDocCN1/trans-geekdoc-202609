
## 注释

### 1.
选择 `IPW` 方法而非其他常见的倾向得分匹配方法（如主分层，也称为亚分类）的原因在于，该权重可直接用于提升建模的结局回归。然而，主分层本质上是在分层（组）层面进行加权，而非个体层面。因此，要使用主分层，只需将治疗组和对照组的分层特异性比例用作 (8.5) 的分母；有关分层加权描述的细节，请参阅 [Imbens 和 Rubin (2015)](#chapter9.xhtml#ref9_19) 第 17.8 节，Lunceford 和 Davidian (2004) 对两种方法的比较。 [Abrevaya 等 (2015)](#chapter9.xhtml#ref9_1) 和 [Athey 和 Imbens (2015)](#chapter9.xhtml#ref9_2) 也提出使用 `IPW` 方法计算条件平均处理效应 (`CATE`)，这等价于对观察数据的提升建模。 [⏎](#chapter9.xhtml#en9_19b)

### 2.
Eqn. (9.5) 中的权重本质上是在衡量整个总体上的平均处理效应 (`ATE`)，而非接受治疗者的平均处理效应 (`ATT`) 或对照者的平均处理效应 (`ATC`)。另外，与衡量总体效应不同，提升建模可能会寻找未接受治疗个体的个体（或亚组）因果效应；即如果一个未接受治疗的个体接受治疗会怎样？因此，在某些情况下应用 `ATT` 或 `ATC` 的权重更为合适；有关计算 `ATC` 情况的数学证明，请参阅 [附录 9.3](#chapter9.xhtml#app9_3)。第 286 页 [⏎](#chapter9.xhtml#en9_29b)

### 3.
这被称为稳定权重，而非分子等于 1 的不稳定权重。稳定权重具有降低变异性的潜在优势；请参阅 Hernan 和 Robins (2016) 第 12.4 节。它们还使伪样本的大小与原始样本相同；有关细节请参阅 [Hernan 和 Robins (2005)](#chapter9.xhtml#ref9_17)。(9.5)、(9.5a) 和 (9.5b) 中的 `P(T)` 和 `1 − P(T)` 常量分量都具有稳定作用。 [⏎](#chapter9.xhtml#en9_39b)

### 4.
由于我们感兴趣的是在某些特征条件下的处理效应而非总体效应，因此除了平均处理效应 (`ATE`)、对照者的平均处理效应 (`ATC`) 和接受治疗者的平均处理效应 (`ATT`) 外，我们在技术上可以分别称它们为条件 ATE（或 `CATE`）、条件 ATC 和条件 ATT。 [⏎](#chapter9.xhtml#en9_49b)

### 5.
例如，请参阅 Hernan 和 Robins (2016) 第 12.5 节，其中估计了 `Marginal Structural Model` 以及效应修饰。另请参阅 VanderWeele (2009)，以了解流行病学中“交互作用”（两种治疗之间）与效应修饰（治疗与协变量之间的交互作用）之间的区别。 [⏎](#chapter9.xhtml#en9_59b)

### 6.
例如，请参阅 [Freedman 和 Berk (2008)](#chapter9.xhtml#ref9_12) 和 Posner 和 Ash (2012) 以了解该方法可能存在的问题。 [⏎](#chapter9.xhtml#en9_69b)

### 7.
尽管 logistic 回归是倾向得分估计最常用的方法，但也可以使用其他方法，如决策树、随机森林、神经网络等。 [⏎](#chapter9.xhtml#en9_79b)

### 8.
虽然本 [第 9.4 节](#chapter9.xhtml#sec9_4) 是关于对观察数据应用倾向得分匹配，但在机器学习文献中讨论了一种平行方法，其中训练数据和应用所开发模型的数据并不相同。这种方法在 [附录 9.4](#chapter9.xhtml#app9_4) 中简要讨论。 [⏎](#chapter9.xhtml#en9_89b)

### 9.
在 SAS 中使用 `Proc logistic` 进行本示例中的所有提升建模方法，使用构建的权重。学术文献指出，当使用权重时，系数的标准误差可能有偏，导致 `p-values` 可能有偏。为了在方差估计中正确纳入权重，可以使用 `proc surveylogistic`，其实际缺点是至少在 SAS 当前版本（9.4）中无法自动执行逐步程序。我们对一些模型尝试了 `proc surveylogistic`，结果与 `proc logistic` 仅有微小差异。 [⏎](#chapter9.xhtml#en9_99b)

### 10.
一些读者可能回忆起在商店购物时忘记使用优惠券的经历。 [⏎](#chapter9.xhtml#en9_109b)

### 11.
在点击率情况下，如果有人点击但未进行购买，则该分量不会为 1，而成为另一个待确定的概率。 [⏎](#chapter9.xhtml#en9_119b)

### 12.
方程 (8.1) 直接估计提升，并且不提供治疗组和对照组反应率的单独估计，尽管可以从 (8.1) 中提取治疗组和对照组反应率分量。第 287 页 [⏎](#chapter9.xhtml#en9_129b)

### 13.
由于包括年龄、收入、支出和财富在内的变量与其各自的对数变量一起估计，我们监控逐步回归的输出以使用以下规则减少共线性：当原始变量及其对数对应物都作为主效应出现时，只选择 `p-value` 较低的一个。治疗虚拟变量的交互效应也同样适用。 [⏎](#chapter9.xhtml#en9_139b)

### 14.
在 [表 9.6](#chapter9.xhtml#tbl9_6) 中，虽然直接响应模型在 Gini 指标方面的表现最低，但其 `R²` 更高，这是由于提升与半十分位数之间更线性关系所致，如 [图 9.6](#chapter9.xhtml#fig9_6) 所示。如第 6 章所述，Gini 指标是更重要的比较指标。 [⏎](#chapter9.xhtml#en9_149b)

### 15.
与上一节的示例类似，包括年龄、收入、支出和财富在内的变量与其各自的对数变量一起估计，并使用以下规则减少共线性：当原始变量及其对数对应物都作为主效应出现时，只选择 `p-value` 较低的一个。治疗虚拟变量的交互效应也同样适用。 [⏎](#chapter9.xhtml#en9_159b)

### 16.
由于 `S` 表示 `log(sales)`，因此销售额的估计值只是模型估计的 `E(S|…)` 的指数函数。 [⏎](#chapter9.xhtml#en9_169b)

### 17.
当使用总体不同时调整训练样本的类似方法在 [附录 9.4](#chapter9.xhtml#app9_4) 中简要讨论。 [⏎](#chapter9.xhtml#en9_179b)

### 18.
这种概率测度的变化在概率论文献中被称为 `Radon-Nikodym derivative`；请参阅 [Billingsley (1995)](#chapter9.xhtml#ref9_8)。 [⏎](#chapter9.xhtml#en9_189b)

## 参考文献

* Abrevaya, Jason, Yu-Chin Hsu, and Robert P. Lieli. 2015. “估计条件平均处理效应”. 《商业与经济统计学杂志》, 33: 485–505. [⏎](#chapter9.xhtml#b9ref9_1)
* Athey, Susan, and Guido W. Imbens. 2015. “估计异质因果效应的机器学习方法”. 工作论文, 斯坦福大学商学院. [⏎](#chapter9.xhtml#b9ref9_2)
* Athey, Susan, Julie Tibshirani, and Stefan Wager. 2019. “广义随机森林”. 《统计学年刊》, 47(2): 1148–1178. [⏎](#chapter9.xhtml#b9ref9_3)
* Bickel, Steffen. 2009. “在训练和测试分布不同的情况下学习”. *博士论文*, 波茨坦大学. [⏎](#chapter9.xhtml#b9ref9_4)
* Bickel, Steffen, Michael Bruckner, and Tobias Scheffer. 2009. “协变量偏移下的判别学习”. 《机器学习研究杂志》 10: 2137–2155.
