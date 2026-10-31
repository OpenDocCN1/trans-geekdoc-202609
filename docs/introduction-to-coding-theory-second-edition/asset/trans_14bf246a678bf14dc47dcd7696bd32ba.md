
唯一可以（也许应该）跳过的章节是关于 MacWilliams 变换的第 3.5 节。剩余的时间应用于第一部分中一章或几章后面的章节。第 7 章将是一个自然的选择，因为二进制 Golay 码可能是所有码中最著名的。通常我会讲授第 6 章，因为它是第一个非标准应用的例子，而且可以在一节课内完成。

另一个选择是讲授第 8 章以及第 9 章的部分内容。这些章节构成一个整体，因为熵函数在第 9 章的渐近表达式中使用。

两学期课程第二学期的典型起点是循环码及其实现理论，第 12 章和第 13 章，以及第 14 章。第 13 章的后半部分是可选的（应用于指纹识别、Roos 界、van Lint-Wilson 界、与传统方法的比较以及第 13.4 节关于常循环码的内容）。关于 BCH 码译码算法的第 13.3 节也可以被舍弃。

第 17 章可被视为编码理论的另一个核心领域，因为它能更好地理解许多重要码。舍弃第一节的主要定理将是可惜的。第一节中的一些应用应该被涵盖。

从这里开始有几个选择。

为了对编码理论及其与伽罗瓦几何的联系进行透彻介绍，可以完全集中在第 17 章。

另一种可能性是缩短第 17 章的内容，转而讲授第 16 章的几个应用。第 23 章中关于 tms-网和球堆积的章节是为研究生课程收尾的良好选择。这也有一个优点，即课程以对一个例外对象——Leech 格的介绍结束。

第三种策略是集中于循环码理论及其应用。这样的课程将以第 18 章结束。

## The database

线性码和量子码参数的表格可在 M. Grassl 的网页上找到

```
http://www.codetables.de
```

## What has changed in the second edition?

变化太多无法穷举。一个宏观性的变化是第二版增加了新的第三部分，专门讨论代数几何码。第一版最后一章中的一个小节已发展为第二版的新第 15 章，包含线性规划的介绍以及对码和正交阵列的显式界的推导。关于加性码和网络码的第 18 章是第一版对应章节的完全重塑版本。循环情形基于更一般的理论，几何方法得到了极大的扩展，并且新增了一个关于网络码的章节。最后一章也发生了变化。第一版中的两个小节已消失，因为它们各自变成了独立的章节。还增加了关于置换码和高度对称码的章节，以及两个旨在提高文本可读性的章节，一个关于文本中使用的各个小域，另一个关于文本中构造的各个短码。

## Textbooks

教材中的早期经典是 E. R. Berlekamp 的《Algebraic Coding Theory》[11]，它特别提供了对循环码传统理论的优秀介绍。MacWilliams 和 Sloane 的 1977 年著作《The Theory of Error-Correcting Codes》[142] 被视为传统编码理论的圣经。较新的入门著作是 J. H. van Lint 的《Introduction to Coding Theory》[211]，这是一部相对简短而密集的文本，在吸引纯数学家进入该领域方面发挥了很大作用。H. Stichtenoth 的著作《Algebraic Function Fields and Codes》[198] 是关于一元代数函数域（等价于代数曲线）理论及其导出码的自成体系的介绍。在本科教材中，我们提到 Vera Pless 的《The Theory of Error-Correcting Codes》[165] 和 R. Hill 的《A first course in coding theory》[112]。Hill 的书是第一本介绍编码几何方法的著作。

Hedayat、Sloane 和 Stufken 的《Orthogonal Arrays: Theory and Applications》[109] 介绍了正交阵列（对偶码）及其在实验设计中的应用。

## Acknowledgments

我感谢 Yves Edel；Wolfgang Ch. Schmid、Peter Hellekalek 以及萨尔茨堡大学数学研究所；Fernanda Pambianco、Stefano Marcugini、Massimo Giulietti、Daniele Bartoli、Giorgio Faina 以及佩鲁贾大学数学与计算机科学系；Bernd Stellmacher 以及基尔大学数学研讨会；C. L. Chen、Ron Crandall、Ludo Tolhuizen、Albrecht Brandis、Allan Struthers、密歇根理工大学；Gary Ebert；以及国家安全局。

![](img/2fa0633d317c0872f05788febf717c11_23_0.png)

## Taylor & Francis

Taylor & Francis Group

http://taylorandfrancis.com

## About the author

Jürgen Bierbrauer 于 1977 年在德国美因茨大学获得数学博士学位，博士论文主题为有限群理论。他的数学兴趣在于离散数学的代数方法及其应用。他于 1977 年至 1994 年在德国海德堡大学任职，并在密歇根州霍顿的密歇根理工大学担任正教授直至 2015 年退休。他的非数学兴趣包括罗曼语族语言、文学和围棋。

![](img/2fa0633d317c0872f05788febf717c11_25_0.png)

## Taylor & Francis

Taylor & Francis Group

http://taylorandfrancis.com

## Part I

### An elementary introduction to coding

![](img/2fa0633d317c0872f05788febf717c11_27_0.png)

Taylor & Francis
Taylor & Francis Group
http://taylorandfrancis.com

## Chapter 1

### The concept of coding

### 1.1 Bitstrings and binary operations

基本概念：位、位串、消息传输、从太空传输图像、摩尔斯电码、异或运算、域 F₂、消息传输模型、纠错的初步思想。

编码理论的对象是通过噪声信道传输消息。图 1.1 显示了描述该情况的标准图示。

首先我们需要理解这幅图中的元素含义：什么是消息、信道、什么是噪声？在过程中我们会遇到更多基本概念。本章将解释其中一些。我们从消息开始。

![](img/2fa0633d317c0872f05788febf717c11_28_0.png)

图 1.1：通过噪声信道的消息传输

如果有 8 条可能发送的消息，那么我们可以将每条消息表示为长度为 3 的位串，如 000 或 011 或 110。我们通常假设已完成此操作，并将 **消息** 定义为位串。以下是一些位串及其长度的例子：

| 位串 | 长度 |
|---|---|
| 000 | 3 |
| 110 | 3 |
| 110011 | 6 |
| 0000011111 | 10 |

### Transmitting pictures from space

假设我们希望从外太空传输一张照片，比如 20 世纪 80 年代初由旅行者号航天器拍摄的土星照片之一（《星际迷航》迷称之为 V'ger）。图片被划分为 800 × 800 像素；每个像素被分配 256 = 2⁸ 个亮度等级之一。因此像素的亮度由长度为 8 的位串表示，而全黑白图片由 800 × 800 × 8 位组成。由于图片实际上是彩色的，同一张照片会被传输三次，每次通过不同的颜色滤镜。因此全彩图片将由长度为 3 × 800 × 800 × 8 = 15,360,000 的位串表示。这就是我们的消息。信道由航天器与地球接收器之间空间的特性决定，尤其是地球大气。一定数量的位将被破坏。这里我们只考虑 0 被发送而 1 被接收或相反类型的错误。

### The Morse code

另一个说明每个消息都可以用位串表示的例子是摩尔斯电码，自 1840 年代以来一直用于电报通信。它用最多五个点和划的序列表示 26 个字母 A、B、…、Z，每个数字 0、1、…、9 以及句号、逗号和问号。点代表短信号，划代表长信号。划的长度大约是点的三倍。例如，

