

![](images/9780262346030.jpg)

**自适应计算与机器学习**

Francis Bach，主编

Christopher Bishop、David Heckerman、Michael Jordan 和 Michael Kearns，副主编

本书后附有“自适应计算与机器学习”丛书已出版书籍的完整列表。

© 2017 麻省理工学院

版权所有。未经出版方书面许可，不得以任何形式或任何电子、机械手段（包括复印、录制或信息存储与检索）复制本书任何部分。

本书由作者使用 Times Roman 和 Mathtime Pro 2 字体排版。

在美国印刷装订。

美国国会图书馆预出版编目数据可查

ISBN: 978-0-262-03779-2

d\_r0

# 图目录

[3.1 MOA 图形用户界面。](#chapter_3.xhtml#fig3-1)

[3.2 MOA GUI 运行两个不同的任务。](#chapter_3.xhtml#fig3-2)

[3.3 练习 3.1，对比朴素贝叶斯分类器和霍夫丁树。](#chapter_3.xhtml#fig3-3)

[3.4 练习 3.2，在同一分类器上对比三种不同的评估方法。](#chapter_3.xhtml#fig3-4)

[3.5 一个 Sigmoid 函数 `f(t) = 1/(1 + e^(-4(t-p)/w))`。](#chapter_3.xhtml#fig3-5)

[3.6 练习 3.3，在非平稳流上对比霍夫丁树和朴素贝叶斯分类器。](#chapter_3.xhtml#fig3-6)

[3.7 练习 3.4，对比三种不同的分类器。](#chapter_3.xhtml#fig3-7)

[4.1 蓄水池采样草图。](#chapter_4.xhtml#fig4-1)

[4.2 Morris 近似计数算法。](#chapter_4.xhtml#fig4-2)

[4.3 线性计数草图。](#chapter_4.xhtml#fig4-3)

[4.4 Cohen 计数算法。](#chapter_4.xhtml#fig4-4)

[4.5 基本 Flajolet-Martin 概率计数器。](#chapter_4.xhtml#fig4-5)

[4.6 SPACESAVING 草图。](#chapter_4.xhtml#fig4-6)

[4.7 宽度为 7、深度为 4 的示例 CM-sketch 结构，对应 `𝜖 = 0.4` 和 `δ = 0.02`。](#chapter_4.xhtml#fig4-7)

[4.8 CM-SKETCH 算法。](#chapter_4.xhtml#fig4-8)

[4.9 COUNTSKETCH 算法。](#chapter_4.xhtml#fig4-9)

[4.10 将 29 位的流划分为桶，其中 `k = 2`。最近的位在右侧。](#chapter_4.xhtml#fig4-10)

[4.11 指数直方图草图。](#chapter_4.xhtml#fig4-11)

[5.1 使用自适应估计器管理变化。图基于文献 [30]。](#chapter_5.xhtml#fig5-1)

[5.2 使用显式变化检测器进行模型修订以管理变化。图基于文献 [30]](#chapter_5.xhtml#fig5-2)

[5.3 使用模型集成管理变化。](#chapter_5.xhtml#fig5-3)

[6.1 在 1,000,000 个实例的流上进行评估，对比留出法、交错测试后训练法、以及带滑动窗口的预测式评估方法。](#chapter_6.xhtml#fig6-1)

[6.2 描述用于判断邮件是否为垃圾邮件的邮件特征的数据集，及其对应的决策树。](#chapter_6.xhtml#fig6-2)

[6.3 霍夫丁树算法。](#chapter_6.xhtml#fig6-3)

[6.4 CVFDT 算法。](#chapter_6.xhtml#fig6-4)

[6.5 两个类别的高斯近似。图基于文献 [199]。](#chapter_6.xhtml#fig6-5)

[6.6 主动学习框架。](#chapter_6.xhtml#fig6-6)

[6.7 变量不确定性策略，带动态阈值。](#chapter_6.xhtml#fig6-7)

[6.8 MOA 图形用户界面。](#chapter_6.xhtml#fig6-8)

[7.1 加权多数算法。](#chapter_7.xhtml#fig7-1)

[7.2 面向 `M` 个模型的在线 Bagging。指示函数 `I(condition)` 在条件为真时返回 1，否则返回 0。](#chapter_7.xhtml#fig7-2)

[9.1 `k`-均值聚类算法，即 Lloyd 算法。](#chapter_9.xhtml#fig9-1)

[9.2 DEN-STREAM 算法。](#chapter_9.xhtml#fig9-2)

[9.3 MOA `Clustering`（聚类）GUI 选项卡。](#chapter_9.xhtml#fig9-3)

[9.4 GUI `Clustering`（聚类）选项卡中的演化簇。](#chapter_9.xhtml#fig9-4)

[10.1 项集数据集示例。](#chapter_10.xhtml#fig10-1)

[10.2 图 10.1 数据集中最小绝对支持度为 3、相对支持度为 0.5 时的频繁项集、闭项集和极大项集。](#chapter_10.xhtml#fig10-2)

[10.3 具有批量更新和滑动窗口的通用流模式挖掘器。](#chapter_10.xhtml#fig10-3)

[10.4 WINGRAPHMINER 算法和 CORESET 过程。](#chapter_10.xhtml#fig10-4)

[10.5 ADAGRAPHMINER 算法。](#chapter_10.xhtml#fig10-5)

[11.1 ADAMS 流编辑器。](#chapter_11.xhtml#fig11-1)

[11.2 ADAMS 流示例。](#chapter_11.xhtml#fig11-2)

[11.3 MEKA GUI。](#chapter_11.xhtml#fig11-3)

[11.4 OpenML 与 MOA 的集成。](#chapter_11.xhtml#fig11-4)

[11.5 SAMOA 中的并行提示。](#chapter_11.xhtml#fig11-5)

[12.1 MOA 图形用户界面。](#chapter_12.xhtml#fig12-1)

[12.2 在 MOA 中设置任务的选项。](#chapter_12.xhtml#fig12-2)

[12.3 RBF 数据生成器的选项对话框。通过存储和加载设置，流式数据集可用于基准测试、重复性验证和比较。](#chapter_12.xhtml#fig12-3)

[12.4 MOA 聚类 GUI 的可视化选项卡。](#chapter_12.xhtml#fig12-4)

[13.1 使用 gnuplot 绘制的两个分类器学习曲线渲染图。](#chapter_13.xhtml#fig13-1)

# 表目录

[1.1 以字节为单位的内存单位倍数。](#chapter_1.xhtml#tab1-1)

[6.1 简单混淆矩阵示例。](#chapter_6.xhtml#tab6-1)

[6.2 表 6.1 的修改版混淆矩阵。](#chapter_6.xhtml#tab6-2)

[6.3 预算分配策略摘要。](#chapter_6.xhtml#tab6-3)

# 前言

实时流数据分析正成为从当前正在发生的事件中获取有用知识的标准，使组织能够在问题出现时快速反应，或检测新趋势，从而帮助其提升绩效。本书介绍了数据流挖掘领域目前使用的许多算法和技术。一个实现了本书许多技术的软件框架可在网络上作为名为 `MOA` 的开源项目获得。

本书的目标是向三类特定读者展示数据流挖掘技术：

1.  希望将流挖掘作为工具使用的读者，他们没有扎实的算法或编程背景，但具备基本的数据挖掘背景。例如管理、商业智能或市场营销等领域的学生或专业人士。我们以面向任务（而非面向算法）的方式，提供了 `MOA` 的实践入门介绍。

2.  希望在数据流挖掘领域进行研究或创新的读者。他们希望了解算法、评估方法等的细节，以便创建新算法或使用现有算法，评估其性能，并可能将其集成到应用中。这类读者包括计算机或数据科学领域的高年级本科生、硕士生和博士生，以及创新环境中的开发人员。

3.  除了上述需求外，还希望尝试在 `MOA` 中加入新算法，并可能将其贡献给该项目的读者。他们需要了解 `MOA` 的类结构，以及如何为 `MOA` 创建新学习器等。

为实现这一目标，本书分为三部分。第一部分是大数据流挖掘的快速入门。它包含三章：两章介绍大数据挖掘和挖掘数据流的基本方法论，还有一章是面向希望自行上手探索的读者的 `MOA` 实践指南。

