
# 开发者机器学习与自然语言处理

![Cover Image](img/Cover.jpg)

The author, developers, and the publisher of any accompanying content, and anyone involved in the composition, production, and manufacturing of this work will not be liable for damages of any kind arising out of the use of (or the inability to use) the algorithms, source code, computer programs, or textual material contained in this publication. This includes, but is not limited to, loss of revenue or profit, or other incidental, physical, or consequential damages arising out of the use of this Work.

*Companion files also available for downloading from the publisher by writing to* info@merclearning.com

**Oswald Campesato**

![image](img/pub.jpg)

*This publication, portions of it, or any accompanying software may not be reproduced in any way, stored in a retrieval system of any type, or transmitted by any means, media, electronic display or mechanical display, including, but not limited to, photocopy, recording, Internet postings, or scanning, without prior permission in writing from the publisher.*

[www.merclearning.com](http://www.merclearning.com)

800-232-0223

O. Campesato. *Natural Language Processing and Machine Learning for Developers.*

212223321     Printed on acid-free paper in the United States of America.

Our titles are available for adoption, license, or bulk purchase by institutions, corporations, etc.

For additional information, please contact the Customer Service Dept. at 800-232-0223(toll free).

All of our titles are available in digital format at *academiccourseware.com* and other digital vendors.

The sole obligation of MERCURY LEARNING AND INFORMATION to the purchaser is to replace the book, based on defective materials or faulty workmanship, but not based on the operation or functionality of the product.

*I’d like to dedicate this book to my parents-*

*may this bring joy and happiness into their lives.*

*Preface*

# 第 5 章 算法和工具包（I）

## 前言

## 这本书的核心价值是什么？

本书提供了关于 NLP 和机器学习的尽可能多的相关信息的快节奏介绍，这些内容可以合理地包含在本书的篇幅之内。一些章节包含详细讨论的主题（例如第 3 章的前半部分），其他章节包含高级统计概念，你在第一次通读本书时可以安全跳过这些内容。本书的宗旨是通过涵盖广泛的主题，帮助具有不同技术背景的开发者，这也是为何包含了大量主题的原因。无论你的背景如何，请牢记以下一点：*你仅通过阅读本书并不会成为机器学习或 NLP 领域的专家，并且需要准备阅读本书中的某些内容多次。*

然而，你将接触到 *许多* NLP 和机器学习主题，许多主题是以概览的方式呈现的，原因有两个。首先，让你接触这些概念很重要。在某些情况下，你可能会发现某些主题能激发你的兴趣，从而通过自学进一步深入；在其他情况下，你可能只需要简要的介绍即可满足需求。

其次，对本书中涵盖的所有主题进行全面处理将使本书的规模可能翻倍，而很少有人愿意阅读 1,000 页的技术书籍。因此，本书提供了 NLP 和机器学习整体格局的广阔视角，基于这样一种信念：这种做法对已经是经验丰富的开发者、需要学习 NLP 和机器学习的读者会更有益。

## 目标受众

本书主要面向具有扎实软件开发背景的人士。具体而言，它是针对那些习惯在线搜索更详细技术信息的开发者。如果你是初学者，还有其他更适合你的书籍，你可以通过在线搜索找到它们。

本书也面向具有极其多样背景的国际读者，涵盖不同年龄层。虽然许多读者能够阅读英文，但他们的母语并非英文（可能是第二、第三甚至第四语言）。因此，本书使用标准英文，而非可能对这些读者产生困惑的口语化表达。正如你所知，人们的学习方式各有不同，包括阅读、书写或听力。本书综合考虑了这些点，旨在为目标读者提供舒适且有意义的学习体验。

## 为什么本书包含如此多的主题？

如前所述，正如上一题的回答中提到的，本书旨在为希望学习 NLP 概念和机器学习的开发者服务。由于这涵盖了技术背景差异巨大的人群，因此也有读者对 NLP “一无所知”。因此，本书向读者介绍了大量与 NLP 相关的概念，随后他们可以自行决定进一步深入研究哪些主题。因此，本书不采用“零基础到高阶”的学习路径，也不要求读者掌握章节和附录中涵盖的所有主题；相反，它是一个信息资源，帮助你决定在哪些方面投入时间和精力。

正如你可能已经知道的那样，学习通常通过迭代和重复的方式进行，累积的接触会提升对技术概念的舒适度和理解。对于某些读者来说，这将是他们通往掌握 NLP 和机器学习之旅的第一步。

请阅读 `ChapterOutline.doc` 文档，了解每个章节的 rationale 以及本书章节的阅读顺序。

## 这本书是如何组织的，我将学到什么？

本书大部分章节采用“配对章节”的形式：前两章提供 NumPy 和 Pandas 的入门材料，随后是一对包含 NLP 概念的章节，再接着是一对展示 NLP 概念的 Python 代码示例章节。

下一对章节介绍机器学习概念和算法（如决策树、随机森林和支持向量机），随后第九章探讨情感分析、推荐系统、COVID-19 分析、垃圾邮件检测以及关于聊天机器人的简要讨论。第十章包含使用 TF2 和 Keras 进行 NLP 任务的示例，第十一章介绍 Transformer 架构、基于 BERT 的模型以及 GPT 家族模型，这些模型均在过去三年内开发，且被认为是 SOTA（“state of the art”）。

附录包含 Python 代码示例的多个主题的入门材料，包括 Python 3、正则表达式、Keras、TF2、Matplotlib 和 Seaborn。附录 A（页数最多）涵盖众多主题，如处理包含不同数据类型的数据集、处理缺失数据、统计概念、如何处理不平衡特征（SMOTE）、分析分类器、方差和相关矩阵、维度减少（包括 SVD 和 t-SNE），以及讨论 Gini 不纯度、熵和 KL-偏差的章节。

## 为什么这本书对深度学习的覆盖极少？

本书面向希望了解 NLP 并入门机器学习的开发者。如果你浏览目录，会发现本书涵盖了大量主题，约 600 页。技术类书籍在页数超过一定规模后会出现“拐点”，超过 1000 页的书阅读时间成本较高，尤其是在该领域持续创新的情况下。

基于上述考虑，深度学习的详尽章节超出了入门书籍的范围，更适合一本名为“Deep Learning and NLP”（或类似标题）的书籍。

## 为什么代码示例主要使用 Python？

大多数代码示例较短（通常不超过一页，甚至不足半页），如有需要，你可以轻松快捷地复制粘贴到新的 Jupyter Notebook 中。执行耗时计算的机器学习代码示例同时提供 Python 脚本和 Jupyter Notebook 两种形式。对于引用 CSV 文件的代码示例，你无需在对应的 Jupyter Notebook 中额外编写代码即可读取 CSV 文件。此外，代码示例执行速度快，无需使用 Google Colaboratory 提供的免费 GPU。

如果决定使用 Google Colaboratory，只需将 Python 代码复制粘贴到笔记本中，并利用上传功能上传已有的 Jupyter Notebook。请注意：如果代码引用 CSV 文件，请确保按照第 1 章的说明在对应的 Jupyter Notebook 中加入相应的代码片段以访问 CSV 文件。

## 这本书需要多少 Keras 知识？

对 Keras 有一定了解会很有帮助，你可以阅读附录 D 了解 Keras。此外，附录中还提供了 TensorFlow 2 入门介绍。请注意，Keras 已深度集成到 TensorFlow 2（在 `tf.keras` 命名空间下），它在“纯” TensorFlow 上提供了抽象层，能够更快速地构建原型。

## 是否需要学习本书的理论部分？

答案取决于你计划在 NLP 和机器学习方面投入的程度。除了构建模型外，你还会使用多种算法来判断哪些能够达到项目所需的准确率（或其他指标）。如果表现不足，机器学习的理论部分可帮助你对模型和数据进行“法医”级分析，理想情况下能指导如何改进模型。

## 代码示例是如何创建的？

本书的代码示例使用 Python 3 和 TensorFlow 2 中内置的 Keras 在 MacBook Pro（macOS Sierra，版本 10.12.6）上进行测试和创建。内容上，示例主要源自作者在 Deep Learning 和 Keras 进阶课程中的实践，部分示例则结合了在线论坛讨论中的短代码片段。关键点是：代码示例必须遵循“四 C”原则——Clear（清晰）、Concise（简洁）、Complete（完整）、Correct（正确），在本书篇幅限制下，应尽可能满足这些要求。

## 如何从本书中获得最大收益？

有些程序员擅长从散文中学习，有些则更喜欢大量的示例代码，这意味着没有一种单一的学习方式适用于所有人。

此外，有些程序员希望先运行代码观察其行为，再回到代码深入探讨细节；也有人则采用相反的方法。

因此，本书中的代码示例类型多样：有短示例、长示例，也有基于前一段代码构建的示例。

## 这本书需要哪些先决知识？

熟练掌握 Python 3.x 是最有帮助的技能。了解其他编程语言（如 Java）同样有帮助，因为它能让你接触到编程概念和构造。技术背景越少，要理解本书涵盖的各类主题就越需要耐心和细致。

*如果想确保能够理解本书内容，建议浏览部分代码示例，了解自己熟悉程度与新颖程度。*

## 伴随光盘是否消除了本书的必要性？

伴随文件包含所有代码示例，可节省你手动输入代码并出错的时间和精力。此外，在无法轻松获取这些文件的情况下，本书的代码示例也提供了光盘上不存在的解释。

*伴随文件可通过发送邮件至 info@merclearning.com 下载。*

## 这本书是否包含生产级代码示例？

-   [代码示例的主要目的是展示如何使用 Python 库来解决各种 NLP 任务，并与机器学习结合使用。可读性优先于编写更紧凑但更难理解（且可能更易出错）的代码。如果你决定在生产 Website 中使用这些代码，则应对其进行与代码库其他部分相同的严格分析。]

## 这本书的非技术先决条件是什么？

尽管这个问题的答案较难量化，但拥有强烈的机器学习学习欲望，以及阅读和理解代码示例的动力和纪律，是非常重要的。

即使是简单的机器语言 API 在你第一次接触时也可能成为挑战，所以请做好准备，需要阅读代码示例多次。

## 如何设置命令行？

如果你是 Mac 用户，有三种方法可以实现。第一种方法是使用 Finder 导航到 Applications > Utilities，然后双击 Utilities 应用程序。接下来，如果你已经有一个命令行可用，可以通过输入以下命令来启动一个新的命令行：

```
open /Applications/Utilities/Terminal.app 
```

第二种 Mac 用户的方法是，在已经可见的命令行中，仅需输入 `command+n`，即可在 MacBook 上打开一个新的命令行。

如果你是 PC 用户，可以安装 Cygwin（开源 *[`cygwin.com/`](https://cygwin.com/)*）来模拟 bash 命令，或者使用另一种工具包，如 MKS（商业产品）。请阅读在线文档，了解下载和安装过程。注意，如果自定义的别名定义在主启动文件（如 `.bash_login`）之外的文件中，则不会自动设置这些别名。

## 伴随文件

本书中的所有代码示例和图表均可通过致信出版社 *info@merclearning.com* 获取。

## 作者其他书籍

本书包含几个附录，这些附录是从以下书籍的部分内容中提取的，这些书籍也由 Mercury Learning and Information 出版：

1. Python Pocket Primer:

    9781938549854

2. Regular Expressions Pocket Primer:

    9781683922278

3. Data Cleaning Pocket Primer

    9781683922179

## 完成本书后的“下一步”是什么？

这个问题的答案差异很大，主要取决于你的目标。如果你主要关注 NLP，那么你可以进一步学习注意力机制、Transformer 和与 BERT 相关的模型等更高级的概念。

如果你主要关注机器学习，那么深度学习和强化学习（以及深度强化学习）等子领域可能会吸引你。好在有很多资源可供选择，你可以通过 Internet 搜索这些资源。还有一点要注意的是，你需要学习的机器学习方面取决于你是谁：机器学习工程师、数据科学家、经理、学生或软件开发人员的需求各不相同。

**Oswald Campesato**

**April 2021**

# CHAPTER 1: INTRODUCTION TO NUMPY

本章提供了 Python NumPy 包的快速介绍，该包不仅适用于 Python 脚本，也适用于基于 Python 的 TensorFlow 脚本。本章包含带有循环、数组和列表的 NumPy 代码示例。你还将学习点积、`reshape()` 方法（非常有用！）、使用 Matplotlib 绘图（详见附录 F）以及线性回归示例。

本章的第一部分简要介绍 NumPy 及其有用特性。第二部分包含使用 NumPy 工作数组的示例，并对比列表和数组的相同 API，同时展示如何轻松计算数组中元素的指数相关值（如平方、立方等）。

本章的第二部分介绍子范围，这些子范围在机器学习任务中非常有用且 frequently 被使用。特别是，你将看到处理负数（-1）子范围的代码示例，这些子范围既适用于向量，也适用于数组，但它们在两者之间的解释不同。

本章的第三部分深入探讨其他 NumPy 方法，包括 `reshape()` 方法，它在处理图像文件时极其有用（且非常常见），因为某些 TensorFlow API 需要将二维数组（(R,G,B) 值）转换为对应的一维向量。

本章的第四部分深入探讨线性回归、均方误差（MSE）以及如何使用 NumPy 的 `linspace()` API 计算 MSE。

## 什么是 NumPy？

NumPy 是一个 Python 模块，提供了许多便捷方法，并具有更好的性能。NumPy 提供了用于科学计算的核心库，包括高性能的多维数组和优秀的向量化数学函数，同时支持线性代数和随机数。

NumPy 的设计灵感来自 MatLab，支持列表、数组等。NumPy 比 MatLab 更易于使用，并且在 TensorFlow 2.x 代码以及 Python 代码中非常常见。此外，第 2 章节包含将 NumPy 与 Pandas 结合使用的代码示例。

### 实用的 NumPy 特性

NumPy 包提供了 `ndarray` 对象，它封装了多维数组的多种数据类型。许多 `ndarray` 操作在编译代码中执行，以提高性能。

NumPy 数组具有以下属性：

*   它们具有固定大小
*   元素具有相同的数据类型
*   元素具有相同的大小（除了 objects）
*   修改数组会创建新数组

现在你对 NumPy 有了基本了解，让我们进入下一节，通过一些示例展示如何使用 NumPy 数组。

## 什么是 NumPy 数组？

数组是用于存储数据的连续内存位置的集合，数组中的每个项称为元素。数组中的元素数量称为数组的维度。下面是一个典型的数组声明示例：

```
arr1 = np.array([1,2,3,4,5])
```

上述代码声明 `arr1` 为一个包含五个元素的数组，你可以通过 `arr1[0]` 到 `arr1[4]` 访问这些元素。注意，第一个元素的索引值为 0，第二个为 1，以此类推。因此，如果你声明一个包含 100 个元素的数组，那么第 100 个元素的索引值为 99。

**NOTE**

*   NumPy 数组的第一个位置的索引为 0。

NumPy 将数组视为向量，数学操作在元素级别上进行。请记住以下区别：“ doubling” 数组会将每个元素乘以 2，而“ doubling” 列表会将列表本身追加到自身。
