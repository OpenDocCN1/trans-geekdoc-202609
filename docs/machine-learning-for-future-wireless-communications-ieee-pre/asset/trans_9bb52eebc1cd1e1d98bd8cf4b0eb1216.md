
`PA` 模型系数的估计，如公式 ([17.6](#c17.xhtml#c17-disp-0006)) 所描述，假设模型基函数的独立性。当基函数相关且数据矩阵的列 ![images](images/c17-i0049.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="bold-italic">X</mi></mrow></math> 存在近似线性相关时，协方差矩阵的逆 ![images](images/c17-i0050.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msup><mrow><mo stretchy="false">(</mo><msup><mi mathvariant="bold-italic">X</mi><mi>H</mi></msup><mi mathvariant="bold-italic">X</mi><mo stretchy="false">)</mo></mrow><mrow><mo>&#8722;</mo><mn>1</mn></mrow></msup></mrow></math> 接近奇异。因此，`LS` 估计对观测响应 ![images](images/c17-i0051.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="bold-italic">y</mi></mrow></math> 中的随机误差（例如随机噪声、测量装置的量化噪声等）变得高度敏感。

![图 17.7 功率放大器行为的最小二乘辨识中的欠拟合和过拟合。](images/c17f007.jpg)

[图 17.7](#c17.xhtml#R_c17-fig-0007) 最小二乘辨识功率放大器行为中的欠拟合和过拟合。

正则化是通过引入额外信息以防止过拟合的过程。一般而言，正则化技术的主要思想是在成本函数中添加正则化项 ![images](images/c17-i0052.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="bold-italic">R</mi><mo stretchy="false">(</mo><mi mathvariant="bold-italic">w</mi><mo stretchy="false">)</mo></mrow></math>：

(17.14)![equation](images/c17-math-0014.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mi>J</mi> <mo stretchy="false">(</mo> <mi mathvariant="bold-italic">w</mi> <mo stretchy="false">)</mo> <mo>=</mo> <mo>&#8214;</mo> <mi mathvariant="bold-italic">y</mi> <mo>&#8722;</mo> <mi mathvariant="bold-italic">X</mi> <mi mathvariant="bold-italic">w</mi> <msubsup> <mrow> <mo>&#8214;</mo> </mrow> <mn>2</mn> <mn>2</mn> </msubsup> <mo>+</mo> <mi>&#955;</mi> <mi mathvariant="bold-italic">R</mi> <mo stretchy="false">(</mo> <mi mathvariant="bold-italic">w</mi> <mo stretchy="false">)</mo> </mrow> </math>

下面将对正则化项进行具体化。因此，`Ridge` 回归、最小绝对收缩和选择算子（`LASSO`）以及 `elastic net` 的成本函数将作为普通最小二乘（`OLS`）回归成本函数的约束版本呈现。在 `Ridge` 回归或 `Tikhonov` 正则化（Tikhonov and Arsensin ([1977](#c17.xhtml#c17-bib-0113))）的情况下，它将受到系数向量平方 ![images](images/c17-i0053.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>&#8467;</mi><mn>2</mn></msub></mrow></math>‐范数（欧几里得范数）的约束，而在 `LASSO`（Tibshirani ([1994](#c17.xhtml#c17-bib-0111))）的情况下，它将受到系数向量 ![images](images/c17-i0054.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>&#8467;</mi><mn>1</mn></msub></mrow></math>‐范数的约束。最后，`elastic net`（Zou and Hastie ([2005](#c17.xhtml#c17-bib-0130))）同时结合了 `Ridge` 回归和 `Lasso` 约束。

### 17.2.4.1 Ridge Regression or Tikhonov `L2` Regularization

在 `L2` 正则化中，目标是在系数平方和的约束下最小化残差平方和：

(17.15)![equation](images/c17-math-0015.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mtable columnalign="right left left"> <mtr> <mtd class="eqnarray-1"/> <mtd/> <mtd class="eqnarray-3"> <munder> <mi>min</mi> <mi mathvariant="bold-italic">w</mi> </munder> <mspace width="1em"/> <munderover> <mo stretchy="false" movablelimits="false">&#8721;</mo> <mrow> <mi>n</mi> <mo>=</mo> <mn>0</mn> </mrow> <mrow> <mi>N</mi> <mo>&#8722;</mo> <mn>1</mn> </mrow> </munderover> <msup> <mrow> <mo stretchy="false">(</mo> <mi>y</mi> <mo stretchy="false">\[</mo> <mi>n</mi> <mo stretchy="false">\]</mo> <mo>&#8722;</mo> <msubsup> <mi mathvariant="bold-italic">&#981;</mi> <mi>x</mi> <mi>H</mi> </msubsup> <mo stretchy="false">\[</mo> <mi>n</mi> <mo stretchy="false">\]</mo> <mi mathvariant="bold-italic">w</mi> <mo stretchy="false">\[</mo> <mi>n</mi> <mo stretchy="false">\]</mo> <mo stretchy="false">)</mo> </mrow> <mn>2</mn> </msup> </mtd> </mtr> <mtr> <mtd class="eqnarray-1"/> <mtd/> <mtd class="eqnarray-3"> <mtext>subject to</mtext> <mspace width="1em"/> <munderover> <mo stretchy="false" movablelimits="false">&#8721;</mo> <mrow> <mi>i</mi> <mo>=</mo> <mn>1</mn> </mrow> <mi>M</mi> </munderover> <mo stretchy="false">&#124;</mo> <msub> <mi>w</mi> <mi>i</mi> </msub> <mo stretchy="false">\[</mo> <mi>n</mi> <mo stretchy="false">\]</mo> <msup> <mo stretchy="false">&#124;</mo> <mn>2</mn> </msup> <mo>&#8804;</mo> <msub> <mi>t</mi> <mn>2</mn> </msub> <mo>.</mo> </mtd> </mtr> </mtable> </mrow> </math>

该约束迫使系数保持在半径为 ![images](images/c17-i0057.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>t</mi><mn>2</mn></msub></mrow></math> 的球体内。如 [图 17.8](#c17.xhtml#c17-fig-0008) 所示，等高线代表最小二乘回归估计的系数取值。`Ridge` 回归或 `Tikhonov` 正则化的解是满足约束的等高线上的系数。约束成本函数也可以写成惩罚残差平方和

![图 17.8 Ridge、LASSO 和 elastic net 正则化。](images/c17f008.jpg)

[图 17.8](#c17.xhtml#R_c17-fig-0008) Ridge、LASSO 和 elastic net 正则化。

