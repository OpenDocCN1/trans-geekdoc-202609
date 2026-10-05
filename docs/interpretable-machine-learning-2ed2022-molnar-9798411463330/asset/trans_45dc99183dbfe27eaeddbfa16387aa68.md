

## 8.3 反事实解释

这意味着它不像像 LIME 等方法那样危险，在 LIME 中，我们不清楚为了进行解释可以向局部模型外推到多远。

反事实方法创建一个新实例，但我们也可以通过报告哪些特征值发生了变化来总结一个反事实。这为我们报告结果提供了两种选择：你可以直接报告反事实实例，也可以突出显示感兴趣实例与反事实实例之间哪些特征发生了变化。

反事实方法不需要访问数据或模型。它也可以通过 API 运行，这对于那些接受第三方审计或在不泄露模型或数据的情况下向用户提供解释的公司来说，非常有吸引力。由于贸易秘密或数据保护原因，公司有保护模型和数据的意图。反事实解释在解释预测结果和保护模型所有者利益之间取得了平衡。

该方法适用于没有使用机器学习的系统。我们可以为任何接收输入并返回输出的系统创建反事实。预测地址租金的系统可能由手写规则组成，这种情况下反事实解释依然有效。

反事实解释方法相对容易实现，因为它本质上是一个函数（具有单个或多个目标），可以使用标准的优化器库进行优化。必须考虑一些额外的细节，例如将特征值限制在有意义的范围内（例如，公寓面积仅为正）。

### 8.3.4 缺点

对于每个实例，你通常会找到多个反事实解释（拉生门效应）。这很不方便——大多数人倾向于解释而非现实世界的复杂性。这也是一个实践性挑战。假设我们为一个实例生成了 23 个反事实解释。我们要全部报告出来吗？还是只报告最好的？如果它们都相对“好”，但差异很大呢？这些问题在每个项目中必须重新回答。拥有多个反事实解释也可能有利，因为人类可以挑选与他们先验知识对应的那些。

### 8.3.5 软件与替代方案

Dandl 等人提出的多目标反事实解释方法实现在 Github 仓库中¹⁶。

> ¹⁶https://github.com/susanne-207/moc/tree/master/counterfactuals

## 第 8 章 局部模型无关方法

在 Python 包 Alibi¹⁷ 中，实现了一个简单的反事实方法¹⁸，以及一个使用类原型来提高算法输出的可解释性和收敛性的扩展方法¹⁹²⁰。

Karimi 等人 (2020)²¹ 也在 Github 仓库²² 中提供了他们的算法 MACE 的 Python 实现。他们将反事实所需的必要标准翻译成逻辑公式，并使用可满足性求解器寻找满足这些标准的反事实。

Mothil 等人 (2020)²³ 开发了 DICE（多样化反事实解释）²⁴，通过确定点过程生成一组多样化的反事实解释。DICE 同时实现了模型无关的方法和基于梯度的方法。

另一种搜索反事实的方法是 Laugel 等人 (2017)²⁵ 提出的增长球（Growing Spheres）算法。他们没有在论文未使用“反事实”一词，但该方法非常相似。他们还定义了一个损失函数，倾向于值变化尽可能少的反事实。他们没有直接优化函数，而是建议首先在感兴趣的点周围画一个球，在该球内采样点，并检查采样点之一是否产生了所需的预测。然后他们收缩或扩展球，直到找到并最终返回一个（稀疏的）反事实。

由 Ribeiro 等人 (2018)²⁶ 提出的 Anchors 是反事实的相反面，参见关于范围规则（Anchors）的章节。

+ ¹⁷https://github.com/Seldon.io/projects/alibi/stable/methods/CF.html
¹⁸https://docs.seldon.io/projects/alibi/en/stable/methods/CFProto.html
¹⁹https://docs.seldon.io/projects/alibi/en/stable/methods/CFProto.html
²⁰Van Loewen, Arnold, and Jane Klaus. Interpretable counterfactual explanations guided by prototypes. arXiv preprint arXiv:1907.02584 (2019).
²¹Karimi, Amir-Hosse, Gilles Barthe, Borja Bale and Isabelnaver. Model-agnostic counterfactual explanations for consequential questions. AISTATS (2020).
²²https://github.com/aimrec/
²³Mothil et al. (2020) Diverse Counterfactual Explanation. Proceedings of the 2020 Conference on Fairness, Accountability, and Transparency.
²⁴https://github.com/interpret/DICE
²⁵Laugel et al. (2017) Growing Spheres for generating counterfactual explanations. arXiv preprint arXiv:1712.08443.
²⁶Ribeiro et al. (2018) Anchors: high-precision model-agnostic explanations. AAAI Conference on Artificial Intelligence.

## 8.4 范围规则 (ANCHORS)

如前所述，算法的结果或解释可以以规则的形式，称为锚点（anchors）。下面的简单示例说明了这样的锚点。例如，假设我们给定一个双变量黑箱模型，预测乘客是否在泰坦尼克号灾难中幸存。现在我们想知道为什么模型预测某个特定个体会幸存。锚点提供了如下所示结果解释。

| 特征 | 数值 |
|---|---|
| 年龄 | 20 |

> 27Marco Ribeiro, Sameer Singh and Carlos Guestrin. "Anchors: high-precision model-agnostic explanations". AAAI Conference on Artificial Intelligence (AAAI), 2018.

