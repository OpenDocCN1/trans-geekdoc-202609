
# 功率放大器行为模型

## 概述
功率放大器行为模型，或黑箱模型，是功率放大器非理想行为的数学描述，主要描述其非线性行为和记忆效应（即 `PA` 动态行为）。与物理模型不同，物理模型需要知道构成 `PA` 的电子元件、其本构关系以及描述其相互作用的理论规则，而 `PA` 行为模型的提取仅依赖于一组输入-输出观测数据。因此，其精度高度依赖于所采用的模型结构和参数提取过程。一般而言，用于近似 `PA` 响应的同一模型也用于估计其逆响应。因此，本小节列出的行为模型是 `PA` 逆行为的有效近似，并在描述数字预失真线性器时将在下一小节中使用。

文献中可以找到大量关于 `PA` 行为建模的出版物，不仅针对单输入单输出（`SISO`）系统，还针对多输入单输出（`MISO`）系统，例如在需要表征并发多频带传输或 `PA` 的动态供电调制策略时。

## Volterra 级数公式
一些最常用的基于多项式的行为模型可视为通用 `Volterra series` 的简化近似。`Volterra series` 旨在描述具有衰减记忆的时间不变非线性系统。离散时间低通等效 `Volterra series` 公式在下文描述。考虑 [图 17.4](#c17.xhtml#c17-fig-0004) 中的一般输入-输出表示，`Volterra series` 的估计输出 ![images](images/c17-i0008.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>&#375;</mi><mo stretchy="false">\[</mo><mi>n</mi><mo stretchy="false">\]</mo></mrow></math> 为

(17.1)![equation](images/c17-math-0001.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mi>&#375;</mi> <mo stretchy="false">\[</mo> <mi>n</mi> <mo stretchy="false">\]</mo> <mo>=</mo> <munderover> <mrow> <mo stretchy="false" movablelimits="false">&#8721;</mo> </mrow> <mrow> <mi>p</mi> <mo>=</mo> <mn>1</mn> </mrow> <mi>P</mi> </munderover> <munderover> <mrow> <mo stretchy="false" movablelimits="false">&#8721;</mo> </mrow> <mrow> <msub> <mi>q</mi> <mi>p</mi> </msub> <mo>=</mo> <mn>0</mn> </mrow> <mrow> <msub> <mi>Q</mi> <mi>p</mi> </msub> <mo>&#8722;</mo> <mn>1</mn> </mrow> </munderover> <mi>&#8943;</mi> <munderover> <mrow> <mo stretchy="false" movablelimits="false">&#8721;</mo> </mrow> <mrow> <msub> <mi>q</mi> <mn>1</mn> </msub> <mo>=</mo> <mn>0</mn> </mrow> <mrow> <msub> <mi>Q</mi> <mn>1</mn> </msub> <mo>&#8722;</mo> <mn>1</mn> </mrow> </munderover> <msub> <mi>h</mi> <mi>p</mi> </msub> <mo stretchy="false">(</mo> <msub> <mi>q</mi> <mn>1</mn> </msub> <mo>,</mo> <mi>&#8943;</mi> <mspace width="0.3em"/> <mo>,</mo> <msub> <mi>q</mi> <mi>p</mi> </msub> <mo stretchy="false">)</mo> <munderover> <mrow> <mo stretchy="false" movablelimits="false">&#8719;</mo> </mrow> <mrow> <mi>i</mi> <mo>=</mo> <mn>1</mn> </mrow> <mi>p</mi> </munderover> <mi>x</mi> <mo stretchy="false">\[</mo> <mi>n</mi> <mo>&#8722;</mo> <msub> <mi>q</mi> <mi>i</mi> </msub> <mo stretchy="false">\]</mo> <mo>.</mo> </mrow> </math> 

该级数由 ![images](images/c17-i0009.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>P</mi></mrow></math> 个维度阶数递增的核组成。使用完整的 `Volterra series` 的主要缺点是，当考虑高阶核时参数数量呈指数增长，而典型的通信信号没有足够的丰富性来充分激励这些核，这最终可能导致病态问题。

## 常见行为模型
由于其简单性，文献中最广泛使用的模型之一是记忆多项式（`MP`），由 Kim 和 Konstantinou 在 ([2001](#c17.xhtml#c17-bib-0060)) 中提出。另一种广泛用于 `SISO` 系统的模型是广义记忆多项式（`GMP`）行为模型，由 D.R. Morgan、Z. Ma 等人在 ([2006](#c17.xhtml#c17-bib-0023)) 中提出。与 `MP` 不同，`GMP` 具有二维核（考虑复信号与滞后和超前包络项之间的交叉项乘积），这提高了建模精度，但代价是增加了参数数量。文献中还有大量用于 `SISO` 系统 `DPD` 目的的其他行为模型：仅举几个例子，Montoro 等人 ([2007](#c17.xhtml#c17-bib-0077)) 提出的 `NARMA` 模型以及 Zhu 等人 ([2006](#c17.xhtml#c17-bib-0129)) 中的动态偏差减小 `Volterra series`。有关 `SISO` 系统 `PA` 行为模型的进一步信息可在 Scheurs 等人 ([2009](#c17.xhtml#c17-bib-0100)) 中找到。此外，在考虑 Roblin 等人 ([2013](#c17.xhtml#c17-bib-0096)) 中所述的并发多频带传输，或与 Gilabert 和 Montoro ([2015](#c17.xhtml#c17-bib-0030)) 中所述的 `PA` 动态供电调制策略相结合，或在 Hausmair 等人 ([2018](#c17.xhtml#c17-bib-0039)) 中所述的多天线系统中，每个发射路径都有自己的 `PA` 和天线单元时，需要 `MISO` 行为模型来表征不同的非线性行为来源。此外，作为基于多项式的行为模型的替代方案，`ANN` 和 `SVR` 方法已在文献中用于 `PA` 行为建模和 `DPD` 线性化目的。如 [第 17.4 节](#c17.xhtml#c17-sec-0018) 和 [第 17.5 节](#c17.xhtml#c17-sec-0031) 所示，`ANNs` 和 `SVR` 通过提供全局近似和更好的外推能力，可以超越经典基于多项式的解决方案（本质上是局部近似）的建模能力。

## 矩阵表示
一般而言，估计的 `PA` 行为模型输出 ![images](images/c17-i0010.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>&#375;</mi><mo stretchy="false">\[</mo><mi>n</mi><mo stretchy="false">\]</mo></mrow></math>（对于 ![images](images/c17-i0011.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>n</mi><mo>=</mo><mn>0</mn><mo>,</mo><mn>1</mn><mo>,</mo><mi>&#8943;</mi><mspace width="0.3em"/><mo>,</mo><mi>N</mi><mo>&#8722;</mo><mn>1</mn></mrow></math>）可按矩阵表示法定义为

[(17.2)](#c17.xhtml#c17-R_disp-0002)![equation](images/c17-math-0002.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mi mathvariant="bold-italic">&#375;</mi> <mo>=</mo> <mi mathvariant="bold-italic">X</mi> <mi mathvariant="bold-italic">w</mi> </mrow> </math> 
