
其中 ![images](images/c14-i0049.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>t</mi></mrow></math> 是迭代次数， ![images](images/c14-i0050.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>x</mi><mrow><mi>t</mi><mo>,</mo><mi>e</mi><mo>=</mo><mo stretchy="false">(</mo><mi>v</mi><mo>,</mo><mi>c</mi><mo stretchy="false">)</mo></mrow></msub></mrow></math>（ ![images](images/c14-i0051.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>x</mi><mrow><mi>e</mi><mo>,</mo><mi>t</mi><mo>=</mo><mo stretchy="false">(</mo><mi>c</mi><mo>,</mo><mi>v</mi><mo stretchy="false">)</mo></mrow></msub></mrow></math>）表示在不同迭代 ![images](images/c14-i0052.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>t</mi></mrow></math> 中，从变量节点 ![images](images/c14-i0053.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>v</mi></mrow></math>（校验节点 ![images](images/c14-i0054.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>c</mi></mrow></math>）到校验节点 ![images](images/c14-i0055.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>c</mi></mrow></math>（变量节点 ![images](images/c14-i0056.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>v</mi></mrow></math>）的消息。

`CE` 用作损失函数。所提出的 `BP-RNN` 具有一个特性，即在每个时间步之后都存在一个最终的边缘化层。我们可以在该层之后计算损失。此外，如式 ([14.12](#c14.xhtml#c14-disp-0012)) 所示的多损失函数可用于增加梯度更新：

[(14.12)](#c14.xhtml#c14-R_disp-0012)![equation](images/c14-math-0012.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mtable> <mtr> <mtd> <mi>L</mi> <mo stretchy="false">(</mo> <mi>o</mi> <mo>,</mo> <mi>y</mi> <mo stretchy="false">)</mo> <mo>=</mo> <mo>&#8722;</mo> <mfrac> <mn>1</mn> <mi>N</mi> </mfrac> <munderover> <mo stretchy="false" movablelimits="false">&#8721;</mo> <mrow> <mi>t</mi> <mo>=</mo> <mn>1</mn> </mrow> <mi>T</mi> </munderover> <munderover> <mo stretchy="false" movablelimits="false">&#8721;</mo> <mrow> <mi>v</mi> <mo>=</mo> <mn>1</mn> </mrow> <mi>N</mi> </munderover> <msub> <mi>y</mi> <mi>v</mi> </msub> <mspace width="0.3em"/> <mi>log</mi> <mo stretchy="false">(</mo> <msub> <mi>o</mi> <mrow> <mi>v</mi> <mo>,</mo> <mi>t</mi> </mrow> </msub> <mo stretchy="false">)</mo> <mo>+</mo> <mo stretchy="false">(</mo> <mn>1</mn> <mo>&#8722;</mo> <msub> <mi>y</mi> <mi>v</mi> </msub> <mo stretchy="false">)</mo> <mi>log</mi> <mo stretchy="false">(</mo> <mn>1</mn> <mo>&#8722;</mo> <msub> <mi>o</mi> <mrow> <mi>v</mi> <mo>,</mo> <mi>t</mi> </mrow> </msub> <mo stretchy="false">)</mo> </mtd> </mtr> </mtable> </mrow> </math>

整个网络架构如图 [图 14.19](#c14.xhtml#c14-fig-0019) 所示。不同层的节点实现不同的方程：变量层中的节点实现式 ([14.10](#c14.xhtml#c14-disp-0010))，而奇偶校验层中的节点实现式 ([14.11](#c14.xhtml#c14-disp-0011))。边缘化层中的节点实现 `sigmoid` 函数。该 `BP-RNN` 结构的目标是训练参数 `w` 以最小化多损失函数。

[表 14.3](#c14.xhtml#R_c14-tbl-0003) `BER` 结果为采用右规则校验矩阵训练的 `BCH (63, 45)` 码。

| 解码类型 || `BP` || `BP-FF` || `BP-RNN` || `BP-RNN (multiloss)` || `BP-FF (multiloss)` |
| --- | --- | --- | --- | --- | --- |
| **性能增益 (dB)** || 0 || 0.8 || 1 || 1.3 || 1.3 |
| --- | --- | --- | --- | --- | --- |

[表 14.4](#c14.xhtml#R_c14-tbl-0004) 利用 DL 进行信道编码设计的最新成果。

| 神经网络类型 || 信道编码中的应用 |
| --- | --- |
| `DNN` || 解码线性码。联合优化。解码多码。 |
| --- | --- |
| `CNN` || 处理信道中的相关噪声。 |
| `RNN` || 解码序列码。优化传统算法。 |

基于这一理论基础，若干仿真结果在 [表 14.3](#c14.xhtml#c14-tbl-0003) 中给出。以 `BCH (63, 45)` 为例，这些仿真比较了不同的解码类型，包括 `BP`、`BP` 前馈 (`BP-FF`)、`BP-RNN`、`BP-RNN (multiloss)` 和 `BP-FF (multiloss)`。需要注意的是，在 [表 14.3](#c14.xhtml#c14-tbl-0003) 中，`BER`=![images](images/c14-i0057.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mn>1</mn><msup><mn>0</mn><mrow><mo>&#8722;</mo><mn>4</mn></mrow></msup></mrow></math> 时的 `BP` 被视为衡量性能增益的基线。

先前的参考工作还引入了具有神经 `BP` 解码器的改进随机冗余迭代算法 (`mRRD`) 以及使用松弛 ![images](images/c14-i0058.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="normal">&#947;</mi></mrow></math> 的 `BP-RNN` 的松弛方法。读者可以参考 (Nachmani et al., [2018](#c14.xhtml#c14-bib-0022)) 了解更多细节。

### 14.4.3 摘要

由于无线通信是在时相关环境中进行的，`RNNs` 通过仔细学习时域信息有望提高整体检测性能。然而，`RNNs` 依赖于循环结构来提高检测性能，通常会带来显著的处理延迟。因此，低延迟的基于 `RNN` 的解码方案将更理想。

## 14.5 结论

在本章中，我们总结了利用 `DL` 技术在信道编码设计方面的最新研究进展。如 [表 14.4](#c14.xhtml#c14-tbl-0004) 所总结的，针对信道编码领域不同任务的神经网络类型仍需更多研究，并且尚未探索出理解基本关系的统一框架。此外，`DL` 技术是否可用于设计通用编码器/解码器尚未得到解答。因此，联合考虑 `DL` 技术和信道编码方案仍是近期有前景的研究方向。

## 参考文献

1. E. Arıkan. Channel polarization: A method for constructing capacity-achieving codes for symmetric binary-input memoryless channels. IEEE Transactions on Information Theory, 55 (7): 3051–3073, Jul. 2009.

2. Claude Berrou, Alain Glavieux, and Punya Thitimajshima. Near Shannon limit error-correcting coding and decoding: Turbo-codes. 1. In *Communications, 1993. ICC'93 Geneva. Technical Program, Conference Record, IEEE International Conference on*, volume 2, pages 1064–1070. IEEE, 1993.

3. Sebastian Cammerer, Tobias Gruber, Jakob Hoydis, and Stephan Ten Brink. Scaling deep learning-based decoding of polar codes via partitioning. *arXiv preprint arXiv:1702.06901*, 2017.

4. Ronan Collobert and Jason Weston. A unified architecture for natural language processing: Deep neural networks with multitask learning. In *Proceedings of the 25th International Conference on Machine learning*, pages 160–167. ACM, 2008.

5. Nghia Doan, Seyyed Ali Hashemi, and Warren J. Gross. Neural successive cancellation decoding of polar codes. In *2018 IEEE 19th International Workshop on Signal Processing Advances in Wireless Communications (SPAWC)*, pages 1–5. IEEE, 2018.

6. Robert Gallager. Low-density parity-check codes. IRE Transactions on Information Theory, 8 (1): 21–28, 1962.

7. Felix A. Gers, Jürgen Schmidhuber, and Fred Cummins. Learning to forget: Continual prediction with LSTM. IEE, 1999.
