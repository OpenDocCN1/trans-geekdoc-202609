

随机选择特征子集的原因是去相关所构建的不同树。这进一步降低了最终模型的方差，超越了袋装法。如果一个或几个特征对标签是非常强的预测因子，这些特征将被选中在许多树中拆分样本。这将导致我们的“森林”中出现许多相关的树。相关预测因子不能通过减少方差来帮助提高预测准确性。模型集成性能更好的主要原因是，好的模型可能会对同一预测达成一致，而坏模型可能会对不同预测产生分歧，因此结合它们可以多样化误差并从而减少方差。相关性使坏模型更有可能达成一致，可能会阻碍多数投票或平均值。

### 13.9.1 信用卡违约预测

在信用卡评级系统中，从潜在客户处收集数据以预测未来客户是否会违约。作为示例，我们考虑一个数据集，其中包含2005年4月至2005年9月台湾信用卡客户的违约付款、人口统计、信用数据、付款记录和账单信息[[10](#c13.xhtml#c13-bib-0011)]。每个特征向量包含26个特征，例如“信用额度”、“性别”、“教育水平”、“婚姻状况”和“年龄”。如果客户下个月违约，标签取值为1，否则为0。在程序13.19（Python）和13.20（`R`）中，构建了分类树和随机森林用于预测。

![FIGURE 13.18 Classification trees for the Taiwan credit default dataset.](images/c13f018.png)

[**FIGURE 13.18**](#c13.xhtml#R_c13-fig-0018) Classification trees for the Taiwan credit default dataset.

从[程序13.19](#c13.xhtml#c13-sec-3019)的输出中，Python中构建的分类树的各种指标，如精确率、召回率、![upper F 1](images/c13-i0508.png)<math display="inline" overflow="scroll"><msub><mi>F</mi><mn>1</mn></msub></math>‐score和准确率为：

![StartLayout 1st Row 1st Column Precision 2nd Column equals StartFraction 421 Over 421 plus 198 EndFraction equals 0.680 comma 3rd Column Recall 4th Column equals StartFraction 421 Over 421 plus 870 EndFraction equals 0.326 comma 2nd Row 1st Column f 1 hyphen score 2nd Column equals StartFraction 2 Over 1 slash 0.680 plus 1 slash 0.326 EndFraction equals 0.441 comma 3rd Column Accuracy 4th Column equals StartFraction 421 plus 4511 Over 6000 EndFraction equals 0.822 period EndLayout](images/c13-math-0062.png)<math display="block" overflow="scroll"><mtable><mtr><mtd columnalign="right"><mtext>Precision</mtext></mtd><mtd columnalign="left"><mo>=</mo><mfrac><mn>421</mn><mrow><mn>421</mn><mo>+</mo><mn>198</mn></mrow></mfrac><mo>=</mo><mn>0.680</mn><mo>,</mo><mspace width="1em"/><mspace width="0em"/></mtd><mtd columnalign="right"><mtext>Recall</mtext></mtd><mtd columnalign="left"><mo>=</mo><mfrac><mn>421</mn><mrow><mn>421</mn><mo>+</mo><mn>870</mn></mrow></mfrac><mo>=</mo><mn>0.326</mn><mo>,</mo></mtd></mtr><mtr><mtd columnalign="right"><msub><mi>f</mi><mn>1</mn></msub><mtext>&#8208;score</mtext></mtd><mtd columnalign="left"><mo>=</mo><mfrac><mn>2</mn><mrow><mn>1</mn><mo stretchy="false">/</mo><mn>0.680</mn><mo>+</mo><mn>1</mn><mo stretchy="false">/</mo><mn>0.326</mn></mrow></mfrac><mo>=</mo><mn>0.441</mn><mo>,</mo><mspace width="1em"/><mspace width="0em"/></mtd><mtd columnalign="right"><mtext>Accuracy</mtext></mtd><mtd columnalign="left"><mo>=</mo><mfrac><mrow><mn>421</mn><mo>+</mo><mn>4511</mn></mrow><mn>6000</mn></mfrac><mo>=</mo><mn>0.822</mn><mo>.</mo></mtd></mtr></mtable></math> 

同样，在Python中计算的随机森林的精确率、召回率、![upper F 1](images/c13-i0509.png)<math display="inline" overflow="scroll"><msub><mi>F</mi><mn>1</mn></msub></math>‐score和准确率为：

![StartLayout 1st Row 1st Column Precision 2nd Column equals StartFraction 491 Over 491 plus 275 EndFraction equals 0.641 comma 3rd Column Recall 4th Column equals StartFraction 491 Over 491 plus 800 EndFraction equals 0.380 comma 2nd Row 1st Column f 1 hyphen score 2nd Column equals StartFraction 2 Over 1 slash 0.641 plus 1 slash 0.380 EndFraction equals 0.477 comma 3rd Column Accuracy 4th Column equals StartFraction 491 plus 4434 Over 6000 EndFraction equals 0.821 period EndLayout](images/c13-math-0063.png)<math display="block" overflow="scroll"><mtable><mtr><mtd columnalign="right"><mtext>Precision</mtext></mtd><mtd columnalign="left"><mo>=</mo><mfrac><mn>491</mn><mrow><mn>491</mn><mo>+</mo><mn>275</mn></mrow></mfrac><mo>=</mo><mn>0.641</mn><mo>,</mo><mspace width="1em"/><mspace width="0em"/></mtd><mtd columnalign="right"><mtext>Recall</mtext></mtd><mtd columnalign="left"><mo>=</mo><mfrac><mn>491</mn><mrow><mn>491</mn><mo>+</mo><mn>800</mn></mrow></mfrac><mo>=</mo><mn>0.380</mn><mo>,</mo></mtd></mtr><mtr><mtd columnalign="right"><msub><mi>f</mi><mn>1</mn></msub><mtext>&#8208;score</mtext></mtd><mtd columnalign="left"><mo>=</mo><mfrac><mn>2</mn><mrow><mn>1</mn><mo stretchy="false">/</mo><mn>0.641</mn><mo>+</mo><mn>1</mn><mo stretchy="false">/</mo><mn>0.380</mn></mrow></mfrac><mo>=</mo><mn>0.477</mn><mo>,</mo><mspace width="1em"/><mspace width="0em"/></mtd><mtd columnalign="right"><mtext>Accuracy</mtext></mtd><mtd columnalign="left"><mo>=</mo><mfrac><mrow><mn>491</mn><mo>+</mo><mn>4434</mn></mrow><mn>6000</mn></mfrac><mo>=</mo><mn>0.821</mn><mo>.</mo></mtd></mtr></mtable></math> 

从[图13.18](#c13.xhtml#c13-fig-0018)a中，Python仅根据26个特征变量中的2个（即`PAY_0`和`PAY_2`）拆分数据集，它们分别代表2005年9月和2005年8月的还款状态。它们记录了客户延迟付款的月数，`‐1`表示无延迟，最大值为九个月。确实，如果客户的付款已经延迟数月，则可能会违约，Python找到的神奇数字是2（大于1.5的最小整数）。同样，从[图13.18](#c13.xhtml#c13-fig-0018)b中，`R`根据`PAY_0`拆分数据集，使用相同的神奇数字2。我们在此采用`caret`库中的`confusionMatrix()`函数来计算`R`中的各种性能指标。读者也可以参考我们的用户指南[[2](#c13.xhtml#c13-bib-0002)]以获取更多讨论。

## 13.A 附录

### 13.A.1 信息论中的熵

我们在此阐述在[第*13.2节](#c13.xhtml#c13-sec-0003)中介绍的熵的定义及其信息论重要性。读者可以参考[[3](#c13.xhtml#c13-bib-0003)]以获取更多细节。设![normal x 1 comma ellipsis comma normal x Subscript n Baseline element-of script upper X](images/c13-i0510.png)<math display="inline" overflow="scroll"><msub><mi mathvariant="normal">x</mi><mn>1</mn></msub><mo>,</mo><mo>&#8230;</mo><mo>,</mo><msub><mi mathvariant="normal">x</mi><mi>n</mi></msub><mo>&#8712;</mo><mi mathvariant="script">X</mi></math>为具有共同概率质量函数![p left-parenthesis x right-parenthesis](images/c13-i0511.png)<math display="inline" overflow="scroll"><mi>p</mi><mo stretchy="false">(</mo><mi>x</mi><mo stretchy="false">)</mo></math>的独立同分布离散随机变量。大数定律的弱形式直接意味着*渐近等分配性质*（AEP），即：

