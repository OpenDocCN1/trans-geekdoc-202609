
不过必须承认，通过在这里揭示机器学习更多的本质，至少更容易定义将典型“形式计算”与机器学习融合的问题。传统上，系统的计算能力与其可训练性之间存在权衡。确实，从我们在这里看到的情况来看，这似乎反映了这样一种感觉：“更大块的计算不可约性”更难通过自适应进化的增量构建过程塞入其中。

## 如何终极看待机器学习

实际上，机器学习的力量来自于利用计算不可约性这一“自然资源”。但当它使用计算不可约性时，是通过“觅食”碰巧推进其目标的片段来实现的。想象一下在砌墙。一种可能是塑造特定形状的砖块，知道它们能拼合。另一种则是看看周围躺着的石头，然后尽力把这些石头拼凑起来砌墙。

如果接着问“为什么墙会有这种图案？”，答案基本上会是“因为这就是碰巧躺在那里的石头能拼出的样子”。这本身没有总括性的理论；它只是可用资源的反映。在机器学习的情况下，人们可以预期，所看到的很大程度上将反映计算不可约性的原始特征。换句话说，机器学习的基础在很大程度上植根于[鲁里奥洛吉科学](https://writings.stephenwolfram.com/2021/09/charting-a-course-for-complexity-metamodeling-ruliology-and-more/#the-pure-basic-science-of-ruliology)。在我们努力理解机器学习中“真正发生了什么”，以及很可能在神经科学中理解更多时，我们很大程度上应该求助于这门科学。

## 历史与个人注记

从某种意义上说，智力史上的某种偶然导致我在这里讨论的基础性问题很久以前没有得到解决；从另一种意义上说，这似乎是某些直觉和工具直到最近才发展起来的必然结果。

# 神经网络与机器学习的演变

## 早期基础（1940 年代–1960 年代）

大脑从根本上由相连的神经细胞构成这一观点在十九世纪后期被提出，并在二十世纪的最初几十年站稳脚跟——以计算方式运作的[神经网络的形式化概念](https://www.wolframscience.com/nks/notes-10-12--history-of-ideas-about-thinking/)在 Warren McCulloch 和 Walter Pitts 1943 年的工作中以完整形式出现。到 1950 年代末，已有以“感知机”形式出现的神经网络硬件实现（通常用于图像处理）。但尽管早期热情高涨，实际效果好坏参半，到了 1960 年代末，人们宣称适合数学分析的简单情况已被“解决”——导致普遍认为“神经网络无法做任何有趣的事”。

自 1940 年代以来，一直有关于神经网络的零星通用分析，特别是使用物理学方法。但这些分析通常最终得到连续近似之类的结果——这对神经网络的信息处理方面几乎无法说明什么。同时，一直存在一种潜在的信念，认为神经网络 somehow 能够解释并复现大脑的工作原理——但似乎不存在能确切说明如何做到这一点的方法。

## 复兴与停滞（1980 年代–2010 年）

随后在 1980 年代初，神经网络迎来了兴趣的复苏，源头有多个方向。部分工作集中在让神经网络执行特定的“类人”任务这一非常实用的努力上。但也有部分更偏向理论，通常使用统计物理学或动力系统的方法。

然而，热度很快消退，随后几十年里只剩下少数团队仍在研究神经网络。

## 深度学习突破（2011 年至今）

然后在 2011 年，将神经网络用于图像分析取得了一个惊人的突破。这是一个重要的实际进展。但它是由技术理念和开发驱动的——而非任何重大的新理论分析或框架。

这也是随后几乎所有进展的模式。人们投入巨大精力设计出行之有效的神经网络系统——并围绕如何最好地做到这一点积累了[各种民间经验](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/#the-practice-and-lore-of-neural-net-training)。但并没有真正尝试建立底层理论；这是一个工程实践领域，而非基础科学。

正是在这种传统下，[ChatGPT 于 2022 年底横空出世](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/)。关于 LLMs 的几乎一切似乎都很复杂。是的，经验上确实存在一些大尺度规律（如缩放定律）。我很快怀疑 LLMs 的成功是人类语言中存在[此前未被清晰识别的普遍规律](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/#what-really-lets-chatgpt-work)的有力暗示。但除了极少数异常例子外，几乎没有关于“LLMs 内部发生了什么”似乎容易解码的内容。而试图给系统运行加上“强护栏”——实际上是为了使其在某种程度上变得“可预测”或“可理解”——通常会大幅降低其能力（这一点在计算不可约性的背景下现在讲得通了）。

## 个人历程与理论探索

我自己与机器学习和神经网络的渊源[始于 1980 年](https://writings.stephenwolfram.com/2015/05/wolfram-language-artificial-intelligence-the-image-identification-project/#personal-backstory)，当时我正在开发我的 [SMP 符号计算系统](https://writings.stephenwolfram.com/2013/06/there-was-a-time-before-mathematica/)，并思考是否可能将该系统的符号模式匹配基础推广为某种“模糊模式匹配”，使其更接近人类思维。我了解神经网络，但将其视为大脑的半写实模型，而非例如我设想的可能“解决”模糊匹配的那类潜在算法来源。

部分正是由于试图理解神经网络等系统的本质，[1981 年我提出了](https://www.wolframscience.com/nks/p17--the-personal-story-of-the-science-in-this-book/)后来被认知为一维元胞自动机的东西。很快我深入研究元胞自动机，并建立了关于复杂行为如何从简单规则中产生的新直觉。但当我得知近期有人利用统计力学思想建立神经网络的理想化模型时，我至少好奇到建立模拟来尝试更多地理解这些模型。

但我做的并不成功。我既无法让模型做出任何有实际意义的有趣事情，也未能获得对它们的良好理论理解。我一直在想，只是“运行”的元胞自动机，与还能“学习”的神经网络等系统之间，可能存在什么关系。事实上，[1985 年我尝试制作了一个基于元胞自动机的最小模型](https://content.wolfram.com/sw-publications/2020/07/approaches-complexity-engineering.pdf)来探索这一点。这就是我现在称之为的“垂直分层规则阵列”。虽然在许多方面我已经在问正确的问题，但这是一个不幸的具体系统选择——我对它的实验并未揭示出我们现在看到的那类现象。

岁月流逝。我在《[新科学](https://www.wolframscience.com/nks/)》中写了一个关于[“人类思维”](https://www.wolframscience.com/nks/chap-10--processes-of-perception-and-analysis/#sect-10-12--human-thinking)的章节，讨论了思维本质的简单基础规则的可能性，甚至包含了一个神经网络的最小离散类比。不过当时我并未发展这些想法。到了 2017 年，即该书出版 15 年后——且了解深度学习的突破后——我开始[更具体地思考神经网络是通过从计算宇宙中采样程序来获得其能力](https://writings.stephenwolfram.com/2017/05/a-new-kind-of-science-a-15-year-view/#machine-learning-and-the-neural-net-renaissance)的。但我仍未完全看清这将如何运作。

与此同时，从机器学习实践经验中涌现出一种新直觉：如果你对几乎任何系统“猛击”“足够用力”，它就会学会。这是否意味着或许不需要神经网络的所有细节也能成功进行机器学习？能否或许构建一个结构足够简单、其运作例如可通过可视化访问的系统？当我在 2023 年初[撰写关于 ChatGPT 和 LLMs 的阐述](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/)时，我特别对此感到好奇。我一直在谈论“LLM 科学”，但没太有机会去研究它。

但随后，几个月前，作为[一项旨在理解科学所做之事与 AI 所做之事之间关系的努力](https://writings.stephenwolfram.com/2024/03/can-ai-solve-science/)的一部分，我尝试了一种[“一次性实验”](https://writings.stephenwolfram.com/2024/03/can-ai-solve-science/#exploring-spaces-of-systems)——令我非常惊讶的是，它似乎成功捕捉到了[使生物进化成为可能的本质](https://writings.stephenwolfram.com/2024/05/why-does-biological-evolution-work-a-minimal-model-for-biological-evolution-and-other-adaptive-processes/)。但其他适应性进化——特别是机器学习——又该如何呢？所需的模型与[我 1985 年研究的内容](https://content.wolfram.com/sw-publications/2020/07/approaches-complexity-engineering.pdf)有着令人尴尬的相似性。但现在我有了新的直觉——并且多亏了 [Wolfram Language](https://www.wolfram.com/language/)，拥有了强大得多的工具。这里呈现的成果正是我在此方面努力的结果。

当然，这只是个开始。但我非常激动，能够看到我认为是机器学习基础科学开端的东西。已经有了明确的实际应用方向（不必说，我计划深入探索这些方向）。并且有迹象表明，我们或许最终能够理解机器学习的“魔力”究竟为何——以及在何时——奏效。

## 致谢

感谢 [Wolfram Institute](https://www.wolframinstitute.org/) 的 Richard Assar 提供的大量帮助。还要感谢 Brad Klee、Tianyi Gu、Nik Murzin 和 Max Niederman 提供的具体成果，感谢 [Symbolica](https://www.symbolica.ai/) 的 George Morgan 及其他人员的早期关注，以及感谢 Kovas Boguta 多年前建议将机器学习与《新科学》中的思想联系起来。
