

![ln upper L left-parenthesis bold-italic beta semicolon bold-italic x 1 comma ellipsis comma bold-italic x Subscript n Baseline comma y 1 comma ellipsis comma y Subscript n Baseline right-parenthesis equals sigma-summation Underscript i equals 1 Overscript n Endscripts left-parenthesis y Subscript i Baseline bold-italic x Subscript i Superscript down-tack Baseline bold-italic beta minus e Superscript bold-italic x Super Subscript i Super Superscript down-tack Superscript bold-italic beta Baseline minus ln left-parenthesis y Subscript i Baseline factorial right-parenthesis right-parenthesis period](images/c10-math-0046.png)<math display="block" overflow="scroll"><mi mathvariant="normal">ln</mi><mi>L</mi><mo stretchy="false">(</mo><mi mathvariant="bold-italic">&#946;</mi><mo>;</mo><msub><mi mathvariant="bold-italic">x</mi><mn>1</mn></msub><mo>,</mo><mo>&#8230;</mo><mo>,</mo><msub><mi mathvariant="bold-italic">x</mi><mi>n</mi></msub><mo>,</mo><msub><mi>y</mi><mn>1</mn></msub><mo>,</mo><mo>&#8230;</mo><mo>,</mo><msub><mi>y</mi><mi>n</mi></msub><mo stretchy="false">)</mo><mo>=</mo><munderover><mrow><mo stretchy="false" movablelimits="false">&#8721;</mo></mrow><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mrow><mi>n</mi></mrow></munderover><mfenced open="(" close=")" separators=""><mrow><msub><mi>y</mi><mi>i</mi></msub><msubsup><mi mathvariant="bold-italic">x</mi><mi>i</mi><mo>&#8868;</mo></msubsup><mi mathvariant="bold-italic">&#946;</mi><mo>&#8722;</mo><msup><mi>e</mi><mrow><msubsup><mi mathvariant="bold-italic">x</mi><mi>i</mi><mo>&#8868;</mo></msubsup><mi mathvariant="bold-italic">&#946;</mi></mrow></msup><mo>&#8722;</mo><mi mathvariant="normal">ln</mi><mo stretchy="false">(</mo><msub><mi>y</mi><mi>i</mi></msub><mo>!</mo><mo stretchy="false">)</mo></mrow></mfenced><mo>.</mo></math>

一般来说，![nabla Subscript bold-italic beta Baseline upper L left-parenthesis bold-italic beta right-parenthesis equals bold 0](images/c10-i0303.png)<math display="inline" overflow="scroll"><msub><mo>&#8711;</mo><mi mathvariant="bold-italic">&#946;</mi></msub><mi>L</mi><mo stretchy="false">(</mo><mi mathvariant="bold-italic">&#946;</mi><mo stretchy="false">)</mo><mo>=</mo><mn mathvariant="bold">0</mn></math>没有解析解，我们可以通过通常的高斯-牛顿算法找到数值最大化器 ![ModifyingAbove bold-italic beta With Ì‚ Subscript MLE](images/c10-i0304.png)<math display="inline" overflow="scroll"><msub><mrow><mover accent="true"><mi mathvariant="bold-italic">&#946;</mi><mo>&#770;</mo></mover></mrow><mtext>MLE</mtext></msub></math>。

接下来，我们给出泊松回归在预测计数方面的应用。*1976年收入动态小组数据集*

在[方案10.19](#c10.xhtml#c10-sec-3019)中，**R**报告称，18岁以下儿童数量与大多数特征之间的关系不显著，因此我们首先移除不显著的特征，然后再次拟合模型。这种向后消元过程重复进行，直到所有剩余特征都足够显著。

[方案10.20](#c10.xhtml#c10-sec-3020)展示了包含剩余特征`hoursw`、`agew`和`experience`的最终模型。首先，特征`hoursw`代表妻子1975年的工作时长。其系数为负（![negative 0.0001087](images/c10-i0305.png)<math display="inline" overflow="scroll"><mo>&#8722;</mo><mn>0.0001087</mn></math>），这意味着如果妻子工作时间更长，她预期的子女数量会减少。其次，特征`experience`是妻子在劳动力市场中之前工作经验的实际年数。其负系数（![negative 0.0259452](images/c10-i0306.png)<math display="inline" overflow="scroll"><mo>&#8722;</mo><mn>0.0259452</mn></math>）表明妻子的工作经验与她预期的子女数量之间存在负相关。最后，我们还观察到响应变量与特征`agew`之间存在类似的负相关。

计数变量与特征之间负相关的合理解释如下：如果一名女性花更多时间工作，她可用于家庭的时间就会减少，因此她倾向于生育更少的孩子。最后，特征`agew`代表妻子的年龄，其系数为负（![negative 0.0550786](images/c10-i0307.png)<math display="inline" overflow="scroll"><mo>&#8722;</mo><mn>0.0550786</mn></math>）。这种负相关可以归因于这样一个事实：随着母亲年龄增长，她的孩子最终会成年，导致18岁以下儿童数量下降；此外，随着妻子年龄增长，她倾向于不再生育更多孩子。

## 10.6 模型评估与实际考虑

### 10.6.1 模型选择：向后消元与信息准则

