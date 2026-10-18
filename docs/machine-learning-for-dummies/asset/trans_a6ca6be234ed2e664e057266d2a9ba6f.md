

SciPy 栈包含许多其他包，你也可以单独下载这些包。这些包为数学、科学和工程提供支持。当你获取 SciPy 时，你会得到一组设计为协同工作的包，用于创建各种类型的应用程序。这些包包括

*   `NumPy`

*   `SciPy`

*   `matplotlib`

*   `IPython`

*   `Sympy`

*   `pandas`

`SciPy` 包本身专注于数值例程，例如数值积分和优化例程。`SciPy` 是一个通用包，为多个问题领域提供功能。它还为特定领域的包提供支持，例如 `Scikit-learn`、`Scikit-image` 和 `statsmodels`。为了让你的 `SciPy` 体验更好，请尝试 [`http://www.scipy-lectures.org/`](http://www.scipy-lectures.org/) 上的资源。该网站包含许多关于 `SciPy` 功能的讲座和教程。

## SHAP

[`https://github.com/slundberg/shap`](https://github.com/slundberg/shap)

了解机器学习模型的工作原理变得越来越重要。例如，欧盟通用数据保护条例（GDPR）([`https://www.kdnuggets.com/2018/03/gdpr-machine-learning-illegal.html`](https://www.kdnuggets.com/2018/03/gdpr-machine-learning-illegal.html)) 在模型处理用户数据时将解释作为要求。使用 `Shapley values`（一种来自合作博弈论的方法）可以通过假设实例的每个特征值都是游戏中的玩家（预测是回报）来创建解释。你可以在 [`https://christophm.github.io/interpretable-ml-book/shapley.html`](https://christophm.github.io/interpretable-ml-book/shapley.html) 上阅读更多关于该理论的内容。SHAP (`SHapley Additive exPlanations`) 包允许你使用 Shapely values 创建解释。主机网站展示了使用此技术的示例，包括：

*   Tree ensembles

*   Deep learning

*   Deep learning gradient

*   Model agnostic linear regression

随包提供的示例笔记本包含其他示例类型。还有文档笔记本可帮助你完成使用 SHAP 包的过程。

## Statsmodels

[`https://www.statsmodels.org/stable/index.html`](https://www.statsmodels.org/stable/index.html)

统计模型必然与机器学习模型不同，否则就没有理由维护两者。你可能会让大多数人同意这一说法（尽管并非所有人都同意）。[第 2 章](#c02.xhtml) 中的“[指定统计在机器学习中的作用](#c02.xhtml#c02-sec-0012)”部分提供了关于统计与机器学习关系的重要信息。[`Towards Data Science`](https://towardsdatascience.com/the-actual-difference-between-statistics-and-machine-learning-64b49f07ea3) 文章在 [`https://towardsdatascience.com/the-actual-difference-between-statistics-and-machine-learning-64b49f07ea3`](https://towardsdatascience.com/the-actual-difference-between-statistics-and-machine-learning-64b49f07ea3) 上很好地描述了模型之间的差异。然而，为你的应用程序提供机器学习模型和统计模型的需求正是你需要 `statsmodels` 的原因——这是一个 Python 包，为以下内容提供类和函数：

*   估计多种不同的统计模型

*   进行统计检验

*   统计数据探索

![Remember](images/remember.png)关于此包需要记住的重要一点是，作者会针对现有统计包测试该包，以确保输出正确。你可以使用 R 样式公式或 pandas `DataFrames` 指定模型。然而，最重要的是，输出易于阅读，因此你不必解释你看到的内容。

## Modin

[`https://github.com/modin-project/modin`](https://github.com/modin-project/modin)

似乎每个人都在寻找应用程序的额外功能，速度总是不错的。你使用 `Modin` 来加速你的 `pandas` 代码，因为它可以利用计算机中可用的多个 CPU 核心。事实上，`Modin` 最终是 `pandas` 的替代品。要使用 `Modin`，你可以这样更改代码：

```
# import pandas as pd
import modin.pandas as pd
```

![Warning](images/warning.png)`Modin` 的好处是，你通常不需要更改代码的其余部分。`Modin` 会自动使用 `Modin` 等效项解释 `Pandas` 调用。因此，你可以尝试 `Modin` 而无需投入大量时间或精力，这使得测试 `Modin` 比你可能尝试的其他包更容易。`Modin` 的坏处是它不支持完整的 `pandas` API，因此在更改之前需要查看限制。

`Modin` 的另一个考虑因素是它依赖于两种计算引擎之一：`Ray` ([`https://github.com/ray-project/ray`](https://github.com/ray-project/ray)) 或 `Dask` ([`https://dask.org/`](https://dask.org/))。如果你使用 Windows，只能使用 `Dask` 引擎；Linux 和 Mac OS 用户可以依赖任一引擎。通常，`Modin` 会选择最适合你的环境和 API 使用的引擎，但你也可以选择依赖特定引擎。关键是，使用多个引擎也会给包带来一定的不可靠性。

## PyTorch

[`https://pytorch.org/`](https://pytorch.org/)

`PyTorch` 是 `TensorFlow` 的替代品。它在学术界和机器学习竞赛（如 Kaggle）中尤其受欢迎。此包使用 `Lua` ([`https://www.lua.org/`](https://www.lua.org/)) 语言编写。Facebook 最初开发了 `PyTorch`，但如今许多其他组织也在使用它，包括 Twitter、Salesforce 和牛津大学。以下是使 `PyTorch` 特别的功能：

*   它非常用户友好

*   它具有高效的内存使用

*   它相对较快

*   它通常用于研究

有些人喜欢 `PyTorch`，因为它像 `Keras` 一样易于阅读，但科学家不会失去使用复杂神经网络的能力。此外，`PyTorch` 直接支持动态计算模型图，这使得它比 `TensorFlow` 更灵活，而无需添加 `TensorFlow Fold`。

## Poetry

[`https://python-poetry.org/`](https://python-poetry.org/)

随着应用程序变得更加复杂，你会添加包来使编码、数据管理、资源使用和其他应用程序功能更容易。问题是，拥有更多包最终意味着在应用程序投入生产时某个时间点需要更多管理。`Poetry` 在 Python 中提供依赖项管理和打包。

管理不仅仅是确保当你想在开发机器以外的地方使用应用程序时，正确的包与你的应用程序一起使用。你还希望确保你的包得到维护。`Poetry` 允许你声明项目依赖的包，并会根据需要为你安装或更新它们。管理任务在这些级别进行：

*   Development

*   Building

*   Publishing

*   Tracking

## Snorkel

[`https://github.com/snorkel-team/snorkel`](https://github.com/snorkel-team/snorkel)

在本书中，你已经看到了数据对机器学习算法输出的影响。但是，在训练算法以供使用时，训练数据是第一位的。当训练数据失败时，整个应用程序也会失败。至少，这是 2016 年斯坦福的推理。Snorkel 团队认为，越来越多的是训练数据，而不是模型、算法或基础设施，决定了机器学习项目是成功还是失败。

`Snorkel` 背后的想法看似简单：它允许用户以编程方式标记、构建和管理训练数据。生成所需的数据，而不是依赖现实世界资源，使你获得的算法更有可能工作更好。毕竟，获取正确的现实世界数据是一件麻烦的事情，假设你能获取它的话。

