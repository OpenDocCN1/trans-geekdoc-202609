
如果我们有超过 `p` = 4![图片](images/B9780443218576000072/si140.png) 个未知数，我们可以以相同的方式迭代进行，依次获得 `q[1]′`、`q[2]′`![图片](images/B9780443218576000072/si134.png) 等的近似值，假设根按模排序，其中 `r[1]`![图片](images/B9780443218576000072/si25.png) 具有最大模。我们在每次新的迭代中累积不准确性，但精度损失是可控的：最大的损失发生在影响最小的系数上。具有相同模的根必须联合处理，正如我在这里对 `r[1]`![图片](images/B9780443218576000072/si25.png) 和 `r[2]`![图片](images/B9780443218576000072/si141.png) 所做的那样。如果某些根的重数大于 1，公式 `[(3.10)]` 必须进行调整；请参阅 `[3]`。

## 3.5 机器学习数学：必读书籍

一般来说，我的方法并非传统。我试图为读者提供原创内容，用通俗易懂的英语解释创新方法，文风读来令人愉悦。如果您正在寻找学习机器学习数学的标准教材，我推荐 *Mathematics for Machine Learning* `[2]` 和 *Introduction to Mathematical Statistics* `[6]`。书籍 *Deep Learning* `[4]` 也涵盖了矩阵代数的数学知识。Zico Kolter 在斯坦福大学 2015 年的讲义（涵盖线性代数）可在[此处](https://cs229.stanford.edu/section/cs229-linalg.pdf)获取。Shaina Bennett 编著的 *Linear Algebra for Data Science*（2021）可在[此处](https://shainarace.github.io/LinearAlgebra/)在线阅读，并包含 R 语言示例。另请参阅 Stanley Chan 编著的 *Introduction to Probability for Data Science*（2021），可在[此处](https://probability4datascience.com/)获取，包含 Matlab® 和 Python 代码，特别是最后一章关于随机过程的内容。

对于包含 Python 代码的实操参考，[StatsModels.org](https://www.statsmodels.org/stable/user-guide.xhtml) 是一个庞大的 GitHub 存储库，涵盖了大量线性代数和时间序列内容。另一个是 Statistics and Machine Learning in Python，见[此处](https://duchesnay.github.io/pystatsml/)。另请参阅 Python [Scikit-learn.org](https://scikit-learn.org/0.15/modules/linear_model.xhtml) 关于线性模型的指南，以及 [Interpretable Machine Learning](https://christophm.github.io/interpretable-ml-book/limo.xhtml)。您不会在任何这些书中找到此处讨论的数学或示例类型。然而，它们是有用的、经典的，又是现代的参考资料。

## 参考文献

*   `[1]` B. Bogacka, 时间序列讲义。伦敦玛丽女王大学；2008。`[链接](https://webspace.maths.qmul.ac.uk/b.bogacka/TimeSeries/)`。

*   `[2]` M. Deisenroth, A. Faisal, C.S. Ong, *Mathematics for Machine Learning*。剑桥大学出版社；2020。`[链接](https://mml-book.github.io/)`。

*   `[3]` A. Farahmand, *Math 55 Lecture Notes*。伯克利大学；2021。`[链接](https://math.berkeley.edu/~arash/notes/8_2.pdf)`。

*   `[4]` I. Goodfellow, Y. Bengio, A. Courville, *Deep Learning*。麻省理工学院出版社；2016。`[链接](http://www.deeplearningbook.org)`。

*   `[5]` V. Granville, *Stochastic Processes and Simulations: A Machine Learning Perspective*。MLTechniques.com；2022。`[链接](https://mltechniques.com/product/album/)`。

*   `[6]` R.V. Hogg, J.W. McKean, A.T. Craig, *Introduction to Mathematical Statistics*。第八版 Pearson；2016。`[链接](https://minerva.it.manchester.ac.uk/~saralees/statbook2.pdf)`。

*   `[7]` M.-A. Muendler, *Linear Difference Equations and Autoregressive Processes*。伯克利大学；2000。`[链接](https://econweb.ucsd.edu/muendler/teach/gen/diffeqn.pdf)`。

*   `[8]` C. Rasmussen, C. Williams, *Gaussian Processes for Machine Learning*。麻省理工学院出版社；2006。`[链接](https://gaussianprocess.org/gpml/chapters/)`。

*   `[9]` S. Yan, A. Yang, 等，Vandermonde 矩阵求逆的显式算法，*2009 国际测试与测量会议*。IEEE；2009。`[链接](https://ieeexplore.ieee.org/document/5413083)`。

# 第 4 章：图像与视频生成

## 高维数据可视化的艺术

### 摘要

我讨论了使用 Python 的 pillow 和 moviepy 库制作专业数据视频、动态 GIF 和其他可视化的不同技术。应用包括：无论特征数量（也称为自变量）多少，可视化预测区间；应用于无限数据集的监督分类；机器学习算法的收敛；以及展示各种大小的物体以各种速度沿各种路径移动的动画。例如，我展示了 300 颗彗星绕太阳运行的视频模拟，以评估碰撞风险。

相关 Python 库允许在像素级别进行低级图像处理。这对于构建专用的、原创的可视化算法特别有用。我还讨论了优化：所需内存量、压缩技术的性能、numpy 与 math 库的对比、用于去像素化图像的抗锯齿等。一些视频使用 RGBA 调色板格式。这种四维颜色编码（红、绿、蓝、Alpha）允许您在物体重叠时设置透明度级别（也称为“不透明度”）。它在涉及混合或监督分类中重叠群组的模型中特别有用。在这种情况下，它不仅有助于可视化，而且实际上能独立解决分类问题。

#### 关键词

空间统计；数据可视化；预测区间；监督分类；数据动画

## 4.1 简介
