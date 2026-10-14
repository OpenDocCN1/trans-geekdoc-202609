
也可以实现分布式隐写术，使得数据隐藏的位置可以预先确定。例如，消息可以总是隐藏在特定图像的预定位置中；因此，接收这些消息的人只需定期检查这些图像。这显然会降低安全性。

消息可以使用任何标准的隐写技术进行编码，例如使用最小比特（LSB）或离散余弦变换（DCT）来存储隐藏消息。在使用分布式隐写术隐藏消息之前，建议先使用加密算法对消息进行加密。同样建议至少对隐写密钥进行加密。

**Note**

将加密与隐写术结合是一种非常强大的数据保护方式。我们在本章中研究的工具之一，如 Invisible Secrets，提供了在 carrier 文件中加密并隐藏数据的选项。

#### Conclusions

在本章中，我们研究了隐写术，这是一个有趣的数据安全领域。最常见的隐写术实现方式是通过 LSB 方法。然而，本章提供了其他方法的简要概述。你应该熟悉隐写术的概念，以及本章中提到的至少一个隐写术工具。

你还被介绍了隐写分析（steganalysis），并获得了关于常见隐写检测方法的简要描述。本章以对分布式隐写术专利方法的良好描述而结束。

#### Test Your Knowledge

[1](#part0027.xhtml#ch16qu1). 最常见的隐写术方法是什么？

[2](#part0027.xhtml#ch16qu2). 单词“steganography”最早出现在哪里？

[3](#part0027.xhtml#ch16qu3). 使用卡片或面具覆盖纸张以仅显示隐藏消息的方法是什么？

[4](#part0027.xhtml#ch16qu4). \_\_\_\_\_\_\_\_\_\_\_ 隐藏数据在处理应用未处理的文件部分中。

[5](#part0027.xhtml#ch16qu5). \_\_\_\_\_\_\_\_\_\_\_ 用一些位替换文件中的一些位以隐藏数据。

[6](#part0027.xhtml#ch16qu6). \_\_\_\_\_\_\_\_\_\_\_ 将有限序列的数据点表示为在不同频率振荡的余弦函数之和。

[7](#part0027.xhtml#ch16qu7). 奇偶校验通常与哪种隐写术一起使用？

[8](#part0027.xhtml#ch16qu8). 最常见的隐写分析方法之一是 \_\_\_\_\_\_\_\_\_\_\_。

[9](#part0027.xhtml#ch16qu9). \_\_\_\_\_\_\_\_\_\_\_ 是一种统计测试，可用于检测隐写术。

[10](#part0027.xhtml#ch16qu10). 隐藏数据的文件被称为什么？

```
[1](#part0027.xhtml#ch16qu1a). LSB (least significant bit)

[2](#part0027.xhtml#ch16qu2a). A book by Johannes Trithemius entitled *Steganographia*

[3](#part0027.xhtml#ch16qu3a). Cardan grille

[4](#part0027.xhtml#ch16qu4a). Injection-based techniques

[5](#part0027.xhtml#ch16qu5a). Substitution-based techniques

[6](#part0027.xhtml#ch16qu6a). Discrete cosine transform (DCT)

[7](#part0027.xhtml#ch16qu7a). Steganophony

[8](#part0027.xhtml#ch16qu8a). the close-color pair

[9](#part0027.xhtml#ch16qu9a). The chi-squared test

[10](#part0027.xhtml#ch16qu10a). The carrier file
```
