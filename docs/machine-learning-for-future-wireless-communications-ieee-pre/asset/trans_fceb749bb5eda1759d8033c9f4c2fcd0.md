
# BP 解码算法

`BP` 算法是一种常用的解码方法，可用于解码 `LDPC` 码或 `polar` 码。`BP` 解码算法可以从 `Tanner graph` 构造而来，它可以表示描述该码的 `parity matrix`。消息通过边传输。每个节点根据通过所有其他边接收到的所有传入消息计算其传出消息。

## 解码方程

整个 `BP` 解码过程可以用以下方程表示：

(14.7)![方程](images/c14-math-0007.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mtable> <mtr> <mtd> <msub> <mi>x</mi> <mrow> <mi>i</mi> <mo>,</mo> <mi>e</mi> </mrow> </msub> <mo>=</mo> <mo stretchy="false">(</mo> <mi>v</mi> <mo>,</mo> <mi>c</mi> <mo stretchy="false">)</mo> <mo>=</mo> <msub> <mi>l</mi> <mi>v</mi> </msub> <mo>+</mo> <munder> <mo stretchy="false" movablelimits="false">&#8721;</mo> <mrow> <msup> <mi>e</mi> <mo>&#8242;</mo> </msup> <mo>=</mo> <mo stretchy="false">(</mo> <mi>v</mi> <mo>,</mo> <msup> <mi>c</mi> <mo>&#8242;</mo> </msup> <mo stretchy="false">)</mo> <mo>,</mo> <msup> <mi>c</mi> <mo>&#8242;</mo> </msup> <mo>&#8800;</mo> <mi>c</mi> </mrow> </munder> <msub> <mi>x</mi> <mrow> <mi>i</mi> <mo>&#8722;</mo> <mn>1</mn> <mo>,</mo> <msup> <mi>e</mi> <mo>&#8242;</mo> </msup> </mrow> </msub> </mtd> </mtr> </mtable> </mrow> </math> (14.8)![方程](images/c14-math-0008.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mtable> <mtr> <mtd> <msub> <mi>x</mi> <mrow> <mi>i</mi> <mo>,</mo> <mi>e</mi> </mrow> </msub> <mo>=</mo> <mn mathvariant="normal">2</mn> <mi mathvariant="normal">tan</mi> <msup> <mi mathvariant="normal">h</mi> <mrow> <mo>&#8722;</mo> <mn mathvariant="normal">1</mn> </mrow> </msup> <mfenced open="(" close=")" separators=""> <munder> <mo stretchy="false" movablelimits="false">&#8719;</mo> <mrow> <msup> <mi>e</mi> <mo>&#8242;</mo> </msup> <mo>=</mo> <mo stretchy="false">(</mo> <mi>v</mi> <mo>,</mo> <msup> <mi>c</mi> <mo>&#8242;</mo> </msup> <mo stretchy="false">)</mo> <mo>,</mo> <msup> <mi>v</mi> <mo>&#8242;</mo> </msup> <mo>&#8800;</mo> <mi>v</mi> </mrow> </munder> <mi>tanh</mi> <mfenced open="(" close=")" separators=""> <mfrac> <mrow> <msub> <mi>x</mi> <mrow> <mi>i</mi> <mo>&#8722;</mo> <mn>1</mn> <mo>,</mo> <msup> <mi>e</mi> <mo>&#8242;</mo> </msup> </mrow> </msub> </mrow> <mn>2</mn> </mfrac> </mfenced> </mfenced> </mtd> </mtr> </mtable> </mrow> </math>

最终 ![图像](images/c14-i0048.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>v</mi></mrow></math>th 网络输出为

(14.9)![方程](images/c14-math-0009.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mtable> <mtr> <mtd> <msub> <mi>o</mi> <mi>v</mi> </msub> <mo>=</mo> <msub> <mi>l</mi> <mi>v</mi> </msub> <mo>+</mo> <munder> <mo stretchy="false" movablelimits="false">&#8721;</mo> <mrow> <msup> <mi>e</mi> <mo>&#8242;</mo> </msup> <mo>=</mo> <mo stretchy="false">(</mo> <mi>v</mi> <mo>,</mo> <msup> <mi>c</mi> <mo>&#8242;</mo> </msup> <mo stretchy="false">)</mo> </mrow> </munder> <msub> <mi>x</mi> <mrow> <mn>2</mn> <mi mathvariant="normal">L</mi> <mo>,</mo> <msup> <mi>e</mi> <mo>&#8242;</mo> </msup> </mrow> </msub> </mtd> </mtr> </mtable> </mrow> </math>

其中 `L` 表示迭代次数，第 `i` 个隐藏层，`i`=1,2,…,2`L`。表示 `e`=(`v`,`c`) 为第 `i` 个隐藏层中处理单元的索引。`x` 是处理单元的输出消息。

## 复杂度和改进

虽然 `BP` 解码的性能对于许多解码过程来说已经足够好，但其复杂度非常高，在硬件上并不友好。为了解决这个问题，研究人员提出了多种改进的 `BP` 解码器，包括 `min-sum` 解码器、归一化 `min-sum` (`NMS`)、偏移 `min-sum` (`OMS`)、神经归一化 `min-sum` (`NNMS`)、神经偏移 `min-sum` (`NOMS`) 等。 (Nachmani et al., [2018](#c14.xhtml#c14-bib-0022))。

![图 14.19 展开三次的循环神经网络架构，对应于三次完整的 BP 迭代。](images/c14f019.jpg)

[图 14.19](#c14.xhtml#R_c14-fig-0019) 展开三次的循环神经网络架构，对应于三次完整的 `BP` 迭代。

## BP-RNN

更重要的是，(Nachmani et al., [2018](#c14.xhtml#c14-bib-0022)) 发起了关于 `RNN` 与 `BP` 解码相关的一些工作。他们使用 `Tanner graph` 中边的绑定权重来表示一个称为 `BP-RNN` 的 `RNN`。修改后的方程为

[(14.10)](#c14.xhtml#c14-R_disp-0010)![方程](images/c14-math-0010.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mtable> <mtr> <mtd> <msub> <mi>x</mi> <mrow> <mi>t</mi> <mo>,</mo> <mi>e</mi> <mo>=</mo> <mo stretchy="false">(</mo> <mi>v</mi> <mo>,</mo> <mi>c</mi> <mo stretchy="false">)</mo> </mrow> </msub> <mo>=</mo> <mi>tanh</mi> <mfenced open="(" close=")" separators=""> <mfrac> <mn>1</mn> <mn>2</mn> </mfrac> <mfenced open="(" close=")" separators=""> <msub> <mi>w</mi> <mi>v</mi> </msub> <msub> <mi>l</mi> <mi>v</mi> </msub> <mo>+</mo> <munder> <mo stretchy="false" movablelimits="false">&#8721;</mo> <mrow> <msup> <mi>e</mi> <mo>&#8242;</mo> </msup> <mo>=</mo> <mo stretchy="false">(</mo> <msup> <mi>c</mi> <mo>&#8242;</mo> </msup> <mo>,</mo> <mi>v</mi> <mo stretchy="false">)</mo> <mo>,</mo> <msup> <mi>c</mi> <mo>&#8242;</mo> </msup> <mo>&#8800;</mo> <mi>c</mi> </mrow> </munder> <msub> <mi>w</mi> <mrow> <mi>e</mi> <mo>,</mo> <msup> <mi>e</mi> <mo>&#8242;</mo> </msup> </mrow> </msub> <msub> <mi>x</mi> <mrow> <mi>t</mi> <mo>&#8722;</mo> <mn>1</mn> <mo>,</mo> <msup> <mi>e</mi> <mo>&#8242;</mo> </msup> </mrow> </msub> </mfenced> </mfenced> </mtd> </mtr> </mtable> </mrow> </math> [(14.11)](#c14.xhtml#c14-R_disp-0011)![方程](images/c14-math-0011.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mtable> <mtr> <mtd> <msub> <mi>x</mi> <mrow> <mi>t</mi> <mo>,</mo> <mi>e</mi> <mo>=</mo> <mo stretchy="false">(</mo> <mi>c</mi> <mo>,</mo> <mi>v</mi> <mo stretchy="false">)</mo> </mrow> </msub> <mo>=</mo> <mn>2</mn> <msup> <mi>tanh</mi> <mrow> <mo>&#8722;</mo> <mn>1</mn> </mrow> </msup> <mfenced open="(" close=")" separators=""> <munder> <mo stretchy="false" movablelimits="false">&#8719;</mo> <mrow> <msup> <mi>e</mi> <mo>&#8242;</mo> </msup> <mo>=</mo> <mo stretchy="false">(</mo> <mi>v</mi> <mo>,</mo> <msup> <mi>c</mi> <mo>&#8242;</mo> </msup> <mo stretchy="false">)</mo> <mo>,</mo> <msup> <mi>v</mi> <mo>&#8242;</mo> </msup> <mo>&#8800;</mo> <mi>v</mi> </mrow> </munder> <msub> <mi>x</mi> <mrow> <mi>t</mi> <mo>,</mo> <msup> <mi>e</mi> <mo>&#8242;</mo> </msup> </mrow> </msub> </mfenced> </mtd> </mtr> </mtable> </mrow> </math>

