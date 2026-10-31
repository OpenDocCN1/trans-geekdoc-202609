
[(17.10)](#c17.xhtml#c17-R_disp-0010)![equation](images/c17-math-0010.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mi mathvariant="bold-italic">U</mi> <mo>=</mo> <msup> <mrow> <mo stretchy="false">(</mo> <msub> <mi mathvariant="bold-italic">&#981;</mi> <mi mathvariant="bold-italic">u</mi> </msub> <mo stretchy="false">\[</mo> <mn>0</mn> <mo stretchy="false">\]</mo> <mo>,</mo> <mi>&#8943;</mi> <mspace width="0.3em"/> <mo>,</mo> <msub> <mi mathvariant="bold-italic">&#981;</mi> <mi mathvariant="bold-italic">u</mi> </msub> <mo stretchy="false">\[</mo> <mi>n</mi> <mo stretchy="false">\]</mo> <mo>,</mo> <mi>&#8943;</mi> <mspace width="0.3em"/> <mo>,</mo> <msub> <mi mathvariant="bold-italic">&#981;</mi> <mi mathvariant="bold-italic">u</mi> </msub> <mo stretchy="false">\[</mo> <mi>N</mi> <mo>&#8722;</mo> <mn>1</mn> <mo stretchy="false">\]</mo> <mo stretchy="false">)</mo> </mrow> <mi>T</mi> </msup> <mo>.</mo> </mrow> </math>

前向路径中公式 ([17.8](#c17.xhtml#c17-disp-0008)) 描述的 DPD 函数可以在可编程逻辑 (PL) 器件中实时实现，采用不同的方法，例如查找表 (LUTs)（例如 Molina et al. ([2017](#c17.xhtml#c17-bib-0076))、Gilabert et al. ([2007](#c17.xhtml#c17-bib-0033))），使用 Horner 法则的多项式方法的复数乘法器，如 Mrabet et al. ([2012](#c17.xhtml#c17-bib-0078)) 中所述，或如 Cao et al. ([2017](#c17.xhtml#c17-bib-0012)) 中所述的复数乘法器和存储块的某种组合。

与前向路径中的 DPD 不同，参数的辨识/自适应不需要实时进行，因此可以在处理系统 (PS) 中实现。因此，DPD 系数可以在比实时慢的时间尺度上迭代提取和自适应。DPD 系数的提取可以按照直接学习或间接学习方法进行。

采用间接学习方法的闭环自适应 DPD 架构的框图如图 [图 17.5](#c17.xhtml#c17-fig-0005) 所示。前向路径中的 DPD 函数由公式 ([17.8](#c17.xhtml#c17-disp-0008)) 描述，或考虑矩阵表示时由公式 ([17.9](#c17.xhtml#c17-disp-0009)) 描述。然而，采用间接学习方法时，PA 逆模型被估计为后失真。也就是说，所做的假设是后失真系数等于预失真系数；如 Braithwaite ([2015](#c17.xhtml#c17-bib-0007)) 中所述，只要发射路径或观测路径中没有饱和，该近似就可以被认为是一个有效的近似。

采用直接学习方法的闭环自适应 DPD 架构的框图如图 [图 17.6](#c17.xhtml#c17-fig-0006) 所示。如 Braithwaite ([2015](#c17.xhtml#c17-bib-0007)) 中所述，与间接学习方法相比，采用直接学习估计时，我们获得了对噪声 PA 输出观测的鲁棒性，并避免了系数向量偏离其最优值。

在直接和间接学习方法中，系数可以迭代提取：

[(17.11)](#c17.xhtml#c17-R_disp-0011)![equation](images/c17-math-0011.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <msup> <mi mathvariant="bold-italic">w</mi> <mrow> <mi>j</mi> <mo>+</mo> <mn>1</mn> </mrow> </msup> <mo>=</mo> <msup> <mi mathvariant="bold-italic">w</mi> <mi>j</mi> </msup> <mo>+</mo> <mi>&#956;</mi> <mi mathvariant="bold-italic">&#916;</mi> <mi>w</mi> <mo>.</mo> </mrow> </math> ![图 17.5 闭环数字预失真线性化：间接学习方法。](images/c17f005.jpg)

[图 17.5](#c17.xhtml#R_c17-fig-0005) 闭环数字预失真线性化：间接学习方法。

![图 17.6 闭环数字预失真线性化：直接学习方法。](images/c17f006.jpg)

[图 17.6](#c17.xhtml#R_c17-fig-0006) 闭环数字预失真线性化：直接学习方法。

然而，考虑直接学习方法时，![images](images/c17-i0042.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="bold-italic">&#916;</mi><mi>w</mi></mrow></math> 是通过求解以下 `LS` 解得到的，

[(17.12)](#c17.xhtml#c17-R_disp-0012)![equation](images/c17-math-0012.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mi mathvariant="bold-italic">&#916;</mi> <mi>w</mi> <mo>=</mo> <msup> <mrow> <mfenced open="(" close=")" separators=""> <mrow> <msup> <mi mathvariant="bold-italic">U</mi> <mi mathvariant="bold">H</mi> </msup> <mi mathvariant="bold-italic">U</mi> </mrow> </mfenced> </mrow> <mrow> <mo>&#8722;</mo> <mn>1</mn> </mrow> </msup> <msup> <mi mathvariant="bold-italic">U</mi> <mi mathvariant="bold">H</mi> </msup> <mi mathvariant="bold-italic">e</mi> </mrow> </math>

其中 ![images](images/c17-i0043.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="bold-italic">e</mi></mrow></math> 是辨识误差的 ![images](images/c17-i0044.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>N</mi><mo>&#215;</mo><mn>1</mn></mrow></math> 向量，定义为

(17.13)![equation](images/c17-math-0013.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mi mathvariant="bold-italic">e</mi> <mo>=</mo> <mfrac> <mi mathvariant="bold-italic">y</mi> <mrow> <msub> <mi>G</mi> <mn>0</mn> </msub> </mrow> </mfrac> <mo>&#8722;</mo> <mi mathvariant="bold-italic">u</mi> </mrow> </math>

其中 ![images](images/c17-i0045.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>G</mi><mn>0</mn></msub></mrow></math> 决定 PA 的期望线性增益，而 ![images](images/c17-i0046.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="bold-italic">y</mi></mrow></math> 和 ![images](images/c17-i0047.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="bold-italic">u</mi></mrow></math> 分别是 PA 输出和发射输入的 ![images](images/c17-i0048.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>N</mi><mo>&#215;</mo><mn>1</mn></mrow></math> 向量。

### 17.2.4 正则化

`LS` 方法在处理大数据集时能够很好地逼近超定系统的解。然而，它可能面临 `underfitting` 或 `overfitting` 的风险（参见 [图 17.7](#c17.xhtml#c17-fig-0007)）。欠拟合模型在模型描述中缺乏必要的系数。相反，过拟合模型包含的参数多于模型实际需要的。欠拟合和过拟合模型都倾向于错误表示训练数据，因此预测性能较差。

