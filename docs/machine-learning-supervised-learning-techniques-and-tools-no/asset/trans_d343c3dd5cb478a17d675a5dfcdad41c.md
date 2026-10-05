

*   似然比（LR）检验。它基于无约束模型和约束模型中似然函数对数的差异：

![image](d2d_images/image559.png)

该值渐近服从自由度为 q 的卡方分布。

对于 Logit 和 Probit 模型中的拟合优度度量，我们有：

*   正确预测百分比。对每个 i 我们计算估计的 `Yi = 1` 的概率：

![image](d2d_images/image440.png)

*   如果 ![image](d2d_images/image118.png) 我们的预测将是 `Yi` 为 1，如果 ![image](d2d_images/image118.png) 我们的预测将是 `Yi` 为 0。观测值 `Yi` 与预测值相符的次数百分比即为正确预测百分比。有趣的是分别计算零和一的正确预测百分比。

*   伪 R²（McFadden）。它基于似然函数对数：

![image](d2d_images/image626.png)

![Texto Descripción generada automáticamente con confianza media](d2d_images/image657.png)

*   信息准则。这些是试图在拟合优度与模型简约设定之间取得平衡的度量，拟合优度由似然函数对数的值衡量。（示例：赤池信息准则 AIC、施瓦茨准则 SC 和汉南-奎因准则 HQ。）选择信息准则值最低的模型。

在解释 Probit 和 Logit 模型中的估计值时，我们通常感兴趣的是变量 `Xj` 的变化对响应概率的影响，如果该变量是连续的，则为：

![image](d2d_images/image642.png)

由于 ![image](d2d_images/image226.png) 依赖于 X，因此有必要对 X 的感兴趣值（样本均值、感兴趣变量的最大值和最小值等）计算偏效应。也可以为每个个体计算偏效应，然后计算其均值。

连续变量 `Xj` 对响应概率 `P(Y \= 1|X)` 的偏效应将为：

![image](d2d_images/image046.png)

其中 `g(.)` 是 logistic（logit）或标准正态（probit）密度函数。该效应因个体而异。如同 Probit 和 Logit 的情况，`g(z)>0` 对所有 z 成立，`Xj` 的偏效应的符号与 `βj` 的符号相同。

两个连续变量 `Xj` 和 `Xh` 的相对效应不依赖于 X。请注意，偏效应的商为 `βj /βh`。

如果 `X1`，例如，是一个虚拟解释变量，其从 1 变到 0 的偏效应将由下式给出：

![image](d2d_images/image300.png)

该值也因个体而异，因为它取决于所有 `X'sj` 的值。

由于在 Probit 中 `g(0) ≈ 0.4`，在 Logit 中 `g(0) ≈ 0.25` 而在 MPL 中 `g(0) = 1`，可以得到估计值之间的以下关系：

![image](d2d_images/image490.png)

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.4 多项选择模型

![image](d2d_images/chapter_title_below.png)

迄今为止研究的模型是离散选择模型，其中选择集只有两种可能的备选方案，被称为二元选择模型。但当选择集有多个离散值时，我们就是处理多项选择模型或多项模型。现在我们将研究最常见的模型。

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

## 3.4.1 多项 Logit 模型

![image](d2d_images/chapter_title_below.png)

多项 Logit 模型是二元模型的扩展，用于响应“无序”且可能性超过 2 种的情况。设 `(Xi , Yi)` 为总体中 i = 1..n 的随机样本。

与二元情况一样，我们感兴趣的是 X 的元素变化如何影响响应概率：

![Texto Descripción generada automáticamente con confianza media](d2d_images/image305.png)

如果 `J=1`，我们处于二元情况。

在这些模型中，偏效应很复杂，甚至参数的符号也不给出效应的符号。如果 `Xk` 是连续的，偏效应将为：

![Texto, Carta Descripción generada automáticamente](d2d_images/image496.png)

注意到：

![Texto, Carta Descripción generada automáticamente](d2d_images/image683.png)

选择 j 的概率，如果选择是在 j 和 h 之间，则遵循参数向量为 `βj -βh` 的标准 Logit 模型：

![Texto, Carta Descripción generada automáticamente](d2d_images/image289.png)

一般而言，我们将得到一致且渐近正态的估计量。

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

## 3.4.2 条件 Logit 模型

![image](d2d_images/chapter_title_below.png)

条件 Logit 模型用于个体（或企业）的选择至少部分基于每个备选方案的可观测属性的问题。在多项 Logit 中，解释变量在备选方案之间不发生变化，即对每个 i，`Xi` 包含特定于个体的变量，而非特定于备选方案的变量，适用于备选方案特征不重要（或我们未观察到它们）的情况。在条件 Logit 模型中，对每个 i，`Xi` 包含个体特定和备选方案特定的变量，适用于备选方案特征可被观察到的情况。

假设我们从基础总体中抽取了大小为 n 的随机样本（i = 1,..., n）。选择备选方案 j 的效用为：

![image](d2d_images/image290.png)

其中 `aij` 是影响偏好的不可观测因素，而 `Xij` 在备选方案之间（也许也在个体之间）变化，但不能包含仅在个体之间变化的元素（不包含常数项）。

例如，我们可以考虑个体 i 使用交通方式 j 通勤所需的时间或交通方式 j 的成本（可能在个体之间变化也可能不变）。

如果扰动项 `atij` 独立服从 Weibull 分布且：

![Texto, Carta Descripción generada automáticamente](d2d_images/image284.png)

其中 `βk` 是 `β` 的第 k 个元素。

条件 Logit 模型的估计通过最大似然法进行。

在条件 Logit 模型中，无关替代品独立性 IAI 假设也得到满足，因为选择 2 个备选方案的概率之比（`Y= j` 而非 `Y=h`）与剩余备选方案无关。 有

![image](d2d_images/image571.png)

无关替代品独立性 IAI 假设源于扰动项独立性假设，对估计很方便，但在某些具有相似备选方案的应用中可能是不现实的限制。无关替代品独立性 IAI 假设认为，两个现有备选方案的相对可能性不受引入第三个备选方案的影响。可以使用 Hausman 和 McFadden 提出的检验来检验 IAI 假设。

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

## 3.4.3 嵌套 Logit 模型

![image](d2d_images/chapter_title_below.png)

