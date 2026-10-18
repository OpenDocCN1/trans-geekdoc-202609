

问题出现在处理个人及其数据时。如果数据处理时没有以做出道德决策为目标，输出可能会有缺陷。[*Counseling Today*](https://ct.counseling.org/2018/01/counseling-artificial-intelligence/) 文章让你了解 AI 与人类情感相关的一些问题。问题是，AI 是否真的可能仅根据面部表情检测情绪。这部分取决于机器学习算法所采用的决策平衡。[文章](http://davidgratzer.com/reading-of-the-week/reading-of-the-week-can-machine-learning-improve-psychotherapy-the-new-jama-psychiatry-paper-also-santa-ono-on-his-mental-illness/) 提供了关于某一特定应用所涉及内容的一些想法。

在为任何影响人类伦理待遇的目的创建机器学习算法时，开发算法输出意味着在速度和治疗价值之间创建正确的平衡。算法不能跳到结论，因为输出可能对接收它的人产生具体且难以逆转的影响。例如，仅根据病史和观察到的行为为患者开某种药物治疗方案，可能会给该人带来以后很难甚至无法修复的问题。

## 验证数据源

阅读本章后，你可能会决定使用任何数量的公共领域或付费数据集进行研究。考虑到所有要求，收集自己的数据可能看起来太麻烦了。问题是，使用第三方数据集并不能免除你以合乎道德的方式行事的义务。当你在网上寻找现有数据集时，你需要考虑来源，并了解来源是如何组装数据集的。由政府机构或学校组装的数据集通常最不值得怀疑，也最不容易给你后来带来问题。

你还需要遵守第三方数据集创建者设定的任何规则。通常，你可以在下载站点、readme 文件中或数据集文件本身中找到关于任何限制和要求的说明。密切关注它们对于确保你不会因数据使用而陷入诉讼至关重要。

在使用任何数据集时，拥有书面使用许可会很有帮助，除非你确定该数据集属于公共领域。数据集创建者通常会在数据集下载站点发布通知，说明该数据集属于公共领域。如果你没有看到这样的通知，假设数据集受版权保护且你需要获得使用许可总是更安全的，尤其是如果此类使用会受到公众关注，例如作为商业问题的一部分。

# 第 22 章

## 十大机器学习包

本章内容

![Bullet](images/check.png)**执行自然语言处理 (NLP) 任务**

![Bullet](images/check.png)**添加科学算法和其他功能**

![Bullet](images/check.png)**加快常见和一些不常见任务**

![Bullet](images/check.png)**提高项目成功的机会**

本书提供了关于特定机器学习包（例如 `Scikit-learn`）的大量信息。当然，`Scikit-learn` 是一个良好且多功能的包，你可以用它开始机器学习之旅。拥有不止几个工具在你的工具箱中很重要，而本章中的建议正是派上用场的地方。这些包为你提供额外的机器学习洞察和功能。尽管还有许多其他包可用，这些包会让你了解下一步去哪里，并使探索其他包也更容易。

## Gensim

[`https://radimrehurek.com/gensim/`](https://radimrehurek.com/gensim/)

`Gensim` 是一个 Python 包，可以对文本数据执行自然语言处理 (NLP) 和无监督学习。它提供了多种可供选择的算法：TF-IDF、随机投影、潜在狄里克莱分配、潜在语义分析，以及两个语义算法：`word2vec` 和 `document2vec` ([`https://code.google.com/archive/p/word2vec/`](https://code.google.com/archive/p/word2vec/)).

`Word2vec` 基于神经网络（浅层而非深度学习网络），它允许将单词有意义地转换为可以语义方式操作的坐标向量。例如，对表示 `Paris` 的向量进行操作，减去向量 `France`，然后加上向量 `Italy`，结果得到向量 `Rome`，这展示了如何使用数学和合适的 `Word2vec` 模型对文本执行语义操作。

## imbalanced-learn

[`https://imbalanced-learn.org/`](https://imbalanced-learn.org/)

分类算法的性能很重要，但大多数算法只有在各类别的类样本数量大致相同时才能表现良好。在处理高度偏斜的数据集时，少数类样本数量较少的情况越来越常见，你需要一种方法来处理它们。解决这个问题的一种方法是重新采样数据集以抵消不平衡，这就是 `imbalanced-learn` 发挥作用的地方。它提供了多种常用于显示类间强不平衡的数据集的重采样技术。这些技术分为以下几类：

*   对多数类进行欠采样

*   对少数类进行过采样

*   结合过采样和欠采样

*   创建集成平衡集

该包在每个类别中提供多种方法，因此非常灵活。你可以将 `imbalanced-learn` 与 `Scikit-learn` 一起使用，并且它是 `Scikit-learn-contrib` 项目的一部分 ([`https://github.com/scikit-learn-contrib`](https://github.com/scikit-learn-contrib))。

## OpenCV

[`https://github.com/skvark/opencv-python`](https://github.com/skvark/opencv-python)

*计算机视觉*，如第 17 章“[重新审视计算机视觉的最新状态](#c17.xhtml#c17-sec-0003)”部分所述，是一种在 2D 图片中检测对象的方法。但是，你需要一个特殊的包来高效地执行此任务。`OpenCV` (`Open Source Computer Vision Package`) 是一个开源计算机视觉和机器学习软件包，拥有 2500 多个优化算法。它包含一套全面的经典和最先进的计算机视觉和机器学习算法。你可以使用这些算法执行与视觉相关的任务，包括：

*   检测和识别面部

*   识别对象

*   对视频中的人类行为进行分类

*   跟踪摄像机移动

*   跟踪移动对象

*   提取对象的 3D 模型

*   从立体相机生成 3D 点云

*   将图像拼接在一起以生成整个场景的高分辨率图像

*   从图像数据库中查找相似图像

*   从使用闪光灯拍摄的图像中去除红眼

*   跟踪眼球运动

*   识别景观并建立标记以将其与增强现实叠加

![Tip](images/tip.png)这个包可以做更多事情，但这是一个很好的开始。安装过程可能比较复杂，所以请务必查看供应商网站以获取详细的安装程序。这个特定的包需要 Python 3.6 或更高版本，所以不要尝试在旧版 Python 上使用它。

## SciPy

[`https://www.scipy.org/`](https://www.scipy.org/)

