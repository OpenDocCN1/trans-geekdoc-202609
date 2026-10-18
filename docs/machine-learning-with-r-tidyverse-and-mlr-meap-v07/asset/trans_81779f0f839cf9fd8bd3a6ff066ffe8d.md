
### 20.1.8 正则化通过惩罚模型参数来防止过拟合

正则化描述了一系列用于限制模型参数幅度以防止过拟合的技术。正则化对于防止因加入预测价值很小或没有预测价值的预测器而导致的过拟合尤为重要。我们在第11章学到了，最常见的两种正则化形式是L2正则化和L1正则化。

在L2正则化中，模型的损失函数会加入一个惩罚项，该项是模型参数的L2范数，由可调超参数 lambda 加权。模型参数的L2范数是参数值的平方和。L2正则化的效果是模型参数可以被缩小到零（除非OLS估计为零），弱预测器会受到更大的惩罚。Ridge回归是L2正则化在线性回归中防止过拟合的一个例子。

在L1正则化中，我们将L1范数加入损失函数，由 lambda 加权。L1范数是参数值的绝对值之和。L1正则化的效果是模型参数可以被缩小到零，从而有效地将它们从模型中移除。因此，L1正则化是一种自动特征选择的形式。LASSO是L1正则化在线性回归中防止过拟合的一个例子。

## 20.2 你可以从这里往哪里发展？

你现在可能在想自己的机器学习教育的下一步是什么。这真的取决于你自己以及你想要达成的目标，但在这一节我会指引你一些优秀的资源，帮助你进一步提升知识和技能。我坚信，巩固新知识的最好方式是使用它，所以请在你的工作中使用本书中学到的技术和算法，并向你的同事传授它们！

### 20.2.1 深度学习

正如我在本书开头提到的，我省略了深度学习（使用人工神经网络的机器学习），因为我认为它值得单独一本专著。但任何机器学习教育都不完整，除非学习这一非凡领域。神经网络是任何机器学习任务的强大工具，但如果你的工作围绕计算机视觉、图像/视频分类，或处理其他复杂数据（如音频文件）进行建模，深度学习是你必须学习的重要方向。对于R，我强烈推荐 *Deep Learning with R*，作者 Francois Chollet 和 Joseph J. Allaire（Manning, 2018）。这本书易于非专业读者阅读，并且会巩固我们在此已经覆盖的基本机器学习概念。

强化学习是机器学习研究和应用的前沿领域，算法通过在做出良好决策时获得奖励来从经验中学习。它常被与监督和无监督算法并列，视为机器学习算法的第三类，已被用于创建能够击败世界冠军棋手的棋盘程序。如果你对强化学习感兴趣，我强烈推荐 *Deep Learning and the Game of Go*，作者 Max Pumperla 和 Kevin Ferguson（Manning, 2019）。

如果你想提升整体的R数据科学技能，并更熟悉 tidyverse 工具（包括我们未使用的那些），我推荐 *R for Data Science*，作者 Garrett Grolemund 和 Hadley Wickham（O'Reilly Media, Inc., 2016）。

如果你想成为 ggplot2 大师，我建议你购买 *ggplot2*，作者 Hadley Wickham（Springer International Publishing, 2016）。

如果你的R技能已经不错，并且想更深入了解语言的工作原理以及进行更高级的编程（如面向对象编程），你会喜欢 *Advanced R*，作者 Hadley Wickham（CRC Press, 2019）。你可能会注意到这位 Hadley 先生经常出现。如果你想及时跟踪R社区以及 tidyverse 的发展，跟随他是件不错的事。

在书中几次提到，某些算法尚未在 mlr 中实现。mlr 包旨在简化你的机器学习经验，而不是降低灵活性，因此如果在其他包（或你自己的）中有一个算法，或者想实现新的性能指标，其实并不难自己实现。

在 mlr 官方网站上有一个教程，介绍如何实现这一方法（以及其他有用的信息和资源）：mlr.mlr-org.com/articles/tutorial/create_learner.html

如果你的工作涉及为回归任务建模非线性关系，我建议你深入了解广义加性模型（GAMs）的内部工作原理。对于R，进行此操作的绝佳场所是 Simon Wood（Chapman and Hall/CRC, 2017）所著的 *Generalized Additive Models: An Introduction with R*。

如果集 ensemble 方法让你兴奋？我们在这本书里只涉及了表面，且仅使用基于树的模型进行 ensemble。如果你相信 ensemble 可以几乎总是改进我们的模型，我建议你阅读 *Ensemble Methods: Foundations and Algorithms*，作者 Zhi-Hua Zhou（Chapman and Hall/CRC, 2012）。

如果你对支持向量机（SVM）如何扭曲特征空间以创建线性边界感到兴奋？SVM 非常流行，其理论相当复杂。如果你想了解如何利用其预测能力，我推荐 *Support Vector Machines*，作者 Andreas Christmann 和 Ingo Steinwart（Springer, 2008）。

有时，你并不关心数据中的常见模式。有时，你真正感兴趣的是不寻常、异常的案例。例如，你可能在尝试识别信用卡欺诈行为，或在寻找恒星中罕见的辐射爆发。

在数据集中识别这类罕见事件可能很困难，但机器学习中的异常检测领域专门解决这些问题。本书中你学到的部分算法可以被重新用于异常检测，例如 SVM 算法。

如果你对罕见和不寻常的事物情有独钟，请查看 *Anomaly Detection Principles and Algorithms*，作者 Kishan G. Mehrotra、Chilukuri K. Mohan 和 HuaMing Huang（Springer, 2017）。

本书中我没有涉及时间序列预测。这是机器学习和统计学关注于根据变量的过去状态预测其未来状态的领域。

时间序列预测的常见应用包括预测股市变量的波动以及预测天气模式。

因此，如果你想致富或保持干燥，我建议你从 Paul Cowpertwait 和 Andrew Metcalfe（Springer, 2009）所著的 *Introductory Time Series with R* 开始。

关于聚类，我们已经覆盖了相当好的 ground，但还有很多内容等待你深入探索。如果你想进一步学习，我推荐 *Data Clustering: Algorithms and Applications*，作者 Charu Aggarwal（Chapman & Hall/CRC, 2013）。

对一般线性模型能够像我们在逻辑回归中那样用于预测类别感到惊讶吗？事实上，我们可以用相同的原理预测计数数据（如泊松回归），或百分比（如 beta 回归）。处理结果不是正态分布连续变量的情形的一般线性模型的扩展形式称为广义线性模型。广义线性模型在构建预测模型时提供了非凡的灵活性，同时仍然保持模型参数的完整可解释性。

如果你想进一步学习，我推荐 *Generalized Linear Models With Examples in R*，作者 Peter K. Dunn 和 Gordon K. Smyth（Springer, 2018），尽管如果你没有扎实的线性建模数学基础，这本书可能会很困难。
